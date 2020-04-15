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
ms.openlocfilehash: 6c9840d9b8c00d4b03e6ea329c7707a0edff9512
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368019"
---
# <a name="timed_mutex-class"></a>timed_mutex — Klasa

Reprezentuje *typ czasowego obiektu mutex*. Obiekty tego typu są używane do wymuszania wzajemnego wykluczenia za pomocą ograniczonego w czasie blokowania w programie.

## <a name="syntax"></a>Składnia

```cpp
class timed_mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[timed_mutex](#timed_mutex)|Tworzy `timed_mutex` obiekt, który nie jest zablokowany.|
|[timed_mutex::~timed_mutex Destruktor](#dtortimed_mutex_destructor)|Zwalnia wszystkie zasoby, które `timed_mutex` są używane przez obiekt.|

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

## <a name="timed_mutexlock"></a><a name="lock"></a>timed_mutex::lock

Blokuje wątek wywołujący, dopóki `mutex`wątek nie uzyska własności . .

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="timed_mutextimed_mutex-constructor"></a><a name="timed_mutex"></a>timed_mutex::timed_mutex konstruktor

Tworzy `timed_mutex` obiekt, który nie jest zablokowany.

```cpp
timed_mutex();
```

## <a name="timed_mutextimed_mutex-destructor"></a><a name="dtortimed_mutex_destructor"></a>timed_mutex::~timed_mutex Destruktor

Zwalnia wszystkie zasoby, które `mutex` są używane przez obiekt.

```cpp
~timed_mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany podczas pracy destruktora, zachowanie jest niezdefiniowane.

## <a name="timed_mutextry_lock"></a><a name="try_lock"></a>timed_mutex::try_lock

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli metoda pomyślnie uzyskuje `mutex`własność ; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="timed_mutextry_lock_for"></a><a name="try_lock_for"></a>timed_mutex::try_lock_for

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
A [chrono::duration](../standard-library/duration-class.md) object, który określa maksymalny czas, przez jaki metoda `mutex`próbuje uzyskać własność .

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli metoda pomyślnie uzyskuje `mutex`własność ; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="timed_mutextry_lock_until"></a><a name="try_lock_until"></a>timed_mutex::try_lock_until

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

**true,** jeśli metoda pomyślnie uzyskuje `mutex`własność ; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="timed_mutexunlock"></a><a name="unlock"></a>timed_mutex::odblokuj

Zwalnia własność `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący `mutex`nie jest właścicielem , zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
