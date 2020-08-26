---
title: pointer_default (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: e4e5ce03e8c0e6ca19814f5d228305b0d97322f9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836195"
---
# <a name="pointer_default"></a>pointer_default

Określa domyślny atrybut wskaźnika dla wszystkich wskaźników, z wyjątkiem wskaźników najwyższego poziomu, które pojawiają się na listach parametrów.

## <a name="syntax"></a>Składnia

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>Parametry

*wartościami*<br/>
Wartość opisująca typ wskaźnika: **PTR**, **ref**lub **Unique**.

## <a name="remarks"></a>Uwagi

Atrybut **pointer_default** C++ ma takie same funkcje jak atrybut [pointer_default](/windows/win32/Midl/pointer-default) MIDL.

## <a name="example"></a>Przykład

Zobacz przykład dla elementu [DefaultValue](defaultvalue.md) dla przykładowego zastosowania **pointer_default**.

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|**interfejsu**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)
