---
title: '&lt;Variant&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 7a812ccc3c8cb2a660c01ad2b17ea75b5d5c9542
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267887"
---
# <a name="ltvariantgt"></a>&lt;Variant&gt;

Variant — obiekt przechowuje i zarządza wartość. Jeśli wariant przechowuje wartość, typ tej wartości musi być jednym z typów argumentu szablonu do wariant. Te argumenty szablonu są określane jako alternatywy.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wariantu >

**Namespace:** standardowe

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator==](../standard-library/forward-list-operators.md#op_eq_eq)|Sprawdza, czy wariantu obiektu po lewej stronie operatora jest równy obiektowi wariantu po prawej stronie.|
|[operator!=](../standard-library/forward-list-operators.md#op_neq)|Sprawdza, czy obiekt wariantu po lewej stronie operatora nie jest równy obiektowi wariantu po prawej stronie.|
|[Operator <](../standard-library/forward-list-operators.md#op_lt)|Sprawdza, czy wariantu obiekt po lewej stronie operatora jest mniejszy niż variant obiektu po prawej stronie.|
|[Operator < =](../standard-library/forward-list-operators.md#op_lt_eq)|Sprawdza, czy wariant obiektu po lewej stronie operatora jest mniejszy niż lub równy obiektowi wariantu po prawej stronie.|
|[operator>](../standard-library/forward-list-operators.md#op_gt)|Sprawdza, czy wariantu obiekt po lewej stronie operatora jest większy niż variant obiektu po prawej stronie.|
|[operator>=](../standard-library/forward-list-operators.md#op_lt_eq)|Sprawdza, czy obiekt wariantu po lewej stronie operatora jest większy lub równy obiektowi wariantu po prawej stronie.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[get](../standard-library/variant-functions.md#get)|Pobiera typ variant obiektu.|
|[get_if](../standard-library/variant-functions.md#get_if)|Pobiera typ variant obiektu, jeśli taki istnieje.|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|Zwróć **true** istnienia wariant.|
|[swap](../standard-library/variant-functions.md#swap)|Zamienia **wariant**.|
|[Odwiedź stronę](../standard-library/variant-functions.md#visit)|Przechodzi do następnego **wariant**.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|Obiekty generowany raport nieprawidłowy dostęp do wartości obiektu variant.|
|[Variant](../standard-library/variant.md)|Obiekt do jednej przechowują wartość jednego z jego typów alternatywnych lub nie ma wartości.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[Skrót](../standard-library/hash-structure.md)||
|[monostate](../standard-library/monostate-structure.md)|Alternatywny typ wariantu Ustaw jako domyślny typ wariantu konstrukcyjną.|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|Pomaga wariantu obiektów.|
|[variant_size](../standard-library/variant-size-structure.md)|Pomaga wariantu obiektów.|

### <a name="objects"></a>Obiekty

|||
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
