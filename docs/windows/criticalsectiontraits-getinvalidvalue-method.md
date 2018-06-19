---
title: CriticalSectionTraits::GetInvalidValue — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- GetInvalidValue method
ms.assetid: 665f30a6-ca9c-4968-8c03-8f84e6b2329b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d72c9dce0765029ee31e079315baec72afd16a46
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883150"
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
 [CriticalSectionTraits, struktura](../windows/criticalsectiontraits-structure.md)