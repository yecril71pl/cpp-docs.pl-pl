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
ms.openlocfilehash: b114d067249e78d7fb935e473cc3cc952c76fe02
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878037"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits — Przestrzeń nazw
Opisuje właściwości popularnych typów zasobów na podstawie dojścia.  
  
## <a name="syntax"></a>Składnia  
  
```  
namespace Microsoft::WRL::Wrappers::HandleTraits;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="structures"></a>Struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CriticalSectionTraits, struktura](../windows/criticalsectiontraits-structure.md)|Specjalizuje się `CriticalSection` obiektu do obsługi Nieprawidłowa sekcja krytyczna lub funkcję, aby zwolnić sekcja krytyczna.|  
|[EventTraits, struktura](../windows/eventtraits-structure.md)|Definiuje właściwości `Event` dojście do klasy.|  
|[FileHandleTraits, struktura](../windows/filehandletraits-structure.md)|Definiuje właściwości dojście do pliku.|  
|[HANDLENullTraits, struktura](../windows/handlenulltraits-structure.md)|Definiuje wspólne cechy niezainicjowany uchwyt.|  
|[HANDLETraits, struktura](../windows/handletraits-structure.md)|Definiuje wspólne cechy dojścia.|  
|[MutexTraits, struktura](../windows/mutextraits-structure.md)|Definiuje typowe cechy [obiektu Mutex](../windows/mutex-class1.md) klasy.|  
|[SemaphoreTraits, struktura](../windows/semaphoretraits-structure.md)|Definiuje wspólne właściwości obiektu semafora.|  
|[SRWLockExclusiveTraits, struktura](../windows/srwlockexclusivetraits-structure.md)|W tym artykule opisano typowe cechy `SRWLock` klasy w trybie blokady na wyłączność.|  
|[SRWLockSharedTraits, struktura](../windows/srwlocksharedtraits-structure.md)|W tym artykule opisano typowe cechy `SRWLock` klasy w trybie blokady udostępniania.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)