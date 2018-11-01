---
title: registration_script — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.registration_script
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
ms.openlocfilehash: 304d4139cb1adbbb7c345cd3ce6f7fc985907712
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555132"
---
# <a name="registrationscript"></a>registration_script

Wykonuje określoną rejestrację niestandardowego skryptu.

## <a name="syntax"></a>Składnia

```cpp
[ registration_script(script) ]
```

### <a name="parameters"></a>Parametry

*skrypt*<br/>
Pełna ścieżka do pliku skryptu (.rgs) niestandardową rejestrację. Wartość **Brak**, takich jak `script = "none"`, wskazuje, czy klasa coclass nie ma żadnych wymagań dotyczących rejestracji.

## <a name="remarks"></a>Uwagi

**Registration_script —** atrybutów języka C++ uruchamia skrypt niestandardową rejestrację, określony przez *skryptu*. Jeśli ten atrybut nie jest określony, plik standard .rgs (zawierający informacje dotyczące rejestrowania składnika) jest używany. Aby uzyskać więcej informacji na temat plików .rgs, zobacz [składnik rejestru Alt (Rejestrator)](../../atl/atl-registry-component-registrar.md).

Ten atrybut wymaga, aby [coclass](coclass.md), [progid](progid.md), lub [vi_progid —](vi-progid.md) atrybutów (lub innego atrybutu, który oznacza jeden z nich) również będą stosowane do tego samego elementu.

## <a name="example"></a>Przykład

Poniższy kod określa, że składnik zawiera skrypt rejestru o nazwie cpp_attr_ref_registration_script.rgs.

```cpp
// cpp_attr_ref_registration_script.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="REG")];

[object, uuid("d9cd196b-6836-470b-9b9b-5b04b828e5b0")]
__interface IFace {};

// requires "cpp_attr_ref_registration_script.rgs"
// create sample .RGS file "cpp_attr_ref_registration_script.rgs" if it does not exist
[ coclass, registration_script(script="cpp_attr_ref_registration_script.rgs"),
  uuid("50d3ad42-3601-4f26-8cfe-0f1f26f98f67")]
class CMyClass:public IFace {};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Co najmniej jeden z następujących czynności: `coclass`, `progid`, lub `vi_progid`.|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[rdx](rdx.md)