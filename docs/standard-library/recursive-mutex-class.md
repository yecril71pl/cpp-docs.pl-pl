---
title: recursive_mutex — Klasa
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.openlocfilehash: 448b4d03e4d38dc45621cddab7d8f5d03b805968
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451682"
---
# <a name="recursivemutex-class"></a>recursive_mutex — Klasa

Reprezentuje *Typ muteksu*. W przeciwieństwie do [obiektu mutex](../standard-library/mutex-class-stl.md), zachowanie wywołań metod blokowania dla obiektów, które są już zablokowane jest dobrze zdefiniowane.

## <a name="syntax"></a>Składnia

```cpp
class recursive_mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|Konstruuje `recursive_mutex` obiekt.|
|[~recursive_mutex Destructor](#dtorrecursive_mutex_destructor)|Zwalnia wszystkie zasoby, które są używane przez `recursive_mutex` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący do momentu, gdy wątek uzyska własność obiektu mutex.|
|[try_lock](#try_lock)|Próbuje uzyskać własność muteksu bez blokowania.|
|[unlock](#unlock)|Zwalnia własność obiektu mutex.|

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

## <a name="recursive_mutex"></a>recursive_mutex

Konstruuje `recursive_mutex` obiekt, który nie jest zablokowany.

```cpp
recursive_mutex();
```

## <a name="dtorrecursive_mutex_destructor"></a>~ recursive_mutex

Zwalnia wszystkie zasoby, które są używane przez obiekt.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany podczas działania destruktora, zachowanie jest niezdefiniowane.

## <a name="try_lock"></a>try_lock

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli metoda pomyślnie uzyska własność `mutex` lub jeśli `mutex**; otherwise, **false`wątek wywołujący jest już właścicielem.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, funkcja natychmiast zwraca **wartość true**, a poprzednia blokada pozostaje w mocy.

## <a name="unlock"></a>odblokowania

Zwalnia własność obiektu mutex.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Ta metoda `mutex` zwalnia własność tylko wtedy, gdy jest wywoływana tak dużo razy, jak [blokady](#lock) i [try_lock](#try_lock) zostały pomyślnie wywołane dla `recursive_mutex` obiektu.

Jeśli wątek wywołujący nie jest własnym `mutex`, zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
