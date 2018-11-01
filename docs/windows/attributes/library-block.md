---
title: library_block — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.library_block
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
ms.openlocfilehash: 76e643cb45d8a87408015e6e0726e47d423147f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459927"
---
# <a name="libraryblock"></a>library_block

Umieszcza konstrukcję wewnątrz bloku Biblioteka IDL.

## <a name="syntax"></a>Składnia

```cpp
[library_block]
```

## <a name="remarks"></a>Uwagi

Umieszczenie konstrukcję wewnątrz bloku biblioteki pozwala mieć pewność, że zostaną przekazane do biblioteki typów, niezależnie od tego, czy jest ona przywoływana. Domyślnie tylko konstrukcje zmodyfikowane przez [coclass](coclass.md), [dispinterface](dispinterface.md), i [idl_module](idl-module.md) atrybuty są umieszczane w bloku biblioteki.

## <a name="example"></a>Przykład

W poniższym kodzie niestandardowy interfejs znajduje się wewnątrz bloku biblioteki.

```cpp
// cpp_attr_ref_library_block.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib")];
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface IMyInterface {
   HRESULT f1();
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)