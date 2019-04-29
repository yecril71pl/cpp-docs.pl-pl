---
title: 4. Zmienne środowiskowe
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: b41829fd9cf2f90312f669ef991f56dda02947f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363196"
---
# <a name="4-environment-variables"></a>4. Zmienne środowiskowe

W tym rozdziale opisano zmienne środowiskowe OpenMP C i interfejsu API języka C++ (lub podobny mechanizm specyficzne dla platformy), kontrolować wykonywanie kodu przetwarzania równoległego.  Nazwy zmiennych środowiskowych muszą być pisane dużą literą. Wartości przypisane do nich uwzględniana wielkość liter i może mieć początkowe i końcowe biały.  Modyfikacje wartości po uruchomieniu programu są ignorowane.

Zmienne środowiskowe są następujące:

- [OMP_SCHEDULE](#41-omp_schedule) ustawia rozmiar typu i fragmentów harmonogramu w czasie wykonywania.
- [OMP_NUM_THREADS](#42-omp_num_threads) Ustawia liczbę wątków używanych podczas wykonywania.
- [OMP_DYNAMIC](#43-omp_dynamic) Włącza lub wyłącza dynamicznego dostosowania liczby wątków.
- [OMP_NESTED](#44-omp_nested) Włącza lub wyłącza równoległości zagnieżdżonych.

W przykładach w tym rozdziale jedynie pokazują, jak tych zmiennych może być ustawione w taki sposób, w środowiskach powłoki (csh) C systemu Unix. W środowiskach systemu DOS i powłoka Korna czynności są podobne:

CSH:  
`setenv OMP_SCHEDULE "dynamic"`

ksh:  
`export OMP_SCHEDULE="dynamic"`

DOS:  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE` ma zastosowanie tylko do `for` i `parallel for` dyrektyw, które mają typ harmonogramu `runtime`. Rozmiar typu i fragmentów harmonogram dla wszystkich takich pętli można ustawić w czasie wykonywania. Ustaw wartość tej zmiennej środowiska dowolny typ harmonogram rozpoznany i opcjonalnie *chunk_size*.

Aby uzyskać `for` i `parallel for` dyrektyw, które mają inny niż typ harmonogramu `runtime`, `OMP_SCHEDULE` jest ignorowana. Wartością domyślną dla tej zmiennej środowiskowej jest zdefiniowane w implementacji. Jeśli opcjonalny *chunk_size* jest ustawiona, wartość musi być dodatnia. Jeśli *chunk_size* nie jest ustawiony na wartość 1 zakłada się, z wyjątkiem sytuacji, gdy harmonogram jest `static`. Aby uzyskać `static` harmonogram, domyślny rozmiar fragmentu jest ustawiony do obszaru iteracji pętli dzielona przez liczbę wątków stosowane do pętli.

Przykład:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Odsyłacze

- [Aby uzyskać](2-directives.md#241-for-construct) — dyrektywa
- [równoległe w](2-directives.md#251-parallel-for-construct) — dyrektywa

## <a name="42-omp_num_threads"></a>4.2 OMP_NUM_THREADS

`OMP_NUM_THREADS` Zmiennej środowiskowej ustawia domyślną liczbę wątków używanych podczas wykonywania. `OMP_NUM_THREADS` jest ignorowana, jeśli ta liczba jest jawnie zmieniona przez wywołanie metody `omp_set_num_threads` procedury biblioteki. Również jest pomijany, jeśli występuje jawna `num_threads` klauzuli w `parallel` dyrektywy.

Wartość `OMP_NUM_THREADS` zmiennej środowiskowej musi być dodatnią liczbą całkowitą. Jego efektem zależy od tego, czy włączona jest dynamiczne Dostosowywanie liczby wątków. Aby uzyskać kompleksowy zestaw reguł o interakcji między `OMP_NUM_THREADS` środowiska zmiennych i dynamicznego dostosowania wątków, zobacz [sekcji 2.3](2-directives.md#23-parallel-construct).

Liczba wątków używanych jest zdefiniowane w implementacji jeśli:

- `OMP_NUM_THREADS` zmienna środowiskowa nie jest określona,
- Określona wartość nie jest dodatnią liczbą całkowitą lub
- wartość jest większa niż maksymalna liczba wątków, w których system może obsłużyć.

Przykład:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Odsyłacze

- [num_threads](2-directives.md#23-parallel-construct) — klauzula
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) — funkcja
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) — funkcja

## <a name="43-omp_dynamic"></a>4.3 OMP_DYNAMIC

`OMP_DYNAMIC` Zmiennej środowiskowej Włącza lub wyłącza dynamiczne Dostosowywanie liczby dostępnych do wykonywania regionów równoległych wątków. `OMP_DYNAMIC` jest ignorowana, gdy jawnie włączona lub wyłączona przez wywołanie metody dynamiczne dostosowywanie `omp_set_dynamic` procedury biblioteki. Jego wartość musi być `TRUE` lub `FALSE`.

Jeśli `OMP_DYNAMIC` ustawiono `TRUE`, liczbę wątków, które są używane do wykonywania regionów równoległych mogą być dostosowywane przez środowisko uruchomieniowe najlepszego wykorzystania zasobów systemowych.  Jeśli `OMP_DYNAMIC` ustawiono `FALSE`, dynamiczne Dostosowywanie jest wyłączona. Stan domyślny jest zdefiniowane w implementacji.

Przykład:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Odsyłacze

- [Regionów równoległych](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) — funkcja

## <a name="44-omp_nested"></a>4.4 OMP_NESTED

`OMP_NESTED` Zmiennej środowiskowej Włącza lub wyłącza zagnieżdżonych równoległości, chyba że zagnieżdżone równoległości jest włączone lub wyłączone przez wywołanie metody `omp_set_nested` procedury biblioteki. Jeśli `OMP_NESTED` ustawiono `TRUE`, zagnieżdżone równoległości jest włączona. Jeśli `OMP_NESTED` ustawiono `FALSE`, zagnieżdżone równoległości jest wyłączona. Wartość domyślna to `FALSE`.

Przykład:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Cross-reference

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) — funkcja
