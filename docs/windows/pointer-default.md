---
title: pointer_default — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pointer_default
dev_langs:
- C++
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 562bc3ebd0c80423eb94d2bc328f72aed8e67985
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604391"
---
# <a name="pointerdefault"></a>pointer_default
Określa domyślny atrybut wskaźnik dla wszystkich wskaźników, z wyjątkiem wskaźniki najwyższego poziomu, które pojawiają się listami parametrów.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ pointer_default(  
   value  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *value*  
 Wartość, która opisuje typ wskaźnika: **ptr**, **ref**, lub **unikatowy**.  
  
## <a name="remarks"></a>Uwagi  
 **Pointer_default —** atrybut C++ ma taką samą funkcjonalność jak [pointer_default —](http://msdn.microsoft.com/library/windows/desktop/aa367141) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [defaultvalue](../windows/defaultvalue.md) do użytku przykładowe **pointer_default —**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**interface**|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   