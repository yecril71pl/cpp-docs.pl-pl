---
title: Podwójna | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dual
dev_langs:
- C++
helpviewer_keywords:
- dual attribute
ms.assetid: 5d4a9069-d819-42cd-ba56-bbcda17157d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3727fc70698d3202734db7bbe72773cbe49bffb9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592916"
---
# <a name="dual"></a>dual

Przełącza interfejsu w pliku .idl, jako podwójnego interfejsu.

## <a name="syntax"></a>Składnia

```cpp
[dual]
```

## <a name="remarks"></a>Uwagi

Gdy **podwójną** atrybut C++ poprzedza interfejs, sprawia, że interfejs, który ma być umieszczony wewnątrz bloku biblioteki w pliku .idl wygenerowany.

## <a name="example"></a>Przykład

Poniższy kod jest blokiem atrybut, który używa **podwójną** przed definicję interfejsu:

```cpp
// cpp_attr_ref_dual.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), dual]

__interface IStatic : IDispatch
{
   HRESULT Func1(int i);
   [   propget,
      id(1),
      bindable,
      displaybind,
      defaultbind,
      requestedit
   ]
   HRESULT P1([out, retval] long *nSize);
   [   propput,
      id(1),
      bindable,
      displaybind,
      defaultbind,
      requestedit
   ]
   HRESULT P1([in] long nSize); 
};

[cpp_quote("#include file.h")];
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interface**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|`dispinterface`|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty w zależności od zastosowania](../windows/attributes-by-usage.md)  
[custom](../windows/custom-cpp.md)  
[dispinterface](../windows/dispinterface.md)  
[object](../windows/object-cpp.md)  
[__interface](../cpp/interface.md)  