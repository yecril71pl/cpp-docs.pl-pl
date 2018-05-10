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
ms.openlocfilehash: 17a57ad56402b345aa64e4e4fd02bc57dd7f0321
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="local-c"></a>local (C++)
Gdy jest używany w nagłówku interfejsu, umożliwia przy użyciu kompilatora MIDL jako generator nagłówka. W przypadku poszczególnych funkcji wyznacza procedury lokalnym, dla których są generowane nie klas zastępczych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[local]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 `local` Atrybut C++ ma te same funkcje co [lokalnego](http://msdn.microsoft.com/library/windows/desktop/aa367071) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Zobacz [call_as](../windows/call-as.md) przykład sposobu użycia `local`.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|`interface`, interfejsu — metoda|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|**dispinterface**|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   
 [Atrybuty — metoda](../windows/method-attributes.md)   
 [call_as](../windows/call-as.md)   
