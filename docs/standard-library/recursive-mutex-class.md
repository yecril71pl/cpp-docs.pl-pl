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
ms.openlocfilehash: 8455548997c4ccf1b950e26e01df67306554b945
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217613"
---
# <a name="recursive_mutex-class"></a>recursive_mutex — Klasa

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
|[~ recursive_mutex destruktor](#dtorrecursive_mutex_destructor)|Zwalnia wszystkie zasoby, które są używane przez `recursive_mutex` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[skręt](#lock)|Blokuje wątek wywołujący do momentu, gdy wątek uzyska własność obiektu mutex.|
|[try_lock](#try_lock)|Próbuje uzyskać własność muteksu bez blokowania.|
|[odblokowania](#unlock)|Zwalnia własność obiektu mutex.|

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

## <a name="recursive_mutex"></a><a name="recursive_mutex"></a>recursive_mutex

Konstruuje `recursive_mutex` obiekt, który nie jest zablokowany.

```cpp
recursive_mutex();
```

## <a name="recursive_mutex"></a><a name="dtorrecursive_mutex_destructor"></a>~ recursive_mutex

Zwalnia wszystkie zasoby, które są używane przez obiekt.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany podczas działania destruktora, zachowanie jest niezdefiniowane.

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli metoda pomyślnie uzyska własność `mutex` lub jeśli wątek wywołujący już należy do obiektu `mutex**; otherwise, **false` .

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex` , funkcja natychmiast zwraca wartość **`true`** , a poprzednia blokada pozostaje w mocy.

## <a name="unlock"></a><a name="unlock"></a>odblokowania

Zwalnia własność obiektu mutex.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Ta metoda zwalnia własność `mutex` tylko wtedy, gdy jest wywoływana tyle razy jak [blokada](#lock) i [try_lock](#try_lock) zostały pomyślnie wywołane dla `recursive_mutex` obiektu.

Jeśli wątek wywołujący nie `mutex` jest własnym, zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
