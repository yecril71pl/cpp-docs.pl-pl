---
title: '&lt;Spuninst&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: 1beade28ceec0f1552def4bc70c2e95e6b2aa24d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215442"
---
# <a name="ltutilitygt"></a>&lt;Spuninst&gt;

Definiuje standardowe typy bibliotek języka C++, funkcje i operatory, które pomagają tworzyć pary obiektów i nimi zarządzać, które są przydatne, gdy dwa obiekty muszą być traktowane tak, jakby były takie same.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<utility>

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Pary są szeroko używane w standardowej bibliotece języka C++. Są one wymagane zarówno jako argumenty, jak i wartości zwracane dla różnych funkcji oraz jako typy elementów dla kontenerów, takich jak [Klasa mapy](../standard-library/map-class.md) i [Klasa multimap](../standard-library/multimap-class.md). \<utility>Nagłówek jest automatycznie dołączany przez, \<map> Aby pomóc w zarządzaniu elementami typu pary klucz/wartość.

> [!NOTE]
> \<utility>Nagłówek używa instrukcji `#include <initializer_list>` . Odnosi się także do programu `class tuple` zgodnie z definicją w \<tuple> .

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|Typ|Opis|
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|Format zmiennoprzecinkowy dla konwersji liczbowej typu pierwotnego.|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|Klasa, która otacza typ `pair` elementu.|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|Klasa, która zawija `pair` liczbę elementów.|

### <a name="objects"></a>Obiekty

|Szablon|Opis|
|-|-|
|[index_sequence](../standard-library/utility-functions.md#index_sequence)|Szablon aliasu zdefiniowany dla typowego przypadku, w którym `T` jest`std::size_t`  |
|[index_sequence_for](../standard-library/utility-functions.md#index_sequence_for)|Szablon aliasu pomocnika do konwersji dowolnego pakietu parametrów typu na sekwencję indeksu o tej samej długości|
|[make_index_sequence](../standard-library/utility-functions.md#make_index_sequence)| Szablon aliasu pomocnika, który upraszcza tworzenie `std::index_sequence` typu. |
|[make_integer_sequence](../standard-library/utility-functions.md#make_integer_sequence)|Szablon aliasu pomocnika, który upraszcza tworzenie `std::integer_sequence` typu.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[as_const](../standard-library/utility-functions.md#asconst)|Zwraca typ.|
|[declval —](../standard-library/utility-functions.md#declval)|Obliczanie wyrażenia skrótu.|
|[zamian](../standard-library/utility-functions.md#exchange)|Przypisuje nową wartość do obiektu i zwraca jego starą wartość.|
|[prześlą](../standard-library/utility-functions.md#forward)|Zachowuje typ odwołania ( `lvalue` lub `rvalue` ) argumentu w celu przesłaniania przez doskonałe przekazywanie.|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[Pobierz](../standard-library/utility-functions.md#get)|Funkcja, która pobiera element z `pair` obiektu.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|Funkcja pomocnika szablonu służąca do konstruowania obiektów typu `pair` , w których typy składników są oparte na typach danych przesłanych jako parametry.|
|[Przenieś](../standard-library/utility-functions.md#move)|Zwraca wartość argumentu przekazaną jako `rvalue` odwołanie.|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[wymiany](../standard-library/utility-functions.md#swap)|Wymienia elementy dwóch `pair` obiektów.|
|[to_chars](../standard-library/utility-functions.md#to_chars)|Konwertuje wartość na ciąg znaków.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator! =](../standard-library/utility-operators.md#op_neq)|Testuje, czy obiekt pary po lewej stronie operatora nie jest równy obiektowi pary po prawej stronie.|
|[operator = =](../standard-library/utility-operators.md#op_eq_eq)|Testuje, czy obiekt pary po lewej stronie operatora jest równy obiektowi pary po prawej stronie.|
|[zakład\<](../standard-library/utility-operators.md#op_lt)|Testuje, czy obiekt pary po lewej stronie operatora jest mniejszy od obiektu pary po prawej stronie.|
|[zakład\<=](../standard-library/utility-operators.md#op_gt_eq)|Testuje, czy obiekt pary po lewej stronie operatora jest mniejszy niż lub równy obiektowi pary po prawej stronie.|
|[>operatora](../standard-library/utility-operators.md#op_gt)|Testuje, czy obiekt pary po lewej stronie operatora jest większy niż obiekt pary po prawej stronie.|
|[>operatora =](../standard-library/utility-operators.md#op_gt_eq)|Testuje, czy obiekt pary po lewej stronie operatora jest większy niż lub równy obiektowi pary po prawej stronie.|

### <a name="structs"></a>Struktury

|Struktura|Opis|
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|Struktura użyta dla `from_chars` .|
|[Identity](../standard-library/identity-structure.md)|Struktura, która dostarcza definicję typu jako parametr szablonu.|
|[in_place_t](../standard-library/in-place-t-struct.md)|Zawiera również struktury `in_place_type_t` i `in_place_index_t` .|
|[integer_sequence](../standard-library/integer-sequence-class.md)|Reprezentuje sekwencję całkowitą.|
|[parowanie](../standard-library/pair-structure.md)|Typ, który umożliwia traktowanie dwóch obiektów jako jednego obiektu.|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|Typ służący do zachowywania osobnego konstruktora i przeciążania funkcji.|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|Struktura użyta dla `to_chars` .|

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
