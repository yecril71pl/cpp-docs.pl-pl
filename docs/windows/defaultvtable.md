---
title: defaultvtable | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.defaultvtable
dev_langs:
- C++
helpviewer_keywords:
- defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 34850646e40ffa9cbd3185b13fdaa93d7c873787
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651443"
---
# <a name="defaultvtable"></a>defaultvtable
Definiuje interfejs jako domyślnym interfejsem obiektu COM vtable.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[ defaultvtable(  
   interface  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *interface*  
 Wyznaczonym interfejsu, który ma być vtable domyślnego dla obiektu COM.  
  
## <a name="remarks"></a>Uwagi  
 **Defaultvtable** atrybut C++ ma taką samą funkcjonalność jak [defaultvtable](http://msdn.microsoft.com/library/windows/desktop/aa366795) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Poniższy kod pokazuje atrybuty dla klasy, która będzie używać **defaultvtable** do określenia domyślnego interfejsu:  
  
```cpp  
// cpp_attr_ref_defaultvtable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI1 {  
   HRESULT x();  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000002")]  
__interface IMyI2 {  
   HRESULT x();  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000003")]  
__interface IMyI3 {  
   HRESULT x();  
};  
  
[coclass, source(IMyI3, IMyI1), default(IMyI3, IMyI2), defaultvtable(IMyI1),  
uuid("00000000-0000-0000-0000-000000000004")]  
class CMyC3 : public IMyI3 {};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, **— struktura**|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|**coclass**|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   