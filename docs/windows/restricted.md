---
title: ograniczone | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.restricted
dev_langs:
- C++
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e1d688d4ebca5d2cc01901f5fe1afaa4536b71bb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="restricted"></a>restricted
Określa, czy członek modułu, interfejsem lub dispinterface nie może być wywoływana arbitralnie.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ restricted(  
   interfaces  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `interfaces`  
 Jeden lub więcej interfejsów, które mogą nie być wywoływana arbitralnie w obiekcie COM. Ten parametr jest prawidłowy tylko po zastosowaniu do klasy.  
  
## <a name="remarks"></a>Uwagi  
 **Ograniczeniami** atrybut C++ ma te same funkcje co [ograniczeniami](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia **ograniczeniami** atrybutu:  
  
```  
// cpp_attr_ref_restricted.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000002")]  
__interface b  
{  
};  
  
[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]  
class c : public a, public b  
{  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Metody interfejsu `interface`, **klasy**, `struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|**coclass** (gdy jest stosowany do **klasy** lub `struct`)|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   
 [Atrybuty metody](../windows/method-attributes.md)   
