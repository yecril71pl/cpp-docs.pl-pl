---
title: mutex — klasa (standardowa biblioteka C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
dev_langs:
- C++
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.workload:
- cplusplus
ms.openlocfilehash: 23e7220d2710465dc8d155cf35ec7d47db4e3c08
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854080"
---
# <a name="mutex-class-c-standard-library"></a>mutex — klasa (standardowa biblioteka C++)

Reprezentuje *typu obiektu mutex*. Obiekty tego typu może służyć do wymuszania wzajemne wykluczenie w programie.

## <a name="syntax"></a>Składnia

```cpp
class mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[mutex](#mutex)|Konstruuje `mutex` obiektu.|
|[mutex:: ~ mutex — destruktor](#dtormutex_destructor)|Zwalnia wszystkie zasoby, które były używane przez `mutex` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Wątek wywołujący blokuje, dopóki wątek uzyskuje prawo własności do `mutex`.|
|[native_handle](#native_handle)|Zwraca typ konkretnej implementacji, który reprezentuje dojście obiektu mutex.|
|[try_lock](#try_lock)|Próbuje uzyskać prawo własności `mutex` bez blokowania.|
|[unlock](#unlock)|Zwalnia własność `mutex`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<obiektu mutex >

**Namespace:** Standard

## <a name="lock"></a>  mutex::Lock

Wątek wywołujący blokuje, dopóki wątek uzyskuje prawo własności do `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący już właścicielem `mutex`, zachowanie jest niezdefiniowany.

## <a name="mutex"></a>  mutex::mutex — Konstruktor

Konstruuje `mutex` obiekt, który nie jest zablokowany.

```cpp
constexpr mutex() noexcept;
```

## <a name="dtormutex_destructor"></a>  mutex:: ~ mutex — destruktor

Zwalnia wszystkie zasoby, które są używane przez `mutex` obiektu.

```cpp
~mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany, po uruchomieniu destruktor, zachowanie jest niezdefiniowany.

## <a name="native_handle"></a>  mutex::native_handle

Zwraca typ konkretnej implementacji, który reprezentuje dojście obiektu mutex. Dojście obiektu mutex można w sposób konkretnej implementacji.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwracana

`native_handle_type` nie zdefiniowano jako `Concurrency::critical_section *` który jest rzutowany jako `void *`.

## <a name="try_lock"></a>  mutex::try_lock

Próbuje uzyskać prawo własności `mutex` bez blokowania.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli metoda pomyślnie uzyskuje prawo własności `mutex`; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący już właścicielem `mutex`, zachowanie jest niezdefiniowany.

## <a name="unlock"></a>  mutex::Unlock

Zwalnia własność `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący nie jest właścicielem `mutex`, zachowanie jest niezdefiniowany.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
