---
title: switch_type — (C++ atrybutów COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_type
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
ms.openlocfilehash: b461769d3d988efae0be7380e1e0112e3f3cf801
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027860"
---
# <a name="switchtype"></a>switch_type

Określa typ zmiennej używanej jako discriminant Unii.

## <a name="syntax"></a>Składnia

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>Parametry

*type*<br/>
Typ przełącznika może być typu Liczba całkowita, znaku, wartość logiczna lub wyliczenia.

## <a name="remarks"></a>Uwagi

**Switch_type —** C++ atrybut ma taką samą funkcjonalność jak [switch_type —](/windows/desktop/Midl/switch-type) atrybutów w MIDL.

Atrybuty C++ nie obsługują [hermetyzowane unie](/windows/desktop/Midl/encapsulated-unions). [Unie nonencapsulated](/windows/desktop/Midl/nonencapsulated-unions) są obsługiwane tylko w następującej postaci:

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

Zobacz [przypadek](case-cpp.md) przykład użycie próbki **switch_type —**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**typedef**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[export](export.md)