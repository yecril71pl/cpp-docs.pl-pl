---
title: "last_is — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.last_is
dev_langs:
- C++
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d7a230299a94ba33a142ca44ebc34981f7201ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lastis"></a>last_is
Określa indeks przekazywanych ostatnim elemencie tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ last_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *wyrażenie*  
 Co najmniej jednego wyrażenia języka C. Pusty argument gniazda są dozwolone.  
  
## <a name="remarks"></a>Uwagi  
 **Last_is —** atrybut C++ ma te same funkcje co [last_is —](http://msdn.microsoft.com/library/windows/desktop/aa367066) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Zobacz [first_is —](../windows/first-is.md) przykład sposobu określania sekcji tablicy.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Pole w `struct` lub **Unii**, interfejs parametru, interfejsu — metoda|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atrybuty parametrów](../windows/parameter-attributes.md)   
 [first_is —](../windows/first-is.md)   
 [max_is —](../windows/max-is.md)   
 [length_is —](../windows/length-is.md)   
 [size_is](../windows/size-is.md)   
