---
title: Aggregatable | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.aggregatable
dev_langs:
- C++
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 66c85999e70e505176700ecaac69b75048ce2422
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595245"
---
# <a name="aggregatable"></a>aggregatable

Wskazuje, że klasa obsługuje agregację.

## <a name="syntax"></a>Składnia

```cpp
[ aggregatable(
   value
) ]
```

### <a name="parameters"></a>Parametry

*wartość* (opcjonalnie)  
Parametr, aby wskazać, kiedy obiekt COM może być agregowany:

- `never` Obiekt COM nie mogą być agregowane.

- `allowed` Obiekt COM można tworzyć bezpośrednio lub może być agregowany. Domyślnie włączone.

- `always` Obiekt COM nie można utworzyć bezpośrednio, a tylko można agregować. Gdy wywołujesz `CoCreateInstance` dla tego obiektu, należy określić obiekt agregacji `IUnknown` interfejsu (kontrolowanie `IUnknown`).

## <a name="remarks"></a>Uwagi

**Się agregowaniu** atrybut C++ ma taką samą funkcjonalność jak [się agregowaniu](http://msdn.microsoft.com/library/windows/desktop/aa366721) atrybutów w MIDL. Oznacza to, że kompilator będzie przekazywać **się agregowaniu** atrybutu za pomocą pliku .idl wygenerowany.

Ten atrybut wymaga, aby [coclass](../windows/coclass.md), [progid](../windows/progid.md), lub [vi_progid —](../windows/vi-progid.md) atrybutów (lub innego atrybutu, który oznacza jeden z nich) również będą stosowane do tego samego elementu. Jeśli dowolny pojedynczy atrybut jest używany, pozostałe dwa są automatycznie stosowane. Na przykład jeśli `progid` zastosowaniu `vi_progid` i `coclass` są również stosowane.

### <a name="atl-projects"></a>Projekty ATL

Jeśli ten atrybut jest używany w projekcie, który korzysta z biblioteki ATL, zachowanie zmiany atrybutów. Oprócz opisane wcześniej zachowanie atrybut dodaje również jedno z następujących makr do klasy docelowej:

|Wartość parametru|Wstawiono — makro|
|---------------------|--------------------|
|`Never`|[DECLARE_NOT_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|
|`Allowed`|[DECLARE_POLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|
|`Always`|[DECLARE_ONLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_aggregatable.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyModule")];

[ coclass, aggregatable(allowed),
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]
class CMyClass {};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Co najmniej jeden z następujących czynności: `coclass`, `progid`, lub `vi_progid`.|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty klasy](../windows/class-attributes.md)  
[Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[Agregacja](http://msdn.microsoft.com/library/windows/desktop/ms686558)  