---
title: iid_is (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: 6a8fe8c7481cd251baff65293607733573f46ea6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832220"
---
# <a name="iid_is"></a>iid_is

Określa identyfikator IID interfejsu COM wskazywanego przez wskaźnik interfejsu.

## <a name="syntax"></a>Składnia

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>Parametry

*wyrażenia*<br/>
Wyrażenie języka C, które określa identyfikator IID interfejsu COM wskazywanego przez wskaźnik interfejsu.

## <a name="remarks"></a>Uwagi

Atrybut **iid_is** C++ ma takie same funkcje jak atrybut [iid_is](/windows/win32/Midl/iid-is) MIDL.

## <a name="example"></a>Przykład

Poniższy kod ilustruje użycie **iid_is**:

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

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|Parametr interfejsu, element członkowski danych|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)
