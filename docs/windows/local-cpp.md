---
title: lokalne (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.local
dev_langs: C++
helpviewer_keywords: local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 007d95d5db0785deae08744b46738d7188e4da70
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
