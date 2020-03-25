---
title: Object (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: 4545d899c13a1eabf8ea5fb6fe3918fb5f05b626
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214693"
---
# <a name="object-c"></a>object (C++)

Identyfikuje niestandardowy interfejs.

## <a name="syntax"></a>Składnia

```cpp
[object]
```

## <a name="remarks"></a>Uwagi

W przypadku powyższej definicji interfejsu atrybut **Object** C++ powoduje umieszczenie interfejsu w pliku. idl jako interfejsu niestandardowego.

Wszystkie interfejsy oznaczone atrybutem Object muszą dziedziczyć po `IUnknown`. Ten warunek jest spełniony, jeśli którykolwiek z interfejsów podstawowych dziedziczy po `IUnknown`. Jeśli żadne interfejsy podstawowe nie dziedziczą z `IUnknown`, kompilator spowoduje, że interfejs oznaczony przy użyciu **obiektu** zostanie utworzony z `IUnknown`.

## <a name="example"></a>Przykład

Zobacz [nonbrowsable](nonbrowsable.md) , aby zapoznać się z przykładem użycia **obiektu**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interface**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|None|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)
