---
title: z ograniczeniami (C++ atrybut com)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: 01dabcd15eb1a14734c16b9e54c0ab2e030d0479
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514057"
---
# <a name="restricted"></a>restricted

Określa, że element członkowski modułu, interfejsu lub dispinterface nie może zostać wywołany arbitralnie.

## <a name="syntax"></a>Składnia

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>Parametry

*interfaces*<br/>
Co najmniej jeden interfejs, który może nie być wywoływany arbitralnie dla obiektu COM. Ten parametr jest prawidłowy tylko wtedy, gdy jest stosowany do klasy.

## <a name="remarks"></a>Uwagi

Atrybut C++ z ograniczeniami ma taką samą funkcjonalność jak atrybut MIDL z [ograniczeniami](/windows/win32/Midl/restricted) .

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak używać atrybutu z **ograniczeniami** :

```cpp
// cpp_attr_ref_restricted.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface b
{
};

[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]
class c : public a, public b
{
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Interface — Metoda, **interfejs**, **Klasa**, **Struktura**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**Klasa coclass** (w przypadku zastosowania do **klasy** lub **struktury**)|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)