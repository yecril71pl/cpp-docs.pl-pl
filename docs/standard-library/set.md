---
title: '&lt;set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <set>
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
ms.openlocfilehash: 633571f00cfe761b687e9b76624029f57ab6043e
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523913"
---
# <a name="ltsetgt"></a>&lt;set&gt;

Definiuje zestaw klas szablonów kontenera i multiset i ich szablonów pomocniczych.

## <a name="syntax"></a>Składnia

```cpp
#include <set>
```

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|Ustaw wersję|Multiset — wersja|Opis|
|-----------------|----------------------|-----------------|
|[Operator! = (set)](../standard-library/set-operators.md#op_neq)|[Operator! = (multiset)](../standard-library/set-operators.md#op_neq)|Sprawdza, czy set lub multiset — obiekt po lewej stronie operatora nie jest równa set lub multiset — obiekt po prawej stronie.|
|[Operator < (ustawiona)](../standard-library/set-operators.md#op_lt)|[Operator < (multiset)](../standard-library/set-operators.md#op_lt_multiset)|Sprawdza, czy set lub multiset — obiekt po lewej stronie operatora jest mniejszy niż set lub multiset — obiekt po prawej stronie.|
|[Operator < = (set)](../standard-library/set-operators.md#op_lt_eq)|[operator\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|Sprawdza, czy set lub multiset — obiekt po lewej stronie operatora jest mniejszy niż lub równe set lub multiset — obiekt po prawej stronie.|
|[Operator == (set)](../standard-library/set-operators.md#op_eq_eq)|[Operator == (multiset)](../standard-library/set-operators.md#op_eq_eq_multiset)|Sprawdza, czy set lub multiset — obiekt po lewej stronie operatora jest równy set lub multiset — obiekt po prawej stronie.|
|[operator > (ustawiona)](../standard-library/set-operators.md#op_gt)|[operator > (multiset)](../standard-library/set-operators.md#op_gt_multiset)|Sprawdza, czy set lub multiset — obiekt po lewej stronie operatora jest większy niż set lub multiset — obiekt po prawej stronie.|
|[operator > = (set)](../standard-library/set-operators.md#op_gt_eq)|[operator > = (multiset)](../standard-library/set-operators.md#op_gt_eq_multiset)|Sprawdza, czy set lub multiset — obiekt po lewej stronie operatora jest większy niż lub równa set lub multiset — obiekt po prawej stronie.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|Ustaw wersję|Multiset — wersja|Opis|
|-----------------|----------------------|-----------------|
|[swap](../standard-library/set-functions.md#swap)|[swap (multiset)](../standard-library/set-functions.md#swap_multiset)|Zamienia elementy z dwóch zestawów lub multisets.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[set, klasa](../standard-library/set-class.md)|Używany do przechowywania i pobierania danych z kolekcji, w której wartości zawartych elementów są unikatowe i służą jako wartości klucza, zgodnie z którymi dane są automatycznie porządkowane.|
|[multiset, klasa](../standard-library/multiset-class.md)|Używane do przechowywania i pobierania danych z kolekcji, w której wartości zawartych elementów nie muszą być unikatowe, i które służą jako wartości klucza, zgodnie z którymi dane są automatycznie porządkowane.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
