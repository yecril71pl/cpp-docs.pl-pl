---
title: Namespace Microsoft::WRL::Wrappers::HandleTraits | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits
dev_langs: C++
helpviewer_keywords: HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3369f7b9264c7b0fd0bfbb9f137278a9f53848d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[Criticalsectiontraits — struktura](../windows/criticalsectiontraits-structure.md)|Specjalizuje się `CriticalSection` obiektu do obsługi Nieprawidłowa sekcja krytyczna lub funkcję, aby zwolnić sekcja krytyczna.|  
|[Eventtraits — struktura](../windows/eventtraits-structure.md)|Definiuje właściwości `Event` dojście do klasy.|  
|[Filehandletraits — struktura](../windows/filehandletraits-structure.md)|Definiuje właściwości dojście do pliku.|  
|[Handlenulltraits — struktura](../windows/handlenulltraits-structure.md)|Definiuje wspólne cechy niezainicjowany uchwyt.|  
|[Handletraits — struktura](../windows/handletraits-structure.md)|Definiuje wspólne cechy dojścia.|  
|[Mutextraits — struktura](../windows/mutextraits-structure.md)|Definiuje typowe cechy [obiektu Mutex](../windows/mutex-class1.md) klasy.|  
|[Semaphoretraits — struktura](../windows/semaphoretraits-structure.md)|Definiuje wspólne właściwości obiektu semafora.|  
|[Srwlockexclusivetraits — struktura](../windows/srwlockexclusivetraits-structure.md)|W tym artykule opisano typowe cechy `SRWLock` klasy w trybie blokady na wyłączność.|  
|[Srwlocksharedtraits — struktura](../windows/srwlocksharedtraits-structure.md)|W tym artykule opisano typowe cechy `SRWLock` klasy w trybie blokady udostępniania.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: wrappers — Namespace](../windows/microsoft-wrl-wrappers-namespace.md)