---
title: Srwlockexclusivetraits — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockExclusiveTraits structure
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 49f1f50b3fa9e34da8831c1cec138b6aefec27a5
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649276"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits — Struktura
W tym artykule opisano typowe cechy `SRWLock` klasy w trybie wyłączności blokady.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct SRWLockExclusiveTraits;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`Type`|Synonim dla wskaźnika do [SRWLOCK](../windows/srwlock-class.md) klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SRWLockExclusiveTraits::GetInvalidValue, metoda](../windows/srwlockexclusivetraits-getinvalidvalue-method.md)|Pobiera **srwlockexclusivetraits —** obiekt, który zawsze jest nieprawidłowy.|  
|[SRWLockExclusiveTraits::Unlock, metoda](../windows/srwlockexclusivetraits-unlock-method.md)|Zwalnia wyłączną kontrolę określonego `SRWLock` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `SRWLockExclusiveTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers::HandleTraits, przestrzeń nazw](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)