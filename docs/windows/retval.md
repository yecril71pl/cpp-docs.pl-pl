---
title: retval | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.retval
dev_langs:
- C++
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d29d619f8e561f1c506b69ffd132c46276026e13
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604593"
---
# <a name="retval"></a>retval

Określa parametr, który otrzymuje wartość zwrotną z elementu członkowskiego.

## <a name="syntax"></a>Składnia

```cpp
[retval]
```

## <a name="remarks"></a>Uwagi

**Retval** atrybut C++ ma taką samą funkcjonalność jak [retval](http://msdn.microsoft.com/library/windows/desktop/aa367158) atrybutów w MIDL.

**retval** musi znajdować się jako ostatni argument w deklaracji funkcji.

## <a name="example"></a>Przykład

Zobacz przykład [możliwej do wiązania](../windows/bindable.md) do użytku przykładowe **retval**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Interfejs parametru metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|**out**|
|**Nieprawidłowe atrybuty**|**in**|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty parametru](../windows/parameter-attributes.md)  
[Atrybuty metody](../windows/method-attributes.md)  