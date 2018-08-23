---
title: obiekt (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.object
dev_langs:
- C++
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e8d69ccb0b5a0c0f0dd13d377841732d9f663e91
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607588"
---
# <a name="object-c"></a>object (C++)

Określa niestandardowy interfejs.

## <a name="syntax"></a>Składnia

```cpp
[object]
```

## <a name="remarks"></a>Uwagi

Gdy poprzedzających definicję interfejsu **obiektu** C++ atrybutu powoduje, że interfejs, który ma być umieszczony w pliku .idl, jako niestandardowego interfejsu.

Dowolny interfejs oznaczona za pomocą obiektu musi dziedziczyć `IUnknown`. Ten warunek jest spełniony, jeśli dowolne interfejsy podstawowe dziedziczyć `IUnknown`. Jeśli nie interfejsy podstawowe dziedziczą z `IUnknown`, kompilator spowoduje, że interfejs oznaczone **obiektu** wyprowadzenia z `IUnknown`.

## <a name="example"></a>Przykład

Zobacz [nonbrowsable —](../windows/nonbrowsable.md) przykład sposobu użycia **obiektu**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interface**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty interfejsu](../windows/interface-attributes.md)  
[dual](../windows/dual.md)  
[dispinterface](../windows/dispinterface.md)  
[custom](../windows/custom-cpp.md)  
[__interface](../cpp/interface.md)  