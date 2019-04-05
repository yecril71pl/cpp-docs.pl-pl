---
title: Microsoft::WRL::Wrappers — Przestrzeń nazw
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: 4b88ad0da31321a696c1238f1c9838d3b3a1c927
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030118"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers — Przestrzeń nazw

Definiuje typy otoki zasobów nabycia jest inicjowania (RAII), które upraszczają Zarządzanie okresem istnienia obiektów, ciągi i uchwyty.

## <a name="syntax"></a>Składnia

```cpp
namespace Microsoft::WRL::Wrappers;
```

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|----------|-----------------|
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[CriticalSection — Klasa](criticalsection-class.md)|Reprezentuje obiekt sekcję krytyczną.|
|[Event — klasa (WRL)](event-class-wrl.md)|Przedstawia zdarzenie.|
|[HandleT — Klasa](handlet-class.md)|Reprezentuje uchwyt do obiektu.|
|[HString — Klasa](hstring-class.md)|Zapewnia obsługę manipulowania uchwytami HSTRING.|
|[HStringReference — Klasa](hstringreference-class.md)|Reprezentuje HSTRING, utworzony na podstawie istniejącego ciągu.|
|[Mutex — Klasa](mutex-class.md)|Reprezentuje obiekt synchronizacji, który wyłącznie kontroluje zasobu udostępnionego.|
|[RoInitializeWrapper — Klasa](roinitializewrapper-class.md)|Inicjuje środowisko wykonawcze Windows.|
|[Semaphore — Klasa](semaphore-class.md)|Reprezentuje obiekt synchronizacji, który kontroluje zasobu udostępnionego, który może obsługiwać ograniczoną liczbę użytkowników.|
|[SRWLock — Klasa](srwlock-class.md)|Reprezentuje kieszeń czytnika/blokadę.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL — Przestrzeń nazw](microsoft-wrl-namespace.md)