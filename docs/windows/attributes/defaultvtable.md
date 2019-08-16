---
title: defaultvtable (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvtable
helpviewer_keywords:
- defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
ms.openlocfilehash: 8ab37af4deab516dc01f55f986811668737cf18c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501644"
---
# <a name="defaultvtable"></a>defaultvtable

Definiuje interfejs jako domyślny interfejs tablicy metod dla obiektu COM.

## <a name="syntax"></a>Składnia

```cpp
[ defaultvtable(interface) ]
```

### <a name="parameters"></a>Parametry

*interface*<br/>
Wyznaczono interfejs, który ma być domyślną tablicą metod wirtualnych dla obiektu COM.

## <a name="remarks"></a>Uwagi

Atrybut **defaultvtable** C++ ma takie same funkcje jak atrybut [defaultvtable](/windows/win32/Midl/defaultvtable) MIDL.

## <a name="example"></a>Przykład

Poniższy kod przedstawia atrybuty klasy, która używa **defaultvtable** do określenia domyślnego interfejsu:

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
|**Dotyczy**|**Klasa**, **Struktura**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**coclass**|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)