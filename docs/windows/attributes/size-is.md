---
title: size_is (C++ atrybutów COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: a7b990a708bafba78c9dc4153315f8b7b20351ba
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033233"
---
# <a name="sizeis"></a>size_is

Określ rozmiar pamięci przydzielonej dla wskaźników o rozmiarze rozmiar wskaźniki do wskaźników o rozmiarze i jedno - lub tablic wielowymiarowych.

## <a name="syntax"></a>Składnia

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>Parametry

*expression*<br/>
Rozmiar pamięci przydzielonej dla wskaźników o rozmiarze.

## <a name="remarks"></a>Uwagi

**Size_is** C++ atrybut ma taką samą funkcjonalność jak [size_is](/windows/desktop/Midl/size-is) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [first_is —](first-is.md) przykład sposobu określania część tablicy.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Pole **struktury** lub **Unii**, interfejs parametrów, metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|`max_is`|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)