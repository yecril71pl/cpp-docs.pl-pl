---
title: obiekt (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.object
dev_langs:
- C++
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 601d67fb48f0ae826474d33e7dca0fbffff9478c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879711"
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
 [Podwójny](../windows/dual.md)   
 [Dispinterface](../windows/dispinterface.md)   
 [Niestandardowe](../windows/custom-cpp.md)   
 [__interface](../cpp/interface.md)   
