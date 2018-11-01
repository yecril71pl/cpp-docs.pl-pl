---
title: Zmienne środowiskowe dla optymalizacji sterowanych profilem
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: 2d69019f01a59f170aeeee22ef10b1af0de07a68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595666"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>Zmienne środowiskowe dla optymalizacji sterowanych profilem

Istnieją trzy zmienne środowiskowe, które wpływają na scenariusze testów na obrazie, który został utworzony za pomocą **/LTCG:PGI** dla sterowanych profilem:

- **PogoSafeMode** Określa, czy ma być używany tryb szybki czy tryb awaryjny profilowania aplikacji.

- **Vcprofile_alloc_scale —** dodaje dodatkową pamięć do wykorzystania przez profiler.

- **Vcprofile_path —** umożliwia określenie folderu przeznaczonego dla plików PGC.

**Zmienne środowiskowe PogoSafeMode i vcprofile_alloc_scale — są przestarzałe, począwszy od programu Visual Studio 2015.** Opcje konsolidatora [przełączników/genprofile i/fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) i [/USEPROFILE](useprofile.md) określają jednakowe zachowanie konsolidatora jako zmienne środowiskowe.

## <a name="pogosafemode"></a>PogoSafeMode

Ta zmienna środowiskowa jest przestarzały. Użyj **EXACT** lub **NOEXACT** argumenty **przełączników/genprofile** lub **/fastgenprofile** do sterowania tym zachowaniem.

Usuń zaznaczenie lub ustaw **PogoSafeMode** zmiennej środowiskowej, aby określić, czy ma być używany tryb szybki czy tryb awaryjny profilowania aplikacji na x86 systemów.

Profilowana Optymalizacja (PGO) ma dwa możliwe tryby podczas fazy profilowania: *trybie szybkim* i *tryb awaryjny*. Gdy profilowanie odbywa się w trybie szybkim, wykorzystuje **INC** instrukcji, aby zwiększyć liczniki danych. **INC** instrukcji jest szybsze, ale nie jest metodą o bezpiecznych wątkach. Gdy profilowanie odbywa się w trybie bezpiecznym, wykorzystuje **INC blokady** instrukcji, aby zwiększyć liczniki danych. **INC blokady** instrukcji ma taką samą funkcjonalność jak **INC** instrukcji ma i jest bezpieczna dla wątków, ale wolniejsza niż **INC** instrukcji.

Domyślnie profilowanie PGO działa w trybie szybkim. **PogoSafeMode** jest wymagany tylko, jeśli chcesz użyć trybu awaryjnego.

Aby uruchomić profilowanie PGO w trybie awaryjnym, należy użyć zmiennej środowiskowej **PogoSafeMode** lub przełącznika konsolidatora **/PogoSafeMode**, w zależności od systemu. Jeśli przeprowadzasz profilowanie na x64 komputera, musisz użyć przełącznika konsolidatora. Jeśli przeprowadzasz profilowanie na x86 komputera, możesz użyć konsolidatora przełączyć lub ustaw **PogoSafeMode** zmienną środowiskową na dowolną wartość przed rozpoczęciem procesu optymalizacji.

### <a name="pogosafemode-syntax"></a>Składnia PogoSafeMode

> **Ustaw PogoSafeMode**[**=**_wartość_]

Ustaw **PogoSafeMode** do każdej wartości, aby włączyć tryb awaryjny. Ustaw bez wartości, aby usunąć poprzednią wartość i ponownie włączyć tryb szybki.

## <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE

Ta zmienna środowiskowa jest przestarzały. Użyj **MEMMIN** i **MEMMAX** argumenty **przełączników/genprofile** lub **/fastgenprofile** do sterowania tym zachowaniem.

Modyfikowanie **vcprofile_alloc_scale —** zmiennej środowiskowej, aby zmienić ilość pamięci przydzielona do przechowywania danych profilu. W rzadkich przypadkach, nie będzie wystarczającej ilości pamięci do obsługi zbieranie danych profilu, podczas uruchamiania scenariuszy testowania. W takich przypadkach można zwiększyć ilość pamięci, ustawiając **vcprofile_alloc_scale —**. Jeśli zostanie wyświetlony komunikat o błędzie podczas przebiegu testu, która wskazuje, że masz za mało pamięci, należy przypisać większej wartości do **vcprofile_alloc_scale —**, dopóki test uruchomiony ukończone bez błędów braku pamięci.

### <a name="vcprofileallocscale-syntax"></a>Vcprofile_alloc_scale — Składnia

> **set VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

*Scale_value* parametr jest współczynnik skalowania ilości pamięci do uruchamiania scenariuszy testowania.  Domyślnym ustawieniem jest 1. Na przykład ten wiersz polecenia ustawia współczynnik skali do 2:

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofilepath"></a>VCPROFILE_PATH

Użyj **vcprofile_path jest** zmiennej środowiskowej, aby określić katalog, aby utworzyć pliki .pgc. Domyślnie pliki .pgc są tworzone w tym samym katalogu co plik binarny, poddawanego profilowaniu. Natomiast jeśli ścieżka bezwzględna pliku binarnego nie istnieje, ponieważ może występować w przypadku uruchamiania scenariuszy profilu na innym komputerze, z której został utworzony plik binarny, możesz ustawić **vcprofile_path jest** do ścieżki, która istnieje na komputerze docelowym.

### <a name="vcprofilepath-syntax"></a>Vcprofile_path — Składnia

> **Ustaw vcprofile_path jest**[**=**_ścieżki_]

Ustaw *ścieżki* parametru, aby ścieżka katalogu, w którym można dodać pliki .pgc. Na przykład ten wiersz polecenia ustawia C:\profile folder:

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>Zobacz także

[Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md)<br/>
[/ GENPROFILE i/fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](useprofile.md)<br/>
