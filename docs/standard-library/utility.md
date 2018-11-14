---
title: '&lt;Narzędzie&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: 3e3904bda2a20392724f86df2443cd71a14a1ad6
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51525130"
---
# <a name="ltutilitygt"></a>&lt;Narzędzie&gt;

Definiuje typy, funkcje i operatory, które pomagają do zarządzania pary obiektów, które są przydatne, gdy dwa obiekty muszą być traktowane tak, jakby były one standardowej biblioteki języka C++.

## <a name="syntax"></a>Składnia

```cpp
#include <utility>
```

## <a name="remarks"></a>Uwagi

Pary są powszechnie używane w standardowej biblioteki języka C++. Są one wymagane zarówno jako argumentów i wartości zwracane dla różnych funkcji i jako typy elementów dla kontenerów, takich jak [map — klasa](../standard-library/map-class.md) i [multimap — klasa](../standard-library/multimap-class.md). \<Narzędzia > Nagłówek jest automatycznie dołączany przez \<mapy > Aby pomóc w zarządzaniu klucz/wartość pary typu elementów.

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|Klasa, która opakowuje typ `pair` elementu.|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|Klasa, która otacza `pair` liczba elementów.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[do przodu](../standard-library/utility-functions.md#forward)|Zachowuje typu odwołania (albo `lvalue` lub `rvalue`) argumentu z trwa zasłonięte doskonałe przekazywanie do przodu.|
|[get](../standard-library/utility-functions.md#get)|Funkcja, która pobiera element z `pair` obiektu.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|Funkcja pomocnika szablonu używane do konstruowania obiektów typu `pair`, gdzie typy składników są oparte na typach danych przekazywane jako parametry.|
|[Przenieś](../standard-library/utility-functions.md#move)|Zwraca przekazana w argumencie jako `rvalue` odwołania.|
|[swap](../standard-library/utility-functions.md#swap)|Zamienia elementy z dwóch `pair` obiektów.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](../standard-library/utility-operators.md#op_neq)|Sprawdza, czy obiekt pary po lewej stronie operatora nie jest równy obiektowi pary po prawej stronie.|
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|Sprawdza, czy obiekt pary po lewej stronie operatora jest równy obiektowi pary po prawej stronie.|
|[Operator <](../standard-library/utility-operators.md#op_lt)|Sprawdza, czy pary obiektu po lewej stronie operatora jest mniejszy niż obiekt pary po prawej stronie.|
|[Operator\<=](../standard-library/utility-operators.md#op_gt_eq)|Sprawdza, czy pary obiektu po lewej stronie operatora jest mniejszy niż lub równy obiektowi pary po prawej stronie.|
|[operator>](../standard-library/utility-operators.md#op_gt)|Sprawdza, czy obiekt pary po lewej stronie operatora jest większy niż obiekt pary po prawej stronie.|
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|Sprawdza, czy obiekt pary po lewej stronie operatora jest większy lub równy obiektowi pary po prawej stronie.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[Tożsamość](../standard-library/identity-structure.md)||
|[para](../standard-library/pair-structure.md)|Typ, który zapewnia możliwość traktowania dwa obiekty jako pojedynczy obiekt.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
