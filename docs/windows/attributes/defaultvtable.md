---
title: defaultvtable (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvtable
helpviewer_keywords:
- defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
ms.openlocfilehash: 40f901345601193db9752ea6c6dca980ded0625d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579936"
---
# <a name="defaultvtable"></a>defaultvtable

Definiuje interfejs jako domyślnym interfejsem obiektu COM vtable.

## <a name="syntax"></a>Składnia

```cpp
[ defaultvtable(interface) ]
```

### <a name="parameters"></a>Parametry

*interface*<br/>
Wyznaczonym interfejsu, który ma być vtable domyślnego dla obiektu COM.

## <a name="remarks"></a>Uwagi

**Defaultvtable** atrybut C++ ma taką samą funkcjonalność jak [defaultvtable](/windows/desktop/Midl/defaultvtable) atrybutów w MIDL.

## <a name="example"></a>Przykład

Poniższy kod pokazuje atrybuty dla klasy, która będzie używać **defaultvtable** do określenia domyślnego interfejsu:

```cpp
// cpp_attr_ref_defaultvtable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI1 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface IMyI2 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000003")]
__interface IMyI3 {
   HRESULT x();
};

[coclass, source(IMyI3, IMyI1), default(IMyI3, IMyI2), defaultvtable(IMyI1),
uuid("00000000-0000-0000-0000-000000000004")]
class CMyC3 : public IMyI3 {};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|**coclass**|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)