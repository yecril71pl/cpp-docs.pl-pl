---
title: '&lt;niej&gt;'
ms.date: 11/04/2016
f1_keywords:
- <queue>
helpviewer_keywords:
- queue header
ms.assetid: 24fcf350-eb0e-48cf-9fef-978be1aeda1f
ms.openlocfilehash: a41d34b45264472a5c8c88ca0619e78444dd8aec
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832597"
---
# <a name="ltqueuegt"></a>&lt;niej&gt;

Definiuje szablony klas priority_queue i kolejki oraz kilka szablonów pomocniczych.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<queue>

**Przestrzeń nazw:** std

> [!NOTE]
> \<queue>Biblioteka używa również `#include <initializer_list>` instrukcji.

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[operator! =](../standard-library/queue-operators.md#op_neq)|Testuje, czy obiekt kolejki po lewej stronie operatora nie jest równy obiektowi kolejki po prawej stronie.|
|[<operatora ](../standard-library/queue-operators.md#op_lt)|Testuje, czy obiekt kolejki po lewej stronie operatora jest mniejszy niż obiekt kolejki po prawej stronie.|
|[zakład\<=](../standard-library/queue-operators.md#op_gt_eq)|Testuje, czy obiekt kolejki po lewej stronie operatora jest mniejszy niż lub równy obiektowi kolejki po prawej stronie.|
|[operator = =](../standard-library/queue-operators.md#op_eq_eq)|Testuje, czy obiekt kolejki po lewej stronie operatora jest równy obiektowi kolejki po prawej stronie.|
|[>operatora ](../standard-library/queue-operators.md#op_gt)|Testuje, czy obiekt kolejki po lewej stronie operatora jest większy niż obiekt kolejki po prawej stronie.|
|[>operatora =](../standard-library/queue-operators.md#op_gt_eq)|Testuje, czy obiekt kolejki po lewej stronie operatora jest większy niż lub równy obiektowi kolejki po prawej stronie.|

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|-|-|
|[Queue — Klasa](../standard-library/queue-class.md)|Klasa adaptera kontenerów szablonu, która zapewnia ograniczenie funkcjonalności ograniczającej dostęp do przednich i z tyłu jednego z typów kontenerów bazowych.|
|[Klasa priority_queue](../standard-library/priority-queue-class.md)|Klasa adaptera kontenerów szablonu, która zapewnia ograniczenie funkcjonalności ograniczającej dostęp do górnego elementu pewnego bazowego typu kontenera, który jest zawsze największy.|

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
