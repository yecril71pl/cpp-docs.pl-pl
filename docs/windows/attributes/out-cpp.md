---
title: out (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.out
dev_langs:
- C++
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fbb7bc07ab3b3942f1a3a6fa20c69327c0bd1a53
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063760"
---
# <a name="out-c"></a>out (C++)

Określa parametry wskaźnika, które zostaną zwrócone z procedury wywoływanej do procedury wywołującej (z serwera do klienta).

## <a name="syntax"></a>Składnia

```cpp
[out]
```

## <a name="remarks"></a>Uwagi

**Się** atrybut C++ ma taką samą funkcjonalność jak [się](/windows/desktop/Midl/out-idl) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [możliwej do wiązania](bindable.md) do użytku przykładowe **się**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Parametr interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)