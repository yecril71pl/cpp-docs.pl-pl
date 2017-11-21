---
title: "Srwlocksharedtraits — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
dev_langs: C++
helpviewer_keywords: SRWLockSharedTraits structure
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3a044baaa463c91c134137214e9708db8c4dfefb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[SRWLockSharedTraits::GetInvalidValue — metoda](../windows/srwlocksharedtraits-getinvalidvalue-method.md)|Pobiera obiekt srwlocksharedtraits —, który zawsze jest nieprawidłowy.|  
|[SRWLockSharedTraits::Unlock — Metoda](../windows/srwlocksharedtraits-unlock-method.md)|Zwalnia wyłączną kontrolę określonego obiektu srwlock —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `SRWLockSharedTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace Microsoft::WRL::Wrappers::HandleTraits](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)