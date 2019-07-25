---
title: '&lt;optional&gt;'
ms.date: 11/04/2016
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: 83a0ad52735f92d731dafb32ad1be5a8278776b4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447183"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Definiuje klasę szablonu kontenera opcjonalnie i kilka szablonów pomocniczych.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> opcjonalne

**Przestrzeń nazw:** std

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|Testuje, `optional` czy obiekt po lewej stronie operatora jest równy `optional` obiektowi po prawej stronie.|
|[operator!=](../standard-library/optional-operators.md#op_neq)|Testuje, `optional` czy obiekt po lewej stronie operatora nie jest równy `optional` obiektowi po prawej stronie.|
|[< operatora](../standard-library/optional-operators.md#op_lt)|Testuje, `optional` czy obiekt po lewej stronie operatora jest mniejszy `optional` od obiektu po prawej stronie.|
|[< operatora =](../standard-library/optional-operators.md#op_lt_eq)|Testuje, `optional` czy obiekt po lewej stronie operatora jest mniejszy od lub równy `optional` obiektowi po prawej stronie.|
|[operator>](../standard-library/optional-operators.md#op_gt)|Testuje, `optional` czy obiekt po lewej stronie operatora jest większy `optional` niż obiekt po prawej stronie.|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|Testuje, `optional` czy obiekt po lewej stronie operatora jest większy niż lub równy `optional` obiektowi po prawej stronie.|

> [!NOTE]
> Oprócz porównywania \<relacyjnego operatory opcjonalne > obsługują również porównanie z **nullopt** i `T`.

### <a name="functions"></a>Funkcje

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Sprawia, że obiekt jest opcjonalny.|
|[swap](../standard-library/optional-functions.md#swap)||

### <a name="classes-and-structs"></a>Klasy i struktury

|||
|-|-|
|[skrótu]()||
|[Klasa opcjonalna](../standard-library/optional-class.md)|Opisuje obiekt, który może lub nie może zawierać wartości.|
|[nullopt_t, struktura](../standard-library/nullopt-t-structure.md)|Opisuje obiekt, który nie utrzymuje wartości.|
|[Klasa bad_optional_access](../standard-library/bad-optional-access-class.md)|Opisuje obiekt zgłoszony jako wyjątek, aby zgłosić próbę uzyskania dostępu do wartości, która nie istnieje.|

### <a name="objects"></a>Obiekty

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)||

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
