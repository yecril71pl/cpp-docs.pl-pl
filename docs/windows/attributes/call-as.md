---
title: call_as (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: f36cf8d1be589cc614a6def583b00af00aabdb61
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501804"
---
# <a name="call_as"></a>call_as

Umożliwia zamapowanie funkcji [lokalnej](local-cpp.md) na funkcję zdalną, dzięki czemu po wywołaniu funkcji zdalnej funkcja lokalna jest wywoływana.

## <a name="syntax"></a>Składnia

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>Parametry

*funkcyjn*<br/>
Funkcja lokalna, która ma być wywoływana, gdy wywoływana jest funkcja zdalna.

## <a name="remarks"></a>Uwagi

Atrybut **call_as** C++ ma takie same funkcje jak atrybut [call_as](/windows/win32/Midl/call-as) MIDL.

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak można użyć **call_as** do mapowania funkcji niezdalnych (`f1`) na funkcję zdalną (`Remf1`):

```cpp
// cpp_attr_ref_call_as.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMInterface {
   [local] HRESULT f1 ( int i );
   [call_as(f1)] HRESULT Remf1 ( int i );
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Interface — Metoda|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[local](local-cpp.md)