---
title: Criticalsectiontraits — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
dev_langs:
- C++
helpviewer_keywords:
- CriticalSectionTraits structure
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 149cb7fba3d0754e47ac656c137af2d9bf759f1a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642194"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits — Struktura
Specjalizuje się `CriticalSection` obiekt na potrzeby obsługi nieprawidłową sekcję krytyczną lub funkcję, aby zwolnić sekcję krytyczną.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CriticalSectionTraits;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`Type`|A **typedef** definiujący wskaźnikiem na sekcję krytyczną. `Type` jest zdefiniowany jako `typedef CRITICAL_SECTION* Type;`.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CriticalSectionTraits::GetInvalidValue, metoda](../windows/criticalsectiontraits-getinvalidvalue-method.md)|Specjalizuje się `CriticalSection` szablonu, aby szablon zawsze jest nieprawidłowy.|  
|[CriticalSectionTraits::Unlock, metoda](../windows/criticalsectiontraits-unlock-method.md)|Specjalizuje się `CriticalSection` szablonu, tak że obsługuje uwalniający własności obiektu określona sekcja krytycznego.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CriticalSectionTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers::HandleTraits, przestrzeń nazw](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)