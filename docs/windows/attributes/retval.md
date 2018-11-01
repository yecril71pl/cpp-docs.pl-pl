---
title: retval (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: 4ac6b72095620a3e857f2877d776e91b273e8f33
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566650"
---
# <a name="retval"></a>retval

Określa parametr, który otrzymuje wartość zwrotną z elementu członkowskiego.

## <a name="syntax"></a>Składnia

```cpp
[retval]
```

## <a name="remarks"></a>Uwagi

**Retval** atrybut C++ ma taką samą funkcjonalność jak [retval](/windows/desktop/Midl/retval) atrybutów w MIDL.

**retval** musi znajdować się jako ostatni argument w deklaracji funkcji.

## <a name="example"></a>Przykład

Zobacz przykład [możliwej do wiązania](bindable.md) do użytku przykładowe **retval**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Interfejs parametru metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|**out**|
|**Nieprawidłowe atrybuty**|**in**|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)