---
title: first_is — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.first_is
helpviewer_keywords:
- first_is attribute
ms.assetid: 89acbf56-3b38-4d44-83e8-1ce2f6f74ffd
ms.openlocfilehash: fcabad8d6c512a84e44f050cd5b34d985d687636
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512833"
---
# <a name="firstis"></a>first_is

Określa indeks pierwszego elementu tablicy mają być przekazywane.

## <a name="syntax"></a>Składnia

```cpp
[ first_is("expression") ]
```

### <a name="parameters"></a>Parametry

*Wyrażenie*<br/>
Co najmniej jednego wyrażenia języka C. Pusty argument miejsca są dozwolone.

## <a name="remarks"></a>Uwagi

**First_is —** atrybut C++ ma taką samą funkcjonalność jak [first_is —](/windows/desktop/Midl/first-is) atrybutów w MIDL.

## <a name="example"></a>Przykład

Poniższy kod przedstawia różne sposoby, aby określić sekcji w tablicy:

```cpp
// cpp_attr_ref_first_is.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"

[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind,
requestedit] HRESULT get_I([out, retval]long *i);
   HRESULT Proc1([in] short First, [in] short Last,
[first_is(First), last_is(Last), size_is(Last-First)] char Arr1[]);
   HRESULT Proc2([in] short First, [in] short Last,
[last_is(First), size_is(Last)] char Arr2[]);
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Pole **struktury** lub **Unii**, interfejs parametrów, metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)