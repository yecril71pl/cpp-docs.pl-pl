---
title: implements_category — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.implements_category
dev_langs:
- C++
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6770f8303af63c66f0d1a656c2b36e034cc2be83
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879038"
---
# <a name="implementscategory"></a>implements_category
Określa kategorii składników zaimplementowany przez klasę docelowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ implements_category(  
   implements_category="uuid"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 **implements_category**  
 Identyfikator kategorii zaimplementowany.  
  
## <a name="remarks"></a>Uwagi  
 **Implements_category —** C++ atrybut określa kategorii składników zaimplementowany przez klasę docelowej. Polega to na tworzenie mapy kategorii i dodawanie oddzielne wpisy określone przez **implements_category —** atrybutu. Aby uzyskać więcej informacji, zobacz [co to są kategorii składników i jak są one działają?](http://msdn.microsoft.com/library/windows/desktop/ms694322).  
  
 Ten atrybut wymaga, aby [coclass](../windows/coclass.md), [progid](../windows/progid.md), lub [vi_progid —](../windows/vi-progid.md) atrybutu (lub inny atrybut, który oznacza jeden z nich) również będą stosowane do tego samego elementu. Jeśli jest używany dowolny pojedynczy atrybut, pozostałe dwa są automatycznie stosowane. Na przykład jeśli **progid** zostanie zastosowana, **vi_progid —** i **coclass** również są stosowane.  
  
## <a name="example"></a>Przykład  
 Poniższy kod określa, że następujący obiekt implementuje Kategoria formantu.  
  
```  
// cpp_attr_ref_implements_category.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="MyLib")];  
[ coclass, implements_category("CATID_Control"),  
  uuid("20a0d0cc-5172-40f5-99ae-5e032f3205ae")]  
class CMyClass {};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, `struct`|  
|**Powtarzalne**|Tak|  
|**Wymaganych atrybutów**|Jedną z następujących: **coclass**, **progid**, lub **vi_progid —**|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty COM](../windows/com-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [IMPLEMENTED_CATEGORY](../atl/reference/category-macros.md#implemented_category)   
 