---
title: "CriticalSectionTraits::GetInvalidValue — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
dev_langs: C++
helpviewer_keywords: GetInvalidValue method
ms.assetid: 665f30a6-ca9c-4968-8c03-8f84e6b2329b
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 67d377ea23c31b9ba7111f139f4c9d2db3ae7004
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="criticalsectiontraitsgetinvalidvalue-method"></a>CriticalSectionTraits::GetInvalidValue — Metoda
Specjalizuje się szablon criticalsection — tak, aby szablon zawsze jest nieprawidłowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
inline static Type GetInvalidValue();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wskaźnik do Nieprawidłowa sekcja krytyczna.  
  
## <a name="remarks"></a>Uwagi  
 *Typu* modyfikator jest zdefiniowany jako `typedef CRITICAL_SECTION* Type;`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [Criticalsectiontraits — struktura](../windows/criticalsectiontraits-structure.md)