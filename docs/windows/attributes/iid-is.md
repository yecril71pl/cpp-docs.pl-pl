---
title: iid_is — (C++ atrybutów COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: b91fb7937bb0e20f2500eace9695bc0ddba21b26
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038560"
---
# <a name="iidis"></a>iid_is

Określa identyfikator IID interfejsu COM, wskazywana przez wskaźnik interfejsu.

## <a name="syntax"></a>Składnia

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>Parametry

*expression*<br/>
Wyrażenie języka C, który określa IID interfejsu COM, wskazywana przez wskaźnik interfejsu.

## <a name="remarks"></a>Uwagi

**Iid_is —** C++ atrybut ma taką samą funkcjonalność jak [iid_is —](/windows/desktop/Midl/iid-is) atrybutów w MIDL.

## <a name="example"></a>Przykład

Poniższy kod przedstawia użycie **iid_is —**:

```cpp
// cpp_attr_ref_iid_is.cpp
// compile with: /LD
#include "wtypes.h"
#include "unknwn.h"
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]
   IUnknown ** ppvObject);
};

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Parametr interfejsu, element członkowski danych|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)