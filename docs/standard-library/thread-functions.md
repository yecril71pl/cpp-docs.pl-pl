---
title: '&lt;Wątek&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
helpviewer_keywords:
- std::get_id [C++]
- std::sleep_for [C++]
- std::sleep_until [C++]
- std::swap [C++]
- std::yield [C++]
ms.openlocfilehash: 948c00f7c0b773bf366f4ea9e102c832e9878d9b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960453"
---
# <a name="ltthreadgt-functions"></a>&lt;Wątek&gt; funkcji

||||
|-|-|-|
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|
|[swap](#swap)|[yield](#yield)|

## <a name="get_id"></a>  get_id —

Jednoznacznie identyfikuje bieżącego wątku wykonywania.

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt typu [Thread::ID —](../standard-library/thread-class.md) , który jednoznacznie identyfikuje bieżącego wątku wykonywania.

## <a name="sleep_for"></a>  sleep_for —

Blokuje wątek wywołujący.

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*  
 A [czas trwania](../standard-library/duration-class.md) obiekt, który określa przedział czasu.

### <a name="remarks"></a>Uwagi

Funkcja blokuje wątek wywołujący dla co najmniej czas, który jest określony przez *Rel_time*. Ta funkcja nie generuje żadnych wyjątków.

## <a name="sleep_until"></a>  sleep_until —

Blokuje wątek wywołujący, co najmniej do określonego czasu.

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*  
 Reprezentuje punkt w czasie.

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="swap"></a>  swap

Zamienia dwa stany **wątku** obiektów.

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Po lewej stronie*  
 Po lewej stronie **wątku** obiektu.

*Po prawej stronie*  
 Po prawej stronie **wątku** obiektu.

### <a name="remarks"></a>Uwagi

Wywołania funkcji `Left.swap(Right)`.

## <a name="yield"></a>  YIELD

Sygnały systemu operacyjnego do uruchomienia innych wątków, nawet wtedy, gdy bieżący wątek zazwyczaj będzie nadal działał.

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>Zobacz także

[\<Wątek >](../standard-library/thread.md)<br/>
