---
title: tylko do odczytu (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.readonly
dev_langs:
- C++
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 297b457bdf2c70a75b9abdc433c87381fd115037
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067751"
---
# <a name="readonly-c"></a>readonly (C++)

Zabrania przypisania element członkowski danych.

## <a name="syntax"></a>Składnia

```cpp
[readonly]
```

## <a name="remarks"></a>Uwagi

**Tylko do odczytu** atrybut C++ ma taką samą funkcjonalność jak [tylko do odczytu](/windows/desktop/Midl/readonly) atrybutów w MIDL.

Jeśli chcesz uniemożliwiają modyfikację parametru metody, należy użyć [w](in-cpp.md) atrybutu.

## <a name="example"></a>Przykład

Poniższy kod pokazuje wykorzystanie **tylko do odczytu** atrybutu:

```cpp
// cpp_attr_ref_readonly.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
#include "unknwn.h"
[module(name="ATLFIRELib")];

[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]
__interface IFireTabCtrl
{
   [readonly, id(1)] int i();
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty składowych danych](data-member-attributes.md)