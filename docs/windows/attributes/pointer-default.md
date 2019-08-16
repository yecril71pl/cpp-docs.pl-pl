---
title: pointer_default (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: c70c372e5f1c3a9c2f620a1fa3505fb9d0436e79
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514258"
---
# <a name="pointer_default"></a>pointer_default

Określa domyślny atrybut wskaźnika dla wszystkich wskaźników, z wyjątkiem wskaźników najwyższego poziomu, które pojawiają się na listach parametrów.

## <a name="syntax"></a>Składnia

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>Parametry

*value*<br/>
Wartość opisująca typ wskaźnika: **PTR**, **ref**lub **Unique**.

## <a name="remarks"></a>Uwagi

Atrybut **pointer_default** C++ ma takie same funkcje jak atrybut [pointer_default](/windows/win32/Midl/pointer-default) MIDL.

## <a name="example"></a>Przykład

Zobacz przykład dla elementu [DefaultValue](defaultvalue.md) dla przykładowego zastosowania **pointer_default**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interface**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)