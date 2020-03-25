---
title: registration_script (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.registration_script
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
ms.openlocfilehash: 780f3d41676d01458f47542d6f0862a278edff6a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214581"
---
# <a name="registration_script"></a>registration_script

Wykonuje określony skrypt rejestracji niestandardowej.

## <a name="syntax"></a>Składnia

```cpp
[ registration_script(script) ]
```

### <a name="parameters"></a>Parametry

*napisy*<br/>
Pełna ścieżka do pliku skryptu rejestracji niestandardowej (RGS). Wartość **none**, taka jak `script = "none"`, wskazuje, że Klasa coclass nie ma wymagań dotyczących rejestracji.

## <a name="remarks"></a>Uwagi

Atrybut **registration_script** C++ wykonuje niestandardowy skrypt rejestracji określony przez *skrypt*. Jeśli ten atrybut nie jest określony, używany jest standardowy plik. RGS (zawierający informacje dotyczące rejestrowania składnika). Aby uzyskać więcej informacji na temat plików. RGS, zobacz [składnik rejestru ATL (Rejestrator)](../../atl/atl-registry-component-registrar.md).

Ten atrybut wymaga, aby atrybut [coclass](coclass.md), [ProgID](progid.md)lub [vi_progid](vi-progid.md) (lub inny atrybut, który implikuje jeden z tych) został również zastosowany do tego samego elementu.

## <a name="example"></a>Przykład

Poniższy kod określa, że składnik ma skrypt rejestru o nazwie cpp_attr_ref_registration_script. RGS.

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
|**Dotyczy**|**Klasa**, **Struktura**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Co najmniej jeden z następujących elementów: `coclass`, `progid`lub `vi_progid`.|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[rdx](rdx.md)
