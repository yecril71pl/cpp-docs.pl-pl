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
ms.openlocfilehash: e305ad54e30455ce7c25f356c454791da0783591
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377268"
---
# <a name="srwlock-class"></a>SRWLock — Klasa

Reprezentuje wąski czytnik/blokadę modułu zapisującego.

## <a name="syntax"></a>Składnia

```cpp
class SRWLock;
```

## <a name="remarks"></a>Uwagi

Wąski czytnik/moduł zapisujący jest używany do synchronizowania dostępu między wątkami do obiektu lub zasobu. Aby uzyskać więcej informacji, zobacz [Funkcje synchronizacji](/windows/win32/Sync/synchronization-functions).

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa                | Opis
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | Synonim obiektu, `SRWLock` który jest nabywany w trybie wyłączności.
`SyncLockShared`    | Synonim obiektu, `SRWLock` który jest nabywany w trybie udostępnionym.

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                     | Opis
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | Inicjuje nowe wystąpienie klasy `SRWLock`.
[SRWLock::~SRWLock](#tilde-srwlock)      | Deinitializes wystąpienia `SRWLock` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                           | Opis
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | Uzyskuje obiekt `SRWLock` w trybie wyłączności.
[SRWLock::LockShared](#lockshared)             | Uzyskuje obiekt `SRWLock` w trybie udostępnionym.
[SRWLock::TryLockEkclusive](#trylockexclusive) | Próbuje uzyskać `SRWLock` obiekt w trybie wyłączności `SRWLock` dla bieżącego lub określonego obiektu.
[SRWLock::TryLockShared](#trylockshared)       | Próbuje uzyskać `SRWLock` obiekt w trybie udostępnionym `SRWLock` dla bieżącego lub określonego obiektu.

### <a name="protected-data-member"></a>Element członkowski chronionych danych

Nazwa                                      | Opis
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock::SRWLock_](#srwlock-data-member) | Zawiera podstawową zmienną `SRWLock` blokady dla bieżącego obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SRWLock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki

## <a name="srwlocksrwlock"></a><a name="tilde-srwlock"></a>SRWLock::~SRWLock

Deinitializes wystąpienia `SRWLock` klasy.

```cpp
~SRWLock();
```

## <a name="srwlocklockexclusive"></a><a name="lockexclusive"></a>SRWLock::LockExclusive

Uzyskuje obiekt `SRWLock` w trybie wyłączności.

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

Obiekt `SRWLock` w trybie wyłączności.

## <a name="srwlocklockshared"></a><a name="lockshared"></a>SRWLock::LockShared

Uzyskuje obiekt `SRWLock` w trybie udostępnionym.

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

Obiekt `SRWLock` w trybie udostępnionym.

## <a name="srwlocksrwlock"></a><a name="srwlock-constructor"></a>SRWLock::SRWLock

Inicjuje nowe wystąpienie klasy `SRWLock`.

```cpp
SRWLock();
```

## <a name="srwlocksrwlock_"></a><a name="srwlock-data-member"></a>SRWLock::SRWLock_

Zawiera podstawową zmienną `SRWLock` blokady dla bieżącego obiektu.

```cpp
SRWLOCK SRWLock_;
```

## <a name="srwlocktrylockexclusive"></a><a name="trylockexclusive"></a>SRWLock::TryLockEkclusive

Próbuje uzyskać `SRWLock` obiekt w trybie wyłączności `SRWLock` dla bieżącego lub określonego obiektu. Jeśli wywołanie zakończy się pomyślnie, wątek wywołujący przejmuje na własność blokady.

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

Jeśli się `SRWLock` powiedzie, obiekt w trybie wyłączności i wątku wywołującego przejmuje na własność blokady. W przeciwnym `SRWLock` razie obiekt, którego stan jest nieprawidłowy.

## <a name="srwlocktrylockshared"></a><a name="trylockshared"></a>SRWLock::TryLockShared

Próbuje uzyskać `SRWLock` obiekt w trybie udostępnionym `SRWLock` dla bieżącego lub określonego obiektu.

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

Jeśli się `SRWLock` powiedzie, obiekt w trybie udostępnionym i wątku wywołującego przejmuje na własność blokady. W przeciwnym `SRWLock` razie obiekt, którego stan jest nieprawidłowy.
