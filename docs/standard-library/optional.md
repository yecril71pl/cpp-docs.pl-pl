---
title: '&lt;optional&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: f3b4896a3cb4774e46b36480dd9769fa131fc287
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957177"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Definiuje klasę `optional` szablonu kontenera i kilka szablonów pomocniczych.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> opcjonalne

**Przestrzeń nazw:** std

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|Testuje, czy obiekt jest równy innemu obiektowi.|
|[operator!=](../standard-library/optional-operators.md#op_neq)|Testuje, czy obiekt nie jest równy innemu obiektowi.|
|[< operatora](../standard-library/optional-operators.md#op_lt)|Testuje, czy obiekt po lewej stronie jest mniejszy niż obiekt po prawej stronie.|
|[< operatora =](../standard-library/optional-operators.md#op_lt_eq)|Testuje, czy obiekt po lewej stronie jest mniejszy niż lub równy obiektowi po prawej stronie.|
|[operator>](../standard-library/optional-operators.md#op_gt)|Testuje, czy obiekt po lewej stronie jest większy niż obiekt po prawej stronie.|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|Testuje, czy obiekt po lewej stronie jest większy lub równy obiektowi po prawej stronie.|

> [!NOTE]
> Oprócz porównywania \<relacyjnego operatory opcjonalne > obsługują również porównanie z **nullopt** i `T`.

### <a name="functions"></a>Funkcje

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Sprawia, że obiekt jest opcjonalny.|
|[swap](../standard-library/optional-functions.md#swap)|Zamienia zawarte wartości dwóch `optional` obiektów.|

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
|[nullopt](../standard-library/optional-functions.md#nullopt)|Wystąpienie `nullopt_t` do porównywania.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
