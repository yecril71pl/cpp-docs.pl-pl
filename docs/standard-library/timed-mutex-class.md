---
title: timed_mutex — Klasa
ms.date: 11/04/2016
f1_keywords:
- mutex/std::timed_mutex
- mutex/std::timed_mutex::timed_mutex
- mutex/std::timed_mutex::lock
- mutex/std::timed_mutex::try_lock
- mutex/std::timed_mutex::try_lock_for
- mutex/std::timed_mutex::try_lock_until
- mutex/std::timed_mutex::unlock
ms.assetid: cd198081-6f38-447a-9dba-e06dfbfafe59
helpviewer_keywords:
- std::timed_mutex [C++]
- std::timed_mutex [C++], timed_mutex
- std::timed_mutex [C++], lock
- std::timed_mutex [C++], try_lock
- std::timed_mutex [C++], try_lock_for
- std::timed_mutex [C++], try_lock_until
- std::timed_mutex [C++], unlock
ms.openlocfilehash: 3329c46f0760a13693507de18a09b974b6b646e2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212101"
---
# <a name="timed_mutex-class"></a>timed_mutex — Klasa

Reprezentuje *Typ muteksu czasu*. Obiekty tego typu są używane do wymuszania wzajemnego wykluczania za pomocą blokowania ograniczonego czasowo w ramach programu.

## <a name="syntax"></a>Składnia

```cpp
class timed_mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[timed_mutex](#timed_mutex)|Konstruuje `timed_mutex` obiekt, który nie jest zablokowany.|
|[timed_mutex:: ~ timed_mutex, destruktor](#dtortimed_mutex_destructor)|Zwalnia wszystkie zasoby, które są używane przez `timed_mutex` obiekt.|

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

## <a name="timed_mutexlock"></a><a name="lock"></a>timed_mutex:: Lock

Blokuje wątek wywołujący do momentu, aż wątek uzyska własność `mutex` .

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex` , zachowanie jest niezdefiniowane.

## <a name="timed_mutextimed_mutex-constructor"></a><a name="timed_mutex"></a>timed_mutex:: timed_mutex, Konstruktor

Konstruuje `timed_mutex` obiekt, który nie jest zablokowany.

```cpp
timed_mutex();
```

## <a name="timed_mutextimed_mutex-destructor"></a><a name="dtortimed_mutex_destructor"></a>timed_mutex:: ~ timed_mutex, destruktor

Zwalnia wszystkie zasoby, które są używane przez `mutex` obiekt.

```cpp
~timed_mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany podczas działania destruktora, zachowanie jest niezdefiniowane.

## <a name="timed_mutextry_lock"></a><a name="try_lock"></a>timed_mutex:: try_lock

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli metoda pomyślnie uzyska własność `mutex` ; w przeciwnym razie, **`false`** .

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex` , zachowanie jest niezdefiniowane.

## <a name="timed_mutextry_lock_for"></a><a name="try_lock_for"></a>timed_mutex:: try_lock_for

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Obiekt [chrono::d wersja](../standard-library/duration-class.md) , który określa maksymalną ilość czasu, jaką Metoda próbuje uzyskać własność `mutex` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli metoda pomyślnie uzyska własność `mutex` ; w przeciwnym razie, **`false`** .

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex` , zachowanie jest niezdefiniowane.

## <a name="timed_mutextry_lock_until"></a><a name="try_lock_until"></a>timed_mutex:: try_lock_until

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

**`true`** Jeśli metoda pomyślnie uzyska własność `mutex` ; w przeciwnym razie, **`false`** .

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex` , zachowanie jest niezdefiniowane.

## <a name="timed_mutexunlock"></a><a name="unlock"></a>timed_mutex:: Unlock

Zwalnia własność `mutex` .

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący nie `mutex` jest własnym, zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
