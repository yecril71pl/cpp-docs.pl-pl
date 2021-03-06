---
title: implements_category (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.implements_category
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
ms.openlocfilehash: cd9a4de8834bc22368393e9ea4639884785af0f2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846124"
---
# <a name="implements_category"></a>implements_category

Określa kategorie składników zaimplementowane przez klasę docelową.

## <a name="syntax"></a>Składnia

```cpp
[ implements_category(implements_category="uuid") ]
```

### <a name="parameters"></a>Parametry

*implements_category*<br/>
Identyfikator zaimplementowanej kategorii.

## <a name="remarks"></a>Uwagi

Atrybut **implements_category** C++ określa kategorie składników zaimplementowane przez klasę docelową. Jest to realizowane przez utworzenie mapy kategorii i dodanie oddzielnych wpisów określonych przez atrybut **implements_category** . Aby uzyskać więcej informacji, zobacz [kategorie składników i jak działają](/windows/win32/com/component-categories-and-how-they-work).

Ten atrybut wymaga, aby atrybut [coclass](coclass.md), [ProgID](progid.md)lub [vi_progid](vi-progid.md) (lub inny atrybut, który implikuje jeden z tych) został również zastosowany do tego samego elementu. W przypadku użycia dowolnego pojedynczego atrybutu zostaną automatycznie zastosowane pozostałe dwa. Na przykład, jeśli `progid` jest stosowany, `vi_progid` i `coclass` są również stosowane.

## <a name="example"></a>Przykład

Poniższy kod określa, że poniższy obiekt implementuje `Control` kategorię.

```cpp
// cpp_attr_ref_implements_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLib")];
[ coclass, implements_category("CATID_Control"),
  uuid("20a0d0cc-5172-40f5-99ae-5e032f3205ae")]
class CMyClass {};
```

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|**`class`**, **`struct`**|
|**Powtarzalne**|Tak|
|**Wymagane atrybuty**|Jeden z następujących: `coclass` , `progid` , lub `vi_progid`|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[IMPLEMENTED_CATEGORY](../../atl/reference/category-macros.md#implemented_category)
