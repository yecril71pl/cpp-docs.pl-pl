---
title: Identyfikator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.id
dev_langs:
- C++
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9225a87f32c3c7bf42ca5fc7de98dd0ab8f12639
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="id"></a>identyfikator
Określa `dispid` parametr dla funkcji członkowskiej (właściwości lub metody, w interfejsie lub dispinterface).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ id(  
   dispid  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `dispid`  
 Identyfikator wysyłania dla metody interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 **Identyfikator** atrybut C++ ma te same funkcje co [identyfikator](http://msdn.microsoft.com/library/windows/desktop/aa367040) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [powiązania](../windows/bindable.md) przykład sposobu użycia **identyfikator**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Metody interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty — metoda](../windows/method-attributes.md)   
 [Atrybuty elementów członkowskich danych](../windows/data-member-attributes.md)   
 [Wartość domyślna](../windows/defaultvalue.md)   
 [w](../windows/in-cpp.md)   
 [out](../windows/out-cpp.md)   
