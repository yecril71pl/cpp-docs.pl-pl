---
title: SRWLockExclusiveTraits — Struktura
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock method
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
ms.openlocfilehash: eb7b30915d6061e8470601df33fecec310d1bbca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374305"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits — Struktura

Opisuje typowe cechy `SRWLock` klasy w trybie blokady wyłączności.

## <a name="syntax"></a>Składnia

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa   | Opis
------ | --------------------------------------------------------------------------
`Type` | Synonim wskaźnika do klasy [SRWLOCK.](srwlock-class.md)

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                        | Opis
----------------------------------------------------------- | --------------------------------------------------------------------
[SRWLockExclusiveTraits::GetInvalidValue](#getinvalidvalue) | Pobiera obiekt, `SRWLockExclusiveTraits` który jest zawsze nieprawidłowy.
[SRWLockExclusiveTraits::Odblokuj](#unlock)                   | Zwalnia wyłączną kontrolę `SRWLock` nad określonym obiektem.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SRWLockExclusiveTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki::HandleTraits

## <a name="srwlockexclusivetraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>SRWLockExclusiveTraits::GetInvalidValue

Pobiera obiekt, `SRWLockExclusiveTraits` który jest zawsze nieprawidłowy.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Wartość zwracana

Pusty `SRWLockExclusiveTraits` obiekt.

## <a name="srwlockexclusivetraitsunlock"></a><a name="unlock"></a>SRWLockExclusiveTraits::Odblokuj

Zwalnia wyłączną kontrolę `SRWLock` nad określonym obiektem.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parametry

*Srwlock*<br/>
Dojście `SRWLock` do obiektu.
