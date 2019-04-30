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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391975"
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
|[CriticalSectionTraits, struktura](criticalsectiontraits-structure.md)|Specjalizuje się `CriticalSection` obiekt na potrzeby obsługi nieprawidłową sekcję krytyczną lub funkcję, aby zwolnić sekcję krytyczną.|
|[EventTraits, struktura](eventtraits-structure.md)|Definiuje właściwości `Event` dojście do klasy.|
|[FileHandleTraits, struktura](filehandletraits-structure.md)|Definiuje właściwości dojście do pliku.|
|[HANDLENullTraits, struktura](handlenulltraits-structure.md)|Definiuje typowe cechy niezainicjowany uchwyt.|
|[HANDLETraits, struktura](handletraits-structure.md)|Definiuje typowe cechy dojście.|
|[MutexTraits, struktura](mutextraits-structure.md)|Definiuje typowe cechy [Mutex](mutex-class.md) klasy.|
|[SemaphoreTraits, struktura](semaphoretraits-structure.md)|Definiuje typowe cechy obiektu semafora.|
|[SRWLockExclusiveTraits, struktura](srwlockexclusivetraits-structure.md)|W tym artykule opisano typowe cechy `SRWLock` klasy w trybie wyłączności blokady.|
|[SRWLockSharedTraits, struktura](srwlocksharedtraits-structure.md)|W tym artykule opisano typowe cechy `SRWLock` klasy w trybie blokady udostępniania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL::Wrappers, przestrzeń nazw](microsoft-wrl-wrappers-namespace.md)