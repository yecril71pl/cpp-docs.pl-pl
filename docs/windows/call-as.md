---
title: call_as | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.call_as
dev_langs:
- C++
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8fb431c6aad10f7e974ed139ddf83cfb0a58d30a
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465873"
---
# <a name="callas"></a>call_as
Włącza [lokalnego](../windows/local-cpp.md) funkcji, które mają być mapowane na funkcję zdalną, więc, że po wywołaniu funkcji zdalnego jest wywoływana funkcja lokalna.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ call_as(  
   function  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *— Funkcja*  
 Funkcja lokalna, który ma być wywoływana, gdy zostanie wywołana funkcja zdalnego.  
  
## <a name="remarks"></a>Uwagi  
 **Call_as** atrybut C++ ma taką samą funkcjonalność jak [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Poniższy kod pokazuje, jak można użyć **call_as** na mapowanie funkcji nonremotable (**f1**) do funkcji może być zastosowana zdalnie (**Remf1**):  
  
```cpp  
// cpp_attr_ref_call_as.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
[dual, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMInterface {  
   [local] HRESULT f1 ( int i );  
   [call_as(f1)] HRESULT Remf1 ( int i );   
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Metody interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty metody](../windows/method-attributes.md)   
 [lokalne](../windows/local-cpp.md)   