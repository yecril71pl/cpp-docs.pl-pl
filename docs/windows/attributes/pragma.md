---
title: dyrektywy (C++ COM atrybut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pragma
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
ms.openlocfilehash: 159e1570c2bde07bb4df8fa904a519e8e0018a6a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041192"
---
# <a name="pragma"></a>pragma

Emituje określonego ciągu w pliku .idl wygenerowany bez znaków cudzysłowu.

## <a name="syntax"></a>Składnia

```cpp
[ pragma(pragma_statement) ];
```

### <a name="parameters"></a>Parametry

*pragma_statement*<br/>
Pragmę, której chcesz przejść do pliku .idl wygenerowany.

## <a name="remarks"></a>Uwagi

**Pragma** atrybut C++ ma taką samą funkcjonalność jak [pragma](/windows/desktop/Midl/pragma) atrybutów w MIDL.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_pragma.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[pragma(pack(4))];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A
{
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[pakiet](../../preprocessor/pack.md)