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
ms.openlocfilehash: 078ec4a1fa1af6c4660ff1171ab1b671ee9872f4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Criticalsectiontraits — struktura](../windows/criticalsectiontraits-structure.md)