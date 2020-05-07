---
title: Regularne biblioteki DLL MFC połączone dynamicznie z MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
ms.openlocfilehash: 3bfed5f75dab4c501708950fdb99f53c40ec142c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315004"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>Regularne biblioteki DLL MFC połączone dynamicznie z MFC

Zwykła Biblioteka MFC dynamicznie połączona z MFC jest biblioteką DLL, która używa wewnętrznie MFC, a eksportowane funkcje w bibliotece DLL mogą być wywoływane przez pliki wykonywalne MFC lub inne niż MFC. Jak opisano w opisie, ten rodzaj biblioteki DLL jest tworzony przy użyciu biblioteki dołączanej dynamicznie MFC (znanej również jako udostępniona wersja MFC). Funkcje są zwykle eksportowane ze zwykłej biblioteki MFC DLL przy użyciu standardowego interfejsu języka C.

Należy dodać `AFX_MANAGE_STATE` makro na początku wszystkich wyeksportowanych funkcji w zwykłych bibliotekach DLL MFC, które dynamicznie łączą się z MFC w celu ustawienia bieżącego stanu modułu dla biblioteki DLL. W tym celu należy dodać następujący wiersz kodu do początku funkcji wyeksportowanych z biblioteki DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Zwykła Biblioteka MFC DLL, dynamicznie połączona z MFC, ma następujące funkcje:

- Jest to nowy typ biblioteki DLL wprowadzonej przez Visual C++ 4,0.

- Plik wykonywalny klienta można napisać w dowolnym języku, który obsługuje biblioteki DLL (C, C++, Pascal, Visual Basic itd.); nie musi to być aplikacja MFC.

- W przeciwieństwie do statycznie połączonej, regularnej biblioteki MFC DLL, ten typ biblioteki DLL jest dynamicznie połączony z biblioteką DLL MFC (znaną również jako udostępniona biblioteka MFC DLL).

- Biblioteka importowana MFC połączona z tym typem biblioteki DLL jest taka sama, jak w przypadku bibliotek DLL lub aplikacji rozszerzenia MFC, przy użyciu biblioteki MFC DLL: MFCxx (D). lib.

Zwykła Biblioteka MFC DLL, dynamicznie połączona z MFC, ma następujące wymagania:

- Te biblioteki DLL są kompilowane ze zdefiniowanym **_AFXDLL** , podobnie jak plik wykonywalny, który jest dynamicznie połączony z biblioteką DLL MFC. Ale **_USRDLL** jest również zdefiniowana, podobnie jak zwykła Biblioteka DLL MFC, która jest statycznie połączona z MFC.

- Ten typ biblioteki DLL musi utworzyć wystąpienie `CWinApp`klasy pochodnej.

- Ten typ biblioteki DLL używa `DllMain` dostarczone przez MFC. Umieść wszystkie kod inicjalizacji specyficzny dla biblioteki `InitInstance` dll w funkcji członkowskiej i `ExitInstance` kod zakończenia w taki sposób, jak w przypadku normalnej aplikacji MFC.

Ponieważ ten rodzaj biblioteki DLL używa biblioteki MFC z dołączaniem dynamicznym, należy jawnie ustawić bieżący stan modułu dla biblioteki DLL. Aby to zrobić, użyj makra [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) na początku każdej funkcji wyeksportowanej z biblioteki DLL.

regularne biblioteki DLL MFC muszą mieć `CWinApp`klasę pochodną i pojedynczy obiekt tej klasy aplikacji, tak jak aplikacja MFC. Jednak `CWinApp` obiekt biblioteki DLL nie ma głównej pompki komunikatów, ponieważ `CWinApp` obiekt aplikacji.

Należy zauważyć, `CWinApp::Run` że mechanizm nie ma zastosowania do biblioteki DLL, ponieważ aplikacja jest właścicielem głównej pompy komunikatów. Jeśli biblioteka DLL wywołuje Niemodalne okna dialogowe lub ma własne główne okno ramek, główna pompa komunikatów aplikacji musi wywołać procedurę wyeksportowanej biblioteki DLL, która wywołuje `CWinApp::PreTranslateMessage`.

Umieść wszystkie inicjalizacje specyficzne dla biblioteki DLL `CWinApp::InitInstance` w funkcji składowej tak jak w przypadku normalnej aplikacji MFC. Funkcja `CWinApp::ExitInstance` członkowska klasy `CWinApp` pochodnej jest wywoływana z funkcji dostarczonej `DllMain` przez MFC, zanim Biblioteka DLL zostanie zwolniona.

W aplikacji należy dystrybuować udostępnione biblioteki DLL MFCx0. dll i pliku MSVCR * 0. dll (lub podobne pliki).

Biblioteka DLL, która jest dynamicznie połączona z MFC, nie może również statycznie łączyć się z MFC. Aplikacje łączą się z regularnymi bibliotekami DLL MFC połączonymi dynamicznie z MFC, podobnie jak w przypadku każdej innej biblioteki DLL.

Symbole są zwykle eksportowane z zwykłej biblioteki MFC DLL przy użyciu standardowego interfejsu języka C. Deklaracja funkcji eksportowanej ze zwykłej biblioteki MFC DLL wygląda następująco:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Wszystkie alokacje pamięci w ramach zwykłej biblioteki MFC DLL powinny pozostać w bibliotece DLL; Biblioteka DLL nie powinna przekazać do wywołującego pliku wykonywalnego ani odebrać z niego żadnego z następujących elementów:

- wskaźniki do obiektów MFC

- wskaźniki do pamięci przydzielonej przez MFC

Jeśli trzeba wykonać dowolne z powyższych czynności lub w przypadku konieczności przekazania obiektów pochodnych MFC między wywołującym plik wykonywalny a biblioteką DLL, należy utworzyć bibliotekę DLL rozszerzenia MFC.

Można bezpiecznie przekazać wskaźniki do pamięci, która została przypisana przez biblioteki uruchomieniowe C między aplikacją a biblioteką DLL tylko w przypadku wykonywania kopii danych. Nie należy usuwać ani zmieniać rozmiarów tych wskaźników ani ich używać bez tworzenia kopii pamięci.

Podczas kompilowania zwykłej biblioteki MFC DLL, która łączy dynamicznie z MFC, należy użyć [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) makro, aby prawidłowo przełączyć stan modułu MFC. W tym celu należy dodać następujący wiersz kodu do początku funkcji wyeksportowanych z biblioteki DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Makro **AFX_MANAGE_STATE** nie powinno być używane w zwykłych bibliotekach DLL MFC, które statycznie łączą się z MFC lub w bibliotekach DLL rozszerzenia MFC. Aby uzyskać więcej informacji, zobacz [Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md).

Aby zapoznać się z przykładem sposobu pisania, kompilowania i używania zwykłej biblioteki MFC DLL, zobacz przykład [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Aby uzyskać więcej informacji na temat zwykłych bibliotek DLL MFC, które dynamicznie łączą się z MFC, zobacz sekcję zatytułowaną "Konwertowanie DLLScreenCap na dynamiczne łączenie z biblioteką MFC DLL" w postaci abstrakcyjnej dla przykładu.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Inicjowanie zwykłych bibliotek DLL MFC](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Stany modułu zwykłej biblioteki DLL MFC połączonej dynamicznie z MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Korzystanie z bibliotek DLL rozszerzeń MFC w bazie danych, OLE i Sockets w zwykłych bibliotekach DLL MFC](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>Zobacz też

[Rodzaje bibliotek DLL](kinds-of-dlls.md)
