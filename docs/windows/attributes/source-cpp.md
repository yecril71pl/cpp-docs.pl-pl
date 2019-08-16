---
title: Source (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.source
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
ms.openlocfilehash: 79614a345e6c07b03df351da93a847fe12e4b110
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514020"
---
# <a name="source-c"></a>source (C++)

Na klasie Określa interfejsy źródłowe obiektu COM dla punktów połączenia. Na właściwości lub metodzie wskazuje, że element członkowski zwraca obiekt lub wariant, który jest źródłem zdarzeń.

## <a name="syntax"></a>Składnia

```cpp
[ source(interfaces) ]
```

### <a name="parameters"></a>Parametry

*interfaces*<br/>
Co najmniej jeden interfejs, który jest określany podczas stosowania atrybutu źródłowego do klasy. Ten parametr nie jest używany, gdy źródło jest stosowane do właściwości lub metody.

## <a name="remarks"></a>Uwagi

Atrybut **Source** C++ ma taką samą funkcjonalność jak [źródłowy](/windows/win32/Midl/source) atrybut MIDL.

Możesz użyć atrybutu [domyślnego](default-cpp.md) , aby określić domyślny interfejs źródłowy dla obiektu.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_source.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT get_I([out, retval]long *i);
};

[object, uuid(11111111-1111-1111-1111-111111111131)]
__interface c
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT et_I([out, retval]long *i);
};

[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]
class N : public b
{
};

[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]
class NN : public b
{
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **Struktura**, **interfejs**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|`coclass`(w przypadku zastosowania do klasy lub struktury)|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[coclass](coclass.md)