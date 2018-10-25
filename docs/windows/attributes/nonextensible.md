---
title: (C++ COM atrybut nonextensible) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a025b54e3c41f283e1877e0b97c7dbb6e5f32bd
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062812"
---
# <a name="nonextensible"></a>nonextensible

Określa, że `IDispatch` wdrożenia zawiera tylko właściwości i metod wymienionych w opisie interfejsu i nie można rozszerzyć za pomocą dodatkowe elementy członkowskie w czasie wykonywania.

## <a name="syntax"></a>Składnia

```cpp
[nonextensible]
```

## <a name="remarks"></a>Uwagi

**Nonextensible** atrybut C++ ma taką samą funkcjonalność jak [nonextensible](/windows/desktop/Midl/nonextensible) atrybutów w MIDL.

Korzystanie z **nonextensible** wymaga również [oleautomation —](oleautomation.md) atrybutu.

## <a name="example"></a>Przykład

Poniższy kod demonstruje jedno użycie **nonextensible** atrybutu:

```cpp
// cpp_attr_ref_nonextensible.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export] typedef long HRESULT;

[dual, nonextensible, ms_union, oleautomation,
uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   HRESULT procedure (int i);
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interface**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|`dual` i `oleautomation`, lub `dispinterface`|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)