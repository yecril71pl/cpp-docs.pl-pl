---
title: v1_enum — (C++ atrybutów COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.v1_enum
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
ms.openlocfilehash: 08654eed7ad467dc22d2cbbf811c9169e5292f16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407149"
---
# <a name="v1enum"></a>v1_enum

Określa, że przekazywane określonego typu wyliczenia jako jednostki 32-bitowych, a nie domyślnej 16-bitowych.

## <a name="syntax"></a>Składnia

```cpp
[v1_enum]
```

## <a name="remarks"></a>Uwagi

**V1_enum —** C++ atrybut ma taką samą funkcjonalność jak [v1_enum —](/windows/desktop/Midl/v1-enum) atrybutów w MIDL.

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

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)