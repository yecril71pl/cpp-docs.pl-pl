---
title: '&lt;Narzędzie&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <utility>
dev_langs:
- C++
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84464f485d39f1146f55fb6b5b1970cf1c9321df
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltutilitygt"></a>&lt;Narzędzie&gt;

Określa typy, funkcje i operatory, które pomogą utworzyć i zarządzać nimi pary obiektów, które są przydatne, gdy dwa obiekty muszą być traktowane jakby były one standardowa biblioteka C++.

## <a name="syntax"></a>Składnia

```cpp
#include <utility>

```

## <a name="remarks"></a>Uwagi

Pary są powszechnie używane w standardowej bibliotece C++. Są one wymagane zarówno jako argumentów i wartości zwracane dla różnych funkcji i jako typów elementów dla kontenerów, takich jak [map — klasa](../standard-library/map-class.md) i [multimap — klasa](../standard-library/multimap-class.md). \<Narzędzie > nagłówka jest automatycznie uwzględniany przez \<mapy > ułatwiających zarządzanie klucza i wartości pary typu elementów.

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|Klasa, która opakowuje typ `pair` elementu.|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|Klasa, która opakowuje `pair` elementu count.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[Prześlij dalej](../standard-library/utility-functions.md#forward)|Zachowuje typu odwołania (albo `lvalue` lub `rvalue`) argumentu z trwa zasłonięty przez doskonałego przekazywania dalej.|
|[get](../standard-library/utility-functions.md#get)|Funkcja, która pobiera element na podstawie `pair` obiektu.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|Funkcja pomocnika szablonu, użyty do utworzenia obiektów typu `pair`, gdzie typów składników są oparte na typach danych przekazywane jako parametry.|
|[Przenieś](../standard-library/utility-functions.md#move)|Zwraca przekazany argument jako `rvalue` odwołania.|
|[swap](../standard-library/utility-functions.md#swap)|Zamienia elementy dwóch `pair` obiektów.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](../standard-library/utility-operators.md#op_neq)|Testy, jeśli obiekt pary po lewej stronie operatora nie jest taki sam jak obiekt pary po prawej stronie.|
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|Testy, jeśli obiekt pary po lewej stronie operatora jest taki sam jak obiekt pary po prawej stronie.|
|[Operator <](../standard-library/utility-operators.md#op_lt)|Testy, jeśli obiekt pary po lewej stronie operatora jest mniejsza niż obiekt pary po prawej stronie.|
|[Operator\<=](../standard-library/utility-operators.md#op_gt_eq)|Testy, jeśli obiekt pary po lewej stronie operatora jest mniejsza niż lub równe obiekt pary po prawej stronie.|
|[operator>](../standard-library/utility-operators.md#op_gt)|Testy, jeśli obiekt pary po lewej stronie operatora jest większy niż obiekt pary po prawej stronie.|
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|Testy, jeśli obiekt pary po lewej stronie operatora jest większa niż lub równa obiekt pary po prawej stronie.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[Tożsamości](../standard-library/identity-structure.md)||
|[para](../standard-library/pair-structure.md)|Typ, który pozwala na traktowanie dwa obiekty jako pojedynczego obiektu.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
