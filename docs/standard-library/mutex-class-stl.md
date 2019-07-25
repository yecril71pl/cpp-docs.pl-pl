---
title: mutex — KlasaC++ (standardowa biblioteka) | Microsoft Docs
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
ms.openlocfilehash: 099cf17db7b99f9cd1d953a603db70f75c33358e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457057"
---
# <a name="mutex-class-c-standard-library"></a>mutex — KlasaC++ (standardowa biblioteka)

Reprezentuje *Typ muteksu*. Obiekty tego typu mogą być używane do wymuszania wzajemnego wykluczania w ramach programu.

## <a name="syntax"></a>Składnia

```cpp
class mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[mutex](#mutex)|Konstruuje `mutex` obiekt.|
|[mutex:: ~ mutex — destruktor](#dtormutex_destructor)|Zwalnia wszystkie zasoby, które były używane przez `mutex` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący do momentu, aż wątek uzyska własność `mutex`.|
|[native_handle](#native_handle)|Zwraca typ specyficzny dla implementacji, który reprezentuje uchwyt obiektu mutex.|
|[try_lock](#try_lock)|Próbuje uzyskać własność `mutex` bez blokowania.|
|[unlock](#unlock)|Zwalnia własność `mutex`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> mutex

**Przestrzeń nazw:** std

## <a name="lock"></a>mutex:: Lock

Blokuje wątek wywołujący do momentu, aż wątek uzyska własność `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="mutex"></a>mutex:: mutex — Konstruktor

Konstruuje `mutex` obiekt, który nie jest zablokowany.

```cpp
constexpr mutex() noexcept;
```

## <a name="dtormutex_destructor"></a>mutex:: ~ mutex — destruktor

Zwalnia wszystkie zasoby, które są używane przez `mutex` obiekt.

```cpp
~mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany podczas działania destruktora, zachowanie jest niezdefiniowane.

## <a name="native_handle"></a>mutex:: native_handle

Zwraca typ specyficzny dla implementacji, który reprezentuje uchwyt obiektu mutex. Uchwytu muteksu można użyć w sposób specyficzny dla implementacji.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwracana

`native_handle_type`jest definiowana jako `Concurrency::critical_section *` rzutowanie jako `void *`.

## <a name="try_lock"></a>mutex:: try_lock

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli metoda pomyślnie uzyska własność `mutex`; w przeciwnym razie, **Fałsz**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="unlock"></a>mutex:: Unlock

Zwalnia własność `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący nie jest własnym `mutex`, zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
