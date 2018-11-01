---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 7aca125879591f71fe2ba60f34b712918350940f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565701"
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
|**Dotyczy**|COM bez **interfejsu**, **klasy**, **wyliczenia**s, `idl_module` metod, składowych interfejsu i parametry interfejsu **typedef**s, **Unii**s, **struktury**s|
|**Powtarzalne**|Tak|
|**Wymaganych atrybutów**|**Klasa coclass** (jeśli jest używany w klasie)|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)