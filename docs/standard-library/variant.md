---
title: '&lt;typu&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 6074c80b20ae0c69d34768bc16d7aaae16c99579
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232823"
---
# <a name="ltvariantgt"></a>&lt;typu&gt;

Obiekt Variant utrzymuje wartość i zarządza nią. Jeśli wariant utrzymuje wartość, typ tej wartości musi być jednym z typów argumentów szablonu przyznanych do wariantu. Te argumenty szablonu są nazywane alternatywami.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<variant>

**Przestrzeń nazw:** std

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator = =](../standard-library/forward-list-operators.md#op_eq_eq)|Testuje, czy obiekt VARIANT po lewej stronie operatora jest równy obiektowi Variant po prawej stronie.|
|[operator! =](../standard-library/forward-list-operators.md#op_neq)|Testuje, czy obiekt VARIANT po lewej stronie operatora nie jest równy obiektowi Variant po prawej stronie.|
|[<operatora](../standard-library/forward-list-operators.md#op_lt)|Testuje, czy obiekt VARIANT po lewej stronie operatora jest mniejszy niż obiekt VARIANT po prawej stronie.|
|[<operatora =](../standard-library/forward-list-operators.md#op_lt_eq)|Testuje, czy obiekt VARIANT po lewej stronie operatora jest mniejszy niż lub równy obiektowi Variant po prawej stronie.|
|[>operatora](../standard-library/forward-list-operators.md#op_gt)|Testuje, czy obiekt VARIANT po lewej stronie operatora jest większy niż obiekt VARIANT po prawej stronie.|
|[>operatora =](../standard-library/forward-list-operators.md#op_lt_eq)|Testuje, czy obiekt VARIANT po lewej stronie operatora jest większy niż lub równy obiektowi Variant po prawej stronie.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[Pobierz](../standard-library/variant-functions.md#get)|Pobiera wariant obiektu.|
|[get_if](../standard-library/variant-functions.md#get_if)|Pobiera wariant obiektu, jeśli istnieje.|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|Zwraca **`true`** , jeśli istnieje wariant.|
|[wymiany](../standard-library/variant-functions.md#swap)|Zamienia **wariant**.|
|[stronę](../standard-library/variant-functions.md#visit)|Przenosi do następnego **wariantu**.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|Obiekty zgłoszone w celu zgłaszania nieprawidłowych dostępu do wartości obiektu Variant.|
|[typu](../standard-library/variant.md)|Obiekt do przechowywania wartości jednego z jej typów alternatywnych lub nie ma wartości.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[skrótu](../standard-library/hash-structure.md)||
|[stan](../standard-library/monostate-structure.md)|Typ alternatywny dla wariantu, który ma być wartością domyślną konstrukcyjną.|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|Ułatwia obiekty wariantów.|
|[variant_size](../standard-library/variant-size-structure.md)|Ułatwia obiekty wariantów.|

### <a name="objects"></a>Obiekty

|||
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
