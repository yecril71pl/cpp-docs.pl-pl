---
title: niestandardowe (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.custom
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 848ea415d0638b6135c69cd14e442f45dab40237
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220364"
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

*uuid*  
Unikatowy identyfikator.

*value*  
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

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Oddzielne atrybuty](../windows/stand-alone-attributes.md)  
[Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[Atrybuty parametru](../windows/parameter-attributes.md)  
[Atrybuty metody](../windows/method-attributes.md)  
[Atrybuty klasy](../windows/class-attributes.md)  
[Atrybuty interfejsu](../windows/interface-attributes.md)  