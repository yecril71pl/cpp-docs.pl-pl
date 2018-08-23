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
ms.openlocfilehash: 462dba3caaef53e49203eab6d006ea59d7b23c0e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590376"
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

*data_type*  
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

[Atrybuty kompilatora](../windows/compiler-attributes.md)  
[Atrybuty parametru](../windows/parameter-attributes.md)  
[Atrybuty metody](../windows/method-attributes.md)  
[id](../windows/id.md)  