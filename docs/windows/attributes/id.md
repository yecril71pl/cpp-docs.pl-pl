---
title: ID (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: f67bf21fbe0040884cba4a54ed8d2a230cb20cd6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830556"
---
# <a name="id"></a>identyfikator

Określa parametr *DISPID* dla funkcji członkowskiej (właściwość lub metoda w interfejsie lub dispinterface).

## <a name="syntax"></a>Składnia

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>Parametry

*DISPID*<br/>
Identyfikator wysyłki dla metody interfejsu.

## <a name="remarks"></a>Uwagi

Atrybut **ID** C++ ma takie same funkcje jak atrybut [ID](/windows/win32/Midl/id) MIDL.

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [powiązania](bindable.md) z przykładem użycia **identyfikatora**.

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|Interface — Metoda|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty elementu członkowskiego danych](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[podczas](in-cpp.md)<br/>
[określoną](out-cpp.md)
