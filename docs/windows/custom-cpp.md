---
title: niestandardowe (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.custom
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e55fd4ad47470a86a0a3d61cc847c20fb21768e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="custom-c"></a>custom (C++)
Definiuje metadanych obiektu w bibliotece typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ custom(  
   uuid,   
   value  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *Identyfikator UUID*  
 Unikatowy identyfikator.  
  
 *value*  
 Wartość, która może znajdować się w typ variant.  
  
## <a name="remarks"></a>Uwagi  
 **Niestandardowych** atrybutu C++ spowoduje, że informacje na umieszczenie w bibliotece typów. Konieczne będzie narzędzie, które odczytuje niestandardowej wartości z biblioteki typów.  
  
 **Niestandardowych** atrybut ma te same funkcje co [niestandardowych](http://msdn.microsoft.com/library/windows/desktop/aa366766) MIDL atrybutu.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Inne niż COM `interface`, **klasy**, `enum`s, `idl_module` metod, elementy członkowskie interfejsu, parametry interfejsu `typedef`s, **Unii**s, `struct`s|  
|**Powtarzalne**|Tak|  
|**Wymaganych atrybutów**|**coclass** (jeśli jest używany dla klasy)|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Oddzielne atrybuty](../windows/stand-alone-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atrybuty parametrów](../windows/parameter-attributes.md)   
 [Atrybuty — metoda](../windows/method-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   
