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
ms.openlocfilehash: e7bd2e5d0993c8e4be7223d98ffb1dbec14cbb74
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502950"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits — Struktura

Definiuje typowe cechy `Semaphore` obiektu.

## <a name="syntax"></a>Składnia

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

Nazwa                               | Opis
---------------------------------- | --------------------------------------
[SemaphoreTraits::Unlock](#unlock) | Kontrola wersji zasobu udostępnionego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="unlock"></a>SemaphoreTraits::Unlock

Kontrola wersji zasobu udostępnionego.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Dojście do `Semaphore` obiektu.

### <a name="remarks"></a>Uwagi

W przypadku operacji odblokowania kończy się niepowodzeniem, `Unlock()` emituje komunikat o błędzie wskazujący przyczynę błędu.
