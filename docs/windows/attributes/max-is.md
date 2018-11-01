---
title: max_is — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: 10732d5ba3251185dc7027e3449486af3037f763
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627477"
---
# <a name="maxis"></a>max_is

Określa maksymalną wartość indeksu prawidłową tablicą.

## <a name="syntax"></a>Składnia

```cpp
[ max_is("expression") ]
```

### <a name="parameters"></a>Parametry

*Wyrażenie*<br/>
Co najmniej jednego wyrażenia języka C. Pusty argument miejsca są dozwolone.

## <a name="remarks"></a>Uwagi

**Max_is —** atrybut C++ ma taką samą funkcjonalność jak [max_is —](/windows/desktop/Midl/max-is) atrybutów w MIDL.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Pole **struktury** lub **Unii**, interfejs parametrów, metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|**size_is**|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Przykład

Zobacz [first_is —](first-is.md) przykład sposobu określania część tablicy.

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)