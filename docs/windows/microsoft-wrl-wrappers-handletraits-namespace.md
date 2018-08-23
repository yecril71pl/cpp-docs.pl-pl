---
title: Namespace Microsoft::WRL::Wrappers::HandleTraits | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
dev_langs:
- C++
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 683759c3bf0b2152ee6fadbb638cd2398daecccd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586132"
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
|[CriticalSectionTraits, struktura](../windows/criticalsectiontraits-structure.md)|Specjalizuje się `CriticalSection` obiekt na potrzeby obsługi nieprawidłową sekcję krytyczną lub funkcję, aby zwolnić sekcję krytyczną.|
|[EventTraits, struktura](../windows/eventtraits-structure.md)|Definiuje właściwości `Event` dojście do klasy.|
|[FileHandleTraits, struktura](../windows/filehandletraits-structure.md)|Definiuje właściwości dojście do pliku.|
|[HANDLENullTraits, struktura](../windows/handlenulltraits-structure.md)|Definiuje typowe cechy niezainicjowany uchwyt.|
|[HANDLETraits, struktura](../windows/handletraits-structure.md)|Definiuje typowe cechy dojście.|
|[MutexTraits, struktura](../windows/mutextraits-structure.md)|Definiuje typowe cechy [Mutex](../windows/mutex-class1.md) klasy.|
|[SemaphoreTraits, struktura](../windows/semaphoretraits-structure.md)|Definiuje typowe cechy obiektu semafora.|
|[SRWLockExclusiveTraits, struktura](../windows/srwlockexclusivetraits-structure.md)|W tym artykule opisano typowe cechy `SRWLock` klasy w trybie wyłączności blokady.|
|[SRWLockSharedTraits, struktura](../windows/srwlocksharedtraits-structure.md)|W tym artykule opisano typowe cechy `SRWLock` klasy w trybie blokady udostępniania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)