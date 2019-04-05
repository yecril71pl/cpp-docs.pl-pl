---
title: (C++ COM atrybut nonextensible)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: ed396b3d55e16cf195949c713ab574812b796a1a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032079"
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
|**Informacje zawarte w tym artykule dotyczą**|**interface**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|`dual` i `oleautomation`, lub `dispinterface`|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)