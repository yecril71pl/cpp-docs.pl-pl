---
title: Opcjonalnie (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.optional
helpviewer_keywords:
- optional attribute
ms.assetid: 86656a66-8e11-4589-8e30-9b0f34eeed03
ms.openlocfilehash: bc6422ff652cfaba5fa71285294b93c1f0e8990e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407591"
---
# <a name="optional-c"></a>optional (C++)

Określa opcjonalny parametr dla funkcji członkowskiej.

## <a name="syntax"></a>Składnia

```cpp
[optional]
```

## <a name="remarks"></a>Uwagi

**Opcjonalne** atrybut C++ ma taką samą funkcjonalność jak [opcjonalne](/windows/desktop/Midl/optional) atrybutów w MIDL.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób **opcjonalne** mogą być używane:

```cpp
// cpp_attr_ref_optional.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] long procedure ([in, optional] VARIANT i);
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Parametr interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)