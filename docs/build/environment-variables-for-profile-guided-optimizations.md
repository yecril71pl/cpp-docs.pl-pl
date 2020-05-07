---
title: Zmienne środowiskowe dla optymalizacji sterowanych profilem
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: 099e57f1ac69223adafe7bec1af4cc3452915e86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195276"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>Zmienne środowiskowe dla optymalizacji sterowanych profilem

Istnieją trzy zmienne środowiskowe, które mają wpływ na scenariusze testowe w obrazie utworzonym za pomocą **/LTCG: PGI** dla optymalizacji profilowanej:

- **PogoSafeMode** określa, czy należy używać trybu szybkiego czy bezpiecznego dla profilowania aplikacji.

- **VCPROFILE_ALLOC_SCALE** dodaje dodatkową pamięć do użycia przez profiler.

- **VCPROFILE_PATH** umożliwia określenie folderu używanego dla plików. pgc.

**Zmienne środowiskowe PogoSafeMode i VCPROFILE_ALLOC_SCALE są przestarzałe, począwszy od programu Visual Studio 2015.** Opcje konsolidatora [/GENPROFILE lub/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) i [/USEPROFILE](reference/useprofile.md) określają takie samo zachowanie konsolidatora jak te zmienne środowiskowe.

## <a name="pogosafemode"></a>PogoSafeMode

Ta zmienna środowiskowa jest przestarzała. Aby kontrolować to zachowanie, należy użyć argumentów **dokładnie** lub **noexact** do **/GENPROFILE** lub **/FASTGENPROFILE** .

Wyczyść lub Ustaw zmienną środowiskową **PogoSafeMode** , aby określić, czy ma być używany tryb szybki czy bezpieczny dla profilowania aplikacji w systemach x86.

Optymalizacja oparta na profilach (PGO) ma dwa możliwe tryby w fazie profilowania: *Tryb szybki* i *tryb bezpieczny*. Gdy profilowanie jest w trybie szybkim, używa instrukcji **Inc** , aby zwiększyć liczniki danych. Instrukcje dla programu **Inc** są szybsze, ale nie są bezpieczne dla wątków. Gdy profilowanie odbywa się w trybie awaryjnym, używa instrukcji **Lock Inc** , aby zwiększyć liczniki danych. Instrukcja **Lock Inc** ma takie same funkcje, jak instrukcja **Inc** , i jest bezpieczna wątkowo, ale jest wolniejsza niż instrukcja **Inc** .

Domyślnie profilowanie PGO działa w trybie szybkim. **PogoSafeMode** jest wymagany tylko wtedy, gdy chcesz używać trybu awaryjnego.

Aby uruchomić profilowanie PGO w trybie awaryjnym, należy użyć zmiennej środowiskowej **PogoSafeMode** lub przełącznika konsolidatora **/PogoSafeMode**, w zależności od systemu. Jeśli przeprowadzasz profilowanie na komputerze z architekturą x64, musisz użyć przełącznika konsolidatora. Jeśli przeprowadzasz profilowanie na komputerze z procesorem x86, możesz użyć przełącznika konsolidatora lub ustawić zmienną środowiskową **PogoSafeMode** na dowolną wartość przed rozpoczęciem procesu optymalizacji.

### <a name="pogosafemode-syntax"></a>Składnia PogoSafeMode

> **Set PogoSafeMode**[**=**_Value_]

Ustaw **PogoSafeMode** na dowolną wartość, aby włączyć tryb awaryjny. Ustaw bez wartości, aby wyczyścić poprzednią wartość i ponownie włączyć tryb szybki.

## <a name="vcprofile_alloc_scale"></a>VCPROFILE_ALLOC_SCALE

Ta zmienna środowiskowa jest przestarzała. Aby kontrolować to zachowanie, użyj argumentów **MEMMIN** i **MEMMAX** do **/GENPROFILE** lub **/FASTGENPROFILE** .

Zmodyfikuj zmienną środowiskową **VCPROFILE_ALLOC_SCALE** , aby zmienić ilość pamięci przydzieloną w celu przechowywania danych profilu. W rzadkich przypadkach nie będzie dostępna wystarczająca ilość pamięci do obsługi gromadzenia danych profilu podczas wykonywania scenariuszy testowych. W takich przypadkach można zwiększyć ilość pamięci przez ustawienie **VCPROFILE_ALLOC_SCALE**. Jeśli podczas przebiegu testowego zostanie wyświetlony komunikat o błędzie informujący o braku wystarczającej ilości pamięci, należy przypisać większą wartość do **VCPROFILE_ALLOC_SCALE**, do momentu zakończenia testu bez błędów braku pamięci.

### <a name="vcprofile_alloc_scale-syntax"></a>Składnia VCPROFILE_ALLOC_SCALE

> **Ustawianie VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

Parametr *scale_value* to współczynnik skalowania ilości pamięci, która ma być używana w scenariuszach testowych.  Domyślnym ustawieniem jest 1. Na przykład ten wiersz polecenia ustawia współczynnik skalowania na 2:

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofile_path"></a>VCPROFILE_PATH

Użyj zmiennej środowiskowej **VCPROFILE_PATH** , aby określić katalog do tworzenia plików. pgc. Domyślnie pliki. pgc są tworzone w tym samym katalogu co plik binarny, który jest profilowany. Jednakże jeśli ścieżka bezwzględna pliku binarnego nie istnieje, tak jak w przypadku uruchamiania scenariuszy profilu na innym komputerze, na którym został skompilowany plik binarny, można ustawić **VCPROFILE_PATH** na ścieżkę, która istnieje na maszynie docelowej.

### <a name="vcprofile_path-syntax"></a>Składnia VCPROFILE_PATH

> **Ustawianie VCPROFILE_PATH**[**=**_ścieżka_]

Ustaw parametr *Path* na ścieżkę katalogu, w której chcesz dodać pliki. pgc. Na przykład ten wiersz polecenia ustawia folder na C:\Profile:

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>Zobacz też

[Optymalizacje sterowane profilem](profile-guided-optimizations.md)<br/>
[/GENPROFILE i/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](reference/useprofile.md)<br/>
