---
title: dispinterface | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dispinterface
dev_langs:
- C++
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a98c9016281a67211a41d1c63fcb9886a0b3c35
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222513"
---
# <a name="dispinterface"></a>dispinterface

Przełącza interfejsu w pliku .idl, jako interfejs ekspedycji.

## <a name="syntax"></a>Składnia

```cpp
[dispinterface]
```

## <a name="remarks"></a>Uwagi

Gdy **dispinterface** atrybut C++ poprzedza interfejs, sprawia, że interfejs, który ma być umieszczony wewnątrz bloku biblioteki w pliku .idl wygenerowany.

O ile nie określono klasy bazowej, interfejs ekspedycji, z której pochodzą z `IDispatch`. Należy określić [identyfikator](../windows/id.md) dla członków interfejs ekspedycji.

Przykład użycia [dispinterface](/windows/desktop/Midl/dispinterface) w dokumentacji MIDL:

```cpp
dispinterface helloPro
   { interface hello; };
```

nie jest prawidłowa dla **dispinterface** atrybutu.

## <a name="example"></a>Przykład

Zobacz przykład [możliwej do wiązania](../windows/bindable.md) przykład sposobu użycia **dispinterface**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interface**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty w zależności od zastosowania](../windows/attributes-by-usage.md)  
[uuid](../windows/uuid-cpp-attributes.md)  
[dual](../windows/dual.md)  
[custom](../windows/custom-cpp.md)  
[object](../windows/object-cpp.md)  
[__interface](../cpp/interface.md)  