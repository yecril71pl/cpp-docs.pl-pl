---
title: async_uuid (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.async_uuid
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
ms.openlocfilehash: 70e73a6286a4b6adaba20b5a35dc16d8389b1948
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501863"
---
# <a name="async_uuid"></a>async_uuid

Określa identyfikator UUID, który kieruje kompilator MIDL do definiowania synchronicznych i asynchronicznych wersji interfejsu COM.

## <a name="syntax"></a>Składnia

```cpp
[async_uuid (uuid)]
```

### <a name="parameters"></a>Parametry

*uuid*<br/>
Identyfikator UUID, który identyfikuje wersję interfejsu.

## <a name="remarks"></a>Uwagi

Atrybut **async_uuid** C++ ma takie same funkcje jak atrybut [async_uuid](/windows/win32/Midl/async-uuid) MIDL.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_async_uuid.cpp
// compile with: /LD
#include <Windows.h>
[module(name="Test")];
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|`interface`|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|**Dual**, **dispinterface**|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)