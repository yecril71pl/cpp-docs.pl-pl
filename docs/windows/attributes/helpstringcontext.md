---
title: helpstringcontext — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringcontext
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
ms.openlocfilehash: a6df5b63291fbc54d6c12a116fccd8372e8ced9a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026113"
---
# <a name="helpstringcontext"></a>helpstringcontext

Określa identyfikator tematu pomocy w pliku hlp lub chm.

## <a name="syntax"></a>Składnia

```cpp
[ helpstringcontext(contextID) ]
```

### <a name="parameters"></a>Parametry

*Identyfikator kontekstu*<br/>
Identyfikator kontekstu pomocy w 32-bitowych w **pomocy** pliku.

## <a name="remarks"></a>Uwagi

**Helpstringcontext —** atrybut C++ ma taką samą funkcjonalność jak [helpstringcontext —](/windows/desktop/Midl/helpstringcontext) odl — atrybut.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_helpstringcontext.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[   object, helpstring("help string"), helpstringcontext(1), uuid="11111111-1111-1111-1111-111111111111"
]
__interface IMyI
{
   HRESULT xx();
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Informacje zawarte w tym artykule dotyczą**|**Klasa**, **interfejsu**, interfejs — metoda|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[moduł](module-cpp.md)