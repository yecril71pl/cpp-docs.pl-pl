---
title: Zwykłe biblioteki DLL MFC połączone statycznie z MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
ms.openlocfilehash: fee2d3b84949241cda421d6ea587e1ab9c6e58e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565545"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>Zwykłe biblioteki DLL MFC połączone statycznie z MFC

Wyrażenie, które biblioteki DLL MFC połączone statycznie z MFC jest biblioteki DLL, która używa wewnętrznie MFC i eksportowanych funkcji w bibliotece DLL może być wywoływany przez pliki wykonywalne MFC lub inne niż MFC. Zgodnie z opisem w nazwę tego rodzaju DLL został skompilowany przy użyciu wersji biblioteki dołączanej MFC. Funkcje eksportowane są zwykle od zwykłej biblioteki MFC DLL za pomocą standardowego interfejsu C. Na przykład sposobu pisania, kompilacji i użyć regularnej biblioteki DLL MFC, zobacz przykład [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap).

Pamiętaj, że termin USRDLL nie jest już używany w dokumentacji języka Visual C++. Regularne biblioteki DLL MFC, która jest połączone statycznie z MFC ma takie same charakterystyki jak dawny USRDLL.

Regularne DLL MFC połączone statycznie z MFC, ma następujące cechy:

- Klient wykonywalny mogą być napisane w dowolnym języku, który obsługuje korzystanie z biblioteki dll (C, C++, Pascal, Visual Basic i tak dalej); nie ma być aplikacji MFC.

- Biblioteka DLL można połączyć z tej samej biblioteki dołączanej MFC używane przez aplikacje. Nie ma już oddzielnych wersji biblioteki dołączanej biblioteki dll.

- Przed wersją 4.0, MFC Usrdll podać ten sam typ funkcjonalność, jak regularne biblioteki DLL MFC połączone statycznie z MFC. Począwszy od Visual C++ w wersji 4.0 termin USRDLL jest przestarzała.

Regularne DLL MFC połączone statycznie z MFC, ma następujące wymagania:

- Tego rodzaju DLL należy utworzyć wystąpienie klasy pochodzącej od `CWinApp`.

- Ten typ korzysta z biblioteki DLL `DllMain` dostarczonych przez MFC. Umieszczenie całego kodu inicjowania biblioteki DLL określonej w `InitInstance` kod funkcji i kończenie działania elementu członkowskiego w `ExitInstance` jak normalna Aplikacja MFC.

- Mimo że termin USRDLL jest przestarzały, nadal należy zdefiniować "**_usrdll —**" w wierszu polecenia kompilatora. Ta definicja Określa, które deklaracji jest pobierane z plikach nagłówkowych MFC.

regularne biblioteki DLL MFC musi mieć `CWinApp`-pochodne klasy i pojedynczy obiekt tej klasy aplikacji, tak jak w aplikacji MFC. Jednak `CWinApp` obiekt biblioteki DLL nie ma pompa głównego wiadomości, tak jak `CWinApp` obiektu aplikacji.

Należy pamiętać, że `CWinApp::Run` mechanizm nie ma zastosowania do biblioteki DLL, ponieważ aplikacja jest właścicielem pompy komunikatów głównego. Jeśli biblioteka DLL otwiera Niemodalne okna dialogowe albo główne okno ramowe własne, pompy komunikatów główny aplikacji musi wywołać procedurę eksportowanych przez DLL, która z kolei wywołuje `CWinApp::PreTranslateMessage` funkcja elementu członkowskiego obiektu aplikacji DLL.

Na przykład tę funkcję, zobacz przykładową DLLScreenCap.

Symbole zwykle są eksportowane z zwykłej biblioteki MFC DLL za pomocą standardowego interfejsu C. Deklaracja funkcji wyeksportowanej z zwykłej biblioteki MFC DLL będzie wyglądać mniej więcej tak:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Wszystkie alokacje pamięci w ramach regularnej biblioteki DLL MFC powinno pozostać w bibliotece DLL; biblioteki DLL należy przekazać do lub nie otrzymywać wywoływania pliku wykonywalnego, dowolny z następujących czynności:

- Wskaźniki do obiektów MFC

- Wskaźniki do pamięci przydzielonej przez MFC

Jeśli musisz wykonać żadnej z powyższych lub potrzebujesz przekazać obiekty pochodzące z MFC między wywoływania pliku wykonywalnego i biblioteki DLL, należy utworzyć rozszerzenia MFC biblioteki DLL.

Jest bezpieczne przekazać wskaźniki do pamięci, która została przydzielona przez biblioteki wykonawczej C między aplikacją a biblioteki DLL tylko wtedy, gdy wykonanie kopii danych. Nie musisz usunąć lub zmienić rozmiar tych wskaźników lub używać ich bez powiększania kopiowania pamięci.

Biblioteka DLL, która jest połączone statycznie z MFC również dynamiczne nie można połączyć z udostępnionej biblioteki MFC DLL. Biblioteka DLL, która jest połączone statycznie z MFC dynamicznie jest powiązany z aplikacją, podobnie jak inne biblioteki DLL; aplikacje przejść do niego, podobnie jak inne biblioteki DLL.

Standardowe biblioteki dołączanej MFC są określane według Konwencji opisanego w [konwencje nazewnictwa bibliotek MFC dll](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Jednak z MFC w wersji 3.0 i nowszych należy już ręcznie określić konsolidatora wersji biblioteki MFC, który ma być połączone w. Zamiast tego w plikach nagłówkowych MFC automatycznie określić definiuje poprawnej wersji biblioteki MFC, łącze w oparciu preprocesora, takich jak  **\_debugowania** lub **_UNICODE**. W plikach nagłówkowych MFC Dodaj dyrektywy /DEFAULTLIB poinstruowanie konsolidator łącze w określonej wersji biblioteki MFC.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Zainicjuj regularną bibliotekę DLL MFC](../build/run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Używanie bibliotek DLL baz danych, OLE i rozszerzeń MFC gniazd w zwykłych bibliotekach MFC DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Tworzenie biblioteki DLL MFC](../mfc/reference/mfc-dll-wizard.md)

- [Zwykłe biblioteki DLL MFC połączone dynamicznie z MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [Biblioteki DLL rozszerzeń MFC](../build/extension-dlls-overview.md)

## <a name="see-also"></a>Zobacz też

[Rodzaje bibliotek DLL](../build/kinds-of-dlls.md)