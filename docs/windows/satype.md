---
title: satype — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.satype
dev_langs:
- C++
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6562721cfdf1fb963a6af71e8a8665887fa4d4ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413110"
---
# <a name="satype"></a>satype

Określa typ danych `SAFEARRAY` struktury.

## <a name="syntax"></a>Składnia

```cpp
[ satype(
   data_type
) ]
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

[Atrybuty kompilatora](../windows/compiler-attributes.md)<br/>
[Atrybuty parametru](../windows/parameter-attributes.md)<br/>
[Atrybuty metody](../windows/method-attributes.md)<br/>
[id](../windows/id.md)  