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
ms.openlocfilehash: 4005f0dc1f75b79650963efc9a6f9f7522bc3395
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476469"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits — Struktura

W tym artykule opisano typowe cechy `SRWLock` klasy w trybie wyłączności blokady.

## <a name="syntax"></a>Składnia

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa   | Opis
------ | --------------------------------------------------------------------------
`Type` | Synonim dla wskaźnika do [SRWLOCK](../windows/srwlock-class.md) klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                        | Opis
----------------------------------------------------------- | --------------------------------------------------------------------
[SRWLockExclusiveTraits::GetInvalidValue](#getinvalidvalue) | Pobiera `SRWLockExclusiveTraits` obiekt, który zawsze jest nieprawidłowy.
[SRWLockExclusiveTraits::Unlock](#unlock)                   | Zwalnia wyłączną kontrolę określonego `SRWLock` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SRWLockExclusiveTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>SRWLockExclusiveTraits::GetInvalidValue

Pobiera `SRWLockExclusiveTraits` obiekt, który zawsze jest nieprawidłowy.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Wartość zwracana

Pusta `SRWLockExclusiveTraits` obiektu.

## <a name="unlock"></a>SRWLockExclusiveTraits::Unlock

Zwalnia wyłączną kontrolę określonego `SRWLock` obiektu.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parametry

*srwlock*<br/>
Dojście do `SRWLock` obiektu.
