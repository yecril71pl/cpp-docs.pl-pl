---
title: Zmienne środowiskowe dla optymalizacji sterowanych profilem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19edc9c8a2702e5b7ac9ae4a49364718f19d3900
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>Zmienne środowiskowe dla optymalizacji sterowanych profilem

Istnieją trzy zmiennych środowiskowych, które mają wpływ na scenariuszy testu na obraz utworzone za pomocą **/LTCG:PGI** dla optymalizacji sterowanych profilem:

- **PogoSafeMode** Określa, czy użyć trybu szybkiego lub w trybie awaryjnym do profilowania aplikacji.

- **Vcprofile_alloc_scale —** dodaje dodatkową pamięć do wykorzystania przez profiler.

- **VCPROFILE_PATH** umożliwia określenie folderu przeznaczonego dla plików PGC.

**Zmienne środowiskowe PogoSafeMode i vcprofile_alloc_scale — są przestarzałe, począwszy od programu Visual Studio 2015.** Opcje konsolidatora [opcji/genprofile lub /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) i [/USEPROFILE](useprofile.md) Określ takie samo zachowanie konsolidatora jako zmienne środowiskowe.

## <a name="pogosafemode"></a>PogoSafeMode

Ta zmienna środowiskowa jest przestarzały. Użyj **EXACT** lub **NOEXACT** argumenty **opcji/genprofile** lub **/FASTGENPROFILE** do kontrolowania tego zachowania.

Usuń zaznaczenie lub ustawić **PogoSafeMode** zmiennej środowiskowej, aby określić, czy użyć trybu szybkiego i tryb awaryjny dla profilowania aplikacji na x86 systemów.

Optymalizacja sterowana profilem — (PGO) ma dwa tryby możliwe podczas fazy profilowania: *trybu szybkiego* i *tryb awaryjny*. Podczas profilowania jest w trybie szybkiego, używa **INC** instrukcji, aby zwiększyć danych liczników. **INC** instrukcji jest szybsze, ale nie jest bezpieczne wątkowo. Podczas profilowania jest w trybie awaryjnym, używa **INC blokady** instrukcji, aby zwiększyć danych liczników. **INC blokady** instrukcji ma te same funkcje co **INC** instrukcji ma i wątkowo, ale jest mniejsza niż **INC** instrukcji.

Domyślnie profilowania PGO działa w trybie Szybkie. **PogoSafeMode** jest wymagane tylko, jeśli chcesz użyć trybu awaryjnego.

Aby uruchomić PGO profilowania w trybie awaryjnym, należy użyć zmiennej środowiskowej **PogoSafeMode** lub przełącznik konsolidatora **/PogoSafeMode**w zależności od systemu. Jeśli przeprowadzasz profilowanie na x64 komputera, należy użyć przełącznika konsolidatora. Jeśli przeprowadzasz profilowanie na x86 komputera, możesz użyć konsolidator przełącznika lub ustaw **PogoSafeMode** zmiennej środowiskowej wartości przed rozpoczęciem procesu optymalizacji.

### <a name="pogosafemode-syntax"></a>Składnia PogoSafeMode

> **Ustaw PogoSafeMode**[**=**_wartość_]

Ustaw **PogoSafeMode** do żadnej wartości, aby włączyć tryb awaryjny. Ustaw bez wartości, aby wyczyścić poprzednią wartość i ponownie włączyć trybu szybkiego.

## <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE

Ta zmienna środowiskowa jest przestarzały. Użyj **MEMMIN** i **MEMMAX** argumenty **opcji/genprofile** lub **/FASTGENPROFILE** do kontrolowania tego zachowania.

Modyfikowanie **vcprofile_alloc_scale —** zmiennej środowiskowej, aby zmienić ilość pamięci przydzielona do przechowywania danych profilu. W rzadkich przypadkach, nie będzie wystarczającej ilości pamięci do obsługi zbierania danych profilu podczas uruchamiania testu scenariuszy. W takich przypadkach można zwiększyć ilość pamięci, ustawiając **vcprofile_alloc_scale —**. Jeśli zostanie wyświetlony komunikat o błędzie podczas uruchomienia testu, który wskazuje, czy masz za mało pamięci, należy przypisać wartość większą do **vcprofile_alloc_scale —**, dopóki test uruchomieniu ukończone bez błędów braku pamięci.

### <a name="vcprofileallocscale-syntax"></a>Vcprofile_alloc_scale — Składnia

> **set VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

*Scale_value* parametr jest czynnik skalowania ilości pamięci do uruchomienia testu scenariuszy.  Domyślnym ustawieniem jest 1. Na przykład ten wiersz polecenia ustawia współczynnik skali 2:

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofilepath"></a>VCPROFILE_PATH

Użyj **VCPROFILE_PATH** zmiennej środowiskowej, aby określić katalog, aby utworzyć pliki .pgc. Domyślnie pliki .pgc są tworzone w tym samym katalogu co plik binarny PROFILOWANEGO. Jednak jeśli ścieżka bezwzględna plik binarny nie istnieje, jak może to miejsce podczas uruchamiania scenariuszy profilu na innym komputerze, z którym został utworzony plik binarny, możesz ustawić **VCPROFILE_PATH** do ścieżki, która istnieje na komputerze docelowym.

### <a name="vcprofilepath-syntax"></a>VCPROFILE_PATH składni

> **Ustaw VCPROFILE_PATH**[**=**_ścieżki_]

Ustaw *ścieżki* parametr ścieżki katalogu, w którym można dodać plików .pgc. Na przykład ten wiersz polecenia ustawia C:\profile folderu:

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>Zobacz także

[Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md)<br/>
[/ Opcję GENPROFILE i /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](useprofile.md)<br/>
