---
title: odl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.odl
dev_langs:
- C++
helpviewer_keywords:
- odl attribute
ms.assetid: 75dcb314-b50f-4a63-9180-507ac1bc78f3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fb7525fb57a336defd6d2d50dae4bc0ee988c1ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="odl"></a>odl
Identyfikuje interfejsu jako interfejsu język opisu obiektów (ODL). Nie wymaga kompilatora MIDL **odl** atrybutu; uznaje się tylko w celu zapewnienia zgodności z starsze .odl — pliki.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[odl]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Odl** atrybut C++ ma te same funkcje co [odl](http://msdn.microsoft.com/library/windows/desktop/aa367126) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
  
```  
// cpp_attr_ref_odl.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLIb")];  
  
[odl, oleautomation, dual, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyInterface  
{  
   HRESULT x();  
};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000002")]  
class cmyClass : public IMyInterface  
{  
public:  
   HRESULT x(){}  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|`interface`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   
