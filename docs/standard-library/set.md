---
title: '&lt;set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <set>
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
ms.openlocfilehash: 4ac5c0bbf94c4d17389efb424d2e12b84717c4a9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846228"
---
# <a name="ltsetgt"></a>&lt;set&gt;

Definiuje zestaw szablonów klas kontenerów i zestawy wielokrotne oraz ich szablony pomocnicze.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<set>

**Przestrzeń nazw:** std

> [!NOTE]
> \<set>Biblioteka używa również `#include <initializer_list>` instrukcji.

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|Ustaw wersję|Wersja zestawu wielokrotnego|Opis|
|-|-|-|
|[operator! = (Set)](../standard-library/set-operators.md#op_neq)|[operator! = (zestaw wielokrotny)](../standard-library/set-operators.md#op_neq)|Testuje, czy obiekt Set lub zestaw wielokrotny po lewej stronie operatora nie jest równy obiektowi Set lub zestawowi wielokrotnemu po prawej stronie.|
|[< operatora (Set)](../standard-library/set-operators.md#op_lt)|[< operatora (zestaw wielokrotny)](../standard-library/set-operators.md#op_lt_multiset)|Testuje, czy obiekt Set lub zestaw wielokrotny po lewej stronie operatora jest mniejszy niż obiekt zestawu lub zestaw wielokrotny po prawej stronie.|
|[<operatora = (Set)](../standard-library/set-operators.md#op_lt_eq)|[operator \< = (zestaw wielokrotny)](../standard-library/set-operators.md#op_lt_eq_multiset)|Testuje, czy obiekt Set lub zestaw wielokrotny po lewej stronie operatora jest mniejszy od lub równy obiektowi Set lub zestawu wielokrotnego po prawej stronie.|
|[operator = = (Set)](../standard-library/set-operators.md#op_eq_eq)|[operator = = (zestaw wielokrotny)](../standard-library/set-operators.md#op_eq_eq_multiset)|Testuje, czy obiekt Set lub zestaw wielokrotny po lewej stronie operatora jest równy obiektowi Set lub zestawowi wielokrotnemu po prawej stronie.|
|[> operatora (Set)](../standard-library/set-operators.md#op_gt)|[> operatora (zestaw wielokrotny)](../standard-library/set-operators.md#op_gt_multiset)|Testuje, czy obiekt Set lub zestaw wielokrotny po lewej stronie operatora jest większy niż obiekt zestawu lub zestaw wielokrotny po prawej stronie.|
|[>operatora = (Set)](../standard-library/set-operators.md#op_gt_eq)|[operator>= (zestaw wielokrotny)](../standard-library/set-operators.md#op_gt_eq_multiset)|Testuje, czy obiekt Set lub zestaw wielokrotny po lewej stronie operatora jest większy niż lub równy obiektowi Set lub zestawowi wielokrotnemu po prawej stronie.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|Ustaw wersję|Wersja zestawu wielokrotnego|Opis|
|-|-|-|
|[wymiany](../standard-library/set-functions.md#swap)|[swap (zestaw wielokrotny)](../standard-library/set-functions.md#swap_multiset)|Wymienia elementy dwóch zestawów lub zestawów wielozbiorówowych.|

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|-|-|
|[Ustaw klasę](../standard-library/set-class.md)|Używany do przechowywania i pobierania danych z kolekcji, w której wartości zawartych elementów są unikatowe i służą jako wartości klucza, zgodnie z którymi dane są automatycznie uporządkowane.|
|[Klasa wielu zestawów](../standard-library/multiset-class.md)|Używany do przechowywania i pobierania danych z kolekcji, w której wartości zawartych elementów nie muszą być unikatowe i w których służą jako wartości klucza, zgodnie z którymi dane są automatycznie porządkowane.|

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
