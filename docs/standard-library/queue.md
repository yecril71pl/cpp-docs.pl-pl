---
title: '&lt;niej&gt;'
ms.date: 11/04/2016
f1_keywords:
- <queue>
helpviewer_keywords:
- queue header
ms.assetid: 24fcf350-eb0e-48cf-9fef-978be1aeda1f
ms.openlocfilehash: 506ab5fccd44ad37a08a9f741f44f24d3a85b87d
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2019
ms.locfileid: "68956996"
---
# <a name="ltqueuegt"></a>&lt;niej&gt;

Definiuje klasy szablonów priority_queue i Queue oraz kilka szablonów pomocniczych.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> kolejki

**Przestrzeń nazw:** std

> [!NOTE]
> `#include <initializer_list>` Biblioteka \<> kolejki używa również instrukcji.

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator!=](../standard-library/queue-operators.md#op_neq)|Testuje, czy obiekt kolejki po lewej stronie operatora nie jest równy obiektowi kolejki po prawej stronie.|
|[< operatora](../standard-library/queue-operators.md#op_lt)|Testuje, czy obiekt kolejki po lewej stronie operatora jest mniejszy niż obiekt kolejki po prawej stronie.|
|[zakład\<=](../standard-library/queue-operators.md#op_gt_eq)|Testuje, czy obiekt kolejki po lewej stronie operatora jest mniejszy niż lub równy obiektowi kolejki po prawej stronie.|
|[operator==](../standard-library/queue-operators.md#op_eq_eq)|Testuje, czy obiekt kolejki po lewej stronie operatora jest równy obiektowi kolejki po prawej stronie.|
|[operator>](../standard-library/queue-operators.md#op_gt)|Testuje, czy obiekt kolejki po lewej stronie operatora jest większy niż obiekt kolejki po prawej stronie.|
|[operator>=](../standard-library/queue-operators.md#op_gt_eq)|Testuje, czy obiekt kolejki po lewej stronie operatora jest większy niż lub równy obiektowi kolejki po prawej stronie.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[queue, klasa](../standard-library/queue-class.md)|Klasa adaptera kontenerów szablonu, która zapewnia ograniczenie funkcjonalności ograniczającej dostęp do przednich i z tyłu jednego z typów kontenerów bazowych.|
|[priority_queue, klasa](../standard-library/priority-queue-class.md)|Klasa adaptera kontenerów szablonu, która zapewnia ograniczenie funkcjonalności ograniczającej dostęp do górnego elementu pewnego bazowego typu kontenera, który jest zawsze największy.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
