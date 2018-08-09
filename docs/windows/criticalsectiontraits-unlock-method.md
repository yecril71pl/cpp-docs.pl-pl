---
title: CriticalSectionTraits::Unlock, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 8fb382f5-6eda-407e-9673-71d77bda4962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b64f44e2188848a25e607c53171e25aa721e9bc4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641369"
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock — Metoda
Specjalizuje się `CriticalSection` szablonu, tak że obsługuje uwalniający własności obiektu określona sekcja krytycznego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *CS*  
 Wskaźnik do obiektu sekcję krytyczną.  
  
## <a name="remarks"></a>Uwagi  
 `Type` Modyfikator jest zdefiniowany jako `typedef CRITICAL_SECTION* Type;`.  
  
 Aby uzyskać więcej informacji, zobacz **funkcja LeaveCriticalSection** w **funkcji synchronizacji** części dokumentacji interfejsu API Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [CriticalSectionTraits, struktura](../windows/criticalsectiontraits-structure.md)