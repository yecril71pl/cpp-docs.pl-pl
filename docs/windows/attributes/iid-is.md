---
title: iid_is — (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.iid_is
dev_langs:
- C++
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b777be28fcee3c11a8f3ae2058d6197f39d2ba22
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060172"
---
# <a name="iidis"></a>iid_is

Określa identyfikator IID interfejsu COM, wskazywana przez wskaźnik interfejsu.

## <a name="syntax"></a>Składnia

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>Parametry

*Wyrażenie*<br/>
Wyrażenie języka C, który określa IID interfejsu COM, wskazywana przez wskaźnik interfejsu.

## <a name="remarks"></a>Uwagi

**Iid_is —** atrybut C++ ma taką samą funkcjonalność jak [iid_is —](/windows/desktop/Midl/iid-is) atrybutów w MIDL.

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

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)