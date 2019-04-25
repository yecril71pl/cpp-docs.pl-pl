---
title: call_as (C++ atrybutów COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: a0051cdca6673800b37d5733c0b849da24010fcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148357"
---
# <a name="callas"></a>call_as

Włącza [lokalnego](local-cpp.md) funkcji, które mają być mapowane na funkcję zdalną, więc, że po wywołaniu funkcji zdalnego jest wywoływana funkcja lokalna.

## <a name="syntax"></a>Składnia

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>Parametry

*— Funkcja*<br/>
Funkcja lokalna, który ma być wywoływana, gdy zostanie wywołana funkcja zdalnego.

## <a name="remarks"></a>Uwagi

**Call_as** C++ atrybut ma taką samą funkcjonalność jak [call_as](/windows/desktop/Midl/call-as) atrybutów w MIDL.

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak można użyć **call_as** na mapowanie funkcji nonremotable (`f1`) do funkcji może być zastosowana zdalnie (`Remf1`):

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
|**Dotyczy**|Metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[local](local-cpp.md)