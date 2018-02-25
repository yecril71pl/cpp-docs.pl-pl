---
title: "&lt;Wątek&gt; funkcje | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::get_id [C++]
- std::sleep_for [C++]
- std::sleep_until [C++]
- std::swap [C++]
- std::yield [C++]
ms.openlocfilehash: 54e4c09c7db5fb29cdfb067b47d8584451277d4a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltthreadgt-functions"></a>&lt;Wątek&gt; funkcji
||||  
|-|-|-|  
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|  
|[swap](#swap)|[yield](#yield)|  
  
##  <a name="get_id"></a>  get_id  
 Unikatowy identyfikator bieżącego wątku do wykonania.  
  
```  
thread::id this_thread::get_id() noexcept;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt typu [Thread::ID —](../standard-library/thread-class.md) który unikatowo identyfikuje bieżącego wątku do wykonania.  
  
##  <a name="sleep_for"></a>  sleep_for —  
 Blokuje wątek wywołujący.  
  
```  
template <class Rep,  
class Period>  
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```  
  
### <a name="parameters"></a>Parametry  
 `Rel_time`  
 A [czas trwania](../standard-library/duration-class.md) obiekt, który określa przedział czasu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja blokuje wątek wywołujący dla co najmniej czasu określonym przez `Rel_time`. Tej funkcji nie generują żadnych wyjątków.  
  
##  <a name="sleep_until"></a>  sleep_until —  
 Blokuje wątek wywołujący co najmniej do określonego czasu.  
  
```  
template <class Clock, class Duration>  
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```  
  
### <a name="parameters"></a>Parametry  
 `Abs_time`  
 Reprezentuje punkt w czasie.  
  
### <a name="remarks"></a>Uwagi  
 Tej funkcji nie generują żadnych wyjątków.  
  
##  <a name="swap"></a>  Swap  
 Zamienia stanów dwóch `thread` obiektów.  
  
```  
void swap(thread& Left, thread& Right) noexcept;  
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Po lewej stronie `thread` obiektu.  
  
 `Right`  
 Prawo `thread` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji `Left.swap(Right)`.  
  
##  <a name="yield"></a>  YIELD  
 Sygnały do innych wątków systemu operacyjnego, nawet wtedy, gdy bieżący wątek zazwyczaj będzie nadal działał.  
  
```  
inline void yield() noexcept;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<Wątek >](../standard-library/thread.md)

