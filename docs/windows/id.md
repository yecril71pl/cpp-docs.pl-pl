---
title: Identyfikator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.id
dev_langs:
- C++
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6c674765a0dfc06648d64a2b3b4e820bb467e700
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882450"
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
 [in](../windows/in-cpp.md)   
 [out](../windows/out-cpp.md)   
