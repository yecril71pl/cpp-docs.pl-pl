---
title: lokalne (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.local
dev_langs:
- C++
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: efa937c1eaabb23fe5a360444f8c2105b735b260
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604203"
---
# <a name="local-c"></a>local (C++)
W przypadku użycia w nagłówku interfejsu, umożliwia kompilatorowi MIDL jako generator nagłówka. W przypadku użycia w poszczególnych funkcji, wyznacza lokalnej procedury, dla którego są generowane nie wycinki.  
  
## <a name="syntax"></a>Składnia  
  
```  
[local]  
```  
  
## <a name="remarks"></a>Uwagi  
 **Lokalnego** atrybut C++ ma taką samą funkcjonalność jak [lokalnego](http://msdn.microsoft.com/library/windows/desktop/aa367071) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Zobacz [call_as](../windows/call-as.md) przykład sposobu użycia **lokalnego**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**interfejs**, interfejs — metoda|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|`dispinterface`|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   
 [Atrybuty metody](../windows/method-attributes.md)   
 [call_as](../windows/call-as.md)   