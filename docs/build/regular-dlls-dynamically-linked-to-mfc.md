---
title: Zwykłe biblioteki DLL MFC połączone dynamicznie z MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
ms.openlocfilehash: 550391d51560ff0beca8252ffb6193dd1e4d89b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632391"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>Zwykłe biblioteki DLL MFC połączone dynamicznie z MFC

Wyrażenie, które biblioteki MFC DLL łączonej dynamicznie z MFC jest biblioteki DLL, która używa wewnętrznie MFC i eksportowanych funkcji w bibliotece DLL może być wywoływany przez pliki wykonywalne MFC lub inne niż MFC. Zgodnie z opisem w nazwę tego rodzaju DLL został skompilowany przy użyciu wersji biblioteki DLL MFC (znany także jako udostępnionej wersja MFC). Funkcje eksportowane są zwykle od zwykłej biblioteki MFC DLL za pomocą standardowego interfejsu C.

Należy dodać `AFX_MANAGE_STATE` — makro na początku wszystkich eksportowanych funkcji w zwykłych bibliotekach MFC dll, która łączy dynamicznie MFC, aby ustawić bieżący stan modułu dla biblioteki DLL. Można to zrobić, dodając następujący wiersz kodu na początku funkcji wyeksportowanych z biblioteki DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Regularne biblioteki MFC DLL łączonej dynamicznie z MFC ma następujące cechy:

- Jest to nowy typ biblioteki DLL wprowadzone przez Visual C++ 4.0.

- Klient wykonywalny mogą być napisane w dowolnym języku, który obsługuje korzystanie z biblioteki dll (C, C++, Pascal, Visual Basic i tak dalej); nie ma być aplikacji MFC.

- W odróżnieniu od statycznie łączonych regularnej biblioteki DLL MFC tego rodzaju DLL dynamicznie połączone z biblioteki MFC DLL (znany także jako udostępnionej biblioteki MFC DLL).

- Importuj biblioteki MFC, połączone z tego rodzaju DLL jest taka sama, jedną dla bibliotek DLL rozszerzeń MFC lub aplikacji przy użyciu biblioteki MFC DLL: lib MFCxx (D).

Regularne biblioteki MFC DLL łączonej dynamicznie z MFC ma następujące wymagania:

- Te biblioteki DLL są kompilowane przy użyciu **_AFXDLL** zdefiniowane, podobnie jak w przypadku pliku wykonywalnego, która jest połączona dynamicznie do MFC DLL. Ale **_usrdll —** jest również definiowany, podobnie jak zwykłej biblioteki MFC DLL, które jest połączone statycznie z MFC.

- Tego rodzaju DLL należy utworzyć wystąpienie `CWinApp`-klasy pochodnej.

- Ten typ korzysta z biblioteki DLL `DllMain` dostarczonych przez MFC. Umieszczenie całego kodu inicjowania biblioteki DLL określonej w `InitInstance` kod funkcji i kończenie działania elementu członkowskiego w `ExitInstance` jak normalna Aplikacja MFC.

Ponieważ tego rodzaju DLL korzysta z wersji biblioteki DLL MFC, musisz jawnie ustawić bieżący stan modułu na jeden dla biblioteki DLL. Aby to zrobić, należy użyć [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) — makro na początku każdej funkcji wyeksportowane z biblioteki DLL.

regularne biblioteki DLL MFC musi mieć `CWinApp`-pochodne klasy i pojedynczy obiekt tej klasy aplikacji, tak jak w aplikacji MFC. Jednak `CWinApp` obiekt biblioteki DLL nie ma pompa głównego wiadomości, tak jak `CWinApp` obiektu aplikacji.

Należy pamiętać, że `CWinApp::Run` mechanizm nie ma zastosowania do biblioteki DLL, ponieważ aplikacja jest właścicielem pompy komunikatów głównego. Jeśli biblioteka DLL ma główne okno ramowe własnych lub wyświetlenie Niemodalne okna dialogowe, pompy komunikatów główny aplikacji musi wywołać procedurę wyeksportowane biblioteki DLL, która wywołuje `CWinApp::PreTranslateMessage`.

Umieść wszystkie Inicjowanie biblioteki DLL określonej w `CWinApp::InitInstance` funkcja elementu członkowskiego, tak jak normalna Aplikacja MFC. `CWinApp::ExitInstance` Funkcji składowej typu usługi `CWinApp` klasy pochodnej jest wywoływana z MFC, pod warunkiem `DllMain` funkcja biblioteki DLL jest zwalniana.

Musisz przeprowadzić dystrybucję udostępnionych bibliotek DLL MFCx0.dll i Msvcr*0.dll (lub podobnych plików) z aplikacją.

Biblioteka DLL, która jest połączona dynamicznie z MFC również statycznie nie można połączyć z MFC. Link aplikacji do zwykłych bibliotekach MFC DLL łączonej dynamicznie z MFC go tak samo jak inne biblioteki DLL.

Symbole zwykle są eksportowane z zwykłej biblioteki MFC DLL za pomocą standardowego interfejsu C. Deklaracja funkcji wyeksportowanej z regularnej biblioteki DLL MFC wygląda następująco:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Wszystkie alokacje pamięci w ramach regularnej biblioteki DLL MFC powinno pozostać w bibliotece DLL; biblioteki DLL należy przekazać do lub nie otrzymywać wywoływania pliku wykonywalnego, dowolny z następujących czynności:

- Wskaźniki do obiektów MFC

- Wskaźniki do pamięci przydzielonej przez MFC

Jeśli musisz wykonać żadnej z powyższych lub należy przekazać obiekty pochodzące z MFC między wywoływania pliku wykonywalnego i biblioteki DLL, należy utworzyć rozszerzenia MFC biblioteki DLL.

Jest bezpieczne przekazać wskaźniki do pamięci, która została przydzielona przez biblioteki wykonawczej C między aplikacją a biblioteki DLL tylko wtedy, gdy wykonanie kopii danych. Nie musisz usunąć lub zmienić rozmiar tych wskaźników lub używać ich bez powiększania kopiowania pamięci.

Gdy kompilowanie regularnej biblioteki MFC DLL, która dynamicznie łączy z MFC, należy użyć makro [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) poprawnie przełączyć stanu modułu MFC. Można to zrobić, dodając następujący wiersz kodu na początku funkcji wyeksportowanych z biblioteki DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

**AFX_MANAGE_STATE** — makro nie należy używać w zwykłych bibliotekach MFC dll, która statycznie łączy się z MFC lub biblioteki DLL rozszerzeń MFC. Aby uzyskać więcej informacji, zobacz [Zarządzanie dane stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md).

Na przykład sposobu pisania, kompilacji i użyć regularnej biblioteki DLL MFC, zobacz przykład [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Aby uzyskać więcej informacji na temat zwykłych bibliotekach MFC dll, która łączy dynamicznie MFC zobacz sekcję pod tytułem "Konwertowanie DLLScreenCap do dynamicznie łączy z biblioteki MFC DLL" w abstrakcyjny dla przykładu.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Zainicjuj regularną bibliotekę DLL MFC](../build/run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Stany modułu zwykłej biblioteki MFC DLL łączonej dynamicznie z MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Używanie bibliotek DLL baz danych, OLE i rozszerzeń MFC gniazd w zwykłych bibliotekach MFC DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>Zobacz też

[Rodzaje bibliotek DLL](../build/kinds-of-dlls.md)