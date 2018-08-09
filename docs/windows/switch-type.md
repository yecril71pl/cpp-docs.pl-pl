---
title: switch_type — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_type
dev_langs:
- C++
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f79aa2683948d54f900c92304cdff29647819a74
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650599"
---
# <a name="switchtype"></a>switch_type
Określa typ zmiennej używanej jako discriminant Unii.  
  
## <a name="syntax"></a>Składnia  
  
```  
[switch_type(  
type  
}]  
```  
  
### <a name="parameters"></a>Parametry  
 *Typ*  
 Typ przełącznika może być typu Liczba całkowita, znaku, wartość logiczna lub wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
 **Switch_type —** atrybut C++ ma taką samą funkcjonalność jak [switch_type —](http://msdn.microsoft.com/library/windows/desktop/aa367276) atrybutów w MIDL.  
  
 Atrybuty C++ nie obsługują [hermetyzowane unie](http://msdn.microsoft.com/library/windows/desktop/aa366811). [Unie nonencapsulated](http://msdn.microsoft.com/library/windows/desktop/aa367119) są obsługiwane tylko w następującej postaci:  
  
```cpp  
// cpp_attr_ref_switch_type.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLibrary")];  
[ export ]  
struct SizedValue2 {  
   [switch_type("char"), switch_is(kind)] union {  
      [case(1), string]  
         wchar_t* wval;  
      [default, string]  
         char* val;  
   };  
   char kind;  
};  
```  
  
## <a name="example"></a>Przykład  
 Zobacz [przypadek](../windows/case-cpp.md) przykład użycie próbki **switch_type —**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**Element TypeDef**|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Element TypeDef, Enum, Union i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   