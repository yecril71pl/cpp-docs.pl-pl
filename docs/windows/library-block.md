---
title: library_block — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.library_block
dev_langs:
- C++
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33febb69db2a8f3bd67205de2e6e5cf019016471
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598496"
---
# <a name="libraryblock"></a>library_block

Umieszcza konstrukcję wewnątrz bloku Biblioteka IDL.

## <a name="syntax"></a>Składnia

```cpp
[library_block]
```

## <a name="remarks"></a>Uwagi

Umieszczenie konstrukcję wewnątrz bloku biblioteki pozwala mieć pewność, że zostaną przekazane do biblioteki typów, niezależnie od tego, czy jest ona przywoływana. Domyślnie tylko konstrukcje zmodyfikowane przez [coclass](../windows/coclass.md), [dispinterface](../windows/dispinterface.md), i [idl_module](../windows/idl-module.md) atrybuty są umieszczane w bloku biblioteki.

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

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](../windows/compiler-attributes.md)  
[Oddzielne atrybuty](../windows/stand-alone-attributes.md)  