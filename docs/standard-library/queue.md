---
title: '&lt;kolejka&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <queue>
dev_langs:
- C++
helpviewer_keywords:
- queue header
ms.assetid: 24fcf350-eb0e-48cf-9fef-978be1aeda1f
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3bccad1ff20a314c562b580d4d5102f283bcef56
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltqueuegt"></a>&lt;Kolejki&gt;

Definiuje priority_queue — klasy szablonu i kolejki i kilka szablonów pomocniczych.

## <a name="syntax"></a>Składnia

```cpp
#include <queue>

```

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](../standard-library/queue-operators.md#op_neq)|Testy, jeśli obiekt kolejki po lewej stronie operatora nie jest taki sam jak obiekt kolejki po prawej stronie.|
|[Operator <](../standard-library/queue-operators.md#op_lt)|Testy, jeśli obiekt kolejki po lewej stronie operatora jest mniejsza niż obiekt kolejki po prawej stronie.|
|[Operator\<=](../standard-library/queue-operators.md#op_gt_eq)|Testy, jeśli obiekt kolejki po lewej stronie operatora jest mniejsza niż lub równe obiekt kolejki po prawej stronie.|
|[operator==](../standard-library/queue-operators.md#op_eq_eq)|Testy, jeśli obiekt kolejki po lewej stronie operatora jest taki sam jak obiekt kolejki po prawej stronie.|
|[operator>](../standard-library/queue-operators.md#op_gt)|Testy, jeśli obiekt kolejki po lewej stronie operatora jest większa niż obiekt kolejki po prawej stronie.|
|[operator>=](../standard-library/queue-operators.md#op_gt_eq)|Testy, jeśli obiekt kolejki po lewej stronie operatora jest większa niż lub równa obiekt kolejki po prawej stronie.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[queue, klasa](../standard-library/queue-class.md)|Klasa karty kontenera szablonu, która umożliwia ograniczenie funkcjonalności ograniczanie dostępu do elementów front i back pewien podstawowy typ kontenera.|
|[priority_queue, klasa](../standard-library/priority-queue-class.md)|Klasa karty kontenera szablonu, która umożliwia ograniczenie funkcjonalności ograniczanie dostępu do górnego elementu niektórych odpowiedni typ kontenera, która jest zawsze największy.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
