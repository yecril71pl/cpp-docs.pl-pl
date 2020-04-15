---
title: klasa mutex (standardowa biblioteka C++)| Dokumenty firmy Microsoft
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
ms.openlocfilehash: 84e6e3a46903a204444df9886556ae2c563304a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364842"
---
# <a name="mutex-class-c-standard-library"></a>klasa mutex (standardowa biblioteka C++)

Reprezentuje *typ mutex*. Obiekty tego typu mogą służyć do wymuszania wzajemnego wykluczenia w programie.

## <a name="syntax"></a>Składnia

```cpp
class mutex;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Mutex](#mutex)|Konstruuje `mutex` obiekt.|
|[mutex::~mutex Destructor](#dtormutex_destructor)|Zwalnia wszystkie zasoby, które `mutex` były używane przez obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Blokuje wątek wywołujący, dopóki `mutex`wątek nie uzyska własności . .|
|[native_handle](#native_handle)|Zwraca typ specyficzny dla implementacji, który reprezentuje dojście obiektu mutex.|
|[try_lock](#try_lock)|Próbuje uzyskać własność `mutex` bez blokowania.|
|[Odblokować](#unlock)|Zwalnia własność `mutex`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mutex>

**Przestrzeń nazw:** std

## <a name="mutexlock"></a><a name="lock"></a>mutex::lock

Blokuje wątek wywołujący, dopóki `mutex`wątek nie uzyska własności . .

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="mutexmutex-constructor"></a><a name="mutex"></a>mutex::mutex Konstruktor

Tworzy `mutex` obiekt, który nie jest zablokowany.

```cpp
constexpr mutex() noexcept;
```

## <a name="mutexmutex-destructor"></a><a name="dtormutex_destructor"></a>mutex::~mutex Destructor

Zwalnia wszystkie zasoby, które `mutex` są używane przez obiekt.

```cpp
~mutex();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt jest zablokowany podczas pracy destruktora, zachowanie jest niezdefiniowane.

## <a name="mutexnative_handle"></a><a name="native_handle"></a>mutex::native_handle

Zwraca typ specyficzny dla implementacji, który reprezentuje dojście obiektu mutex. Dojście obiektu mutex może być używane w sposób specyficzny dla implementacji.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwracana

`native_handle_type`jest zdefiniowany `Concurrency::critical_section *` jako, który `void *`jest oddanych jako .

## <a name="mutextry_lock"></a><a name="try_lock"></a>mutex::try_lock

Próbuje uzyskać własność `mutex` bez blokowania.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli metoda pomyślnie uzyskuje `mutex`własność ; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący jest już właścicielem `mutex`, zachowanie jest niezdefiniowane.

## <a name="mutexunlock"></a><a name="unlock"></a>mutex::odblokuj

Zwalnia własność `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Jeśli wątek wywołujący `mutex`nie jest właścicielem , zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
