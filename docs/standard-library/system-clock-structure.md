---
title: "system_clock — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
dev_langs:
- C++
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 757094f61d7f58de4f51da46b28dc90105968a99
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="systemclock-structure"></a>system_clock — Struktura
Reprezentuje *typ zegara* opartego na zegarze w czasie rzeczywistym systemu.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct system_clock;  
```  
  
## <a name="remarks"></a>Uwagi  
 A *typ zegara* jest używany do uzyskania bieżącego czasu jako czas UTC. Typ zawiera instancją typu [czas trwania](../standard-library/duration-class.md) i szablonu klasy [time_point —](../standard-library/time-point-class.md)i definiuje statycznej funkcji członkowskiej `now()` zwracającą czas.  
  
 Zegar jest *monotoniczna* Jeśli wartość, która jest zwracana przez pierwsze wywołanie w celu `now()` zawsze jest mniejsza niż wartość zwracaną przez kolejne wywołanie `now()`.  
  
 Zegar jest *stałej* przypadku *monotoniczna* i jeśli czas między zegarowych jest stałą.  
  
 W tej implementacji `system_clock` CGI `high_resolution_clock`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`system_clock::duration`|Jest to synonim `duration<rep, period>`.|  
|`system_clock::period`|Synonim dla typu, który jest używany do reprezentowania okres znaczników w zawartych w niej tworzenia wystąpienia elementu `duration`.|  
|`system_clock::rep`|Synonim dla typu, który jest używany do reprezentowania liczbę taktów zegara w zawartych w niej tworzenia wystąpienia elementu `duration`.|  
|`system_clock::time_point`|Jest to synonim `time_point<Clock, duration>`, gdzie `Clock` jest synonimem sam typ zegara lub inny typ zegara, oparty na tej samej epoki i ma takie same zagnieżdżone `duration` typu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[from_time_t](#from_time_t)|Statyczna. Zwraca `time_point` która najbardziej podobny przez określony czas.|  
|[Teraz](#now)|Statyczna. Zwraca bieżącą godzinę.|  
|[to_time_t](#to_time_t)|Statyczna. Zwraca `time_t` obiekt, który najlepiej oblicza przybliżoną określonej `time_point`.|  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[system_clock::is_monotonic — stała](#is_monotonic_constant)|Określa, czy typ zegara monotoniczna.|  
|[system_clock::is_steady Constant](#is_steady_constant)|Określa, czy typ zegara jest stałą.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<chrono >  
  
 **Namespace:** std::chrono  
  
##  <a name="from_time_t"></a>  system_clock::from_time_t
 Statyczna metoda, która zwraca [time_point —](../standard-library/time-point-class.md) najlepiej odpowiadającej zbliżonego czas reprezentowany przez `Tm`.  
  
```  
static time_point from_time_t(time_t Tm) noexcept;  
```  
  
### <a name="parameters"></a>Parametry  
 `Tm`  
 A [time_t —](../c-runtime-library/standard-types.md) obiektu.  
  
##  <a name="is_monotonic_constant"></a>  system_clock::is_monotonic — stała  
 Wartość statyczną, który określa, czy typ zegara monotoniczna.  
  
```  
static const bool is_monotonic = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W tej implementacji `system_clock::is_monotonic` zawsze zwraca `false`.  
  
### <a name="remarks"></a>Uwagi  
 Zegar jest *monotoniczna* Jeśli wartość, która jest zwracana przez pierwsze wywołanie w celu `now()` zawsze jest mniejsza niż wartość zwracaną przez kolejne wywołanie `now()`.  
  
##  <a name="is_steady_constant"></a>  system_clock::is_steady — stała  
 Wartość statyczną, który określa, czy typ zegara *stałej*.  
  
```  
static const bool is_steady = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W tej implementacji `system_clock::is_steady` zawsze zwraca `false`.  
  
### <a name="remarks"></a>Uwagi  
 Zegar jest *stałej* przypadku [monotoniczna](#is_monotonic_constant) i jeśli czas między zegarowych jest stałą.  
  
##  <a name="now"></a>  system_clock::Now
 Metoda statyczna zwraca bieżącą godzinę.  
  
```  
static time_point now() noexcept;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [time_point —](../standard-library/time-point-class.md) obiekt, który reprezentuje bieżący czas.  
  
##  <a name="to_time_t"></a>  system_clock::to_time_t
 Statyczna metoda, która zwraca [time_t —](../c-runtime-library/standard-types.md) najlepiej odpowiadającej zbliżonego czas reprezentowany przez `Time`.  
  
```  
static time_t to_time_t(const time_point& Time) noexcept;  
```  
  
### <a name="parameters"></a>Parametry  
 `Time`  
 A [time_point —](../standard-library/time-point-class.md) obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)   
 [steady_clock, struktura](../standard-library/steady-clock-struct.md)
