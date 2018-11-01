---
title: '&lt;set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <set>
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
ms.openlocfilehash: f5f33cbb179e3d0304f8128066dc04d6c3927d8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565376"
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
