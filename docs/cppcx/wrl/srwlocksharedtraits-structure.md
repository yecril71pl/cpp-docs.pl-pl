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
ms.openlocfilehash: 0dc43d4b9c16145ed7a5abe03cddb598c59b1e94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374299"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits — Struktura

W tym artykule opisano typowe cechy `SRWLock` klasy w trybie blokady udostępnionej.

## <a name="syntax"></a>Składnia

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa   | Opis
------ | --------------------------------------------------------------------------
`Type` | Synonim wskaźnika do klasy [SRWLOCK.](srwlock-class.md)

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                     | Opis
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLockSharedTraits::GetInvalidValue](#getinvalidvalue) | Pobiera obiekt, `SRWLockSharedTraits` który jest zawsze nieprawidłowy.
[SRWLockSharedTraits::Odblokuj](#unlock)                   | Zwalnia wyłączną kontrolę `SRWLock` nad określonym obiektem.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SRWLockSharedTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki::HandleTraits

## <a name="srwlocksharedtraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>SRWLockSharedTraits::GetInvalidValue

Pobiera obiekt, `SRWLockSharedTraits` który jest zawsze nieprawidłowy.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Wartość zwracana

Dojście `SRWLockSharedTraits` do obiektu.

## <a name="srwlocksharedtraitsunlock"></a><a name="unlock"></a>SRWLockSharedTraits::Odblokuj

Zwalnia wyłączną kontrolę `SRWLock` nad określonym obiektem.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parametry

*Srwlock*<br/>
Dojście `SRWLock` do obiektu.
