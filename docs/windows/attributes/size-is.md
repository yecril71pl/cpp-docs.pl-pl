---
title: size_is (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.size_is
dev_langs:
- C++
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6cbcc63e2fb9cadb576ec8272809b523a1138707
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063617"
---
# <a name="sizeis"></a>size_is

Określ rozmiar pamięci przydzielonej dla wskaźników o rozmiarze rozmiar wskaźniki do wskaźników o rozmiarze i jedno - lub tablic wielowymiarowych.

## <a name="syntax"></a>Składnia

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>Parametry

*Wyrażenie*<br/>
Rozmiar pamięci przydzielonej dla wskaźników o rozmiarze.

## <a name="remarks"></a>Uwagi

**Size_is** atrybut C++ ma taką samą funkcjonalność jak [size_is](/windows/desktop/Midl/size-is) atrybutów w MIDL.

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

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)