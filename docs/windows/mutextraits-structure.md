---
title: Mutextraits — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
dev_langs:
- C++
helpviewer_keywords:
- MutexTraits structure
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0406ec7938a623be7b16e0535e9d2c0c769f8392
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874593"
---
# <a name="mutextraits-structure"></a>MutexTraits — Struktura
Definiuje typowe cechy [obiektu Mutex](../windows/mutex-class1.md) klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct MutexTraits : HANDLENullTraits;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[MutexTraits::Unlock, metoda](../windows/mutextraits-unlock-method.md)|Zwalnia wyłączną kontrolę zasobu udostępnionego.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `HANDLENullTraits`  
  
 `MutexTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers::HandleTraits, przestrzeń nazw](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)