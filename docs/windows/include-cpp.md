---
title: obejmują (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.include
dev_langs:
- C++
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8fe604074b843e7c0b76c2e671e0abd9e40770a7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598463"
---
# <a name="include-c"></a>include (C++)

Określa jeden lub więcej plików nagłówka do uwzględnienia w pliku .idl wygenerowany.

## <a name="syntax"></a>Składnia

```cpp
[ include(
   header_file
) ];
```

### <a name="parameters"></a>Parametry

*header_file*  
Nazwa pliku, którego chcesz zawarte w pliku .idl wygenerowany.

## <a name="remarks"></a>Uwagi

**Obejmują** atrybut C++ powoduje `#include` instrukcję, aby umieszczona pod `import "docobj.idl"` instrukcja w pliku .idl wygenerowany.

**Obejmują** atrybut C++ ma taką samą funkcjonalność jak [obejmują](http://msdn.microsoft.com/library/windows/desktop/aa367052) atrybutów w MIDL.

## <a name="example"></a>Przykład

Poniższy kod przedstawia przykład sposobu użycia **obejmują**. W tym przykładzie include.h plik zawiera tylko `#include` instrukcji.

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
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

[Atrybuty IDL](../windows/idl-attributes.md)  
[Oddzielne atrybuty](../windows/stand-alone-attributes.md)  
[import](../windows/import.md)  
[importidl](../windows/importidl.md)  
[includelib —](../windows/includelib-cpp.md)  
[importlib](../windows/importlib.md)  