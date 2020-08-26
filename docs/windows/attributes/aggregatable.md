---
title: agregowany (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregatable
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
ms.openlocfilehash: 6782b1ca28eb07b3f726bd85cd7fffa9b1f1bad2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836377"
---
# <a name="aggregatable"></a>aggregatable

Wskazuje, że Klasa obsługuje agregację.

## <a name="syntax"></a>Składnia

```cpp
[ aggregatable(value) ]
```

### <a name="parameters"></a>Parametry

*wartościami*<br/>
Obowiązkowe Parametr wskazujący, kiedy można agregować obiekt COM:

- `never` Nie można agregować obiektu COM.

- `allowed` Obiekt COM można utworzyć bezpośrednio lub może być zagregowany. Jest to opcja domyślna.

- `always` Obiektu COM nie można utworzyć bezpośrednio i można go agregować tylko. Po wywołaniu `CoCreateInstance` dla tego obiektu należy określić interfejs obiektu agregowania `IUnknown` (kontrolka `IUnknown` ).

## <a name="remarks"></a>Uwagi

**Agregowany** atrybut C++ ma taką samą funkcjonalność jak atrybut MIDL, który jest [agregowany](/windows/win32/Midl/aggregatable) . Oznacza to, że kompilator przekaże atrybut **agregowany** do wygenerowanego pliku IDL.

Ten atrybut wymaga, aby atrybut [coclass](coclass.md), [ProgID](progid.md)lub [vi_progid](vi-progid.md) (lub inny atrybut, który implikuje jeden z tych) został również zastosowany do tego samego elementu. W przypadku użycia dowolnego pojedynczego atrybutu zostaną automatycznie zastosowane pozostałe dwa. Na przykład, jeśli `progid` jest stosowany, `vi_progid` i `coclass` są również stosowane.

### <a name="atl-projects"></a>Projekty ATL

Jeśli ten atrybut jest używany w projekcie, który korzysta z ATL, zachowanie zmiany atrybutu. Oprócz wcześniej opisanych zachowań, atrybut dodaje również jeden z następujących makr do klasy docelowej:

|Wartość parametru|Wstawione makro|
|---------------------|--------------------|
|`Never`|[DECLARE_NOT_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|
|`Allowed`|[DECLARE_POLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|
|`Always`|[DECLARE_ONLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_aggregatable.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyModule")];

[ coclass, aggregatable(allowed),
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]
class CMyClass {};
```

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|**`class`**, **`struct`**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Co najmniej jeden z następujących elementów: `coclass` , `progid` , lub `vi_progid` .|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty typedef, enum, Union i struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Agregacji](/windows/win32/com/aggregation)
