---
title: Microsoft::WRL::Wrappers — Przestrzeń nazw
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: eac85d10351a141ce561da4272d033644128608f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535489"
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
|[CriticalSection, klasa](../windows/criticalsection-class.md)|Reprezentuje obiekt sekcję krytyczną.|
|[Event, Klasa (WRL)](../windows/event-class-wrl.md)|Przedstawia zdarzenie.|
|[HandleT, klasa](../windows/handlet-class.md)|Reprezentuje uchwyt do obiektu.|
|[HString, klasa](../windows/hstring-class.md)|Zapewnia obsługę manipulowania uchwytami HSTRING.|
|[HStringReference, klasa](../windows/hstringreference-class.md)|Reprezentuje HSTRING, utworzony na podstawie istniejącego ciągu.|
|[Mutex — Klasa](../windows/mutex-class.md)|Reprezentuje obiekt synchronizacji, który wyłącznie kontroluje zasobu udostępnionego.|
|[RoInitializeWrapper, klasa](../windows/roinitializewrapper-class.md)|Inicjuje środowisko wykonawcze Windows.|
|[Semaphore, klasa](../windows/semaphore-class.md)|Reprezentuje obiekt synchronizacji, który kontroluje zasobu udostępnionego, który może obsługiwać ograniczoną liczbę użytkowników.|
|[SRWLock, klasa](../windows/srwlock-class.md)|Reprezentuje kieszeń czytnika/blokadę.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)