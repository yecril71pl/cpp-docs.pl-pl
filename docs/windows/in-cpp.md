---
title: w programie (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.in
dev_langs:
- C++
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6c447147802d91df0f280a82c61d919ee673970a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222993"
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

Zobacz [możliwej do wiązania](../windows/bindable.md) przykład sposobu użycia **w**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Interfejs parametru metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|**retval**|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty parametru](../windows/parameter-attributes.md)  
[Atrybuty metody](../windows/method-attributes.md)  
[defaultvalue](../windows/defaultvalue.md)  
[id](../windows/id.md)  
[out](../windows/out-cpp.md)  