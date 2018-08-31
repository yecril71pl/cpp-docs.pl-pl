---
title: może być powiązana | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.bindable
dev_langs:
- C++
helpviewer_keywords:
- bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2e0ce7cffb397aaa170f13bac9fc1f4c1693d25f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214855"
---
# <a name="bindable"></a>bindable

Wskazuje, że właściwość obsługuje powiązanie danych.

## <a name="syntax"></a>Składnia

```cpp
[bindable]
```

## <a name="remarks"></a>Uwagi

**Możliwej do wiązania** atrybut C++ ma taką samą funkcjonalność jak [możliwej do wiązania](/windows/desktop/Midl/bindable) atrybutów w MIDL. Służy zdefiniowane za pomocą właściwości [propget](../windows/propget.md), [propput](../windows/propput.md), lub [propputref](../windows/propputref.md) atrybutów lub można ręcznie zdefiniować metodę możliwej do wiązania.

Poniższe przykłady MFC pokazują użycie **możliwej do wiązania**:

- [Próbki kontrolki: Kontrolki ActiveX oparty na bibliotece MFC](https://msdn.microsoft.com/a44adf86-0ba0-4504-bedb-512b6cba2e63)

- [Przykład OK: Kontrolki ActiveX](https://msdn.microsoft.com/9ba34d04-280e-49f4-90ae-41a6be44c95b)

- [Przykład TESTHELP: Formant ActiveX przy użyciu etykietek narzędzi i pomocy](https://msdn.microsoft.com/d822861d-c6f0-4d0a-ad11-970eebb1e8cd)

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak można użyć **możliwej do wiązania** we właściwości:

```cpp
// cpp_attr_ref_bindable.cpp
// compile with: /LD
#include <windows.h>
[
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"),
   dispinterface,
   helpstring("property demo Interface")  
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

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty metody](../windows/method-attributes.md)  
[defaultbind](../windows/defaultbind.md)  
[displaybind](../windows/displaybind.md)  
[immediatebind](../windows/immediatebind.md)  
[requestedit](../windows/requestedit.md)  