---
title: defaultcollelem — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.defaultcollelem
dev_langs:
- C++
helpviewer_keywords:
- defaultcollelem attribute
ms.assetid: 3dbbd293-8b83-4f70-a36b-64cc1d0b6713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 58038fdb621ca8d31ace1f756e5f3dc122af06b1
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644963"
---
# <a name="defaultcollelem"></a>defaultcollelem
Używane do optymalizacji kodu języka Visual Basic.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[defaultcollelem]  
```  
  
## <a name="remarks"></a>Uwagi  
 **Defaultcollelem —** atrybut C++ ma taką samą funkcjonalność jak [defaultcollelem —](http://msdn.microsoft.com/library/windows/desktop/aa366792) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia metodę interfejsu przy użyciu **defaultcollelem —** atrybutu:  
  
```cpp  
// cpp_attr_ref_defaultcollelem.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyForm   
{     
   [propget, id(1), bindable, defaultcollelem, displaybind,   
   defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);  
   [propput, id(1), bindable, defaultcollelem, displaybind,   
   defaultbind, requestedit] HRESULT P1([in] long nSize);  
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
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty metody](../windows/method-attributes.md)   