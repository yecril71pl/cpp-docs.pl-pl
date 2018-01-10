---
title: "CriticalSectionTraits::Unlock — Metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
dev_langs: C++
helpviewer_keywords: Unlock method
ms.assetid: 8fb382f5-6eda-407e-9673-71d77bda4962
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f9880364c24b1e2e5889e9e9e2666683c2237f7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock — Metoda
Specjalizuje się szablon criticalsection —, dzięki czemu obsługuje zwolnić prawo własności obiektu określona sekcja krytyczna.  
  
## <a name="syntax"></a>Składnia  
  
```  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cs`  
 Wskaźnik do obiektu sekcja krytyczna.  
  
## <a name="remarks"></a>Uwagi  
 *Typu* modyfikator jest zdefiniowany jako `typedef CRITICAL_SECTION* Type;`.  
  
 Aby uzyskać więcej informacji, zobacz "Funkcja LeaveCriticalSection" w sekcji "Funkcje synchronizacji" w dokumentacji interfejsu API systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [CriticalSectionTraits, struktura](../windows/criticalsectiontraits-structure.md)