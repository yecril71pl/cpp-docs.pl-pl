---
title: w przypadku (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.case
dev_langs:
- C++
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 30d665861688054a4f6b7491f449014afe646c71
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="case-c"></a>case (C++)
Używane z [switch_type —](../windows/switch-type.md) atrybutu w **Unii**.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ case(  
   value  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *value*  
 Możliwe wartości wejściowej, dla którego chcesz podać przetwarzania. Typ **wartość** może być jedną z następujących typów:  
  
-   `int`  
  
-   `char`  
  
-   `boolean`  
  
-   `enum`  
  
 lub identyfikator takiego typu.  
  
## <a name="remarks"></a>Uwagi  
 **Przypadku** atrybut C++ ma te same funkcje co **przypadku** MIDL atrybutu. Ten atrybut jest używany tylko z [switch_type —](../windows/switch-type.md) atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia korzystanie z **przypadku** atrybutu:  
  
```  
// cpp_attr_ref_case.cpp  
// compile with: /LD  
#include <unknwn.h>  
[export]  
struct SizedValue2 {  
   [switch_type(char), switch_is(kind)] union {  
      [case(1), string]  
          wchar_t* wval;  
      [default, string]  
          char* val;  
   };  
    char kind;  
};  
[module(name="ATLFIRELib")];  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Element członkowski **klasy** lub `struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
