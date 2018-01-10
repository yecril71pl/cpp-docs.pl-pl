---
title: "Biblioteki DLL MFC regularne połączone dynamicznie z MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 930d56f7bc296225e6fefcf92e49087a2aed99cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>Biblioteki DLL MFC regularne połączone dynamicznie z MFC
Regularne, które biblioteki MFC DLL połączone dynamicznie z MFC jest bibliotekę DLL, która MFC jest używane wewnętrznie i eksportowanych funkcji w bibliotece DLL może być wywoływany przez pliki wykonywalne MFC lub innego typu niż MFC. Zgodnie z opisem w nazwę, tego rodzaju biblioteki DLL jest utworzony przy użyciu wersja biblioteki DLL MFC (znanej także jako udostępniony wersja MFC). Funkcje eksportowane są zazwyczaj ze standardowych biblioteki MFC DLL przy użyciu standardowych interfejsów C.  
  
 Należy dodać `AFX_MANAGE_STATE` makro na początku eksportowane funkcje w zwykłych bibliotekach DLL MFC, która łączy dynamicznie z MFC, aby ustawić bieżący stan modułu dla biblioteki DLL. Można to zrobić, dodając następujący wiersz kodu na początku funkcji wyeksportowanych z biblioteki DLL:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 Regularne biblioteki MFC DLL połączone dynamicznie z MFC zawiera następujące funkcje:  
  
-   Jest to nowy typ biblioteki DLL wprowadzone przez Visual C++ 4.0.  
  
-   Plik wykonywalny klienta mogą być napisane w dowolnym języku, który obsługuje korzystanie z biblioteki dll (C, C++ Pascal, Visual Basic i tak dalej); nie ma być aplikacji MFC.  
  
-   W przeciwieństwie do statycznie połączone regularne biblioteki DLL MFC tego rodzaju biblioteki DLL jest połączona dynamicznie do biblioteki MFC DLL (znanej także jako udostępnionej biblioteki MFC DLL).  
  
-   Importuj biblioteki MFC, połączony z tego typu biblioteki DLL jest taka sama jak biblioteki DLL rozszerzenia MFC lub aplikacji przy użyciu biblioteki MFC DLL: .lib MFCxx (D).  
  
 Regularne biblioteki MFC DLL połączone dynamicznie z MFC ma następujące wymagania:  
  
-   Te biblioteki DLL są kompilowane przy użyciu **_AFXDLL** zdefiniowane, podobnie jak plik wykonywalny, który jest połączona dynamicznie biblioteki DLL MFC. Ale **_usrdll —** jest także zdefiniowana, podobnie jak regularne biblioteki DLL MFC, która jest połączone statycznie z MFC.  
  
-   Ten typ biblioteki DLL należy utworzyć wystąpienia `CWinApp`-klasy.  
  
-   Ten typ korzysta z biblioteki DLL `DllMain` dostarczonych przez MFC. Umieścić cały kod inicjowania specyficznej dla biblioteki DLL w `InitInstance` funkcji i kończenie działania kod elementu członkowskiego w `ExitInstance` jak normalne aplikacji MFC.  
  
 Ponieważ tego rodzaju DLL korzysta z wersji biblioteki DLL MFC, użytkownik musi jawnie ustawione bieżący stan modułu dla biblioteki DLL. Aby to zrobić, użyj [afx_manage_state —](../mfc/reference/extension-dll-macros.md#afx_manage_state) makro na początku każdej funkcji wyeksportowane z biblioteki DLL.  
  
 Regularne biblioteki DLL MFC musi mieć `CWinApp`-pochodzi z klasy i pojedynczego obiektu dla tej klasy aplikacji, tak jak w przypadku aplikacji MFC. Jednak `CWinApp` obiekt biblioteki DLL nie ma pompa głównej wiadomości, tak jak w przypadku `CWinApp` obiektu aplikacji.  
  
 Należy pamiętać, że `CWinApp::Run` mechanizm nie ma zastosowania do biblioteki DLL, ponieważ aplikacja jest właścicielem pompa głównej wiadomości. Jeśli ma główne okno ramowe własnej biblioteki DLL lub wyświetlenie Niemodalne okna dialogowe, przekazywanie komunikatów głównego aplikacji należy wywołać procedury wyeksportowane biblioteki DLL, która wywołuje `CWinApp::PreTranslateMessage`.  
  
 Umieść wszystkie inicjowania specyficznej dla biblioteki DLL w `CWinApp::InitInstance` funkcji członkowskiej jak normalne aplikacji MFC. `CWinApp::ExitInstance` Funkcji członkowskiej klasy z `CWinApp` klasy pochodnej jest wywoływana z MFC podane `DllMain` funkcji przed biblioteki DLL jest zwalniany.  
  
 Musisz przeprowadzić dystrybucję udostępnionego MFCx0.dll bibliotek DLL i Msvcr*0.dll (lub podobny plików) z aplikacją.  
  
 Biblioteki DLL, która jest połączona dynamicznie z MFC nie może połączyć również statycznie z MFC. Łącze aplikacji do biblioteki MFC DLL połączone dynamicznie z MFC go tak samo jak inne biblioteki DLL.  
  
 Symbole zwykle są eksportowane z zwykły biblioteki MFC DLL przy użyciu standardowych interfejsów C. Deklaracja funkcji wyeksportowanej z regularną bibliotekę DLL MFC wygląda następująco:  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 Alokacja pamięci w regularnych bibliotek DLL MFC powinny pozostać w pliku DLL; biblioteki DLL nie należy przekazać do ani otrzymywać wywołanie pliku wykonywalnego jedną z następujących czynności:  
  
-   Wskaźniki do obiektów MFC  
  
-   Wskaźniki do pamięci przydzielonej przez MFC  
  
 Jeśli musisz wykonać żadnej z powyższych, czy musisz przekazać pochodnych MFC obiektów między wywołanie pliku wykonywalnego i Biblioteka DLL, należy utworzyć bibliotekę DLL rozszerzenia MFC.  
  
 Jest to bezpieczne przekazać wskaźników do pamięci, które zostały przydzielone przez biblioteki wykonawcze języka C między aplikacją a biblioteki DLL tylko wtedy, gdy wykonanie kopii danych. Nie musisz usunąć lub zmienić rozmiar te wskaźniki lub z nich korzystać bez kopii pamięci.  
  
 Podczas tworzenia regularną bibliotekę DLL MFC, który dynamicznie łączy się MFC, musisz użyć makra [afx_manage_state —](../mfc/reference/extension-dll-macros.md#afx_manage_state) poprawnie przełączyć stanu modułu MFC. Można to zrobić, dodając następujący wiersz kodu na początku funkcji wyeksportowanych z biblioteki DLL:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 **Afx_manage_state —** makro nie powinna być używana w zwykłych bibliotekach DLL MFC, która łączy statycznie z MFC lub biblioteki DLL rozszerzeń MFC. Aby uzyskać więcej informacji, zobacz [Zarządzanie danych stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md).  
  
 Na przykład sposobu zapisu, tworzenia i używania regularną bibliotekę DLL MFC Zobacz przykład [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Aby uzyskać więcej informacji na temat regularne biblioteki DLL MFC, która łączy dynamicznie z MFC zobacz sekcję zatytułowany "Konwertowanie DLLScreenCap do dynamicznie łącza z biblioteki MFC DLL" abstract przykładowej.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Inicjowanie MFC dll](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Stany modułu zwykłej biblioteki MFC DLL połączone dynamicznie z MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
  
-   [Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [Używanie bibliotek DLL baz danych, OLE i rozszerzeń MFC gniazd w zwykłych bibliotekach MFC DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Rodzaje bibliotek DLL](../build/kinds-of-dlls.md)