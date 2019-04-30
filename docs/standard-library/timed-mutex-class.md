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
ms.openlocfilehash: 9aae1205866a0bf982ab7c41b792aac0f63ea149
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411958"
---
# <a name="timedmutex-class"></a>timed_mutex — Klasa

Reprezentuje *upłynął limit czasu typu obiektu mutex*. Obiekty tego typu są używane w celu wymuszenia wzajemnego wykluczenia przez ograniczony czas blokowania w programie.

## <a name="syntax"></a>Składnia

```cpp
class timed_mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[timed_mutex](#timed_mutex)|Konstruuje `timed_mutex` obiektu, który nie jest zablokowany.|
|[timed_mutex::~timed_mutex Destructor](#dtortimed_mutex_destructor)|Zwalnia wszelkie zasoby, które są używane przez `timed_mutex` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący, aż wątek uzyskuje własność `mutex`.|
|[try_lock](#try_lock)|Próby uzyskania własności `mutex` bez blokowania.|
|[try_lock_for](#try_lock_for)|Próby uzyskania własności `mutex` określony interwał czasu.|
|[try_lock_until](#try_lock_until)|Próby uzyskania własności `mutex` do określonego czasu.|
|[unlock](#unlock)|Zwalnia własność `mutex`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mutex >

**Namespace:** standardowe

## <a name="lock"></a>  timed_mutex::lock

Blokuje wątek wywołujący, aż wątek uzyskuje własność `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="timed_mutex"></a>  timed_mutex::timed_mutex — Konstruktor

Konstruuje `timed_mutex` obiektu, który nie jest zablokowany.

```cpp
timed_mutex();
```

## <a name="dtortimed_mutex_destructor"></a>  timed_mutex:: ~ timed_mutex — destruktor

Zwalnia wszelkie zasoby, które są używane przez `mutex` obiektu.

```cpp
~timed_mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany, po uruchomieniu destruktora, zachowanie jest niezdefiniowane.

## <a name="try_lock"></a>  timed_mutex::try_lock

Próby uzyskania własności `mutex` bez blokowania.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli metoda pomyślnie uzyskuje własność `mutex`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="try_lock_for"></a>  timed_mutex::try_lock_for

Próby uzyskania własności `mutex` bez blokowania.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*<br/>
A [chrono::duration](../standard-library/duration-class.md) obiektu, który określa maksymalną ilość czasu, która metoda podejmuje próbę uzyskania własności `mutex`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli metoda pomyślnie uzyskuje własność `mutex`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="try_lock_until"></a>  timed_mutex::try_lock_until

Próby uzyskania własności `mutex` bez blokowania.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*<br/>
Punkt w czasie, który określa próg, po upływie którego metoda nie jest już próby uzyskania własności `mutex`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli metoda pomyślnie uzyskuje własność `mutex`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="unlock"></a>  timed_mutex::unlock

Zwalnia własność `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący nie jest właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
