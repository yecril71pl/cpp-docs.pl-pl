---
title: '&lt;funkcje gwintu&gt;'
ms.date: 11/04/2016
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
ms.openlocfilehash: bb0a0a12ec2882701447804f9c88d1776a196cb7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375835"
---
# <a name="ltthreadgt-functions"></a>&lt;funkcje gwintu&gt;

||||
|-|-|-|
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|
|[Wymiany](#swap)|[yield](#yield)|

## <a name="get_id"></a><a name="get_id"></a>get_id

Jednoznacznie identyfikuje bieżący wątek wykonywania.

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt typu [thread::id,](../standard-library/thread-class.md) który jednoznacznie identyfikuje bieżący wątek wykonywania.

## <a name="sleep_for"></a><a name="sleep_for"></a>sleep_for

Blokuje wątek wywołujący.

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Obiekt [czasu trwania,](../standard-library/duration-class.md) który określa przedział czasu.

### <a name="remarks"></a>Uwagi

Funkcja blokuje wątek wywołujący przez co najmniej czas określony przez *Rel_time*. Ta funkcja nie zgłasza żadnych wyjątków.

## <a name="sleep_until"></a><a name="sleep_until"></a>sleep_until

Blokuje wątek wywołujący co najmniej do określonego czasu.

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Reprezentuje punkt w czasie.

### <a name="remarks"></a>Uwagi

Ta funkcja nie zgłasza żadnych wyjątków.

## <a name="swap"></a><a name="swap"></a>Wymiany

Zamienia stany dwóch obiektów **wątku.**

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Lewej*\
Lewy obiekt **wątku.**

*Prawo*\
Prawy obiekt **wątku.**

### <a name="remarks"></a>Uwagi

Funkcja wywołuje `Left.swap(Right)`.

## <a name="yield"></a><a name="yield"></a>Wydajność

Sygnalizuje system operacyjny do uruchomienia innych wątków, nawet jeśli bieżący wątek będzie zwykle nadal działać.

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>Zobacz też

[\<>gwintów](../standard-library/thread.md)
