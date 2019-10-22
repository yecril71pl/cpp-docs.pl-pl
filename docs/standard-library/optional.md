---
title: '&lt;optional&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: bce31811c98d351f3c561b3136d41f7ed23d13e0
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687255"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Definiuje szablon klasy kontenera `optional` i kilka szablonów pomocniczych.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<optional >

**Przestrzeń nazw:** std

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator = =](../standard-library/optional-operators.md#op_eq_eq)|Testuje, czy obiekt jest równy innemu obiektowi.|
|[operator!=](../standard-library/optional-operators.md#op_neq)|Testuje, czy obiekt nie jest równy innemu obiektowi.|
|[< operatora](../standard-library/optional-operators.md#op_lt)|Testuje, czy obiekt po lewej stronie jest mniejszy niż obiekt po prawej stronie.|
|[< operatora =](../standard-library/optional-operators.md#op_lt_eq)|Testuje, czy obiekt po lewej stronie jest mniejszy niż lub równy obiektowi po prawej stronie.|
|[> operatora](../standard-library/optional-operators.md#op_gt)|Testuje, czy obiekt po lewej stronie jest większy niż obiekt po prawej stronie.|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|Testuje, czy obiekt po lewej stronie jest większy lub równy obiektowi po prawej stronie.|

> [!NOTE]
> Oprócz porównania relacyjnego operatory \<optional > obsługują również porównanie z **nullopt** i `T`.

### <a name="functions"></a>Funkcje

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Sprawia, że obiekt jest opcjonalny.|
|[wymiany](../standard-library/optional-functions.md#swap)|Zamienia zawarte wartości dwóch `optional` obiektów.|

### <a name="classes-and-structs"></a>Klasy i struktury

|||
|-|-|
|hash|Zwraca wartość skrótu zawartego obiektu.|
|[Klasa opcjonalna](../standard-library/optional-class.md)|Opisuje obiekt, który może lub nie może zawierać wartości.|
|[nullopt_t, struktura](../standard-library/nullopt-t-structure.md)|Opisuje obiekt, który nie utrzymuje wartości.|
|[Klasa bad_optional_access](../standard-library/bad-optional-access-class.md)|Opisuje obiekt zgłoszony jako wyjątek, aby zgłosić próbę uzyskania dostępu do wartości, która nie istnieje.|

### <a name="objects"></a>Obiekty

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)|Wystąpienie `nullopt_t` do porównania.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
