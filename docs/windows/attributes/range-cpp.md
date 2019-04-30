---
title: zakres (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.range
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
ms.openlocfilehash: 9ce941fe95f2bbef3895c039984db1e1d2985ae1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407487"
---
# <a name="range-c"></a>range (C++)

Określa zakres dopuszczalnych wartości dla argumentów lub pól, których wartości są ustawione w czasie wykonywania.

## <a name="syntax"></a>Składnia

```cpp
[ range(low, high) ]
```

### <a name="parameters"></a>Parametry

*Niska*<br/>
Wartość zakresu niski.

*high*<br/>
Wartość zakresu wysoka.

## <a name="remarks"></a>Uwagi

**Zakres** atrybut C++ ma taką samą funkcjonalność jak [zakres](/windows/desktop/Midl/range) atrybutów w MIDL.

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

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Metody interfejsu, parametr interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[Atrybuty składowych danych](data-member-attributes.md)