---
title: przypadek (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 1e7a15d81c8efd5320cf142faa3e3f381f81abd7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079678"
---
# <a name="case-c"></a>case (C++)

Używane z [switch_type —](switch-type.md) atrybutu w **Unii**.

## <a name="syntax"></a>Składnia

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>Parametry

*value*<br/>
Możliwa wartość danych wejściowych, dla którego chcesz podać przetwarzania. Typ **wartość** może być jedną z następujących typów:

- `int`

- `char`

- `boolean`

- `enum`

lub identyfikator takiego typu.

## <a name="remarks"></a>Uwagi

**Przypadek** atrybut C++ ma taką samą funkcjonalność jak **przypadek** atrybutów w MIDL. Ten atrybut jest używany tylko z [switch_type —](switch-type.md) atrybutu.

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

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)