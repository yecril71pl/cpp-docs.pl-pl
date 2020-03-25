---
title: Case (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.case
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
ms.openlocfilehash: da72fff3bb600b5db2fba0ecdfe9c6a768836f3c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167343"
---
# <a name="case-c"></a>case (C++)

Używany z atrybutem [switch_type](switch-type.md) w **Unii**.

## <a name="syntax"></a>Składnia

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>Parametry

*value*<br/>
Możliwa wartość wejściowa, dla której ma zostać przetworzone przetwarzanie. Typ **wartości** może być jednym z następujących typów:

- `int`

- `char`

- `boolean`

- `enum`

lub identyfikator takiego typu.

## <a name="remarks"></a>Uwagi

Atrybut **Case** C++ ma takie same funkcje jak atrybut MIDL **przypadku** . Ten atrybut jest używany tylko z atrybutem [switch_type](switch-type.md) .

## <a name="example"></a>Przykład

Poniższy kod przedstawia użycie atrybutu **Case** :

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
|**Dotyczy**|Składowa **klasy** lub **struktury**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|None|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)
