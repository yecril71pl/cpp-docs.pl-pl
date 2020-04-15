---
title: SemaphoreTraits — Struktura
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock method
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
ms.openlocfilehash: 11719576c9fc7b23f4cd318ee1b3ed9ca3f5edaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360740"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits — Struktura

Definiuje wspólne cechy `Semaphore` obiektu.

## <a name="syntax"></a>Składnia

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

Nazwa                               | Opis
---------------------------------- | --------------------------------------
[SemaphoreTraits::Odblokuj](#unlock) | Zwalnia kontrolę nad zasobem udostępnionym.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki::HandleTraits

## <a name="semaphoretraitsunlock"></a><a name="unlock"></a>SemaphoreTraits::Odblokuj

Zwalnia kontrolę nad zasobem udostępnionym.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Dojście `Semaphore` do obiektu.

### <a name="remarks"></a>Uwagi

Jeśli operacja odblokowania `Unlock()` nie powiedzie się, emituje błąd, który wskazuje przyczynę błędu.
