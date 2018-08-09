---
title: propputref | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propputref
dev_langs:
- C++
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d72fa9523b850e5c7d76b587c37b181f21df25c0
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013983"
---
# <a name="propputref"></a>propputref
Określa funkcję ustawienie właściwości, która używa odwołania, a nie wartość.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[propputref]  
```  
  
## <a name="remarks"></a>Uwagi  
 **Propputref** atrybut C++ ma taką samą funkcjonalność jak [propputref](http://msdn.microsoft.com/library/windows/desktop/aa367147) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [możliwej do wiązania](../windows/bindable.md) do użytku przykładowe **propputref**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Metoda|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|`propget`, `propput`|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty metody](../windows/method-attributes.md)   
 [propget](../windows/propget.md)   
 [propput](../windows/propput.md)   