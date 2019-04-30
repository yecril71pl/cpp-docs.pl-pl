---
title: ograniczone (atrybut COM C++)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: 86f40fa49daf88668e37bef07f0db33d01cf1942
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407357"
---
# <a name="restricted"></a>restricted

Określa, że jest członkiem moduł, interfejs lub dispinterface nie może być wywoływana arbitralnie.

## <a name="syntax"></a>Składnia

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>Parametry

*interfaces*<br/>
Jeden lub więcej interfejsów, które może nie być wywoływana arbitralnie obiektu COM. Ten parametr jest prawidłowy tylko w przypadku zastosowania do klasy.

## <a name="remarks"></a>Uwagi

**Ograniczeniami** atrybut C++ ma taką samą funkcjonalność jak [ograniczeniami](/windows/desktop/Midl/restricted) atrybutów w MIDL.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób użycia **ograniczeniami** atrybutu:

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
|**Dotyczy**|Metody interfejsu **interfejsu**, **klasy**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|**Klasa coclass** (po zastosowaniu do **klasy** lub **struktury**)|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)