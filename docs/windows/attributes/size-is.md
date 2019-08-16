---
title: size_is (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: 504f1bf72b8ffa15e8df50bb00c86ef909688f1e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514038"
---
# <a name="size_is"></a>size_is

Określ rozmiar pamięci przydzieloną dla wskaźników rozmiaru, wskaźniki rozmiaru do wskaźników rozmiaru i tablic pojedynczych lub wielowymiarowych.

## <a name="syntax"></a>Składnia

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>Parametry

*expression*<br/>
Rozmiar pamięci przydzieloną dla wskaźników rozmiaru.

## <a name="remarks"></a>Uwagi

Atrybut **size_is** C++ ma takie same funkcje jak atrybut [size_is](/windows/win32/Midl/size-is) MIDL.

## <a name="example"></a>Przykład

Zobacz przykład dla [first_is](first-is.md) , aby uzyskać przykład sposobu określania sekcji tablicy.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Pole w **strukturze** lub **Unii**, parametr interfejsu, metoda interfejsu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|`max_is`|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)