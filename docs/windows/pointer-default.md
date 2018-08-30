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
ms.openlocfilehash: aac6e0456bf8a63712c498114d403c05af5ccddb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212211"
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

*value*  
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

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty interfejsu](../windows/interface-attributes.md)  