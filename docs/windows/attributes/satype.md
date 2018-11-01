---
title: satype — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: 3d2d921e750adad0089df0d00590f256b56c732e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517692"
---
# <a name="satype"></a>satype

Określa typ danych `SAFEARRAY` struktury.

## <a name="syntax"></a>Składnia

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>Parametry

*data_type*<br/>
Typ danych dla `SAFEARRAY` struktury danych, który jest przekazywany jako parametr do metody interfejsu.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Interfejs parametru metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

## <a name="remarks"></a>Uwagi

**Satype —** C++ atrybut określa typ danych `SAFEARRAY`.

> [!NOTE]
> Poziom pośrednictwa zostanie usunięte ze `SAFEARRAY` wskaźnika w pliku .idl wygenerowany, w jaki sposób zostanie ona zadeklarowana w pliku .cpp.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_satype.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyModule")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A {
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[id](id.md)