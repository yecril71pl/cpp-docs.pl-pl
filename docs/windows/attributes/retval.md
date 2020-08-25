---
title: retval (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: f90893390bc67cb495e646f61e3d61a994e42e50
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845994"
---
# <a name="retval"></a>retval

Określa parametr, który odbiera wartość zwracaną przez element członkowski.

## <a name="syntax"></a>Składnia

```cpp
[retval]
```

## <a name="remarks"></a>Uwagi

Atrybut **retval** C++ ma te same funkcje, co atrybut [retval](/windows/win32/Midl/retval) MIDL.

element **retval** musi znajdować się na ostatnim argumencie w deklaracji funkcji.

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [powiązania](bindable.md) dla przykładowego użycia programu **retval**.

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|Parametr interfejsu, metoda interfejsu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**określoną**|
|**Nieprawidłowe atrybuty**|**podczas**|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)
