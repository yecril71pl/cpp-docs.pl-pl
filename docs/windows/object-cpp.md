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
ms.openlocfilehash: 9e1cf7f100c34023e6fea96c9764cce2371dcaaf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412695"
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

[Atrybuty IDL](../windows/idl-attributes.md)<br/>
[Atrybuty interfejsu](../windows/interface-attributes.md)<br/>
[dual](../windows/dual.md)<br/>
[dispinterface](../windows/dispinterface.md)<br/>
[custom](../windows/custom-cpp.md)<br/>
[__interface](../cpp/interface.md)  