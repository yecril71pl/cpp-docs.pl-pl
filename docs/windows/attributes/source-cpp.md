---
title: źródło (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.source
dev_langs:
- C++
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f7bc10b89df58dc72c35855fea43c2a0387f9efd
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058469"
---
# <a name="source-c"></a>source (C++)

W klasie określa interfejsy źródła obiektu COM dla punktów połączenia. W właściwości lub metody oznacza, że elementu członkowskiego zwraca obiekt lub wariant, który jest źródłem zdarzeń.

## <a name="syntax"></a>Składnia

```cpp
[ source(interfaces) ]
```

### <a name="parameters"></a>Parametry

*interfaces*<br/>
Jeden lub więcej interfejsów, określ, po zastosowaniu źródła atrybutów do klasy. Ten parametr nie jest używany, gdy źródło jest stosowany do właściwości lub metody.

## <a name="remarks"></a>Uwagi

**Źródła** atrybut C++ ma taką samą funkcjonalność jak [źródła](/windows/desktop/Midl/source) atrybutów w MIDL.

Możesz użyć [domyślne](default-cpp.md) atrybutu, aby określić domyślnym interfejsie źródła obiektu.

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
|**Dotyczy**|**Klasa**, **struktury**, **interfejsu**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|`coclass` (w przypadku zastosowania do klasy lub struktury)|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[coclass](coclass.md)