---
title: "registration_script — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.registration_script
dev_langs: C++
helpviewer_keywords: registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2260006e45407051f37e220d01cebd0ba8f797d7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="registrationscript"></a>registration_script
Wykonuje określoną rejestrację niestandardowych skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ registration_script(   
   script   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *skrypt*  
 Pełna ścieżka do pliku skryptu (.rgs) niestandardowych rejestracji. Wartość **Brak**, takich jak `script = "none"`, wskazuje, że klasa coclass nie ma rejestracji wymagań.  
  
## <a name="remarks"></a>Uwagi  
 **Registration_script —** atrybutu C++ wykonuje skryptu niestandardowego rejestracji określony przez **skryptu**. Jeśli ten atrybut nie jest określony, używany jest pliku .rgs standardowe (zawierający informacje dotyczące rejestrowania składnika). Aby uzyskać więcej informacji na plików .rgs, zobacz [składnik rejestru Alt (Rejestrator)](../atl/atl-registry-component-registrar.md).  
  
 Ten atrybut wymaga, aby [coclass](../windows/coclass.md), [progid](../windows/progid.md), lub [vi_progid —](../windows/vi-progid.md) atrybutu (lub inny atrybut, który oznacza jeden z nich) również będą stosowane do tego samego elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod określa, czy składnik ma skryptu rejestru o nazwie cpp_attr_ref_registration_script.rgs.  
  
```  
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
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**,`struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Co najmniej jeden z następujących: **coclass**, **progid**, lub **vi_progid —**.|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty COM](../windows/com-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [RDX](../windows/rdx.md)   
