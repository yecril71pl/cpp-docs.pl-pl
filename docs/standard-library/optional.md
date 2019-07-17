---
title: '&lt;optional&gt;'
ms.date: 11/04/2016
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: c73ad2ad94a5de29bc2c457fdf6ca8b9c783615c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267899"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Definiuje klasę szablonu pojemnika opcjonalne i kilka szablonów pomocniczych.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<opcjonalne >

**Namespace:** standardowe

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|Sprawdza, czy `optional` obiekt po lewej stronie operatora jest równy `optional` obiektu po prawej stronie.|
|[operator!=](../standard-library/optional-operators.md#op_neq)|Sprawdza, czy `optional` obiektu po lewej stronie operatora nie jest równa `optional` obiektu po prawej stronie.|
|[Operator <](../standard-library/optional-operators.md#op_lt)|Sprawdza, czy `optional` obiekt po lewej stronie operatora jest mniejszy od `optional` obiektu po prawej stronie.|
|[Operator < =](../standard-library/optional-operators.md#op_lt_eq)|Sprawdza, czy `optional` obiekt po lewej stronie operatora jest mniejszy niż lub równe `optional` obiektu po prawej stronie.|
|[operator>](../standard-library/optional-operators.md#op_gt)|Sprawdza, czy `optional` obiekt po lewej stronie operatora jest większy niż `optional` obiektu po prawej stronie.|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|Sprawdza, czy `optional` obiektu po lewej stronie operatora jest większy niż lub równa `optional` obiektu po prawej stronie.|

> [!NOTE]
> Oprócz relacyjnych porównuje \<opcjonalne > Operatorzy pomocy technicznej porównanie z **nullopt** i `T`.

### <a name="functions"></a>Funkcje

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Sprawia, że obiekt opcjonalne.|
|[swap](../standard-library/optional-functions.md#swap)||

### <a name="classes-and-structs"></a>Klasy i struktury

|||
|-|-|
|[Skrót]()||
|[Klasa opcjonalne](../standard-library/optional-class.md)|Opisuje obiekt, który może lub nie może zawierać wartości.|
|[nullopt_t — struktura](../standard-library/nullopt-t-structure.md)|Opisuje obiekt przechowujący nie wartość.|
|[bad_optional_access klasy](../standard-library/bad-optional-access-class.md)|Opisuje obiekt, który został zgłoszony jako wyjątek do zgłaszania próba uzyskania dostępu do wartości nie istnieje.|

### <a name="objects"></a>Obiekty

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)||

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
