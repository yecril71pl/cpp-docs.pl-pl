---
title: ciąg (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.string
dev_langs:
- C++
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 405042e14835c3224389540696b9714873001912
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428086"
---
# <a name="string-c"></a>string (C++)

Oznacza to, że jednowymiarowy **char**, **wchar_t**, `byte` (lub równoważnego) tablicy lub wskaźnika do tablicy takie, które muszą być traktowane jako ciąg.

## <a name="syntax"></a>Składnia

```cpp
[string]
```

## <a name="remarks"></a>Uwagi

**Ciąg** atrybut C++ ma taką samą funkcjonalność jak [ciąg](/windows/desktop/Midl/string) atrybutów w MIDL.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób użycia **ciąg** w interfejsie, a także na element typedef:

```cpp
// cpp_attr_ref_string.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, string] typedef char a[21];
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1)] HRESULT Method3([in, string] char *pC);
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Tablicy lub wskaźnika do tablicy, interfejs parametrów, metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)<br/>
[Atrybuty tablicy](../windows/array-attributes.md)<br/>
[export](../windows/export.md)  