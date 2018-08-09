---
title: dispinterface | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dispinterface
dev_langs:
- C++
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 18308cc66e2a01aa5e0396f098096ee9d49416bf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644333"
---
# <a name="dispinterface"></a>dispinterface
Przełącza interfejsu w pliku .idl, jako interfejs ekspedycji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[dispinterface]  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy **dispinterface** atrybut C++ poprzedza interfejs, sprawia, że interfejs, który ma być umieszczony wewnątrz bloku biblioteki w pliku .idl wygenerowany.  
  
 O ile nie określono klasy bazowej, interfejs ekspedycji, z której pochodzą z `IDispatch`. Należy określić [identyfikator](../windows/id.md) dla członków interfejs ekspedycji.  
  
 Przykład użycia [dispinterface](http://msdn.microsoft.com/library/windows/desktop/aa366802) w dokumentacji MIDL:  
  
```cpp  
dispinterface helloPro   
   { interface hello; };   
```  
  
 nie jest prawidłowa dla **dispinterface** atrybutu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [możliwej do wiązania](../windows/bindable.md) przykład sposobu użycia **dispinterface**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**interface**|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty w zależności od użycia](../windows/attributes-by-usage.md)   
 [Identyfikator UUID](../windows/uuid-cpp-attributes.md)   
 [Podwójne](../windows/dual.md)   
 [Niestandardowe](../windows/custom-cpp.md)   
 [obiekt](../windows/object-cpp.md)   
 [__interface](../cpp/interface.md)   