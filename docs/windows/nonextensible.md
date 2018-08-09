---
title: nonextensible | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 812f5e2462236faef1b2b13d5fb25320319e773e
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015732"
---
# <a name="nonextensible"></a>nonextensible
Określa, że `IDispatch` wdrożenia zawiera tylko właściwości i metod wymienionych w opisie interfejsu i nie można rozszerzyć za pomocą dodatkowe elementy członkowskie w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[nonextensible]  
```  
  
## <a name="remarks"></a>Uwagi  
 **Nonextensible** atrybut C++ ma taką samą funkcjonalność jak [nonextensible](http://msdn.microsoft.com/library/windows/desktop/aa367120) atrybutów w MIDL.  
  
 Korzystanie z **nonextensible** wymaga również [oleautomation —](../windows/oleautomation.md) atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod demonstruje jedno użycie **nonextensible** atrybutu:  
  
```cpp  
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
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**interface**|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|`dual` i `oleautomation`, lub `dispinterface`|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   