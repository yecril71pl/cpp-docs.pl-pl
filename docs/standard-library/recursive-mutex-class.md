---
title: recursive_mutex — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
dev_langs:
- C++
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.workload:
- cplusplus
ms.openlocfilehash: 89c39f006cee8c62c22f3caf7e2c10ee9a0c1d03
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864937"
---
# <a name="recursivemutex-class"></a>recursive_mutex — Klasa

Reprezentuje *typu obiektu mutex*. Contrast do [obiektu mutex](../standard-library/mutex-class-stl.md), zachowanie wywołania metod blokowania dla obiektów, które są już zablokowane jest dobrze zdefiniowany.

## <a name="syntax"></a>Składnia

```cpp
class recursive_mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|Konstruuje `recursive_mutex` obiektu.|
|[~recursive_mutex Destructor](#dtorrecursive_mutex_destructor)|Zwalnia wszystkie zasoby, które są używane przez `recursive_mutex` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Wątek wywołujący blokuje, dopóki wątek uzyskuje prawo własności obiektu mutex.|
|[try_lock](#try_lock)|Próbuje uzyskać prawo własności obiektu mutex bez blokowania.|
|[unlock](#unlock)|Zwalnia prawo własności obiektu mutex.|

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

## <a name="recursive_mutex"></a>  recursive_mutex

Konstruuje `recursive_mutex` obiekt, który nie jest zablokowany.

```cpp
recursive_mutex();
```

## <a name="dtorrecursive_mutex_destructor"></a>  ~ recursive_mutex

Zwalnia wszystkie zasoby, które są używane przez obiekt.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany, po uruchomieniu destruktor, zachowanie jest niezdefiniowany.

## <a name="try_lock"></a>  try_lock

Próbuje uzyskać prawo własności `mutex` bez blokowania.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli metoda pomyślnie uzyskuje prawo własności `mutex` lub jeśli wątek wywołujący już właścicielem `mutex`; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący już właścicielem `mutex`, funkcja natychmiast zwraca `true`, i obowiązuje poprzedniej blokady.

## <a name="unlock"></a>  odblokowywanie

Zwalnia prawo własności obiektu mutex.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Ta metoda zwalnia własność `mutex` tylko wtedy, gdy jest ona wywoływana tyle razy, ile [blokady](#lock) i [try_lock](#try_lock) pomyślnie wywołana dla `recursive_mutex` obiektu.

Jeśli wątek wywołujący nie jest właścicielem `mutex`, zachowanie jest niezdefiniowany.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
