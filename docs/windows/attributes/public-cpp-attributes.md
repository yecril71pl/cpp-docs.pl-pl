---
title: Public (atrybuty C++) (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.public
helpviewer_keywords:
- public attribute
ms.assetid: c42e1fd5-6cb1-48fe-8a03-95f2a2e0137c
ms.openlocfilehash: d5307b96c58492aa06f115ca7a814aa221062e01
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224373"
---
# <a name="public-c-attributes"></a>public (Atrybuty C++)

Zapewnia, że element typedef przejdzie do biblioteki typów, nawet jeśli nie jest przywoływany w pliku. idl.

## <a name="syntax"></a>Składnia

```cpp
[public]
```

## <a name="remarks"></a>Uwagi

**`public`** Atrybut C++ ma takie same funkcje jak [publiczny](/windows/win32/Midl/public) atrybut MIDL.

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak używać **`public`** atrybutu:

```cpp
// cpp_attr_ref_public.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, public] typedef long MEMBERID;

[dispinterface, uuid(99999999-9999-9999-9999-000000000000)]
__interface IFireTabCtrl : IDispatch
{
   [id(2)] long procedure ([in, optional] VARIANT i);
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**`typedef`**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty typedef, enum, Union i struct](typedef-enum-union-and-struct-attributes.md)
