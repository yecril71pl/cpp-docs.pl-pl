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
ms.openlocfilehash: deebac1516724469882391c3c856a9ed7a588c88
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018981"
---
# <a name="mutextraits-structure"></a>MutexTraits — Struktura
Definiuje typowe cechy [Mutex](../windows/mutex-class1.md) klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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