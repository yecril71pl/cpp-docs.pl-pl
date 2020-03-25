---
title: Microsoft::WRL::Wrappers — Przestrzeń nazw
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: ece26b3f9928d44a593de830cf8a25c57e4c2d89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213749"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers — Przestrzeń nazw

Definiuje typy otoki inicjującej pozyskiwanie zasobów (RAII), które upraszczają zarządzanie obiektami, ciągami i uchwytami.

## <a name="syntax"></a>Składnia

```cpp
namespace Microsoft::WRL::Wrappers;
```

## <a name="members"></a>Members

### <a name="typedefs"></a>Typedefs

|Name (Nazwa)|Opis|
|----------|-----------------|
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|

### <a name="classes"></a>Klasy

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CriticalSection, klasa](criticalsection-class.md)|Reprezentuje obiekt sekcji krytycznej.|
|[Event, Klasa (WRL)](event-class-wrl.md)|Reprezentuje zdarzenie.|
|[HandleT, klasa](handlet-class.md)|Reprezentuje dojście do obiektu.|
|[HString, klasa](hstring-class.md)|Zapewnia obsługę manipulowania dojściami HSTRING.|
|[HStringReference, klasa](hstringreference-class.md)|Reprezentuje element HSTRING, który jest tworzony na podstawie istniejącego ciągu.|
|[Mutex — Klasa](mutex-class.md)|Reprezentuje obiekt synchronizacji, który kontroluje wyłącznie zasób udostępniony.|
|[RoInitializeWrapper, klasa](roinitializewrapper-class.md)|Inicjuje środowisko wykonawcze systemu Windows.|
|[Semaphore, klasa](semaphore-class.md)|Reprezentuje obiekt synchronizacji, który kontroluje zasób udostępniony, który może obsługiwać ograniczoną liczbę użytkowników.|
|[SRWLock, klasa](srwlock-class.md)|Przedstawia cienkią blokadę czytnika/składnika zapisywania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers. h

**Przestrzeń nazw:** Microsoft:: WRL:: otoki

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)
