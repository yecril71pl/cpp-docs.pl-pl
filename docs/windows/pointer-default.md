---
title: pointer_default — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pointer_default
dev_langs:
- C++
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 54b02ab188ddd122bd3751f73a3edb33d87266f9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388215"
---
# <a name="pointerdefault"></a>pointer_default

Określa domyślny atrybut wskaźnik dla wszystkich wskaźników, z wyjątkiem wskaźniki najwyższego poziomu, które pojawiają się listami parametrów.

## <a name="syntax"></a>Składnia

```cpp
[ pointer_default(
   value
) ]
```

### <a name="parameters"></a>Parametry

*value*<br/>
Wartość, która opisuje typ wskaźnika: **ptr**, **ref**, lub **unikatowy**.

## <a name="remarks"></a>Uwagi

**Pointer_default —** atrybut C++ ma taką samą funkcjonalność jak [pointer_default —](/windows/desktop/Midl/pointer-default) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [defaultvalue](../windows/defaultvalue.md) do użytku przykładowe **pointer_default —**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interface**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)<br/>
[Atrybuty interfejsu](../windows/interface-attributes.md)  