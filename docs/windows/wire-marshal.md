---
title: wire_marshal — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.wire_marshal
dev_langs:
- C++
helpviewer_keywords:
- wire_marshal attribute
ms.assetid: 244f9d72-776d-4ebd-b60a-cee600a126b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4c13889c15476ff263658d7b5b4024e7a5deebe5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890216"
---
# <a name="wiremarshal"></a>wire_marshal
Określa typ danych, który będzie używany do przesłania zamiast typu dane specyficzne dla aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[wire_marshal]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Wire_marshal —** atrybut C++ ma te same funkcje co [wire_marshal —](http://msdn.microsoft.com/library/windows/desktop/aa367309) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia korzystanie z **wire_marshal —**:  
  
```  
// cpp_attr_ref_wire_marshal.cpp  
// compile with: /LD  
#include "windows.h"  
[module(name="MyLibrary")];  
  
[export, public] typedef unsigned long _FOUR_BYTE_DATA;  
  
[export] typedef struct _TWO_X_TWO_BYTE_DATA {  
   unsigned short low;  
   unsigned short high;  
} TWO_X_TWO_BYTE_DATA ;  
  
[export, wire_marshal(TWO_X_TWO_BYTE_DATA)] typedef _FOUR_BYTE_DATA FOUR_BYTE_DATA;  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|`typedef`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)   
