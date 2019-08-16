---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 19f28963a18abf42c6f629ac0f6491628387aa6d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490997"
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

*value*<br/>
Wartość, która może zostać wprowadzona do wariantu.

## <a name="remarks"></a>Uwagi

Atrybut **niestandardowy** C++ spowoduje umieszczenie informacji w bibliotece typów. Wymagane jest narzędzie, które odczytuje wartość niestandardową z biblioteki typów.

Atrybut **niestandardowy** ma taką samą funkcjonalność jak [niestandardowy](/windows/win32/Midl/custom) atrybut MIDL.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Interfejs**niebędący modelem COM, **Klasa**, `idl_module` **Wyliczenie**s, metody, składowe interfejsu, parametry interfejsu, **typedef**s, **Union**s, **struct**s|
|**Powtarzalne**|Tak|
|**Wymagane atrybuty**|**Klasa coclass** (używany w klasie)|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)