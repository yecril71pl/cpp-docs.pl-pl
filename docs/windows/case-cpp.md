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
ms.openlocfilehash: 109ca7b833791aa982e17335801e8fe1fc538987
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606639"
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

- `int`

- `char`

- `boolean`

- `enum`

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
[Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[Atrybuty klasy](../windows/class-attributes.md)  