---
title: '&lt;Spuninst&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: eaae94bcffcda6e113001dd7070bcc80e7c14d09
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458080"
---
# <a name="ltutilitygt"></a>&lt;Spuninst&gt;

Definiuje C++ standardowe typy bibliotek, funkcje i operatory, które ułatwiają konstruowanie par obiektów i zarządzanie nimi, co jest przydatne, gdy dwa obiekty muszą być traktowane tak, jakby były takie same.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> narzędzi

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Pary są szeroko używane w C++ standardowej bibliotece. Są one wymagane zarówno jako argumenty, jak i wartości zwracane dla różnych funkcji oraz jako typy elementów dla kontenerów, takich jak [Klasa mapy](../standard-library/map-class.md) i [Klasa multimap](../standard-library/multimap-class.md). Nagłówek > \<narzędzia jest automatycznie dołączany przez mapowanie > do ułatwienia zarządzania elementami typu pary klucz/wartość. \<

> [!NOTE]
> `#include <initializer_list>`Nagłówek > \<narzędzia używa instrukcji. Odnosi się to `class tuple` również do zdefiniowanej w \<> krotek.

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|||
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|Format zmiennoprzecinkowy dla konwersji liczbowej typu pierwotnego.|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|Klasa, która otacza typ `pair` elementu.|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|Klasa, która zawija `pair` liczbę elementów.|

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
|[as_const](../standard-library/utility-functions.md#asconst)|Zwraca typ.|
|[declval —](../standard-library/utility-functions.md#declval)|Obliczanie wyrażenia skrótu.|
|[exchange](../standard-library/utility-functions.md#exchange)|Przypisuje nową wartość do obiektu i zwraca jego starą wartość.|
|[prześlą](../standard-library/utility-functions.md#forward)|Zachowuje typ odwołania ( `lvalue` lub `rvalue`) argumentu w celu przesłaniania przez doskonałe przekazywanie.|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[get](../standard-library/utility-functions.md#get)|Funkcja, która pobiera element z `pair` obiektu.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|Funkcja pomocnika szablonu służąca do konstruowania obiektów `pair`typu, w których typy składników są oparte na typach danych przesłanych jako parametry.|
|[Przenieś](../standard-library/utility-functions.md#move)|Zwraca wartość argumentu przekazaną jako `rvalue` odwołanie.|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[swap](../standard-library/utility-functions.md#swap)|Wymienia elementy dwóch `pair` obiektów.|
|[to_chars](../standard-library/utility-functions.md#to_chars)|Konwertuje wartość na ciąg znaków.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator!=](../standard-library/utility-operators.md#op_neq)|Testuje, czy obiekt pary po lewej stronie operatora nie jest równy obiektowi pary po prawej stronie.|
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|Testuje, czy obiekt pary po lewej stronie operatora jest równy obiektowi pary po prawej stronie.|
|[zakład\<](../standard-library/utility-operators.md#op_lt)|Testuje, czy obiekt pary po lewej stronie operatora jest mniejszy od obiektu pary po prawej stronie.|
|[zakład\<=](../standard-library/utility-operators.md#op_gt_eq)|Testuje, czy obiekt pary po lewej stronie operatora jest mniejszy niż lub równy obiektowi pary po prawej stronie.|
|[operator>](../standard-library/utility-operators.md#op_gt)|Testuje, czy obiekt pary po lewej stronie operatora jest większy niż obiekt pary po prawej stronie.|
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|Testuje, czy obiekt pary po lewej stronie operatora jest większy niż lub równy obiektowi pary po prawej stronie.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|Struktura użyta dla `from_chars`.|
|[Identity](../standard-library/identity-structure.md)|Struktura, która dostarcza definicję typu jako parametr szablonu.|
|[in_place_t](../standard-library/in-place-t-struct.md)|Zawiera również struktury `in_place_type_t` i `in_place_index_t`.|
|[integer_sequence](../standard-library/integer-sequence-class.md)|Reprezentuje sekwencję całkowitą.|
|[wzrok](../standard-library/pair-structure.md)|Typ, który umożliwia traktowanie dwóch obiektów jako jednego obiektu.|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|Typ służący do zachowywania osobnego konstruktora i przeciążania funkcji.|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|Struktura użyta dla `to_chars`.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
