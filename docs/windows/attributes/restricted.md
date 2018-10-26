---
title: ograniczone (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.restricted
dev_langs:
- C++
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb13132c651323fcdffef2c06215314ad193c91d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071105"
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

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)