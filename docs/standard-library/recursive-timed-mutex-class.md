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
ms.openlocfilehash: 15517425f3d81bc3798df2e42f39ac0b0d32ba31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217600"
---
# <a name="recursive_timed_mutex-class"></a>recursive_timed_mutex — Klasa

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
|[~ recursive_timed_mutex destruktor](#dtorrecursive_timed_mutex_destructor)|Zwalnia wszystkie zasoby, które są używane przez `recursive_timed_mutex` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[skręt](#lock)|Blokuje wątek wywołujący do momentu, aż wątek uzyska własność `mutex` .|
|[try_lock](#try_lock)|Próbuje uzyskać własność `mutex` bez blokowania.|
|[try_lock_for](#try_lock_for)|Próbuje uzyskać własność przez `mutex` określony przedział czasu.|
|[try_lock_until](#try_lock_until)|Próbuje uzyskać własność do `mutex` określonego czasu.|
|[odblokowania](#unlock)|Zwalnia własność `mutex` .|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<mutex>

**Przestrzeń nazw:** std

## <a name="lock"></a><a name="lock"></a>skręt

Blokuje wątek wywołujący do momentu, aż wątek uzyska własność `mutex` .

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex` , metoda zwraca natychmiast, a poprzednia blokada pozostaje w mocy.

## <a name="recursive_timed_mutex-constructor"></a><a name="recursive_timed_mutex"></a>Konstruktor recursive_timed_mutex

Konstruuje `recursive_timed_mutex` obiekt, który nie jest zablokowany.

```cpp
recursive_timed_mutex();
```

## <a name="recursive_timed_mutex-destructor"></a><a name="dtorrecursive_timed_mutex_destructor"></a>~ recursive_timed_mutex destruktor

Zwalnia wszystkie zasoby, które są używane przez `recursive_timed_mutex` obiekt.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany podczas działania destruktora, zachowanie jest niezdefiniowane.

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli metoda pomyślnie uzyskała własność `mutex` lub jeśli wątek wywołujący jest już właścicielem `mutex` ; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex` , funkcja natychmiast zwraca wartość **`true`** , a poprzednia blokada pozostaje w mocy.

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Obiekt [chrono::d wersja](../standard-library/duration-class.md) , który określa maksymalną ilość czasu, jaką Metoda próbuje uzyskać własność `mutex` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli metoda pomyślnie uzyska własność `mutex` lub jeśli wątek wywołujący jest już właścicielem `mutex` ; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex` , Metoda natychmiast zwraca wartość **`true`** , a poprzednia blokada pozostaje w efekcie.

## <a name="try_lock_until"></a><a name="try_lock_until"></a>try_lock_until

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Punkt w czasie, który określa próg, po którym metoda nie próbuje uzyskać własności `mutex` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli metoda pomyślnie uzyska własność `mutex` lub jeśli wątek wywołujący jest już właścicielem `mutex` ; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex` , Metoda natychmiast zwraca wartość **`true`** , a poprzednia blokada pozostaje w efekcie.

## <a name="unlock"></a><a name="unlock"></a>odblokowania

Zwalnia własność `mutex` .

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Ta metoda zwalnia własność `mutex` tylko wtedy, gdy jest wywoływana tyle razy jak [blokada](#lock), [try_lock](#try_lock), [try_lock_for](#try_lock_for)i [try_lock_until](#try_lock_until) została pomyślnie wywołana dla `recursive_timed_mutex` obiektu.

Jeśli wątek wywołujący nie `mutex` jest własnym, zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
