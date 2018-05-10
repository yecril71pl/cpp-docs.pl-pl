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
ms.openlocfilehash: 68707ea7e00665d12165c7838b1a2ad3440f944d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="callas"></a>call_as
Umożliwia [lokalnego](../windows/local-cpp.md) funkcji można mapować na funkcję zdalną, tak aby po wywołaniu funkcji zdalnego jest wywoływana funkcja lokalna.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ call_as(  
   function  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *Funkcja*  
 Funkcja lokalna, która ma być wywoływana po wywołaniu funkcji zdalnego.  
  
## <a name="remarks"></a>Uwagi  
 **Call_as** atrybut C++ ma te same funkcje co [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób korzystania **call_as** na mapowanie funkcji nonremotable (**f1**) do funkcji może być zastosowana zdalnie (**Remf1**):  
  
```  
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
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Metody interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty — metoda](../windows/method-attributes.md)   
 [lokalne](../windows/local-cpp.md)   
