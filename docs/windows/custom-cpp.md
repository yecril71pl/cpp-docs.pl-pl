---
title: niestandardowe (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.custom
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7222d7021665a76c7e087033f5152d2836008caa
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460935"
---
# <a name="custom-c"></a>custom (C++)
Definiuje metadanych dla obiektu w bibliotece typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ custom(  
   uuid,   
   value  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *uuid*  
 Unikatowy identyfikator.  
  
 *value*  
 Wartość, które można umieścić w wariant.  
  
## <a name="remarks"></a>Uwagi  
 **Niestandardowe** atrybut C++ spowoduje, że informacje, aby zostać umieszczone w bibliotece typów. Należy to narzędzie, które odczytuje wartość niestandardowej z biblioteki typów.  
  
 **Niestandardowe** atrybut ma taką samą funkcjonalność jak [niestandardowe](http://msdn.microsoft.com/library/windows/desktop/aa366766) atrybutów w MIDL.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|COM bez **interfejsu**, **klasy**, **wyliczenia**s, `idl_module` metod, składowych interfejsu i parametry interfejsu **typedef**s, **Unii**s, **struktury**s|  
|**Powtarzalne**|Tak|  
|**Wymaganych atrybutów**|**Klasa coclass** (jeśli jest używany w klasie)|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Oddzielne atrybuty](../windows/stand-alone-attributes.md)   
 [Element TypeDef, Enum, Union i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atrybuty parametru](../windows/parameter-attributes.md)   
 [Atrybuty metody](../windows/method-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   