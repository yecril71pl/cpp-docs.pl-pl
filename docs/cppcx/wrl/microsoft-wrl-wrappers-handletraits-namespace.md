---
title: Microsoft::WRL::Wrappers::HandleTraits — Przestrzeń nazw
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: 6ed8156b6a0e71d40d1579fc9a33912f698e1773
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030397"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits — Przestrzeń nazw

W tym artykule opisano charakterystyki popularnych typów zasobów opartych na dojście.

## <a name="syntax"></a>Składnia

```cpp
namespace Microsoft::WRL::Wrappers::HandleTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="structures"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[CriticalSectionTraits — Struktura](criticalsectiontraits-structure.md)|Specjalizuje się `CriticalSection` obiekt na potrzeby obsługi nieprawidłową sekcję krytyczną lub funkcję, aby zwolnić sekcję krytyczną.|
|[EventTraits — Struktura](eventtraits-structure.md)|Definiuje właściwości `Event` dojście do klasy.|
|[FileHandleTraits — Struktura](filehandletraits-structure.md)|Definiuje właściwości dojście do pliku.|
|[HANDLENullTraits — Struktura](handlenulltraits-structure.md)|Definiuje typowe cechy niezainicjowany uchwyt.|
|[HANDLETraits — Struktura](handletraits-structure.md)|Definiuje typowe cechy dojście.|
|[MutexTraits — Struktura](mutextraits-structure.md)|Definiuje typowe cechy [Mutex](mutex-class.md) klasy.|
|[SemaphoreTraits — Struktura](semaphoretraits-structure.md)|Definiuje typowe cechy obiektu semafora.|
|[SRWLockExclusiveTraits — Struktura](srwlockexclusivetraits-structure.md)|W tym artykule opisano typowe cechy `SRWLock` klasy w trybie wyłączności blokady.|
|[SRWLockSharedTraits — Struktura](srwlocksharedtraits-structure.md)|W tym artykule opisano typowe cechy `SRWLock` klasy w trybie blokady udostępniania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL::Wrappers — Przestrzeń nazw](microsoft-wrl-wrappers-namespace.md)