---
title: propput | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propput
dev_langs:
- C++
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: af96a6825c88fb479709b2b6138f3fe6286b8b17
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016814"
---
# <a name="propput"></a>propput
Określa funkcję ustawienie właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[propput]  
```  
  
## <a name="remarks"></a>Uwagi  
 **Propput** atrybut C++ ma taką samą funkcjonalność jak [propput](http://msdn.microsoft.com/library/windows/desktop/aa367146) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [możliwej do wiązania](../windows/bindable.md) do użytku przykładowe **propput**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Metoda|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|`propget`, `propputref`|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty metody](../windows/method-attributes.md)   
 [propget](../windows/propget.md)   
 [propputref](../windows/propputref.md)