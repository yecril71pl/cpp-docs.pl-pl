---
title: mutex — klasa (standardowa biblioteka C++) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.openlocfilehash: 7766b063eb89a14a94eaa41ebfa17f3e4a1c102e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158581"
---
# <a name="mutex-class-c-standard-library"></a>mutex — klasa (standardowa biblioteka C++)

Reprezentuje *typu obiektu mutex*. Obiekty tego typu może służyć do wymuszenia wzajemnego wykluczenia w ramach programu.

## <a name="syntax"></a>Składnia

```cpp
class mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[mutex](#mutex)|Konstruuje `mutex` obiektu.|
|[mutex:: ~ mutex — destruktor](#dtormutex_destructor)|Zwalnia wszelkie zasoby, które były używane przez `mutex` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący, aż wątek uzyskuje własność `mutex`.|
|[native_handle](#native_handle)|Zwraca typ zależny od implementacji, który reprezentuje uchwyt mutex.|
|[try_lock](#try_lock)|Próby uzyskania własności `mutex` bez blokowania.|
|[unlock](#unlock)|Zwalnia własność `mutex`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mutex >

**Namespace:** standardowe

## <a name="lock"></a>  mutex::Lock —

Blokuje wątek wywołujący, aż wątek uzyskuje własność `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="mutex"></a>  mutex::mutex — Konstruktor

Konstruuje `mutex` obiektu, który nie jest zablokowany.

```cpp
constexpr mutex() noexcept;
```

## <a name="dtormutex_destructor"></a>  mutex:: ~ mutex — destruktor

Zwalnia wszelkie zasoby, które są używane przez `mutex` obiektu.

```cpp
~mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany, po uruchomieniu destruktora, zachowanie jest niezdefiniowane.

## <a name="native_handle"></a>  mutex::native_handle

Zwraca typ zależny od implementacji, który reprezentuje uchwyt mutex. Uchwyt mutex może służyć w sposób specyficzne dla implementacji.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwracana

`native_handle_type` jest zdefiniowany jako `Concurrency::critical_section *` , jest rzutowany jako `void *`.

## <a name="try_lock"></a>  mutex::try_lock

Próby uzyskania własności `mutex` bez blokowania.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli metoda pomyślnie uzyskuje własność `mutex`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="unlock"></a>  mutex::Unlock —

Zwalnia własność `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący nie jest właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
