---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 227e67696e679452a9c6c0e18c04e3d918f7a93f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029437"
---
# <a name="custom-c"></a>custom (C++)

Definiuje metadanych dla obiektu w bibliotece typów.

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
Wartość, które można umieścić w wariant.

## <a name="remarks"></a>Uwagi

**Niestandardowe** atrybut C++ spowoduje, że informacje, aby zostać umieszczone w bibliotece typów. Należy to narzędzie, które odczytuje wartość niestandardowej z biblioteki typów.

**Niestandardowe** atrybut ma taką samą funkcjonalność jak [niestandardowe](/windows/desktop/Midl/custom) atrybutów w MIDL.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Informacje zawarte w tym artykule dotyczą**|COM bez **interfejsu**, **klasy**, **wyliczenia**s, `idl_module` metod, składowych interfejsu i parametry interfejsu **typedef**s, **Unii**s, **struktury**s|
|**Powtarzalne**|Tak|
|**Wymaganych atrybutów**|**Klasa coclass** (jeśli jest używany w klasie)|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[atrybuty IDL](idl-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)