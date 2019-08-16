---
title: ciąg (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: 978f1f546c0df8de4ff167ddf5ddf724feb31b6e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514008"
---
# <a name="string-c"></a>string (C++)

Wskazuje, że tablica Jednowymiarowa, **wchar_t**, `byte` (lub równoważna) lub wskaźnik do takiej tablicy musi być traktowana jako ciąg.

## <a name="syntax"></a>Składnia

```cpp
[string]
```

## <a name="remarks"></a>Uwagi

Atrybut **String** C++ ma takie same funkcje jak atrybut MIDL [ciągu](/windows/win32/Midl/string) .

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak używać **ciągu** w interfejsie i w typedef:

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
|**Dotyczy**|Tablica lub wskaźnik do tablicy, parametr interfejsu, metoda interfejsu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty tablicy](array-attributes.md)<br/>
[export](export.md)