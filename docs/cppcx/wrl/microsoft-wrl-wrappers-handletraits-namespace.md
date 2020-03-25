---
title: Microsoft::WRL::Wrappers::HandleTraits — Przestrzeń nazw
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: b19cc426fc7c1b4fc6ec0638730d59998f8c108a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213736"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits — Przestrzeń nazw

Opisuje charakterystykę typowych typów zasobów opartych na obsłudze.

## <a name="syntax"></a>Składnia

```cpp
namespace Microsoft::WRL::Wrappers::HandleTraits;
```

## <a name="members"></a>Members

### <a name="structures"></a>Struktury

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CriticalSectionTraits, struktura](criticalsectiontraits-structure.md)|Wyspecjalizowano obiekt `CriticalSection` do obsługi nieprawidłowej sekcji krytycznej lub funkcji w celu wydania sekcji krytycznej.|
|[EventTraits, struktura](eventtraits-structure.md)|Definiuje charakterystykę dojścia klasy `Event`.|
|[FileHandleTraits, struktura](filehandletraits-structure.md)|Definiuje charakterystykę dojścia do pliku.|
|[HANDLENullTraits, struktura](handlenulltraits-structure.md)|Definiuje typowe cechy niezainicjowanego dojścia.|
|[HANDLETraits, struktura](handletraits-structure.md)|Definiuje typowe cechy dojścia.|
|[MutexTraits, struktura](mutextraits-structure.md)|Definiuje typowe cechy klasy [mutex](mutex-class.md) .|
|[SemaphoreTraits, struktura](semaphoretraits-structure.md)|Definiuje typowe cechy obiektu semafora.|
|[SRWLockExclusiveTraits, struktura](srwlockexclusivetraits-structure.md)|Opisuje typowe cechy klasy `SRWLock` w trybie blokady wyłącznej.|
|[SRWLockSharedTraits, struktura](srwlocksharedtraits-structure.md)|Opisuje typowe cechy klasy `SRWLock` w trybie blokady udostępnionej.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers. h

**Przestrzeń nazw:** Microsoft:: WRL:: otoki

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers, przestrzeń nazw](microsoft-wrl-wrappers-namespace.md)
