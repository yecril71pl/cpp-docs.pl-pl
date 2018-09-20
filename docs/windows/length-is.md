---
title: length_is — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.length_is
dev_langs:
- C++
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aff0c2e2600f7f0c300d1043c9844104fd70c4e4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415339"
---
# <a name="lengthis"></a>length_is

Określa liczbę elementów tablicy, które mają być przekazywane.

## <a name="syntax"></a>Składnia

```cpp
[ length_is(
   "expression"
) ]
```

### <a name="parameters"></a>Parametry

*Wyrażenie*<br/>
Co najmniej jednego wyrażenia języka C. Pusty argument miejsca są dozwolone.

## <a name="remarks"></a>Uwagi

**Length_is —** atrybut C++ ma taką samą funkcjonalność jak [length_is —](/windows/desktop/Midl/length-is) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz [first_is —](../windows/first-is.md) przykład sposobu określania część tablicy.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Pole **struktury** lub **Unii**, interfejs parametrów, metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](../windows/parameter-attributes.md)<br/>
[first_is](../windows/first-is.md)<br/>
[max_is](../windows/max-is.md)<br/>
[last_is](../windows/last-is.md)<br/>
[size_is](../windows/size-is.md)  