---
title: helpstringcontext (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringcontext
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
ms.openlocfilehash: e6d4a6b4ab2381fc9ebe0f237978c92fe0f656c5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224451"
---
# <a name="helpstringcontext"></a>helpstringcontext

Określa identyfikator tematu pomocy w pliku HLP lub chm.

## <a name="syntax"></a>Składnia

```cpp
[ helpstringcontext(contextID) ]
```

### <a name="parameters"></a>Parametry

*Identyfikator ContextId*<br/>
32-bitowy identyfikator kontekstu pomocy w pliku **pomocy** .

## <a name="remarks"></a>Uwagi

Atrybut **helpstringcontext** C++ ma takie same funkcje jak atrybut [helpstringcontext](/windows/win32/Midl/helpstringcontext) odl.

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
|**Dotyczy**|**`class`**, **interfejs**, metoda interfejsu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[elementu](module-cpp.md)
