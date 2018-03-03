---
title: "Runtimeclassflags — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassFlags structure
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 85eb42c537845d86ce8cf3b1f20db7e9eeffe76f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags — Struktura
Zawiera typ wystąpienia [runtimeclass —](../windows/runtimeclass-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   unsigned int flags  
>  
struct RuntimeClassFlags;  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 A [runtimeclasstype — wyliczenie](../windows/runtimeclasstype-enumeration.md) wartość.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[RuntimeClassFlags::value, stała](../windows/runtimeclassflags-value-constant.md)|Zawiera [runtimeclasstype — wyliczenie](../windows/runtimeclasstype-enumeration.md) wartość.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `RuntimeClassFlags`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)