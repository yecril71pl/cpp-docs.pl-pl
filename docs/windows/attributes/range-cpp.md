---
title: Range (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.range
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
ms.openlocfilehash: 8ed0ba2c53992dd19d1c4491f8085e955146224c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839481"
---
# <a name="range-c"></a>range (C++)

Określa zakres dozwolonych wartości dla argumentów lub pól, których wartości są ustawiane w czasie wykonywania.

## <a name="syntax"></a>Składnia

```cpp
[ range(low, high) ]
```

### <a name="parameters"></a>Parametry

*małą*<br/>
Wartość dolnego zakresu.

*wysokowydajn*<br/>
Wartość wysokiego zakresu.

## <a name="remarks"></a>Uwagi

Atrybut **Range** języka C++ ma takie same funkcje jak atrybut [Range](/windows/win32/Midl/range) MIDL.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_range.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);
};
```

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|Interface — Metoda, parametr interfejsu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[Atrybuty elementu członkowskiego danych](data-member-attributes.md)
