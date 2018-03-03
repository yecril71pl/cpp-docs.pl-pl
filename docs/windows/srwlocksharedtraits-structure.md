---
title: "Srwlocksharedtraits — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockSharedTraits structure
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cadf94f1d336de7bac13572a045e7ac8487013cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits — Struktura
W tym artykule opisano typowe cechy srwlock — klasa w trybie blokady udostępniania.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct SRWLockSharedTraits;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`Type`|Synonim dla wskaźnika do [srwlock —](../windows/srwlock-class.md) klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SRWLockSharedTraits::GetInvalidValue, metoda](../windows/srwlocksharedtraits-getinvalidvalue-method.md)|Pobiera obiekt srwlocksharedtraits —, który zawsze jest nieprawidłowy.|  
|[SRWLockSharedTraits::Unlock, metoda](../windows/srwlocksharedtraits-unlock-method.md)|Zwalnia wyłączną kontrolę określonego obiektu srwlock —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `SRWLockSharedTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers::HandleTraits, przestrzeń nazw](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)