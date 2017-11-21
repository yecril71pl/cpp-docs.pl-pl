---
title: "switch_type — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.switch_type
dev_langs: C++
helpviewer_keywords: switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 99ec139c1ff10456639249c94451877a18cbbf51
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="switchtype"></a>switch_type
Określa typ zmiennej używanej jako discriminant Unii.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[switch_type(  
type  
}]  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Typ przełącznika może być typu Liczba całkowita, znak, wartość logiczna lub wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
 **Switch_type —** atrybut C++ ma te same funkcje co [switch_type —](http://msdn.microsoft.com/library/windows/desktop/aa367276) MIDL atrybutu.  
  
 Atrybuty C++ nie obsługują [hermetyzowany unie](http://msdn.microsoft.com/library/windows/desktop/aa366811). [Unie nonencapsulated](http://msdn.microsoft.com/library/windows/desktop/aa367119) są obsługiwane tylko w następującej postaci:  
  
```  
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
 Zobacz [przypadku](../windows/case-cpp.md) przykład użycie próbki **switch_type —**.  
  
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
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Eksportuj](../windows/export.md)   
