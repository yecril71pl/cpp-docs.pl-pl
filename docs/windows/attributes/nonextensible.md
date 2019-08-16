---
title: nierozszerzalnyC++ (atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: f2947e223d068ea6cc92a41abe19cb7f920112b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514400"
---
# <a name="nonextensible"></a>nonextensible

Określa, że `IDispatch` implementacja zawiera tylko właściwości i metody wymienione w opisie interfejsu i nie można go rozszerzyć z dodatkowymi elementami członkowskimi w czasie wykonywania.

## <a name="syntax"></a>Składnia

```cpp
[nonextensible]
```

## <a name="remarks"></a>Uwagi

Atrybut C++ nierozszerzalny ma taką samą funkcjonalność jak atrybut [](/windows/win32/Midl/nonextensible) nierozszerzalny MIDL.

Użycie nierozszerzalne wymaga również atrybutu [OleAutomation](oleautomation.md) .

## <a name="example"></a>Przykład

Poniższy kod pokazuje jedno użycie atrybutu nierozszerzalny:

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
|**Wymagane atrybuty**|`dual`i `oleautomation`lub`dispinterface`|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)