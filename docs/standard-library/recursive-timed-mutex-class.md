---
title: recursive_timed_mutex — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::lock
- mutex/std::recursive_timed_mutex::try_lock
- mutex/std::recursive_timed_mutex::try_lock_for
- mutex/std::recursive_timed_mutex::try_lock_until
- mutex/std::recursive_timed_mutex::unlock
dev_langs:
- C++
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::recursive_timed_mutex [C++]
- std::recursive_timed_mutex [C++], recursive_timed_mutex
- std::recursive_timed_mutex [C++], lock
- std::recursive_timed_mutex [C++], try_lock
- std::recursive_timed_mutex [C++], try_lock_for
- std::recursive_timed_mutex [C++], try_lock_until
- std::recursive_timed_mutex [C++], unlock
ms.workload:
- cplusplus
ms.openlocfilehash: 9b4a87cadedb11368d7803231b96d0f7a5acfb99
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863715"
---
# <a name="recursivetimedmutex-class"></a>recursive_timed_mutex — Klasa

Reprezentuje *upłynął typu obiektu mutex*. Obiekty tego typu są używane do wymuszania wykluczanie wzajemne przy użyciu czas blokowania w programie. W przeciwieństwie do obiektów typu [timed_mutex](../standard-library/timed-mutex-class.md), efekt podczas wywoływania metody blokowania `recursive_timed_mutex` obiektów jest dobrze zdefiniowany.

## <a name="syntax"></a>Składnia

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|Konstruuje `recursive_timed_mutex` obiekt, który nie jest zablokowany.|
|[~recursive_timed_mutex Destructor](#dtorrecursive_timed_mutex_destructor)|Zwalnia wszystkie zasoby, które są używane przez `recursive_timed_mutex` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Wątek wywołujący blokuje, dopóki wątek uzyskuje prawo własności do `mutex`.|
|[try_lock](#try_lock)|Próbuje uzyskać prawo własności `mutex` bez blokowania.|
|[try_lock_for](#try_lock_for)|Próbuje uzyskać prawo własności `mutex` określony interwał czasu.|
|[try_lock_until](#try_lock_until)|Próbuje uzyskać prawo własności `mutex` dopiero po określonym czasie.|
|[unlock](#unlock)|Zwalnia własność `mutex`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<obiektu mutex >

**Namespace:** Standard

## <a name="lock"></a>  blokady

Wątek wywołujący blokuje, dopóki wątek uzyskuje prawo własności do `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący już właścicielem `mutex`, metoda zwraca natychmiast i poprzednia blokada będzie obowiązywać.

## <a name="recursive_timed_mutex"></a>  recursive_timed_mutex — Konstruktor

Konstruuje `recursive_timed_mutex` obiekt, który nie jest zablokowany.

```cpp
recursive_timed_mutex();
```

## <a name="dtorrecursive_timed_mutex_destructor"></a>  ~ recursive_timed_mutex — destruktor

Zwalnia wszystkie zasoby, które są używane przez `recursive_timed_mutex` obiektu.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany, po uruchomieniu destruktor, zachowanie jest niezdefiniowany.

## <a name="try_lock"></a>  try_lock

Próbuje uzyskać prawo własności `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli metoda pomyślnie uzyskał własność `mutex` lub jeśli wątek wywołujący już właścicielem `mutex`; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący już właścicielem `mutex`, funkcja natychmiast zwraca `true`, i obowiązuje poprzedniej blokady.

## <a name="try_lock_for"></a>  try_lock_for

Próbuje uzyskać prawo własności `mutex` bez blokowania.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

`Rel_time` A [chrono::duration](../standard-library/duration-class.md) obiekt, który określa maksymalną ilość czasu, który próbuje uzyskać prawo własności do metody `mutex`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli metoda pomyślnie uzyskuje prawo własności `mutex` lub jeśli wątek wywołujący już właścicielem `mutex`; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący już właścicielem `mutex`, metoda natychmiast zwraca `true`, i obowiązuje poprzedniej blokady.

## <a name="try_lock_until"></a>  try_lock_until

Próbuje uzyskać prawo własności `mutex` bez blokowania.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

`Abs_time` Punktu w czasie, który określa próg, po upływie którego metoda nie jest już próbuje uzyskać prawo własności do `mutex`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli metoda pomyślnie uzyskuje prawo własności `mutex` lub jeśli wątek wywołujący już właścicielem `mutex`; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący już właścicielem `mutex`, metoda natychmiast zwraca `true`, i obowiązuje poprzedniej blokady.

## <a name="unlock"></a>  odblokowywanie

Zwalnia własność `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Ta metoda zwalnia własność `mutex` tylko wtedy, gdy jest ona wywoływana tyle razy, ile [blokady](#lock), [try_lock](#try_lock), [try_lock_for](#try_lock_for), i [try_lock_ dopóki](#try_lock_until) pomyślnie wywołana dla `recursive_timed_mutex` obiektu.

Jeśli wątek wywołujący nie jest właścicielem `mutex`, zachowanie jest niezdefiniowany.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
