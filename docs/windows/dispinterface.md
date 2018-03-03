---
title: dispinterface | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.dispinterface
dev_langs:
- C++
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cf7fb54b4059bc56aea967f03b9e4c2874f84e82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
 [podwójne](../windows/dual.md)   
 [niestandardowe](../windows/custom-cpp.md)   
 [obiekt](../windows/object-cpp.md)   
 [__interface](../cpp/interface.md)   
