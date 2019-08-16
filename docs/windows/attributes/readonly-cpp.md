---
title: ReadOnly (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.readonly
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
ms.openlocfilehash: 93f7393f76596766e841dfc25f6d12e20e3db618
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514133"
---
# <a name="readonly-c"></a>readonly (C++)

Zabrania przypisania do elementu członkowskiego danych.

## <a name="syntax"></a>Składnia

```cpp
[readonly]
```

## <a name="remarks"></a>Uwagi

Atrybut **ReadOnly** C++ ma takie same funkcje jak atrybut MIDL [tylko do odczytu](/windows/win32/Midl/readonly) .

Jeśli chcesz zabronić modyfikacji parametru metody, Użyj atrybutu [in](in-cpp.md) .

## <a name="example"></a>Przykład

Poniższy kod przedstawia użycie atrybutu **ReadOnly** :

```cpp
// cpp_attr_ref_readonly.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
#include "unknwn.h"
[module(name="ATLFIRELib")];

[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]
__interface IFireTabCtrl
{
   [readonly, id(1)] int i();
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
[Atrybuty składowych danych](data-member-attributes.md)