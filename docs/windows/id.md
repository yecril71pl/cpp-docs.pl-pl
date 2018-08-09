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
ms.openlocfilehash: 5a89758933aef4646aaf11d08d7193d48a44f468
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013548"
---
# <a name="id"></a>identyfikator
Określa *dispid* parametr dla funkcji członkowskiej (właściwość lub metodę w interfejsie lub dispinterface).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[ id(  
   dispid  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *identyfikator DISPID*  
 Identyfikator wysyłania dla metody interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 **Identyfikator** atrybut C++ ma taką samą funkcjonalność jak [identyfikator](http://msdn.microsoft.com/library/windows/desktop/aa367040) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [możliwej do wiązania](../windows/bindable.md) przykład sposobu użycia **identyfikator**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Metody interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty metody](../windows/method-attributes.md)   
 [Atrybuty elementów członkowskich danych](../windows/data-member-attributes.md)   
 [DefaultValue](../windows/defaultvalue.md)   
 [in](../windows/in-cpp.md)   
 [out](../windows/out-cpp.md)   