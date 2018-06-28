---
title: requires_category — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.requires_category
dev_langs:
- C++
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3a6822773292fd651eaae3be5c00fb2b693a80a9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882319"
---
# <a name="requirescategory"></a>requires_category
Określa wymagany składnik kategorii klasy docelowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
     [ requires_category(   
  requires_category  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *requires_category*  
 Identyfikator kategorii wymagane.  
  
## <a name="remarks"></a>Uwagi  
 **Requires_category —** C++ atrybut określa kategorii składników wymaganych przez klasy docelowej. Aby uzyskać więcej informacji, zobacz [REQUIRED_CATEGORY](../atl/reference/category-macros.md#required_category).  
  
 Ten atrybut wymaga, aby [coclass](../windows/coclass.md), [progid](../windows/progid.md), lub [vi_progid —](../windows/vi-progid.md) atrybutu (lub inny atrybut, który oznacza jeden z nich) również będą stosowane do tego samego elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod wymaga, że obiekt implementować Kategoria formantu.  
  
```  
// cpp_attr_ref_requires_category.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="MyLibrary")];  
  
[ coclass, requires_category("CATID_Control"),  
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]  
class CMyClass {};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, `struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Co najmniej jeden z następujących: **coclass**, **progid**, lub **vi_progid —**.|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty COM](../windows/com-attributes.md)   
 [implements_category](../windows/implements-category.md)   
