---
title: v1_enum — (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.v1_enum
dev_langs:
- C++
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c1deb68164cdcbd93b6c4992f1c2a19b01095d57
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058418"
---
# <a name="v1enum"></a>v1_enum

Określa, że przekazywane określonego typu wyliczenia jako jednostki 32-bitowych, a nie domyślnej 16-bitowych.

## <a name="syntax"></a>Składnia

```cpp
[v1_enum]
```

## <a name="remarks"></a>Uwagi

**V1_enum —** atrybut C++ ma taką samą funkcjonalność jak [v1_enum —](/windows/desktop/Midl/v1-enum) atrybutów w MIDL.

## <a name="example"></a>Przykład

Poniższy kod pokazuje wykorzystanie **v1_enum —**:

```cpp
// cpp_attr_ref_v1_enum.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export, v1_enum]
enum eList {
   e1 = 1, e2 = 2
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Typy wyliczeniowe|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)