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
ms.openlocfilehash: 93ce7b99728d1ce89c8124efd6c74aea7ff66d22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320143"
---
# <a name="recursive_timed_mutex-class"></a>recursive_timed_mutex — Klasa

Reprezentuje *typ czasowego obiektu mutex*. Obiekty tego typu są używane do wymuszania wzajemnego wykluczenia przy użyciu ograniczonego w czasie blokowania w programie. W przeciwieństwie do obiektów typu [timed_mutex,](../standard-library/timed-mutex-class.md)efekt wywoływania `recursive_timed_mutex` metod blokowania dla obiektów jest dobrze zdefiniowany.

## <a name="syntax"></a>Składnia

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|Tworzy `recursive_timed_mutex` obiekt, który nie jest zablokowany.|
|[~recursive_timed_mutex Destruktor](#dtorrecursive_timed_mutex_destructor)|Zwalnia wszystkie zasoby, które `recursive_timed_mutex` są używane przez obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący, dopóki `mutex`wątek nie uzyska własności . .|
|[try_lock](#try_lock)|Próbuje uzyskać własność `mutex` bez blokowania.|
|[try_lock_for](#try_lock_for)|Próbuje uzyskać własność `mutex` dla określonego przedziału czasu.|
|[try_lock_until](#try_lock_until)|Próbuje uzyskać własność `mutex` do określonego czasu.|
|[Odblokować](#unlock)|Zwalnia własność `mutex`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mutex>

**Przestrzeń nazw:** std

## <a name="lock"></a><a name="lock"></a>Blokady

Blokuje wątek wywołujący, dopóki `mutex`wątek nie uzyska własności . .

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, metoda zwraca natychmiast, a poprzednia blokada pozostaje w mocy.

## <a name="recursive_timed_mutex-constructor"></a><a name="recursive_timed_mutex"></a>Konstruktor recursive_timed_mutex

Tworzy `recursive_timed_mutex` obiekt, który nie jest zablokowany.

```cpp
recursive_timed_mutex();
```

## <a name="recursive_timed_mutex-destructor"></a><a name="dtorrecursive_timed_mutex_destructor"></a>~recursive_timed_mutex Destruktor

Zwalnia wszystkie zasoby, które `recursive_timed_mutex` są używane przez obiekt.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany podczas pracy destruktora, zachowanie jest niezdefiniowane.

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli metoda pomyślnie `mutex` uzyskała własność lub jeśli `mutex`wątek wywołujący jest już właścicielem ; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, funkcja natychmiast zwraca **true**, a poprzednia blokada pozostaje w mocy.

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
A [chrono::duration](../standard-library/duration-class.md) object, który określa maksymalny czas, przez jaki metoda `mutex`próbuje uzyskać własność .

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli metoda pomyślnie uzyskuje `mutex` własność lub jeśli wątek wywołujący jest już właścicielem `mutex`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, metoda natychmiast zwraca **true**, a poprzednia blokada pozostaje w mocy.

## <a name="try_lock_until"></a><a name="try_lock_until"></a>try_lock_until

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Punkt w czasie, który określa próg, po którym metoda nie `mutex`próbuje już uzyskać własność .

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli metoda pomyślnie uzyskuje `mutex` własność lub jeśli wątek wywołujący jest już właścicielem `mutex`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, metoda natychmiast zwraca **true**, a poprzednia blokada pozostaje w mocy.

## <a name="unlock"></a><a name="unlock"></a>Odblokować

Zwalnia własność `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Ta metoda zwalnia `mutex` własność tylko po jest nazywany tyle razy, jak [blokada](#lock), [try_lock](#try_lock) [, try_lock_for](#try_lock_for), i `recursive_timed_mutex` [try_lock_until](#try_lock_until) zostały wywołane pomyślnie na obiekcie.

Jeśli wątek wywołujący `mutex`nie jest właścicielem , zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
