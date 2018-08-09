---
title: CriticalSectionTraits::GetInvalidValue, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 01efd9bf3941a5b19e1f0fe6c106d47f1b6e9fcf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642064"
---
# <a name="criticalsectiontraitsgetinvalidvalue-method"></a>CriticalSectionTraits::GetInvalidValue — Metoda
Specjalizuje się **CriticalSection** szablonu, aby szablon zawsze jest nieprawidłowy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline static Type GetInvalidValue();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wskaźnik do Nieprawidłowa sekcja krytycznego.  
  
## <a name="remarks"></a>Uwagi  
 `Type` Modyfikator jest zdefiniowany jako `typedef CRITICAL_SECTION* Type;`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [CriticalSectionTraits, struktura](../windows/criticalsectiontraits-structure.md)