---
title: "Criticalsectiontraits — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
dev_langs: C++
helpviewer_keywords: CriticalSectionTraits structure
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 95428e0513193c78f135157b09a354e050014f23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits — Struktura
Specjalizuje się obiekt criticalsection — Obsługa Nieprawidłowa sekcja krytyczna lub funkcję, aby zwolnić sekcja krytyczna.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CriticalSectionTraits;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`Type`|A `typedef` definiuje wskaźnik do sekcja krytyczna. `Type`nie zdefiniowano jako `typedef CRITICAL_SECTION* Type;`.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CriticalSectionTraits::GetInvalidValue — metoda](../windows/criticalsectiontraits-getinvalidvalue-method.md)|Specjalizuje się szablon criticalsection — tak, aby szablon zawsze jest nieprawidłowy.|  
|[CriticalSectionTraits::Unlock — Metoda](../windows/criticalsectiontraits-unlock-method.md)|Specjalizuje się szablon criticalsection —, dzięki czemu obsługuje zwolnić prawo własności obiektu określona sekcja krytyczna.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CriticalSectionTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace Microsoft::WRL::Wrappers::HandleTraits](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)