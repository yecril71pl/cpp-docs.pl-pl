---
title: recursive_timed_mutex — Klasa
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::lock
- mutex/std::recursive_timed_mutex::try_lock
- mutex/std::recursive_timed_mutex::try_lock_for
- mutex/std::recursive_timed_mutex::try_lock_until
- mutex/std::recursive_timed_mutex::unlock
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
helpviewer_keywords:
- std::recursive_timed_mutex [C++]
- std::recursive_timed_mutex [C++], recursive_timed_mutex
- std::recursive_timed_mutex [C++], lock
- std::recursive_timed_mutex [C++], try_lock
- std::recursive_timed_mutex [C++], try_lock_for
- std::recursive_timed_mutex [C++], try_lock_until
- std::recursive_timed_mutex [C++], unlock
ms.openlocfilehash: 6ae61d17084cc744cac8819ac2c0ca48eb59add7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460118"
---
# <a name="recursivetimedmutex-class"></a>recursive_timed_mutex — Klasa

Reprezentuje *Typ muteksu czasu*. Obiekty tego typu są używane do wymuszania wzajemnego wykluczania przy użyciu blokowania ograniczonego czasowo w ramach programu. W przeciwieństwie do obiektów typu [timed_mutex](../standard-library/timed-mutex-class.md), efekt wywołania metod blokowania dla `recursive_timed_mutex` obiektów jest dobrze zdefiniowany.

## <a name="syntax"></a>Składnia

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|Konstruuje `recursive_timed_mutex` obiekt, który nie jest zablokowany.|
|[~recursive_timed_mutex Destructor](#dtorrecursive_timed_mutex_destructor)|Zwalnia wszystkie zasoby, które są używane przez `recursive_timed_mutex` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący do momentu, aż wątek uzyska własność `mutex`.|
|[try_lock](#try_lock)|Próbuje uzyskać własność `mutex` bez blokowania.|
|[try_lock_for](#try_lock_for)|Próbuje uzyskać własność `mutex` przez określony przedział czasu.|
|[try_lock_until](#try_lock_until)|Próbuje uzyskać własność `mutex` do określonego czasu.|
|[unlock](#unlock)|Zwalnia własność `mutex`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> mutex

**Przestrzeń nazw:** std

## <a name="lock"></a>skręt

Blokuje wątek wywołujący do momentu, aż wątek uzyska własność `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, metoda zwraca natychmiast, a poprzednia blokada pozostaje w mocy.

## <a name="recursive_timed_mutex"></a>Konstruktor recursive_timed_mutex

Konstruuje `recursive_timed_mutex` obiekt, który nie jest zablokowany.

```cpp
recursive_timed_mutex();
```

## <a name="dtorrecursive_timed_mutex_destructor"></a>~ recursive_timed_mutex destruktor

Zwalnia wszystkie zasoby, które są używane przez `recursive_timed_mutex` obiekt.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany podczas działania destruktora, zachowanie jest niezdefiniowane.

## <a name="try_lock"></a>try_lock

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli metoda pomyślnie uzyskała własność `mutex` lub jeśli `mutex`wątek wywołujący jest już właścicielem; w przeciwnym razie, **Fałsz**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, funkcja natychmiast zwraca **wartość true**, a poprzednia blokada pozostaje w mocy.

## <a name="try_lock_for"></a>try_lock_for

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Obiekt [chrono::d wersja](../standard-library/duration-class.md) , który określa maksymalną ilość czasu, jaką Metoda próbuje uzyskać własność `mutex`.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli metoda pomyślnie uzyska własność `mutex` lub jeśli `mutex`wątek wywołujący jest już właścicielem; w przeciwnym razie, **Fałsz**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, Metoda natychmiast zwraca **wartość true**, a poprzednia blokada pozostaje w mocy.

## <a name="try_lock_until"></a>try_lock_until

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Punkt w czasie, który określa próg, po którym metoda nie próbuje uzyskać własności `mutex`.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli metoda pomyślnie uzyska własność `mutex` lub jeśli `mutex`wątek wywołujący jest już właścicielem; w przeciwnym razie, **Fałsz**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, Metoda natychmiast zwraca **wartość true**, a poprzednia blokada pozostaje w mocy.

## <a name="unlock"></a>odblokowania

Zwalnia własność `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Ta metoda `mutex` zwalnia własność tylko wtedy, gdy jest wywoływana tak dużo razy, jak [blokady](#lock), [try_lock](#try_lock), [try_lock_for](#try_lock_for) `recursive_timed_mutex` i [try_lock_until](#try_lock_until) zostały pomyślnie wywołane dla obiektu.

Jeśli wątek wywołujący nie jest własnym `mutex`, zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
