---
title: com_interface_entry — (C++ atrybutów COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.com_interface_entry
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
ms.openlocfilehash: 65d174679f851613e064568b071cfcbdad8f0f06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148266"
---
# <a name="cominterfaceentry-c"></a>com_interface_entry (C++)

Dodaje wpis interfejsu do mapy COM klasy docelowej.

## <a name="syntax"></a>Składnia

```cpp
[ com_interface_entry(
  com_interface_entry) ]
```

### <a name="parameters"></a>Parametry

*com_interface_entry*<br/>
Ciąg zawierający tekst wpisu. Aby uzyskać listę możliwych wartości, zobacz [com_interface_entry — makra](../../atl/reference/com-interface-entry-macros.md).

## <a name="remarks"></a>Uwagi

**Com_interface_entry —** C++ atrybut wstawia retransmitowanych w systemie zawartość ciągu znaków do mapy interfejsu COM, obiektu docelowego. Jeśli ten atrybut jest stosowany jeden raz do obiektu docelowego, wpis jest wstawiany do początku istniejącej mapy interfejsu. Jeśli ten atrybut jest stosowany wielokrotnie do tego samego obiektu docelowego, wpisy zostaną wstawione na początku mapę interfejsu w kolejności, w której zostały odebrane.

Ten atrybut wymaga, aby [coclass](coclass.md), [progid](progid.md), lub [vi_progid —](vi-progid.md) atrybutów (lub innego atrybutu, który oznacza jeden z nich) również będą stosowane do tego samego elementu. Jeśli dowolny pojedynczy atrybut jest używany, pozostałe dwa są automatycznie stosowane. Na przykład jeśli `progid` zastosowaniu `vi_progid` i `coclass` są również stosowane.

Ponieważ pierwsze użycie **com_interface_entry —** powoduje, że nowy interfejs, który ma zostać wstawiony na początku mapę interfejsu musi mieć jedną z następujących typów com_interface_entry —:

- COM_INTERFACE_ENTRY —

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

Dodatkowe sposoby użycia **com_interface_entry —** atrybut można używać wszystkich obsługiwanych typów com_interface_entry —.

To ograniczenie jest konieczne, ponieważ ATL używa pierwszy wpis w mapie interfejsu jako tożsamość `IUnknown`; w związku z tym, wpis musi być prawidłową interfejsu. Na przykład poniższy przykładowy kod jest nieprawidłowe, ponieważ pierwszy wpis w mapie interfejsu nie określa rzeczywistego interfejsu COM.

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>Przykład

Poniższy kod dodaje dwa wpisy do istniejącej mapy interfejsu COM z `CMyBaseClass`. Pierwsza to standardowy interfejs, a druga ukrywa `IDebugTest` interfejsu.

```cpp
// cpp_attr_ref_com_interface_entry.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name ="ldld")];

[ object,
  uuid("7dbebed3-d636-4917-af62-c767a720a5b9")]
__interface IDebugTest{};

[ object,
  uuid("2875ceac-f94b-4087-8e13-d13dc167fcfc")]
__interface IMyClass{};

[ coclass,
  com_interface_entry ("COM_INTERFACE_ENTRY (IMyClass)"),
  com_interface_entry ("COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"),
  uuid("b85f8626-e76e-4775-b6a0-4826a9e94af2")
]

class CMyClass: public IMyClass, public IDebugTest
{
};
```

Wynikowy mapy obiektu COM dla `CMyBaseClass` jest następująca:

```cpp
BEGIN_COM_MAP(CMyClass)
    COM_INTERFACE_ENTRY (IMyClass)
    COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)
    COM_INTERFACE_ENTRY(IMyClass)
    COM_INTERFACE_ENTRY2(IDispatch, IMyClass)
    COM_INTERFACE_ENTRY(IDebugTest)
    COM_INTERFACE_ENTRY(IProvideClassInfo)
END_COM_MAP()
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **— struktura**|
|**Powtarzalne**|Tak|
|**Wymaganych atrybutów**|Co najmniej jeden z następujących czynności: `coclass`, `progid`, lub `vi_progid`.|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)