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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392001"
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
|[CriticalSection, klasa](criticalsection-class.md)|Reprezentuje obiekt sekcję krytyczną.|
|[Event, Klasa (WRL)](event-class-wrl.md)|Przedstawia zdarzenie.|
|[HandleT, klasa](handlet-class.md)|Reprezentuje uchwyt do obiektu.|
|[HString, klasa](hstring-class.md)|Zapewnia obsługę manipulowania uchwytami HSTRING.|
|[HStringReference, klasa](hstringreference-class.md)|Reprezentuje HSTRING, utworzony na podstawie istniejącego ciągu.|
|[Mutex — Klasa](mutex-class.md)|Reprezentuje obiekt synchronizacji, który wyłącznie kontroluje zasobu udostępnionego.|
|[RoInitializeWrapper, klasa](roinitializewrapper-class.md)|Inicjuje środowisko wykonawcze Windows.|
|[Semaphore, klasa](semaphore-class.md)|Reprezentuje obiekt synchronizacji, który kontroluje zasobu udostępnionego, który może obsługiwać ograniczoną liczbę użytkowników.|
|[SRWLock, klasa](srwlock-class.md)|Reprezentuje kieszeń czytnika/blokadę.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)