---
title: źródło (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 921510a548f638f06953f95abe79f825e57e179b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586861"
---
# <a name="source-c"></a>source (C++)

W klasie określa interfejsy źródła obiektu COM dla punktów połączenia. W właściwości lub metody oznacza, że elementu członkowskiego zwraca obiekt lub wariant, który jest źródłem zdarzeń.

## <a name="syntax"></a>Składnia

```cpp
[ source(
   interfaces
) ]
```

### <a name="parameters"></a>Parametry

*interfaces*  
Jeden lub więcej interfejsów, określ, po zastosowaniu źródła atrybutów do klasy. Ten parametr nie jest używany, gdy źródło jest stosowany do właściwości lub metody.

## <a name="remarks"></a>Uwagi

**Źródła** atrybut C++ ma taką samą funkcjonalność jak [źródła](http://msdn.microsoft.com/library/windows/desktop/aa367166) atrybutów w MIDL.

Możesz użyć [domyślne](../windows/default-cpp.md) atrybutu, aby określić domyślnym interfejsie źródła obiektu.

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

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty klasy](../windows/class-attributes.md)  
[Atrybuty metody](../windows/method-attributes.md)  
[coclass](../windows/coclass.md)  