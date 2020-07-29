---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 185517720af7e61f6a04068e8868d258a51f262f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215325"
---
# <a name="custom-c"></a>custom (C++)

Definiuje metadane dla obiektu w bibliotece typów.

## <a name="syntax"></a>Składnia

```cpp
[ custom(
   uuid,
   value
) ];
```

### <a name="parameters"></a>Parametry

*uuid*<br/>
Unikatowy identyfikator.

*wartościami*<br/>
Wartość, która może zostać wprowadzona do wariantu.

## <a name="remarks"></a>Uwagi

**Niestandardowy** atrybut C++ spowoduje umieszczenie informacji w bibliotece typów. Wymagane jest narzędzie, które odczytuje wartość niestandardową z biblioteki typów.

Atrybut **niestandardowy** ma taką samą funkcjonalność jak [niestandardowy](/windows/win32/Midl/custom) atrybut MIDL.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Interfejs**niebędący modelem COM, **`class`** , **`enum`** s, `idl_module` metody, elementy członkowskie interfejsu, parametry interfejsu, **`typedef`** s, **`union`** s, **`struct`** s|
|**Powtarzalne**|Tak|
|**Wymagane atrybuty**|**Klasa coclass** (używana w klasie)|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty autonomiczne](stand-alone-attributes.md)<br/>
[Atrybuty typedef, enum, Union i struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)
