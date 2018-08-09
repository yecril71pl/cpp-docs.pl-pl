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
ms.openlocfilehash: d6543ada6840b292d6a7b981eefeab41642c42df
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017935"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits — Struktura
W tym artykule opisano typowe cechy `SRWLock` klasy w trybie wyłączności blokady.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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