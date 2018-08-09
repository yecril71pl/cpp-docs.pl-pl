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
ms.openlocfilehash: ddccbc1fcecafe5ac924098a344cfb7592ce2116
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647830"
---
# <a name="case-c"></a>case (C++)
Używane z [switch_type —](../windows/switch-type.md) atrybutu w **Unii**.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[ case(  
   value  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *value*  
 Możliwa wartość danych wejściowych, dla którego chcesz podać przetwarzania. Typ **wartość** może być jedną z następujących typów:  
  
-   `int`  
  
-   `char`  
  
-   `boolean`  
  
-   `enum`  
  
 lub identyfikator takiego typu.  
  
## <a name="remarks"></a>Uwagi  
 **Przypadek** atrybut C++ ma taką samą funkcjonalność jak **przypadek** atrybutów w MIDL. Ten atrybut jest używany tylko z [switch_type —](../windows/switch-type.md) atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod pokazuje wykorzystanie **przypadek** atrybutu:  
  
```cpp  
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
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Członek **klasy** lub **— struktura**|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Element TypeDef, Enum, Union i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   