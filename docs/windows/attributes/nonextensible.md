---
title: nierozszerzalnyC++ (atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: 2a1cd4d685e2fd141c6e11feaea488f44a884c80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214692"
---
# <a name="nonextensible"></a>nonextensible

Określa, że implementacja `IDispatch` zawiera tylko właściwości i metody wymienione w opisie interfejsu i nie można jej rozszerzyć z dodatkowymi elementami członkowskimi w czasie wykonywania.

## <a name="syntax"></a>Składnia

```cpp
[nonextensible]
```

## <a name="remarks"></a>Uwagi

Atrybut **nierozszerzalny** C++ ma taką samą funkcjonalność jak atrybut [nierozszerzalny](/windows/win32/Midl/nonextensible) MIDL.

Użycie **nierozszerzalne** wymaga również atrybutu [OleAutomation](oleautomation.md) .

## <a name="example"></a>Przykład

Poniższy kod pokazuje jedno użycie atrybutu **nierozszerzalny** :

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
|**Wymagane atrybuty**|`dual` i `oleautomation`, lub `dispinterface`|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)
