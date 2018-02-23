---
title: "Biblioteki DLL MFC regularne połączone statycznie z MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ef25785e3d1e37ee622572f03fce56b1fa236aa
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>Biblioteki DLL MFC regularne połączone statycznie z MFC
Regularne, które biblioteki MFC DLL połączone statycznie z MFC jest bibliotekę DLL, która MFC jest używane wewnętrznie i eksportowanych funkcji w bibliotece DLL może być wywoływany przez pliki wykonywalne MFC lub innego typu niż MFC. Zgodnie z opisem w nazwę, tego rodzaju biblioteki DLL jest utworzony przy użyciu wersji biblioteki dołączanej statycznie z MFC. Funkcje eksportowane są zazwyczaj ze standardowych biblioteki MFC DLL przy użyciu standardowych interfejsów C. Na przykład sposobu zapisu, tworzenia i używania regularną bibliotekę DLL MFC Zobacz przykład [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap).  
  
 Należy pamiętać, że termin USRDLL nie jest już używany w dokumentacji Visual C++. Regularne biblioteki DLL MFC, która jest połączone statycznie z MFC ma takie same charakterystyki jak wcześniejsze USRDLL.  
  
 Regularne biblioteki DLL MFC, połączone statycznie z MFC, zawiera następujące funkcje:  
  
-   Plik wykonywalny klienta mogą być napisane w dowolnym języku, który obsługuje korzystanie z biblioteki dll (C, C++ Pascal, Visual Basic i tak dalej); nie ma być aplikacji MFC.  
  
-   Biblioteki DLL można połączyć z tej samej biblioteki dołączanej statycznie MFC używane przez aplikacje. Nie ma osobną wersję biblioteki dołączanej statycznie dla bibliotek DLL.  
  
-   Przed wersja 4.0 MFC USRDLLs dostarczony do tego samego typu funkcji jako MFC DLL połączone statycznie z MFC. Począwszy od programu Visual C++ w wersji 4.0 termin USRDLL jest przestarzała.  
  
 Regularne biblioteki DLL MFC, połączone statycznie z MFC, ma następujące wymagania:  
  
-   Tego typu biblioteki DLL należy utworzyć wystąpienia klasy pochodzącej od `CWinApp`.  
  
-   Ten typ korzysta z biblioteki DLL `DllMain` dostarczonych przez MFC. Umieścić cały kod inicjowania specyficznej dla biblioteki DLL w `InitInstance` funkcji i kończenie działania kod elementu członkowskiego w `ExitInstance` jak normalne aplikacji MFC.  
  
-   Mimo że termin USRDLL jest przestarzały, nadal należy zdefiniować "**_usrdll —**" w wierszu polecenia kompilatora. Ta definicja Określa, które deklaracje dołączana z plików nagłówek MFC.  
  
 Regularne biblioteki DLL MFC musi mieć `CWinApp`-pochodzi z klasy i pojedynczego obiektu dla tej klasy aplikacji, tak jak w przypadku aplikacji MFC. Jednak `CWinApp` obiekt biblioteki DLL nie ma pompa głównej wiadomości, tak jak w przypadku `CWinApp` obiektu aplikacji.  
  
 Należy pamiętać, że `CWinApp::Run` mechanizm nie ma zastosowania do biblioteki DLL, ponieważ aplikacja jest właścicielem pompa głównej wiadomości. Ma główne okno ramowe własnej biblioteki DLL lub otwiera Niemodalne okna dialogowe, przekazywanie komunikatów głównego aplikacji, należy wywołać procedury wyeksportowane przez bibliotekę DLL, która z kolei wywołuje `CWinApp::PreTranslateMessage` funkcji członkowskiej klasy obiektu aplikacji DLL.  
  
 Na przykład tej funkcji, zobacz przykład DLLScreenCap.  
  
 Symbole zwykle są eksportowane z zwykły biblioteki MFC DLL przy użyciu standardowych interfejsów C. Deklaracja funkcji wyeksportowanej z regularną bibliotekę DLL MFC będzie wyglądać mniej więcej tak:  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 Alokacja pamięci w regularnych bibliotek DLL MFC powinny pozostać w pliku DLL; biblioteki DLL nie należy przekazać do ani otrzymywać wywołanie pliku wykonywalnego jedną z następujących czynności:  
  
-   Wskaźniki do obiektów MFC  
  
-   Wskaźniki do pamięci przydzielonej przez MFC  
  
 Jeśli musisz wykonać żadnej z powyższych lub muszą podawać pochodnych MFC obiektów między wywołanie pliku wykonywalnego i Biblioteka DLL, należy utworzyć bibliotekę DLL rozszerzenia MFC.  
  
 Jest to bezpieczne przekazać wskaźników do pamięci, które zostały przydzielone przez biblioteki wykonawcze języka C między aplikacją a biblioteki DLL tylko wtedy, gdy wykonanie kopii danych. Nie musisz usunąć lub zmienić rozmiar te wskaźniki lub z nich korzystać bez kopii pamięci.  
  
 Biblioteki DLL, która jest połączone statycznie z MFC również dynamicznie nie można połączyć z udostępnionej biblioteki DLL MFC. Biblioteki DLL, która jest połączone statycznie z MFC dynamicznie jest powiązany z aplikacji, podobnie jak inne biblioteki DLL; aplikacje link jej podobnie jak inne biblioteki DLL.  
  
 Standardowe biblioteki dołączanej statycznie MFC są nazywane zgodnie z Konwencją opisanego w [konwencje nazewnictwa bibliotek MFC dll](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Jednak z MFC w wersji 3.0 i nowszych go nie trzeba już ręcznie określić do konsolidatora wersji biblioteki MFC, które mają zostać połączone w. Zamiast tego pliki nagłówków MFC automatycznie określić poprawną wersję biblioteki MFC, aby połączyć w oparciu o preprocesora definiuje, takich jak  **\_debugowania** lub **_unicode —**. Pliki nagłówka MFC Dodaj dyrektywy /DEFAULTLIB poinstruowanie konsolidator łącze w określonej wersji biblioteki MFC.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Inicjowanie MFC dll](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [Używanie bibliotek DLL baz danych, OLE i rozszerzeń MFC gniazd w zwykłych bibliotekach MFC DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Tworzenie biblioteki DLL MFC](../mfc/reference/mfc-dll-wizard.md)  
  
-   [Zwykłe biblioteki DLL MFC połączone dynamicznie z MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Biblioteki DLL rozszerzeń MFC](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Rodzaje bibliotek DLL](../build/kinds-of-dlls.md)