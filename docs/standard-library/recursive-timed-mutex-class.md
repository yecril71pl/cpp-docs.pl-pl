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
ms.openlocfilehash: 2cb6fe8588f4b81ae5c67533c4b9124ae8c9b252
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618156"
---
# <a name="recursivetimedmutex-class"></a>recursive_timed_mutex — Klasa

Reprezentuje *upłynął limit czasu typu obiektu mutex*. Obiekty tego typu są używane w celu wymuszenia wzajemnego wykluczenia, korzystając z ograniczonej czasowo blokowanie w programie. W przeciwieństwie do obiektów tego typu [timed_mutex](../standard-library/timed-mutex-class.md), efekt podczas wywoływania metody blokowania `recursive_timed_mutex` obiektów jest dobrze zdefiniowany.

## <a name="syntax"></a>Składnia

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|Konstruuje `recursive_timed_mutex` obiektu, który nie jest zablokowany.|
|[~recursive_timed_mutex Destructor](#dtorrecursive_timed_mutex_destructor)|Zwalnia wszelkie zasoby, które są używane przez `recursive_timed_mutex` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący, aż wątek uzyskuje własność `mutex`.|
|[try_lock —](#try_lock)|Próby uzyskania własności `mutex` bez blokowania.|
|[try_lock_for](#try_lock_for)|Próby uzyskania własności `mutex` określony interwał czasu.|
|[try_lock_until](#try_lock_until)|Próby uzyskania własności `mutex` do określonego czasu.|
|[unlock](#unlock)|Zwalnia własność `mutex`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mutex >

**Namespace:** standardowe

## <a name="lock"></a>  Blokady

Blokuje wątek wywołujący, aż wątek uzyskuje własność `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, metoda zwraca natychmiast i obowiązuje poprzednią blokadę.

## <a name="recursive_timed_mutex"></a>  recursive_timed_mutex konstruktora

Konstruuje `recursive_timed_mutex` obiektu, który nie jest zablokowany.

```cpp
recursive_timed_mutex();
```

## <a name="dtorrecursive_timed_mutex_destructor"></a>  ~ recursive_timed_mutex — destruktor

Zwalnia wszelkie zasoby, które są używane przez `recursive_timed_mutex` obiektu.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany, po uruchomieniu destruktora, zachowanie jest niezdefiniowane.

## <a name="try_lock"></a>  try_lock —

Próby uzyskania własności `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli metoda pomyślnie uzyskał własności `mutex` lub jeśli wątek wywołujący jest już właścicielem `mutex`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, funkcja natychmiast zwraca **true**, i obowiązuje poprzednią blokadę.

## <a name="try_lock_for"></a>  try_lock_for —

Próby uzyskania własności `mutex` bez blokowania.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*<br/>
A [chrono::duration](../standard-library/duration-class.md) obiektu, który określa maksymalną ilość czasu, która metoda podejmuje próbę uzyskania własności `mutex`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli metoda pomyślnie uzyskuje własność `mutex` lub jeśli wątek wywołujący jest już właścicielem `mutex`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, metoda natychmiast zwraca **true**, i obowiązuje poprzednią blokadę.

## <a name="try_lock_until"></a>  try_lock_until

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

**wartość true,** Jeśli metoda pomyślnie uzyskuje własność `mutex` lub jeśli wątek wywołujący jest już właścicielem `mutex`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, metoda natychmiast zwraca **true**, i obowiązuje poprzednią blokadę.

## <a name="unlock"></a>  Odblokowywanie

Zwalnia własność `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Ta metoda zwalnia własność `mutex` tylko wtedy, gdy jest on nazywany tyle razy, ile [blokady](#lock), [try_lock —](#try_lock), [try_lock_for —](#try_lock_for), i [try_lock_ do momentu](#try_lock_until) pomyślnie wywołana dla `recursive_timed_mutex` obiektu.

Jeśli wątek wywołujący nie jest właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
