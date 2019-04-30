---
title: ciąg (C++ COM atrybut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: e1b528fb922a15655de403c6099ee1d36e2fb3de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407279"
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

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty tablicy](array-attributes.md)<br/>
[export](export.md)