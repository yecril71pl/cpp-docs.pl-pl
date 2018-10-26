---
title: implements_category — (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.implements_category
dev_langs:
- C++
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f56562621d217e577abcf694fccb7de14fc4b56
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059184"
---
# <a name="implementscategory"></a>implements_category

Określa kategorii składników implementowane przez klasy docelowej.

## <a name="syntax"></a>Składnia

```cpp
[ implements_category(implements_category="uuid") ]
```

### <a name="parameters"></a>Parametry

*implements_category*<br/>
Identyfikator kategorii zaimplementowane.

## <a name="remarks"></a>Uwagi

**Implements_category —** C++ atrybut określa kategorii składników implementowane przez klasy docelowej. Odbywa się przez utworzenie mapy kategorii i dodawanie oddzielne wpisy określone przez **implements_category —** atrybutu. Aby uzyskać więcej informacji, zobacz [co to są kategorii składników i jak są one działają?](https://msdn.microsoft.com/library/windows/desktop/ms694322).

Ten atrybut wymaga, aby [coclass](coclass.md), [progid](progid.md), lub [vi_progid —](vi-progid.md) atrybutów (lub innego atrybutu, który oznacza jeden z nich) również będą stosowane do tego samego elementu. Jeśli dowolny pojedynczy atrybut jest używany, pozostałe dwa są automatycznie stosowane. Na przykład jeśli `progid` zastosowaniu `vi_progid` i `coclass` są również stosowane.

## <a name="example"></a>Przykład

Poniższy kod określa, że następujący obiekt implementuje `Control` kategorii.

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

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **— struktura**|
|**Powtarzalne**|Tak|
|**Wymaganych atrybutów**|Jedną z następujących: `coclass`, `progid`, lub `vi_progid`|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[IMPLEMENTED_CATEGORY](../../atl/reference/category-macros.md#implemented_category)