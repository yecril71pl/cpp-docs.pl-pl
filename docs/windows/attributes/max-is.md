---
title: max_is — (C++ atrybutów COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: dca2a3dc18aa3c3e75bbb682ed0b1b90adcd9236
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409281"
---
# <a name="maxis"></a>max_is

Określa maksymalną wartość indeksu prawidłową tablicą.

## <a name="syntax"></a>Składnia

```cpp
[ max_is("expression") ]
```

### <a name="parameters"></a>Parametry

*expression*<br/>
Co najmniej jednego wyrażenia języka C. Pusty argument miejsca są dozwolone.

## <a name="remarks"></a>Uwagi

**Max_is —** C++ atrybut ma taką samą funkcjonalność jak [max_is —](/windows/desktop/Midl/max-is) atrybutów w MIDL.

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

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)