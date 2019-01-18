---
title: 4. Zmienne środowiskowe
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: 5d08031c252d1f3c45fc45c021d24476b393fe33
ms.sourcegitcommit: 2ebbf8093fadb9a1b78a4381439bcd5c01a89267
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397332"
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

## <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE` ma zastosowanie tylko do `for` i `parallel for` dyrektyw, które mają typ harmonogramu `runtime`. Rozmiar typu i fragmentów harmonogram dla wszystkich takich pętli można ustawić w czasie wykonywania. Ustaw wartość tej zmiennej środowiska dowolny typ harmonogram rozpoznany i opcjonalnie *chunk_size*.

Aby uzyskać `for` i `parallel for` dyrektyw, które mają inny niż typ harmonogramu `runtime`, `OMP_SCHEDULE` jest ignorowana. Wartością domyślną dla tej zmiennej środowiskowej jest zdefiniowane w implementacji. Jeśli opcjonalny *chunk_size* jest ustawiona, wartość musi być dodatnia. Jeśli *chunk_size* nie jest ustawiony na wartość 1 zakłada się, z wyjątkiem sytuacji, gdy harmonogram jest `static`. Aby uzyskać `static` harmonogram, domyślny rozmiar fragmentu jest ustawiony do obszaru iteracji pętli dzielona przez liczbę wątków stosowane do pętli.

Przykład:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Odsyłacze

- [Aby uzyskać](2-4-1-for-construct.md) — dyrektywa
- [równoległe w](2-5-1-parallel-for-construct.md) — dyrektywa

## <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS

`OMP_NUM_THREADS` Zmiennej środowiskowej ustawia domyślną liczbę wątków używanych podczas wykonywania. `OMP_NUM_THREADS` jest ignorowana, jeśli ta liczba jest jawnie zmieniona przez wywołanie metody `omp_set_num_threads` procedury biblioteki. Również jest pomijany, jeśli występuje jawna `num_threads` klauzuli w `parallel` dyrektywy.

Wartość `OMP_NUM_THREADS` zmiennej środowiskowej musi być dodatnią liczbą całkowitą. Jego efektem zależy od tego, czy włączona jest dynamiczne Dostosowywanie liczby wątków. Aby uzyskać kompleksowy zestaw reguł o interakcji między `OMP_NUM_THREADS` środowiska zmiennych i dynamicznego dostosowania wątków, patrz sekcja 2.3.

Liczba wątków używanych jest zdefiniowane w implementacji jeśli:

- `OMP_NUM_THREADS` zmienna środowiskowa nie jest określona,
- Określona wartość nie jest dodatnią liczbą całkowitą lub
- wartość jest większa niż maksymalna liczba wątków, w których system może obsłużyć.

Przykład:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Odsyłacze

- [num_threads](2-3-parallel-construct.md) — klauzula
- [omp_set_num_threads](3-1-1-omp-set-num-threads-function.md) — funkcja
- [omp_set_dynamic](3-1-7-omp-set-dynamic-function.md) — funkcja

## <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC

`OMP_DYNAMIC` Zmiennej środowiskowej Włącza lub wyłącza dynamiczne Dostosowywanie liczby dostępnych do wykonywania regionów równoległych wątków. `OMP_DYNAMIC` jest ignorowana, gdy jawnie włączona lub wyłączona przez wywołanie metody dynamiczne dostosowywanie `omp_set_dynamic` procedury biblioteki. Jego wartość musi być `TRUE` lub `FALSE`.

Jeśli `OMP_DYNAMIC` ustawiono `TRUE`, liczbę wątków, które są używane do wykonywania regionów równoległych mogą być dostosowywane przez środowisko uruchomieniowe najlepszego wykorzystania zasobów systemowych.  Jeśli `OMP_DYNAMIC` ustawiono `FALSE`, dynamiczne Dostosowywanie jest wyłączona. Stan domyślny jest zdefiniowane w implementacji.

Przykład:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Odsyłacze

- [Regionów równoległych](2-3-parallel-construct.md)
- [omp_set_dynamic](3-1-7-omp-set-dynamic-function.md) — funkcja

## <a name="44-ompnested"></a>4.4 OMP_NESTED

`OMP_NESTED` Zmiennej środowiskowej Włącza lub wyłącza zagnieżdżonych równoległości, chyba że zagnieżdżone równoległości jest włączone lub wyłączone przez wywołanie metody `omp_set_nested` procedury biblioteki. Jeśli `OMP_NESTED` ustawiono `TRUE`, zagnieżdżone równoległości jest włączona. Jeśli `OMP_NESTED` ustawiono `FALSE`, zagnieżdżone równoległości jest wyłączona. Wartość domyślna to `FALSE`.

Przykład:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Cross-reference

- [omp_set_nested](3-1-9-omp-set-nested-function.md) — funkcja
