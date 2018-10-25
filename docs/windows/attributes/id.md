---
title: Identyfikator (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.id
dev_langs:
- C++
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7ae22069acfa13bcaa71630f919b4ab3fede86a4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057689"
---
# <a name="id"></a>identyfikator

Określa *dispid* parametr dla funkcji członkowskiej (właściwość lub metodę w interfejsie lub dispinterface).

## <a name="syntax"></a>Składnia

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>Parametry

*identyfikator DISPID*<br/>
Identyfikator wysyłania dla metody interfejsu.

## <a name="remarks"></a>Uwagi

**Identyfikator** atrybut C++ ma taką samą funkcjonalność jak [identyfikator](/windows/desktop/Midl/id) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [możliwej do wiązania](bindable.md) przykład sposobu użycia **identyfikator**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty składowych danych](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)