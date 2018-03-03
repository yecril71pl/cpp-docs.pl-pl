---
title: agregowaniu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.aggregatable
dev_langs:
- C++
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ec044e18fdd8bcd21fbad8d2e46c847c876cc00d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="aggregatable"></a>aggregatable
Wskazuje, że klasa obsługuje agregacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ aggregatable(   
   value  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *wartość* (opcjonalnie)  
 Parametr wskazuje, kiedy można agregować obiektu COM:  
  
-   **nigdy nie** obiekt COM nie może być agregowany.  
  
-   **dozwolone** obiekt COM można tworzyć bezpośrednio lub może być agregowany. Domyślnie włączone.  
  
-   **zawsze** obiekt COM nie można bezpośrednio utworzyć i tylko może być agregowany. Podczas wywoływania `CoCreateInstance` dla tego obiektu, należy określić obiekt agregację **IUnknown** interfejsu (kontrolowanie **IUnknown**).  
  
## <a name="remarks"></a>Uwagi  
 **Agregowaniu** atrybut C++ ma te same funkcje co [agregowaniu](http://msdn.microsoft.com/library/windows/desktop/aa366721) MIDL atrybutu. Oznacza to, że kompilator będzie przekazać **agregowaniu** atrybutu za pomocą pliku .idl wygenerowany.  
  
 Ten atrybut wymaga, aby [coclass](../windows/coclass.md), [progid](../windows/progid.md), lub [vi_progid —](../windows/vi-progid.md) atrybutu (lub inny atrybut, który oznacza jeden z nich) również będą stosowane do tego samego elementu. Jeśli jest używany dowolny pojedynczy atrybut, pozostałe dwa są automatycznie stosowane. Na przykład jeśli **progid** zostanie zastosowana, **vi_progid —** i **coclass** również są stosowane.  
  
 **Projekty ATL**  
  
 Jeśli ten atrybut jest używany w projekcie, który używa ATL, zachowanie zmiany atrybutów. Oprócz opisane wcześniej zachowanie atrybutu dodaje również jedno z następujących makr do klasy docelowej:  
  
|Wartość parametru|Wstawione — makro|  
|---------------------|--------------------|  
|**Nigdy nie**|[DECLARE_NOT_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|  
|**Dozwolone**|[DECLARE_POLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|  
|**Zawsze**|[DECLARE_ONLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|  
  
## <a name="example"></a>Przykład  
  
```  
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
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**,`struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Co najmniej jeden z następujących: **coclass**, **progid**, lub **vi_progid —**.|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Agregacja](http://msdn.microsoft.com/library/windows/desktop/ms686558)   
