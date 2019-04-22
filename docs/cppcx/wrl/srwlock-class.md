---
title: SRWLock — Klasa
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock_
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::~SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
helpviewer_keywords:
- Microsoft::WRL::Wrappers::SRWLock class
- Microsoft::WRL::Wrappers::SRWLock::LockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::LockShared method
- Microsoft::WRL::Wrappers::SRWLock::SRWLock, constructor
- Microsoft::WRL::Wrappers::SRWLock::SRWLock_ data member
- Microsoft::WRL::Wrappers::SRWLock::~SRWLock, destructor
- Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::TryLockShared method
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
ms.openlocfilehash: 6d4a504d9465c858af59a88cf0ef611bf88c3fde
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787494"
---
# <a name="srwlock-class"></a>SRWLock — Klasa

Reprezentuje kieszeń czytnika/blokadę.

## <a name="syntax"></a>Składnia

```cpp
class SRWLock;
```

## <a name="remarks"></a>Uwagi

Cienki czytnika/blokadę służy do synchronizowania dostępu w wątkach do obiektu lub zasobu. Aby uzyskać więcej informacji, zobacz [funkcji synchronizacji](/windows/desktop/Sync/synchronization-functions).

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa                | Opis
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | Synonim dla `SRWLock` obiekt, który jest uzyskiwany w trybie wyłączności.
`SyncLockShared`    | Synonim dla `SRWLock` obiekt, który jest uzyskiwany w trybie udostępniania.

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                     | Opis
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | Inicjuje nowe wystąpienie klasy `SRWLock` klasy.
[SRWLock::~SRWLock](#tilde-srwlock)      | Wyłącza wystąpienie `SRWLock` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                           | Opis
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | Uzyskuje `SRWLock` obiektu w trybie wyłączności.
[SRWLock::LockShared](#lockshared)             | Uzyskuje `SRWLock` obiektu w tryb udostępniania.
[SRWLock::TryLockExclusive](#trylockexclusive) | Próbuje pobrać `SRWLock` obiektu w trybie wyłączności dla bieżącej lub określonej `SRWLock` obiektu.
[SRWLock::TryLockShared](#trylockshared)       | Próbuje pobrać `SRWLock` obiektu w tryb udostępniania dla bieżącej lub określonej `SRWLock` obiektu.

### <a name="protected-data-member"></a>Element członkowski danych chronionych

Nazwa                                      | Opis
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock::SRWLock_](#srwlock-data-member) | Zawiera podstawowe zmienną blokady dla bieżącego `SRWLock` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SRWLock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="tilde-srwlock"></a>SRWLock:: ~ SRWLock

Wyłącza wystąpienie `SRWLock` klasy.

```cpp
~SRWLock();
```

## <a name="lockexclusive"></a>SRWLock::LockExclusive

Uzyskuje `SRWLock` obiektu w trybie wyłączności.

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Wskaźnik do `SRWLock` obiektu.

### <a name="return-value"></a>Wartość zwracana

`SRWLock` Obiektu w trybie wyłączności.

## <a name="lockshared"></a>SRWLock::LockShared

Uzyskuje `SRWLock` obiektu w tryb udostępniania.

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Wskaźnik do `SRWLock` obiektu.

### <a name="return-value"></a>Wartość zwracana

`SRWLock` Obiektu w tryb udostępniania.

## <a name="srwlock-constructor"></a>SRWLock::SRWLock

Inicjuje nowe wystąpienie klasy `SRWLock` klasy.

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>SRWLock::SRWLock_

Zawiera podstawowe zmienną blokady dla bieżącego `SRWLock` obiektu.

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>SRWLock::TryLockExclusive

Próbuje pobrać `SRWLock` obiektu w trybie wyłączności dla bieżącej lub określonej `SRWLock` obiektu. Jeśli wywołanie zakończy się pomyślnie, wątek wywołujący przejmuje na własność blokadę.

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Wskaźnik do `SRWLock` obiektu.

### <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia `SRWLock` obiektu w trybie wyłączności i Wątek wywołujący przejmuje na własność blokadę. W przeciwnym razie `SRWLock` obiektu, którego stan jest nieprawidłowy.

## <a name="trylockshared"></a>SRWLock::TryLockShared

Próbuje pobrać `SRWLock` obiektu w tryb udostępniania dla bieżącej lub określonej `SRWLock` obiektu.

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Wskaźnik do `SRWLock` obiektu.

### <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia `SRWLock` obiektu w tryb udostępniania i Wątek wywołujący przejmuje na własność blokadę. W przeciwnym razie `SRWLock` obiektu, którego stan jest nieprawidłowy.
