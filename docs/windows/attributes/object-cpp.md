---
title: obiekt (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: c0f544e84e5110761dfd01e25abef4352f055ff5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407539"
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

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)