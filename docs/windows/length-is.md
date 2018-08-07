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
ms.openlocfilehash: 8e0294c7cc118c4014e998ad570d7e1e453ea2c6
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606504"
---
# <a name="lengthis"></a>length_is
Określa liczbę elementów tablicy, które mają być przekazywane.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ length_is(  
   "expression"  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Wyrażenie*  
 Co najmniej jednego wyrażenia języka C. Pusty argument miejsca są dozwolone.  
  
## <a name="remarks"></a>Uwagi  
 **Length_is —** atrybut C++ ma taką samą funkcjonalność jak [length_is —](http://msdn.microsoft.com/library/windows/desktop/aa367068) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Zobacz [first_is —](../windows/first-is.md) przykład sposobu określania część tablicy.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Pole **struktury** lub **Unii**, interfejs parametrów, metody interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Element TypeDef, Enum, Union i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atrybuty parametru](../windows/parameter-attributes.md)   
 [first_is —](../windows/first-is.md)   
 [max_is —](../windows/max-is.md)   
 [last_is —](../windows/last-is.md)   
 [size_is](../windows/size-is.md)   