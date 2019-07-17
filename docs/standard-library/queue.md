---
title: '&lt;kolejki&gt;'
ms.date: 11/04/2016
f1_keywords:
- <queue>
helpviewer_keywords:
- queue header
ms.assetid: 24fcf350-eb0e-48cf-9fef-978be1aeda1f
ms.openlocfilehash: 641ab1bfe99360320509b806149fcedfe1068879
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240362"
---
# <a name="ltqueuegt"></a>&lt;kolejki&gt;

Definiuje priority_queue — klasy szablonu i kolejki oraz kilka szablonów pomocniczych.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<kolejki >

**Namespace:** standardowe

> [!NOTE]
> \<Kolejki > używa również biblioteki `#include <initializer_list>` instrukcji.

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator!=](../standard-library/queue-operators.md#op_neq)|Sprawdza, czy obiekt kolejki po lewej stronie operatora nie jest taki sam jak obiekt kolejki po prawej stronie.|
|[Operator <](../standard-library/queue-operators.md#op_lt)|Sprawdza, czy obiekt kolejki po lewej stronie operatora jest mniejszy niż obiekt kolejki po prawej stronie.|
|[Operator\<=](../standard-library/queue-operators.md#op_gt_eq)|Sprawdza, czy kolejka obiektu po lewej stronie operatora jest mniejszy niż lub równy obiektowi kolejki po prawej stronie.|
|[operator==](../standard-library/queue-operators.md#op_eq_eq)|Sprawdza, czy obiekt kolejki po lewej stronie operatora jest równy obiektowi kolejki po prawej stronie.|
|[operator>](../standard-library/queue-operators.md#op_gt)|Sprawdza, czy obiekt kolejki po lewej stronie operatora jest większy niż obiekt kolejki po prawej stronie.|
|[operator>=](../standard-library/queue-operators.md#op_gt_eq)|Sprawdza, czy obiekt kolejki po lewej stronie operatora jest większy lub równy obiektowi kolejki po prawej stronie.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[swap]()||

### <a name="classes"></a>Klasy

|||
|-|-|
|[queue, klasa](../standard-library/queue-class.md)|Klasa adaptera kontenera szablonu, która umożliwia ograniczenie funkcjonalności, ograniczanie dostępu do przodu i Wstecz elementów pewne podstawowy typ kontenera.|
|[priority_queue, klasa](../standard-library/priority-queue-class.md)|Klasa adaptera kontenera szablonu, która umożliwia ograniczenie funkcjonalności, ograniczanie dostępu do górnego elementu niektóre bazowego typu kontenera, który zawsze jest największy.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
