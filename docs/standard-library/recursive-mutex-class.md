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
ms.openlocfilehash: 8be17c8ab361272678c25326464261e153da6a49
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534410"
---
# <a name="recursivemutex-class"></a>recursive_mutex — Klasa

Reprezentuje *typu obiektu mutex*. W przeciwieństwie do [mutex](../standard-library/mutex-class-stl.md), zachowanie wywołania blokowania metod dla obiektów, które są już zablokowane jest dobrze zdefiniowany.

## <a name="syntax"></a>Składnia

```cpp
class recursive_mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|Konstruuje `recursive_mutex` obiektu.|
|[~recursive_mutex Destructor](#dtorrecursive_mutex_destructor)|Zwalnia wszelkie zasoby, które są używane przez `recursive_mutex` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący, aż wątek uzyskuje własność obiektu mutex.|
|[try_lock —](#try_lock)|Próby uzyskania własności obiektu mutex bez blokowania.|
|[unlock](#unlock)|Zwalnia własność obiektu mutex.|

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

## <a name="recursive_mutex"></a>  recursive_mutex

Konstruuje `recursive_mutex` obiektu, który nie jest zablokowany.

```cpp
recursive_mutex();
```

## <a name="dtorrecursive_mutex_destructor"></a>  ~ recursive_mutex

Zwalnia wszelkie zasoby, które są używane przez obiekt.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany, po uruchomieniu destruktora, zachowanie jest niezdefiniowane.

## <a name="try_lock"></a>  try_lock —

Próby uzyskania własności `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli metoda pomyślnie uzyskuje własność `mutex` lub jeśli wątek wywołujący jest już właścicielem `mutex**; otherwise, **false`.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, funkcja natychmiast zwraca **true**, i obowiązuje poprzednią blokadę.

## <a name="unlock"></a>  Odblokowywanie

Zwalnia własność obiektu mutex.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Ta metoda zwalnia własność `mutex` tylko wtedy, gdy jest on nazywany tyle razy, ile [blokady](#lock) i [try_lock —](#try_lock) pomyślnie wywołana dla `recursive_mutex` obiektu.

Jeśli wątek wywołujący nie jest właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
