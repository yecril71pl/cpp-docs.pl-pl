---
title: importlib | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importlib
dev_langs:
- C++
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b9522db579641d79b8b77cc870cd1df6f03c0413
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607676"
---
# <a name="importlib"></a>importlib

Sprawia, że typy, które już zostały skompilowane do do biblioteki typów, trwa tworzenie innej biblioteki typów.

## <a name="syntax"></a>Składnia

```cpp
[ importlib(
   "tlb_file"
) ];
```

### <a name="parameters"></a>Parametry

*tlb_file*  
Nazwa pliku .tlb w cudzysłowie, które mają zostać zaimportowany do biblioteki typów w bieżącym projekcie.

## <a name="remarks"></a>Uwagi

**Importlib** atrybut C++ powoduje `importlib` instrukcji, które mają być umieszczone w bloku biblioteki pliku .idl wygenerowany. **Importlib** atrybut ma taką samą funkcjonalność jak [importlib](http://msdn.microsoft.com/library/windows/desktop/aa367050) atrybutów w MIDL.

## <a name="example"></a>Przykład

Poniższy kod przedstawia przykład sposobu użycia **importlib**:

```cpp
// cpp_attr_ref_importlib.cpp
// compile with: /LD
[module(name="MyLib")];
[importlib("importlib.tlb")];
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
[import](../windows/import.md)  
[importidl](../windows/importidl.md)  
[include](../windows/include-cpp.md)  
[includelib —](../windows/includelib-cpp.md)