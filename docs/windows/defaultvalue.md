---
title: DefaultValue | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.defaultvalue
dev_langs:
- C++
helpviewer_keywords:
- defaultvalue attribute
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: deda09913f2774a2b3b246a285df0c8b6f1c62eb
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652828"
---
# <a name="defaultvalue"></a>defaultvalue
Umożliwia określenie wartości domyślnej dla typizowany parametr opcjonalny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[ defaultvalue= value ]  
```  
  
### <a name="parameters"></a>Parametry  
 *value*  
 Wartość domyślna parametru.  
  
## <a name="remarks"></a>Uwagi  
 **Defaultvalue** atrybut C++ ma taką samą funkcjonalność jak [defaultvalue](http://msdn.microsoft.com/library/windows/desktop/aa366793) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia metodę interfejsu przy użyciu **defaultvalue** atrybutu:  
  
```cpp  
// cpp_attr_ref_defaultvalue.cpp  
// compile with: /LD  
#include <windows.h>  
  
[export] typedef long HRESULT;  
[export, ptr, string] typedef unsigned char * MY_STRING_TYPE;  
  
[  uuid("479B29EE-9A2C-11D0-B696-00A0C903487A"),  
   dual, oleautomation,  
   helpstring("IFireTabCtrl Interface"),  
   helpcontext(122), pointer_default(unique) ]  
  
__interface IFireTabCtrl : IDispatch {  
   [bindable, propget] HRESULT get_Size([out, retval, defaultvalue("33")] long *nSize);  
   [bindable, propput] HRESULT put_Size([in] int nSize);  
};  
  
[ module(name="ATLFIRELib", uuid="479B29E1-9A2C-11D0-B696-00A0C903487A",  
      version="1.0", helpstring="ATLFire 1.0 Type Library") ];  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Parametr interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty parametru](../windows/parameter-attributes.md)   
 [limit](../windows/out-cpp.md)   
 [retval](../windows/retval.md)   
 [in](../windows/in-cpp.md)   
 [pointer_default —](../windows/pointer-default.md)   
 [unique](../windows/unique-cpp.md)   