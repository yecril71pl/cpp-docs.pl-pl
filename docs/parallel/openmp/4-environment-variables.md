---
title: 4. Zmienne środowiskowe
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: b41829fd9cf2f90312f669ef991f56dda02947f7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882869"
---
# <a name="4-environment-variables"></a>4. zmienne środowiskowe

W tym rozdziale opisano zmienne środowiskowe C++ środowiska OpenMP C i interfejsu API (lub podobne mechanizmy specyficzne dla platformy) kontrolujące wykonywanie kodu równoległego.  Nazwy zmiennych środowiskowych muszą być pisane wielką literą. Wartości przypisanych do nich nie uwzględniają wielkości liter i mogą zawierać odstępy wiodące i końcowe.  Modyfikacje wartości po rozpoczęciu pracy programu zostały zignorowane.

Zmienne środowiskowe są następujące:

- [OMP_SCHEDULE](#41-omp_schedule) ustawia typ harmonogramu czasu wykonywania i rozmiar fragmentu.
- [OMP_NUM_THREADS](#42-omp_num_threads) ustawia liczbę wątków, które mają być używane podczas wykonywania.
- [OMP_DYNAMIC](#43-omp_dynamic) włącza lub wyłącza dynamiczne dopasowanie liczby wątków.
- [OMP_NESTED](#44-omp_nested) włącza lub wyłącza zagnieżdżoną równoległość.

W przykładach w tym rozdziale przedstawiono tylko te zmienne, które można ustawić w środowiskach powłoki C Shell (CSH). W środowiskach powłoki Korna i systemu DOS działania są podobne:

csh:  
`setenv OMP_SCHEDULE "dynamic"`

ksh:  
`export OMP_SCHEDULE="dynamic"`

DOS:  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a>4,1 OMP_SCHEDULE

`OMP_SCHEDULE` ma zastosowanie tylko do dyrektywy `for` i `parallel for`, które mają `runtime`typ harmonogramu. Typ harmonogramu i rozmiar fragmentu dla wszystkich takich pętli można ustawić w czasie wykonywania. Ustaw tę zmienną środowiskową na dowolny rozpoznany typ harmonogramu i opcjonalne *chunk_size*.

W przypadku dyrektyw `for` i `parallel for`, które mają typ harmonogramu inny niż `runtime`, `OMP_SCHEDULE` jest ignorowana. Wartością domyślną dla tej zmiennej środowiskowej jest zdefiniowana implementacja. Jeśli opcjonalny *chunk_size* jest ustawiony, wartość musi być dodatnia. Jeśli *chunk_size* nie jest ustawiona, zostanie przyjęta wartość 1, z wyjątkiem sytuacji, gdy harmonogram jest `static`. W przypadku harmonogramu `static` domyślny rozmiar fragmentu jest ustawiany na przestrzeń iteracji pętli podzieloną przez liczbę wątków zastosowanych do pętli.

Przykład:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Odsyłacze

- [dla](2-directives.md#241-for-construct) dyrektywy
- [Parallel dla](2-directives.md#251-parallel-for-construct) dyrektywy

## <a name="42-omp_num_threads"></a>4,2 OMP_NUM_THREADS

Zmienna środowiskowa `OMP_NUM_THREADS` ustawia domyślną liczbę wątków do użycia podczas wykonywania. `OMP_NUM_THREADS` jest ignorowany, jeśli ten numer zostanie jawnie zmieniony przez wywołanie procedury biblioteki `omp_set_num_threads`. Jest on również ignorowany, jeśli istnieje jawna klauzula `num_threads` w dyrektywie `parallel`.

Wartość zmiennej środowiskowej `OMP_NUM_THREADS` musi być dodatnią liczbą całkowitą. Jego wpływ zależy od tego, czy włączone jest dynamiczne dopasowanie liczby wątków. Aby uzyskać kompleksowy zestaw reguł dotyczących interakcji między zmienną środowiskową `OMP_NUM_THREADS` i dynamiczne dopasowanie wątków, zobacz [sekcję 2,3](2-directives.md#23-parallel-construct).

Liczba wątków do użycia jest definiowana przez implementację, jeśli:

- Zmienna środowiskowa `OMP_NUM_THREADS` nie jest określona,
- określona wartość nie jest dodatnią liczbą całkowitą.
- wartość jest większa niż maksymalna liczba wątków obsługiwanych przez system.

Przykład:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Odsyłacze

- klauzula [num_threads](2-directives.md#23-parallel-construct)
- Funkcja [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)
- Funkcja [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)

## <a name="43-omp_dynamic"></a>4,3 OMP_DYNAMIC

Zmienna środowiskowa `OMP_DYNAMIC` włącza lub wyłącza dynamiczne dopasowanie liczby wątków dostępnych do wykonywania równoległych regionów. `OMP_DYNAMIC` jest ignorowana, gdy dynamiczne dopasowanie jest jawnie włączone lub wyłączone przez wywołanie procedury biblioteki `omp_set_dynamic`. Wartość musi być `TRUE` lub `FALSE`.

Jeśli `OMP_DYNAMIC` jest ustawiona na `TRUE`, liczba wątków używanych do wykonywania regionów równoległych może zostać dostosowana przez środowisko uruchomieniowe, aby najlepiej wykorzystać zasoby systemowe.  Jeśli `OMP_DYNAMIC` jest ustawiona na `FALSE`, dynamiczne dopasowanie jest wyłączone. Domyślnym warunkiem jest zdefiniowana implementacja.

Przykład:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Odsyłacze

- [Równoległe regiony](2-directives.md#23-parallel-construct)
- Funkcja [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)

## <a name="44-omp_nested"></a>4,4 OMP_NESTED

Zmienna środowiskowa `OMP_NESTED` włącza lub wyłącza zagnieżdżoną równoległość, chyba że zagnieżdżona równoległość jest włączona lub wyłączona przez wywołanie procedury biblioteki `omp_set_nested`. Jeśli `OMP_NESTED` jest ustawiona na `TRUE`, zagnieżdżona równoległość jest włączona. Jeśli `OMP_NESTED` jest ustawiona na `FALSE`, zagnieżdżona równoległość jest wyłączona. Wartością domyślną jest `FALSE`.

Przykład:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Odwołanie krzyżowe

- Funkcja [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)
