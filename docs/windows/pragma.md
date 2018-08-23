---
title: pragma | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pragma
dev_langs:
- C++
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4f8ff470af7b7c825fb1c1dc7bf118e969a4b992
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603056"
---
# <a name="pragma"></a>pragma

Emituje określonego ciągu w pliku .idl wygenerowany bez znaków cudzysłowu.

## <a name="syntax"></a>Składnia

```cpp
[ pragma(
   pragma_statement
) ];
```

### <a name="parameters"></a>Parametry

*pragma_statement*  
Pragmę, której chcesz przejść do pliku .idl wygenerowany.

## <a name="remarks"></a>Uwagi

**Pragma** atrybut C++ ma taką samą funkcjonalność jak [pragma](http://msdn.microsoft.com/library/windows/desktop/aa367143) atrybutów w MIDL.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_pragma.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[pragma(pack(4))];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A
{
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Oddzielne atrybuty](../windows/stand-alone-attributes.md)  
[pakiet](../preprocessor/pack.md)  