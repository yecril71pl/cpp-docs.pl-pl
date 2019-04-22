---
title: SRWLockSharedTraits — Struktura
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock method
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
ms.openlocfilehash: af567fd333854519df4543ad24084e52cda4d96e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786804"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits — Struktura

W tym artykule opisano typowe cechy `SRWLock` klasy w trybie blokady udostępniania.

## <a name="syntax"></a>Składnia

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa   | Opis
------ | --------------------------------------------------------------------------
`Type` | Synonim dla wskaźnika do [SRWLOCK](srwlock-class.md) klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                     | Opis
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLockSharedTraits::GetInvalidValue](#getinvalidvalue) | Pobiera `SRWLockSharedTraits` obiekt, który zawsze jest nieprawidłowy.
[SRWLockSharedTraits::Unlock](#unlock)                   | Zwalnia wyłączną kontrolę określonego `SRWLock` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SRWLockSharedTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>SRWLockSharedTraits::GetInvalidValue

Pobiera `SRWLockSharedTraits` obiekt, który zawsze jest nieprawidłowy.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do `SRWLockSharedTraits` obiektu.

## <a name="unlock"></a>SRWLockSharedTraits::Unlock

Zwalnia wyłączną kontrolę określonego `SRWLock` obiektu.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parametry

*srwlock*<br/>
Dojście do `SRWLock` obiektu.
