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
ms.openlocfilehash: 7ff83b156054774a06a371e7832dc73dc95a579c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221261"
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