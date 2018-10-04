---
title: obiekt (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 14bb20cae26ecb012362b65f86aae5e422170a1a
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789617"
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