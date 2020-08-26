---
title: '&lt;&gt;funkcje wątku'
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
ms.openlocfilehash: 64a62180243d77f361c243b2a89de56b0a14920e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845045"
---
# <a name="ltthreadgt-functions"></a>&lt;&gt;funkcje wątku

[get_id](#get_id)\
[sleep_for](#sleep_for)\
[sleep_until](#sleep_until)\
[wymiany](#swap)\
[yield](#yield)

## <a name="get_id"></a><a name="get_id"></a> get_id

Jednoznacznie identyfikuje bieżący wątek wykonania.

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt typu [thread:: ID](../standard-library/thread-class.md) , który jednoznacznie identyfikuje bieżący wątek wykonywania.

## <a name="sleep_for"></a><a name="sleep_for"></a> sleep_for

Blokuje wątek wywołujący.

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Obiekt [czasu trwania](../standard-library/duration-class.md) , który określa przedział czasu.

### <a name="remarks"></a>Uwagi

Funkcja blokuje wątek wywołujący przez co najmniej godzinę określoną przez *Rel_time*. Ta funkcja nie generuje żadnych wyjątków.

## <a name="sleep_until"></a><a name="sleep_until"></a> sleep_until

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

Ta funkcja nie generuje żadnych wyjątków.

## <a name="swap"></a><a name="swap"></a> wymiany

Zamienia Stany dwóch `thread` obiektów.

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewy `thread` obiekt.

*Kliknij*\
Prawidłowy `thread` obiekt.

### <a name="remarks"></a>Uwagi

Wywołania funkcji `Left.swap(Right)` .

## <a name="yield"></a><a name="yield"></a> zbiór

Sygnalizuje systemowi operacyjnemu Uruchamianie innych wątków, nawet jeśli bieżący wątek będzie normalnie nadal działać.

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>Zobacz też

[\<thread>](../standard-library/thread.md)
