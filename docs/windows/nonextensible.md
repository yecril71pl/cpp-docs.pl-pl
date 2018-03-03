---
title: "nonextensible — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 31aa2bf8572a1a0e8ed785d55bb6960cfe6cf75e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="nonextensible"></a>nonextensible
Określa, że `IDispatch` implementacji zawiera tylko właściwości i metod wymienionych w opisie interfejsu i nie może zostać rozszerzony o dodatkowe elementy członkowskie w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[nonextensible]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Nonextensible —** atrybut C++ ma te same funkcje co [nonextensible —](http://msdn.microsoft.com/library/windows/desktop/aa367120) MIDL atrybutu.  
  
 Użycie **nonextensible —** wymaga również [oleautomation](../windows/oleautomation.md) atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia użycie jednego **nonextensible —** atrybutu:  
  
```  
// cpp_attr_ref_nonextensible.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export] typedef long HRESULT;  
  
[dual, nonextensible, ms_union, oleautomation,   
uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   HRESULT procedure (int i);   
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|`interface`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|**Podwójna** i **oleautomation**, lub **dispinterface**|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   
