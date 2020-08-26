---
title: out (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.out
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
ms.openlocfilehash: b99e520a11c2e8110d2e63fa85ddb1dd444e56e6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837102"
---
# <a name="out-c"></a>out (C++)

Identyfikuje parametry wskaźnika, które są zwracane z wywoływanej procedury do procedury wywołującej (z serwera do klienta).

## <a name="syntax"></a>Składnia

```cpp
[out]
```

## <a name="remarks"></a>Uwagi

Atrybut **out** języka C++ ma takie same funkcje jak atrybut [out](/windows/win32/Midl/out-idl) MIDL.

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [powiązania](bindable.md) dla przykładowego użycia **.**

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|Parametr interfejsu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)
