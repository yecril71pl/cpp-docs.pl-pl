---
title: obiekt (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.object
dev_langs:
- C++
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5714d7c3bd029c7b1df636044ed1968f53600848
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="object-c"></a>object (C++)
Określa niestandardowy interfejs.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[object]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy poprzedzających definicję interfejsu **obiektu** atrybut C++ powoduje interfejsu, który ma być umieszczony w pliku .idl jako niestandardowego interfejsu.  
  
 Każdy interfejs oznaczony atrybutem obiektu musi dziedziczyć z **IUnknown**. Ten warunek jest spełniony, jeśli w interfejsach podstawowej dziedziczyć **IUnknown**. Jeśli nie interfejsach podstawowych dziedziczyć **IUnknown**, kompilator spowoduje, że interfejs oznaczony atrybutem **obiektu** pochodzić z **IUnknown**.  
  
## <a name="example"></a>Przykład  
 Zobacz [nonbrowsable —](../windows/nonbrowsable.md) przykład sposobu użycia **obiektu**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|`interface`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   
 [podwójne](../windows/dual.md)   
 [dispinterface](../windows/dispinterface.md)   
 [niestandardowe](../windows/custom-cpp.md)   
 [__interface](../cpp/interface.md)   
