---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: f51b0210fff4db5be359fa94237f4d7c77b4fef2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214893"
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
|**Dotyczy**|**Interfejs**inny niż com, **Klasa**, **Wyliczenie**s, metody `idl_module`, składowe interfejsu, parametry interfejsu, **typedef**s, **Union**s, **struct**s|
|**Powtarzalne**|Yes|
|**Wymagane atrybuty**|**Klasa coclass** (używana w klasie)|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)
