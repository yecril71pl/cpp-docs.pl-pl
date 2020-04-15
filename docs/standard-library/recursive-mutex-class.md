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
ms.openlocfilehash: 9ab7a96a7c07582450ab41b140dcc5494a63661f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320203"
---
# <a name="recursive_mutex-class"></a>recursive_mutex — Klasa

Reprezentuje *typ mutex*. W przeciwieństwie do [obiektu mutex](../standard-library/mutex-class-stl.md)zachowanie wywołań metod blokowania dla obiektów, które są już zablokowane, jest dobrze zdefiniowane.

## <a name="syntax"></a>Składnia

```cpp
class recursive_mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|Konstruuje `recursive_mutex` obiekt.|
|[~recursive_mutex Destruktor](#dtorrecursive_mutex_destructor)|Zwalnia wszystkie zasoby, które `recursive_mutex` są używane przez obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący, dopóki wątek nie uzyska własności obiektu mutex.|
|[try_lock](#try_lock)|Próbuje uzyskać własność obiektu mutex bez blokowania.|
|[Odblokować](#unlock)|Zwalnia własność obiektu mutex.|

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

## <a name="recursive_mutex"></a><a name="recursive_mutex"></a>recursive_mutex

Tworzy `recursive_mutex` obiekt, który nie jest zablokowany.

```cpp
recursive_mutex();
```

## <a name="recursive_mutex"></a><a name="dtorrecursive_mutex_destructor"></a>~recursive_mutex

Zwalnia wszystkie zasoby, które są używane przez obiekt.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany podczas pracy destruktora, zachowanie jest niezdefiniowane.

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli metoda pomyślnie uzyskuje `mutex` własność lub jeśli wątek wywołujący jest już właścicielem `mutex**; otherwise, **false`.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, funkcja natychmiast zwraca **true**, a poprzednia blokada pozostaje w mocy.

## <a name="unlock"></a><a name="unlock"></a>Odblokować

Zwalnia własność obiektu mutex.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Ta metoda zwalnia `mutex` własność tylko po jest wywoływana tyle razy, jak [blokada](#lock) `recursive_mutex` i [try_lock](#try_lock) zostały wywołane pomyślnie na obiekt.

Jeśli wątek wywołujący `mutex`nie jest właścicielem , zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
