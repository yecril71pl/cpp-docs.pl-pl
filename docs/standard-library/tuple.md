---
title: '&lt;tuple&gt;'
ms.date: 11/04/2016
f1_keywords:
- <tuple>
helpviewer_keywords:
- tuple header
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
ms.openlocfilehash: b1eeba2fced21f5a38799db7fc4af259e03bc266
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841847"
---
# <a name="lttuplegt"></a>&lt;tuple&gt;

Definiuje szablon, `tuple` którego wystąpienia zawierają obiekty o różnych typach.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<tuple>

**Przestrzeń nazw:** std

## <a name="members"></a>Elementy członkowskie

### <a name="classes-and-structs"></a>Klasy i struktury

|Nazwa|Opis|
|-|-|
|[Krotka — Klasa](../standard-library/tuple-class.md)|Otacza sekwencję o stałej długości elementów.|
|[Klasa tuple_element](../standard-library/tuple-element-class-tuple.md)|Zawija typ `tuple` elementu.|
|[Klasa tuple_size](../standard-library/tuple-size-class-tuple.md)|Zawija `tuple` liczbę elementów.|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||

### <a name="objects"></a>Obiekty

|Nazwa|Opis|
|-|-|
|[tuple_element_t](../standard-library/tuple-functions.md#tuple_element_t)||
|[tuple_size_v](../standard-library/tuple-functions.md#tuple_size_v)||

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[operator = =](../standard-library/tuple-operators.md#op_eq_eq)|Porównywanie `tuple` obiektów, równe.|
|[operator! =](../standard-library/tuple-operators.md#op_neq)|Porównanie `tuple` obiektów, a nie równa się.|
|[<operatora ](../standard-library/tuple-operators.md#op_lt)|Porównanie `tuple` obiektów, mniejsze niż.|
|[<operatora =](../standard-library/tuple-operators.md#op_lt_eq)|Porównanie `tuple` obiektów, mniejsze niż lub równe.|
|[>operatora ](../standard-library/tuple-operators.md#op_gt)|Porównanie `tuple` obiektów, większe niż.|
|[>operatora =](../standard-library/tuple-operators.md#op_gt_eq)|Porównanie `tuple` obiektów, większe niż lub równe.|

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[stosowa](../standard-library/tuple-functions.md#apply)|Wywołuje funkcję z krotką.|
|[forward_as_tuple](../standard-library/tuple-functions.md#forward)|Konstruuje krotkę odwołań.|
|[get](../standard-library/tuple-functions.md#get)|Pobiera element z `tuple` obiektu.|
|[make_from_tuple](../standard-library/tuple-functions.md#make_from_tuple)|Skrót od do `tuple` .|
|[make_tuple](../standard-library/tuple-functions.md#make_tuple)|Tworzy `tuple` wartości elementu z.|
|[wymiany](../standard-library/tuple-functions.md#swap)||
|[równe](../standard-library/tuple-functions.md#tie)|Tworzy `tuple` odwołania do elementu z.|
|[tuple_cat](../standard-library/tuple-functions.md#tuple_cat)|Konstruuje obiekt krotki z zakresem elementów typu.|

## <a name="see-also"></a>Zobacz też

[\<array>](../standard-library/array.md)
