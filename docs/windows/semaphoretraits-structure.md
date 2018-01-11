---
title: "Semaphoretraits — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
dev_langs: C++
helpviewer_keywords: SemaphoreTraits structure
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 103f02109558d9f301f9f1eec867e9379c102e17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits — Struktura
Definiuje wspólne właściwości obiektu semafora.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct SemaphoreTraits : HANDLENullTraits;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SemaphoreTraits::Unlock, metoda](../windows/semaphoretraits-unlock-method.md)|Kontrola wersji zasobu udostępnionego.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `HANDLENullTraits`  
  
 `SemaphoreTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers::HandleTraits, przestrzeń nazw](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)