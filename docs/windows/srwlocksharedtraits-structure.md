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
ms.openlocfilehash: 6a18edef3fa658608459244143a5e48738f0c3a9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889649"
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