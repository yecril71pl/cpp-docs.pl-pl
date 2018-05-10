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
ms.openlocfilehash: 10f398e83650dc63c002801ac999816e48f7bdd4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="dispinterface"></a>dispinterface
Umieszcza interfejsu w pliku .idl jako interfejs wysyłania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[dispinterface]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy **dispinterface** atrybutu C++ poprzedza interfejs, powoduje interfejsu, który ma być umieszczony wewnątrz bloku biblioteki w pliku .idl wygenerowany.  
  
 Jeśli nie podasz klasy podstawowej, interfejs wysyłania będzie dziedziczyć `IDispatch`. Należy określić [identyfikator](../windows/id.md) dla elementów członkowskich interfejsu wysyłania.  
  
 Przykład użycia [dispinterface](http://msdn.microsoft.com/library/windows/desktop/aa366802) w dokumentacji MIDL:  
  
```  
dispinterface helloPro   
   { interface hello; };   
```  
  
 nie jest prawidłowa dla **dispinterface** atrybutu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [powiązania](../windows/bindable.md) przykład sposobu użycia **dispinterface**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|`interface`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|**Podwójna**, **obiektu**, **oleautomation**, `local`, **ms_union —**|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty w zależności od użycia](../windows/attributes-by-usage.md)   
 [Identyfikator UUID](../windows/uuid-cpp-attributes.md)   
 [Podwójny](../windows/dual.md)   
 [Niestandardowe](../windows/custom-cpp.md)   
 [Obiekt](../windows/object-cpp.md)   
 [__interface](../cpp/interface.md)   
