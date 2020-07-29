---
title: switch_type (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_type
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
ms.openlocfilehash: 13ea76e1153e1a42fd41fe0c087a7c7f15416760
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211934"
---
# <a name="switch_type"></a>switch_type

Określa typ zmiennej używanej jako discriminant Unii.

## <a name="syntax"></a>Składnia

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>Parametry

*Wprowadź*<br/>
Typ przełącznika może być liczbą całkowitą, znakiem, wartością logiczną lub typem wyliczenia.

## <a name="remarks"></a>Uwagi

Atrybut **switch_type** C++ ma takie same funkcje jak atrybut [switch_type](/windows/win32/Midl/switch-type) MIDL.

Atrybuty języka C++ nie obsługują [przyhermetyzowanych Unii](/windows/win32/Midl/encapsulated-unions). [Niehermetyzowane Unii](/windows/win32/Midl/nonencapsulated-unions) są obsługiwane tylko w następującej postaci:

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

Zobacz przykład [przypadku](case-cpp.md) przykładowego zastosowania **switch_type**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**`typedef`**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty typedef, enum, Union i struct](typedef-enum-union-and-struct-attributes.md)<br/>
[wywozu](export.md)
