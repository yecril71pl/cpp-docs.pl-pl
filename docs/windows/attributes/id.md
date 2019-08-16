---
title: ID (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 6f1d1d2b9d147e8b33b3b5fae629e0805971bb71
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501408"
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

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Interface — Metoda|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty składowych danych](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)