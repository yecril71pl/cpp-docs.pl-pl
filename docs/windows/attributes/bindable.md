---
title: może być powiązana (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.bindable
helpviewer_keywords:
- bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
ms.openlocfilehash: 07f446b946d6703c4a8b9ae59ae0edd8172c6879
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037240"
---
# <a name="bindable"></a>bindable

Wskazuje, że właściwość obsługuje powiązanie danych.

## <a name="syntax"></a>Składnia

```cpp
[bindable]
```

## <a name="remarks"></a>Uwagi

**Możliwej do wiązania** atrybut C++ ma taką samą funkcjonalność jak [możliwej do wiązania](/windows/desktop/Midl/bindable) atrybutów w MIDL. Służy zdefiniowane za pomocą właściwości [propget](propget.md), [propput](propput.md), lub [propputref](propputref.md) atrybutów lub można ręcznie zdefiniować metodę możliwej do wiązania.

Poniższe przykłady MFC pokazują użycie **możliwej do wiązania**:

- [Przykłady formantów: Kontrolki ActiveX oparty na bibliotece MFC](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

- [Przykład OK: ActiveX Control](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

- [Przykład TESTHELP: Kontrolki ActiveX z etykietek narzędzi i pomocy](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak można użyć **możliwej do wiązania** we właściwości:

```cpp
// cpp_attr_ref_bindable.cpp
// compile with: /LD
#include <windows.h>
[
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"), dispinterface, helpstring("property demo Interface")
]
__interface IPropDemo : IDispatch {

   [propget, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);
   [propput, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);
   [id(3), bindable, propget] HRESULT Object([out, retval] IDispatch **ppObj);
   [id(3), bindable, propputref] HRESULT Object([in] IDispatch* pObj);
   [id(-552), helpstring("method AboutBox")] HRESULT AboutBox();
};

[ module(name="PropDemoLib", uuid="479B29E2-9A2C-11D0-B696-00A0C903487A", version="1.0", helpstring="property demo") ];
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

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)