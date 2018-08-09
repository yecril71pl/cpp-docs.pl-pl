---
title: max_is — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.max_is
dev_langs:
- C++
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2799039aa2c198bcea3784876d8299fcaec59b20
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012452"
---
# <a name="maxis"></a>max_is
Określa maksymalną wartość indeksu prawidłową tablicą.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[ max_is(  
   "expression"  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Wyrażenie*  
 Co najmniej jednego wyrażenia języka C. Pusty argument miejsca są dozwolone.  
  
## <a name="remarks"></a>Uwagi  
 **Max_is —** atrybut C++ ma taką samą funkcjonalność jak [max_is —](http://msdn.microsoft.com/library/windows/desktop/aa367074) atrybutów w MIDL.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Pole **struktury** lub **Unii**, interfejs parametrów, metody interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|**size_is**|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [first_is —](../windows/first-is.md) przykład sposobu określania część tablicy.  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Element TypeDef, Enum, Union i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atrybuty parametru](../windows/parameter-attributes.md)   
 [first_is —](../windows/first-is.md)   
 [last_is —](../windows/last-is.md)   
 [length_is —](../windows/length-is.md)   
 [size_is](../windows/size-is.md)   