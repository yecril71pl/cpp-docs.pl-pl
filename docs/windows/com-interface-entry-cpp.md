---
title: "com_interface_entry — (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.com_interface_entry
dev_langs: C++
helpviewer_keywords: com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 58c74602c4170cbe0816dcdf14e0196cca44af42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cominterfaceentry-c"></a>com_interface_entry (C++)
Dodaje interfejs wpis w mapie modelu COM klasy docelowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
     [ com_interface_entry(   
  com_interface_entry  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *com_interface_entry —*  
 Ciąg zawierający wpis tekstu. Aby uzyskać listę możliwych wartości, zobacz [com_interface_entry — makra](../atl/reference/com-interface-entry-macros.md).  
  
## <a name="remarks"></a>Uwagi  
 `com_interface_entry` Atrybut C++ Wstawia zawartość retransmitowanych w systemie ciągu znaków na mapie interfejsu COM obiektu docelowego. Jeśli atrybut jest stosowany jeden raz do obiektu docelowego, wpis zostanie wstawiony do początku istniejącej mapy interfejsu. Jeśli ten atrybut jest stosowany wielokrotnie do tego samego obiektu docelowego, wpisy są wstawiane na początku na mapie interfejsu w kolejności ich odbierania.  
  
 Ten atrybut wymaga, aby [coclass](../windows/coclass.md), [progid](../windows/progid.md), lub [vi_progid —](../windows/vi-progid.md) atrybutu (lub inny atrybut, który oznacza jeden z nich) również będą stosowane do tego samego elementu. Jeśli jest używany dowolny pojedynczy atrybut, pozostałe dwa są automatycznie stosowane. Na przykład jeśli **progid** zostanie zastosowana, **vi_progid —** i **coclass** również są stosowane.  
  
 Ponieważ pierwszy użycie `com_interface_entry` powoduje, że nowy interfejs do wstawienia na początku na mapie interfejsu musi mieć jedną z następujących typów com_interface_entry —:  
  
-   COM_INTERFACE_ENTRY —  
  
-   COM_INTERFACE_ENTRY_IID  
  
-   COM_INTERFACE_ENTRY2  
  
-   COM_INTERFACE_ENTRY2_IID  
  
 Dodatkowe sposoby użycia `com_interface_entry` atrybut można używać wszystkich obsługiwanych typów com_interface_entry —.  
  
 To ograniczenie jest konieczne, ponieważ ATL używa pierwszego wpis w mapie interfejsów jako tożsamość **IUnknown**; w związku z tym wpis musi być prawidłowym interfejsem. Na przykład następujący przykładowy kod jest nieprawidłowy, ponieważ pierwszy wpis w mapie interfejsów nie określono rzeczywistego interfejsu COM.  
  
```  
[ coclass, com_interface_entry =  
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"  
]  
   class CMyClass  
   {  
   };  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod dodaje dwóch wpisów do istniejącej mapy interfejsu COM z **CMyBaseClass**. Pierwszy jest standardowym interfejsem, a drugi ukrywa **IDebugTest** interfejsu.  
  
```  
// cpp_attr_ref_com_interface_entry.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name ="ldld")];  
  
[ object,  
  uuid("7dbebed3-d636-4917-af62-c767a720a5b9")]  
__interface IDebugTest{};  
  
[ object,  
  uuid("2875ceac-f94b-4087-8e13-d13dc167fcfc")]  
__interface IMyClass{};  
  
[ coclass,  
  com_interface_entry ("COM_INTERFACE_ENTRY (IMyClass)"),  
  com_interface_entry ("COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"),  
  uuid("b85f8626-e76e-4775-b6a0-4826a9e94af2")  
]  
  
class CMyClass: public IMyClass, public IDebugTest  
{  
};  
```  
  
 Wynikowa mapy obiektu COM dla **CMyBaseClass** wygląda następująco:  
  
```  
BEGIN_COM_MAP(CMyClass)  
    COM_INTERFACE_ENTRY (IMyClass)  
    COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)  
    COM_INTERFACE_ENTRY(IMyClass)  
    COM_INTERFACE_ENTRY2(IDispatch, IMyClass)  
    COM_INTERFACE_ENTRY(IDebugTest)  
    COM_INTERFACE_ENTRY(IProvideClassInfo)  
END_COM_MAP()  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**,`struct`|  
|**Powtarzalne**|Tak|  
|**Wymaganych atrybutów**|Co najmniej jeden z następujących: **coclass**, **progid**, lub **vi_progid —**.|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty COM](../windows/com-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)   
