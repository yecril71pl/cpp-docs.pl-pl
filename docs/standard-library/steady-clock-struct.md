---
title: "steady_clock — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- chrono/std::chrono::steady_clock
dev_langs:
- C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2651b8d7bdb50997c7757f85687dcf425f6d7e2f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="steadyclock-struct"></a>steady_clock — struktura
Reprezentuje `steady` zegara.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct steady_clock;  
```  
  
## <a name="remarks"></a>Uwagi  
 W systemie Windows steady_clock opakowuje funkcji QueryPerformanceCounter.  
  
 Zegar jest *monotoniczna* Jeśli wartość, która jest zwracana przez pierwsze wywołanie w celu `now()` zawsze jest mniejsza niż wartość zwracaną przez kolejne wywołanie `now()`.  
  
 Zegar jest *stałej* przypadku *monotoniczna* i jeśli czas między zegarowych jest stałą.  
  
 High_resolution_clock jest typdef dla steady_clock.  
  
## <a name="public-functions"></a>Funkcje publiczne  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|Teraz|Zwraca bieżącą godzinę jako wartość time_point —.|  
  
## <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`system_clock::is_steady`|Przechowuje `true`. A `steady_clock` jest *stałej*.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<chrono >  
  
 **Namespace:** std::chrono  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)   
 [system_clock, struktura](../standard-library/system-clock-structure.md)
