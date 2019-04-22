---
title: w (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: 06d78552ef2ebb878ed630eb377e6249ba60cad4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034540"
---
# <a name="in-c"></a>in (C++)

Wskazuje, że parametr zostanie przekazany z procedury wywołującej do procedury wywoływanej.

## <a name="syntax"></a>Składnia

```cpp
[in]
```

## <a name="remarks"></a>Uwagi

**w** atrybut C++ ma taką samą funkcjonalność jak [w](/windows/desktop/Midl/in) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz [możliwej do wiązania](bindable.md) przykład sposobu użycia **w**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Interfejs parametru metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|**retval**|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)<br/>
[out](out-cpp.md)