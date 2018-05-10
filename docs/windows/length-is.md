---
title: length_is — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.length_is
dev_langs:
- C++
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6d41c2c4747f69b5ddfae4cd5863c072cd2316ec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="lengthis"></a>length_is
Określa liczbę elementów tablicy ma zostać przesłany.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ length_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *wyrażenie*  
 Co najmniej jednego wyrażenia języka C. Pusty argument gniazda są dozwolone.  
  
## <a name="remarks"></a>Uwagi  
 **Length_is —** atrybut C++ ma te same funkcje co [length_is —](http://msdn.microsoft.com/library/windows/desktop/aa367068) MIDL atrybutu.  
  
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
 [last_is —](../windows/last-is.md)   
 [size_is](../windows/size-is.md)   
