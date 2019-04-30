---
title: odl (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.odl
helpviewer_keywords:
- odl attribute
ms.assetid: 75dcb314-b50f-4a63-9180-507ac1bc78f3
ms.openlocfilehash: 90f9f1df23542138b2fac0dcfe0e122f1993d805
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407643"
---
# <a name="odl"></a>odl

Identyfikuje interfejs jako interfejs język opisu obiektów (ODL). Nie jest wymagane przez kompilator MIDL **odl** atrybutu; uznaje się tylko na potrzeby utrzymywania zgodności z starsze .odl — pliki.

## <a name="syntax"></a>Składnia

```cpp
[odl]
```

## <a name="remarks"></a>Uwagi

**Odl** atrybut C++ ma taką samą funkcjonalność jak [odl](/windows/desktop/Midl/odl) atrybutów w MIDL.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_odl.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLIb")];

[odl, oleautomation, dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyInterface
{
   HRESULT x();
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
class cmyClass : public IMyInterface
{
public:
   HRESULT x(){}
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interface**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)