---
title: Regularne biblioteki MFC DLL statycznie połączone z MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
ms.openlocfilehash: 1f05b5e3c268935cf3161fb7184e04b3e3ea1446
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314783"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>Regularne biblioteki MFC DLL statycznie połączone z MFC

Regularna biblioteka MFC DLL statycznie połączona z MFC jest biblioteką DLL, która używa wewnętrznie MFC, a eksportowane funkcje w bibliotece DLL mogą być wywoływane przez pliki wykonywalne MFC lub inne niż MFC. Jak opisano w opisie, ten rodzaj biblioteki DLL jest tworzony przy użyciu biblioteki dołączanej statycznej MFC. Funkcje są zwykle eksportowane ze zwykłej biblioteki MFC DLL przy użyciu standardowego interfejsu języka C. Aby zapoznać się z przykładem sposobu pisania, kompilowania i używania zwykłej biblioteki MFC DLL, zobacz przykład [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap).

Należy zauważyć, że termin USRDLL nie jest już używany w dokumentacji Visual C++. Zwykła Biblioteka MFC DLL, która jest statycznie połączona z MFC, ma takie same charakterystyki jak dawny USRDLL.

Zwykła Biblioteka MFC DLL, statycznie połączona z MFC, ma następujące funkcje:

- Plik wykonywalny klienta można napisać w dowolnym języku, który obsługuje biblioteki DLL (C, C++, Pascal, Visual Basic itd.); nie musi to być aplikacja MFC.

- Biblioteka DLL może łączyć się z tymi samymi bibliotekami statycznego łącza MFC używanymi przez aplikacje. Nie istnieje już oddzielna wersja bibliotek linków statycznych dla bibliotek DLL.

- Przed wersją 4,0 MFC USRDLL pod warunkiem, że ten sam typ funkcjonalności jest taki sam jak regularne biblioteki MFC DLL statycznie połączone z MFC. W przypadku Visual C++ w wersji 4,0 termin USRDLL jest przestarzały.

Zwykła Biblioteka MFC DLL, statycznie połączona z MFC, ma następujące wymagania:

- Ten typ biblioteki DLL musi utworzyć wystąpienie klasy pochodnej `CWinApp` .

- Ten typ biblioteki DLL używa `DllMain` dostarczone przez MFC. Umieść wszystkie kod inicjalizacji specyficzny dla biblioteki DLL w `InitInstance` funkcji członkowskiej i kod zakończenia w `ExitInstance` taki sposób, jak w przypadku normalnej aplikacji MFC.

- Mimo że termin USRDLL jest przestarzały, nadal trzeba zdefiniować "**_USRDLL**" w wierszu polecenia kompilatora. Ta definicja określa, które deklaracje są ściągane z plików nagłówkowych MFC.

regularne biblioteki DLL MFC muszą mieć `CWinApp` klasę pochodną i pojedynczy obiekt tej klasy aplikacji, tak jak aplikacja MFC. Jednak `CWinApp` obiekt biblioteki DLL nie ma głównej pompki komunikatów, ponieważ `CWinApp` obiekt aplikacji.

Należy zauważyć, że mechanizm nie ma `CWinApp::Run` zastosowania do biblioteki DLL, ponieważ aplikacja jest właścicielem głównej pompy komunikatów. Jeśli biblioteka DLL otwiera Niemodalne okna dialogowe lub ma własne główne okno ramek, główna pompa komunikatów aplikacji musi wywołać procedurę wyeksportowaną przez bibliotekę DLL, która z kolei wywołuje `CWinApp::PreTranslateMessage` funkcję członkowską obiektu aplikacji DLL.

Aby zapoznać się z przykładem tej funkcji, zobacz przykład DLLScreenCap.

Symbole są zwykle eksportowane z zwykłej biblioteki MFC DLL przy użyciu standardowego interfejsu języka C. Deklaracja funkcji eksportowanej ze zwykłej biblioteki MFC DLL będzie wyglądać następująco:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Wszystkie alokacje pamięci w ramach zwykłej biblioteki MFC DLL powinny pozostać w bibliotece DLL; Biblioteka DLL nie powinna przekazać do wywołującego pliku wykonywalnego ani odebrać z niego żadnego z następujących elementów:

- Wskaźniki do obiektów MFC

- Wskaźniki do pamięci przydzielonej przez MFC

Jeśli trzeba wykonać dowolne z powyższych lub wymagać przekazania obiektów pochodnych MFC między wywołującym plik wykonywalny a biblioteką DLL, należy utworzyć bibliotekę DLL rozszerzenia MFC.

Można bezpiecznie przekazać wskaźniki do pamięci, która została przypisana przez biblioteki uruchomieniowe C między aplikacją a biblioteką DLL tylko w przypadku wykonywania kopii danych. Nie należy usuwać ani zmieniać rozmiarów tych wskaźników ani ich używać bez tworzenia kopii pamięci.

Biblioteka DLL statycznie połączona z MFC nie może również dynamicznie łączyć się z udostępnionymi bibliotekami DLL MFC. Biblioteka DLL, która jest statycznie połączona z MFC, jest dynamicznie powiązana z aplikacją tak samo jak inna Biblioteka DLL; aplikacje mają do nich połączenie, podobnie jak każda inna Biblioteka DLL.

Standardowe biblioteki statyczne DLL MFC są nazywane zgodnie z Konwencją opisaną w [konwencjach nazewnictwa dla bibliotek DLL MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Jednak w przypadku MFC w wersji 3,0 i nowszych nie jest już konieczne ręczne określenie konsolidatora wersji biblioteki MFC, która ma zostać połączona. Zamiast tego pliki nagłówkowe MFC automatycznie określają poprawną wersję biblioteki MFC do łączenia w oparciu o zdefiniowane Definicje preprocesora, takie jak ** \_ DEBUG** lub **_UNICODE**. Pliki nagłówkowe MFC dodają dyrektywy/DEFAULTLIB, które nakazuje konsolidatorowi łączenie się z określoną wersją biblioteki MFC.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Inicjowanie zwykłych bibliotek DLL MFC](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Korzystanie z bibliotek DLL rozszerzeń MFC w bazie danych, OLE i Sockets w zwykłych bibliotekach DLL MFC](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Tworzenie biblioteki MFC DLL](../mfc/reference/mfc-dll-wizard.md)

- [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Biblioteki DLL rozszerzeń MFC](extension-dlls-overview.md)

## <a name="see-also"></a>Zobacz także

[Rodzaje bibliotek DLL](kinds-of-dlls.md)
