---
title: out (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.out
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
ms.openlocfilehash: 11c8e4473f0b849fab7846a825b90da3ed9f036f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514288"
---
# <a name="out-c"></a>out (C++)

Identyfikuje parametry wskaźnika, które są zwracane z wywoływanej procedury do procedury wywołującej (z serwera do klienta).

## <a name="syntax"></a>Składnia

```cpp
[out]
```

## <a name="remarks"></a>Uwagi

Atrybut **out** C++ ma taką samą funkcjonalność, jak atrybut [out](/windows/win32/Midl/out-idl) MIDL.

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [powiązania](bindable.md) dla przykładowego użycia.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Parametr interfejsu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)