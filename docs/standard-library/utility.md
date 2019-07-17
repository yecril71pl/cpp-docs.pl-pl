---
title: '&lt;Narzędzie&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: 76b04c3c26f6ec49f1d816feaeec7e21312d79a9
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246283"
---
# <a name="ltutilitygt"></a>&lt;Narzędzie&gt;

Definiuje typy, funkcje i operatory, które pomagają do zarządzania pary obiektów, które są przydatne, gdy dwa obiekty muszą być traktowane tak, jakby były one standardowej biblioteki języka C++.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<Narzędzia >

**Namespace:** standardowe

## <a name="remarks"></a>Uwagi

Pary są powszechnie używane w standardowej biblioteki języka C++. Są one wymagane zarówno jako argumentów i wartości zwracane dla różnych funkcji i jako typy elementów dla kontenerów, takich jak [map — klasa](../standard-library/map-class.md) i [multimap — klasa](../standard-library/multimap-class.md). \<Narzędzia > Nagłówek jest automatycznie dołączany przez \<mapy > Aby pomóc w zarządzaniu klucz/wartość pary typu elementów.

> [!NOTE]
> \<Narzędzia > nagłówka używa instrukcji `#include <initializer_list>`. Również odwołuje się do `class tuple` zgodnie z definicją w \<krotki >.

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|||
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|Formatu zmiennoprzecinkowego pierwotnych konwersji wartości liczbowych.|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|Klasa, która opakowuje typ `pair` elementu.|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|Klasa, która otacza `pair` liczba elementów.|

### <a name="objects"></a>Obiekty

|||
|-|-|
|[index_sequence](../standard-library/utility-functions.md#index_sequence)||
|[index_sequence_for](../standard-library/utility-functions.md#index_sequence_for)||
|[make_index_sequence](../standard-library/utility-functions.md#make_index_sequence)||
|[make_integer_sequence](../standard-library/utility-functions.md#make_integer_sequence)||

### <a name="functions"></a>Funkcje

|||
|-|-|
|[as_const](../standard-library/utility-functions.md#asconst)|Zwraca typu.|
|[declval —](../standard-library/utility-functions.md#declval)|Obliczanie wyrażenia skrót.|
|[exchange](../standard-library/utility-functions.md#exchange)|Przypisuje nową wartość do obiektu i zwraca starą wartość.|
|[do przodu](../standard-library/utility-functions.md#forward)|Zachowuje typu odwołania (albo `lvalue` lub `rvalue`) argumentu z trwa zasłonięte doskonałe przekazywanie do przodu.|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[get](../standard-library/utility-functions.md#get)|Funkcja, która pobiera element z `pair` obiektu.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|Funkcja pomocnika szablonu używane do konstruowania obiektów typu `pair`, gdzie typy składników są oparte na typach danych przekazywane jako parametry.|
|[Przenieś](../standard-library/utility-functions.md#move)|Zwraca przekazana w argumencie jako `rvalue` odwołania.|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[swap](../standard-library/utility-functions.md#swap)|Zamienia elementy z dwóch `pair` obiektów.|
|[to_chars](../standard-library/utility-functions.md#to_chars)|Konwertuje wartość na ciąg znaków.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator!=](../standard-library/utility-operators.md#op_neq)|Sprawdza, czy obiekt pary po lewej stronie operatora nie jest równy obiektowi pary po prawej stronie.|
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|Sprawdza, czy obiekt pary po lewej stronie operatora jest równy obiektowi pary po prawej stronie.|
|[Operator\<](../standard-library/utility-operators.md#op_lt)|Sprawdza, czy pary obiektu po lewej stronie operatora jest mniejszy niż obiekt pary po prawej stronie.|
|[Operator\<=](../standard-library/utility-operators.md#op_gt_eq)|Sprawdza, czy pary obiektu po lewej stronie operatora jest mniejszy niż lub równy obiektowi pary po prawej stronie.|
|[operator>](../standard-library/utility-operators.md#op_gt)|Sprawdza, czy obiekt pary po lewej stronie operatora jest większy niż obiekt pary po prawej stronie.|
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|Sprawdza, czy obiekt pary po lewej stronie operatora jest większy lub równy obiektowi pary po prawej stronie.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|Struktury używane dla `from_chars`.|
|[Tożsamość](../standard-library/identity-structure.md)|Struktury, która zawiera definicję dla typu jako parametru szablonu.|
|[in_place_t](../standard-library/in-place-t-struct.md)|Zawiera również struktury `in_place_type_t` i `in_place_index_t`.|
|[integer_sequence](../standard-library/integer-sequence-class.md)|Reprezentuje sekwencję liczby całkowitej.|
|[para](../standard-library/pair-structure.md)|Typ, który zapewnia możliwość traktowania dwa obiekty jako pojedynczy obiekt.|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|Typ używany do przechowywania w osobnych Konstruktor i przeciążenie funkcji.|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|Struktury używane dla `to_chars`.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
