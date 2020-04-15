---
title: 4. Zmienne środowiskowe
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: e93c59654c17ed6dbfb7483ac2dce716ce24b52a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370267"
---
# <a name="4-environment-variables"></a>4. Zmienne środowiskowe

W tym rozdziale opisano zmienne środowiskowe interfejsu API OpenMP C i C++ (lub podobne mechanizmy specyficzne dla platformy), które kontrolują wykonywanie kodu równoległego.  Nazwy zmiennych środowiskowych muszą być wielkie litery. Przypisane do nich wartości są niewrażliwe na wielkości liter i mogą mieć odstęp wiodący i końcowy.  Modyfikacje wartości po uruchomieniu programu są ignorowane.

Zmienne środowiskowe są następujące:

- [OMP_SCHEDULE](#41-omp_schedule) ustawia typ harmonogramu wykonywania i rozmiar fragmentu.
- [OMP_NUM_THREADS](#42-omp_num_threads) ustawia liczbę wątków do użycia podczas wykonywania.
- [OMP_DYNAMIC](#43-omp_dynamic) włącza lub wyłącza dynamiczną regulację liczby wątków.
- [OMP_NESTED](#44-omp_nested) włącza lub wyłącza równoległości zagnieżdżone.

Przykłady w tym rozdziale pokazują tylko, jak te zmienne mogą być ustawione w środowiskach powłoki Uniks C (csh). W środowiskach Korn shell i DOS akcje są podobne:

Csh:  
`setenv OMP_SCHEDULE "dynamic"`

Ksh:  
`export OMP_SCHEDULE="dynamic"`

Dos:  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a><a name="41-omp_schedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE`ma zastosowanie `for` tylko `parallel for` do i dyrektyw, `runtime`które mają typ harmonogramu . Typ harmonogramu i rozmiar fragmentu dla wszystkich takich pętli można ustawić w czasie wykonywania. Ustaw tę zmienną środowiskową na dowolny rozpoznany typ harmonogramu i na opcjonalną *chunk_size*.

Dla `for` `parallel for` i dyrektyw, które mają `runtime`typ `OMP_SCHEDULE` harmonogramu inny niż , jest ignorowany. Wartość domyślna dla tej zmiennej środowiskowej jest zdefiniowana w implementacji. Jeśli ustawiono *opcjonalny chunk_size,* wartość musi być dodatnia. Jeśli *chunk_size* nie jest ustawiona, przyjmuje się wartość 1, z `static`wyjątkiem sytuacji, gdy harmonogram jest . W `static` przypadku harmonogramu domyślny rozmiar fragmentu jest ustawiony na spację iteracji pętli podzieloną przez liczbę wątków zastosowanych do pętli.

Przykład:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Odsyłacze

- [dla](2-directives.md#241-for-construct) dyrektywy
- [równolegle do](2-directives.md#251-parallel-for-construct) dyrektywy

## <a name="42-omp_num_threads"></a><a name="42-omp_num_threads"></a>4.2 OMP_NUM_THREADS

Zmienna środowiskowa `OMP_NUM_THREADS` ustawia domyślną liczbę wątków do użycia podczas wykonywania. `OMP_NUM_THREADS`jest ignorowana, jeśli ten numer jest `omp_set_num_threads` jawnie zmieniony przez wywołanie procedury biblioteki. Jest również ignorowane, jeśli istnieje `num_threads` jawna `parallel` klauzula w dyrektywie.

Wartość zmiennej `OMP_NUM_THREADS` środowiskowej musi być dodatnią całkowitej liczby. Jego efekt zależy od tego, czy dynamiczna regulacja liczby wątków jest włączona. Aby uzyskać kompleksowy zestaw reguł `OMP_NUM_THREADS` dotyczących interakcji między zmienną środowiskową a dynamiczną regulacją wątków, zobacz [sekcję 2.3](2-directives.md#23-parallel-construct).

Liczba wątków do użycia jest zdefiniowana w implementacji, jeśli:

- zmienna `OMP_NUM_THREADS` środowiskowa nie jest określona,
- określona wartość nie jest dodatnią całkowitej liczby, lub
- wartość jest większa niż maksymalna liczba wątków, które system może obsługiwać.

Przykład:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Odsyłacze

- [num_threads klauzula](2-directives.md#23-parallel-construct)
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) funkcja
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) funkcja

## <a name="43-omp_dynamic"></a><a name="43-omp_dynamic"></a>4.3 OMP_DYNAMIC

Zmienna środowiskowa `OMP_DYNAMIC` włącza lub wyłącza dynamiczne dostosowanie liczby wątków dostępnych do wykonywania regionów równoległych. `OMP_DYNAMIC`jest ignorowana, gdy dynamiczne dopasowanie jest jawnie włączone lub wyłączone przez wywołanie procedury `omp_set_dynamic` biblioteki. Jego wartość `TRUE` musi `FALSE`być lub .

Jeśli `OMP_DYNAMIC` jest `TRUE`ustawiona na , liczba wątków, które są używane do wykonywania regionów równoległych mogą być dostosowane przez środowisko wykonawcze, aby jak najlepiej wykorzystać zasoby systemowe.  Jeśli `OMP_DYNAMIC` jest `FALSE`ustawiona na , regulacja dynamiczna jest wyłączona. Warunkiem domyślnym jest zdefiniowana implementacja.

Przykład:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Odsyłacze

- [Regiony równoległe](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) funkcja

## <a name="44-omp_nested"></a><a name="44-omp_nested"></a>4.4 OMP_NESTED

Zmienna środowiskowa `OMP_NESTED` włącza lub wyłącza równoległości zagnieżdżonej, `omp_set_nested` chyba że zagnieżdżone równoległości jest włączona lub wyłączona przez wywołanie procedury biblioteki. Jeśli `OMP_NESTED` jest `TRUE`ustawiona na , zagnieżdżony równoległość jest włączona. Jeśli `OMP_NESTED` jest `FALSE`ustawiona na , zagnieżdżony równoległość jest wyłączona. Wartością domyślną jest `FALSE`.

Przykład:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Odsyłacza

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) funkcja
