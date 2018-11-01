---
title: obiekt (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: 1cae9e6b014f33dfbbcccdeb4172d6f35349e307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526174"
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

Zobacz [nonbrowsable —](nonbrowsable.md) przykład sposobu użycia **obiektu**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interface**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)