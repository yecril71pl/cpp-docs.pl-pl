---
title: pointer_default — (C++ atrybutów COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: 37bd2b16fb7a7c1c186f59897898e08cc73fffae
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59022669"
---
# <a name="pointerdefault"></a>pointer_default

Określa domyślny atrybut wskaźnik dla wszystkich wskaźników, z wyjątkiem wskaźniki najwyższego poziomu, które pojawiają się listami parametrów.

## <a name="syntax"></a>Składnia

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>Parametry

*value*<br/>
Wartość, która opisuje typ wskaźnika: **ptr**, **ref**, lub **unikatowy**.

## <a name="remarks"></a>Uwagi

**Pointer_default —** C++ atrybut ma taką samą funkcjonalność jak [pointer_default —](/windows/desktop/Midl/pointer-default) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [defaultvalue](defaultvalue.md) do użytku przykładowe **pointer_default —**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interface**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)