---
title: '&lt;chrono&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
ms.openlocfilehash: fc0af2eeb2e3207537fa6edf056aa7382198a5d8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053763"
---
# <a name="ltchronogt-functions"></a>&lt;chrono&gt; funkcji

||||
|-|-|-|
|[duration_cast](#duration_cast)|[time_point_cast](#time_point_cast)|

## <a name="duration_cast"></a>  duration_cast —

Rzutowania `duration` obiektu określonego typu.

```cpp
template <class To, class Rep, class Period>
constexpr To duration_cast(const duration<Rep, Period>& Dur);
```

### <a name="return-value"></a>Wartość zwracana

A `duration` obiektu typu `To` reprezentujący przedział czasu `Dur`, który jest przycinany, jeśli ma się zmieścić w typ docelowy.

### <a name="remarks"></a>Uwagi

Jeśli `To` jest egzemplarzem z `duration`, ta funkcja nie uczestniczy w przeciążeniu rozdzielczości.

## <a name="time_point_cast"></a>  time_point_cast —

Rzutowania [time_point](../standard-library/time-point-class.md) obiektu określonego typu.

```cpp
template <class To, class Clock, class Duration>
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);
```

### <a name="return-value"></a>Wartość zwracana

A `time_point` obiekt, który ma czas trwania typu `To`.

### <a name="remarks"></a>Uwagi

Chyba że `To` jest egzemplarzem z [czas trwania](../standard-library/duration-class.md), ta funkcja nie uczestniczy w przeciążeniu rozdzielczości.

## <a name="see-also"></a>Zobacz także

[\<chrono>](../standard-library/chrono.md)<br/>
