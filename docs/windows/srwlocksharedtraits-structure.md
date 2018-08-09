---
title: Srwlocksharedtraits — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockSharedTraits structure
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c606a1a7d32a02442e767a31543a76a4dccf295e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652477"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits — Struktura
W tym artykule opisano typowe cechy `SRWLock` klasy w trybie blokady udostępniania.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct SRWLockSharedTraits;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`Type`|Synonim dla wskaźnika do [SRWLOCK](../windows/srwlock-class.md) klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SRWLockSharedTraits::GetInvalidValue, metoda](../windows/srwlocksharedtraits-getinvalidvalue-method.md)|Pobiera **srwlocksharedtraits —** obiekt, który zawsze jest nieprawidłowy.|  
|[SRWLockSharedTraits::Unlock, metoda](../windows/srwlocksharedtraits-unlock-method.md)|Zwalnia wyłączną kontrolę określonego `SRWLock` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `SRWLockSharedTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers::HandleTraits, przestrzeń nazw](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)