---
title: '&lt;chrono&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 41ea765f98882bb0f3f1531e284ca06a6fb79067
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltchronogt-functions"></a>&lt;chrono&gt; funkcji
||||  
|-|-|-|  
|[duration_cast](#duration_cast)|[time_point_cast](#time_point_cast)|  
  

##  <a name="duration_cast"></a>  duration_cast —
 Rzutowania `duration` obiektu określonego typu.  
  
```  
template <class To, class Rep, class Period>  
constexpr To duration_cast(const duration<Rep, Period>& Dur);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `duration` typu obiektu `To` reprezentujący interwał `Dur`, który został obcięty, jeśli pasuje do typu docelowego.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `To` jest instancją typu `duration`, ta funkcja nie uczestniczy w Rozpoznanie przeciążenia.  
  
##  <a name="time_point_cast"></a>  time_point_cast —
 Rzutowania [time_point —](../standard-library/time-point-class.md) obiektu określonego typu.  
  
```  
template <class To, class Clock, class Duration>  
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `time_point` obiekt, który ma czas trwania typu `To`.  
  
### <a name="remarks"></a>Uwagi  
 O ile `To` jest instancją typu [czas trwania](../standard-library/duration-class.md), ta funkcja nie uczestniczy w Rozpoznanie przeciążenia.  
  
## <a name="see-also"></a>Zobacz też  
 [\<chrono>](../standard-library/chrono.md)

