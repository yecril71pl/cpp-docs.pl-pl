---
title: "powiązania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.bindable
dev_langs: C++
helpviewer_keywords: bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5266bca832a128242bcbbc8904ad9650e4432fe2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="bindable"></a>bindable
Wskazuje, że właściwość obsługuje powiązanie danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[bindable]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Powiązania** atrybut C++ ma te same funkcje co [powiązania](http://msdn.microsoft.com/library/windows/desktop/aa366738) MIDL atrybutu. Można go używać na właściwości zdefiniowane z [propget](../windows/propget.md), [propput](../windows/propput.md), lub [propputref](../windows/propputref.md) atrybutów, albo ręcznie zdefiniować można powiązać metodę.  
  
 Poniższe przykłady MFC Pokaż stosowania **powiązania**:  
  
-   [Próbki kontrolki: Kontrolki ActiveX MFC na podstawie](http://msdn.microsoft.com/en-us/a44adf86-0ba0-4504-bedb-512b6cba2e63)  
  
-   [Próbka OK: Formant ActiveX](http://msdn.microsoft.com/en-us/9ba34d04-280e-49f4-90ae-41a6be44c95b)  
  
-   [Przykład TESTHELP: Formantu ActiveX Pomocy i etykietki narzędzi](http://msdn.microsoft.com/en-us/d822861d-c6f0-4d0a-ad11-970eebb1e8cd)  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób korzystania **powiązania** we właściwości:  
  
```  
// cpp_attr_ref_bindable.cpp  
// compile with: /LD  
#include <windows.h>  
[  
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"),  
   dispinterface,  
   helpstring("property demo Interface")  
]  
__interface IPropDemo : IDispatch {  
  
   [propget, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);  
   [propput, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);  
   [id(3), bindable, propget] HRESULT Object([out, retval] IDispatch **ppObj);  
   [id(3), bindable, propputref] HRESULT Object([in] IDispatch* pObj);     
   [id(-552), helpstring("method AboutBox")] HRESULT AboutBox();  
};  
  
[ module(name="PropDemoLib", uuid="479B29E2-9A2C-11D0-B696-00A0C903487A", version="1.0", helpstring="property demo") ];  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Metody interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty — metoda](../windows/method-attributes.md)   
 [defaultbind —](../windows/defaultbind.md)   
 [displaybind —](../windows/displaybind.md)   
 [immediatebind —](../windows/immediatebind.md)   
 [requestedit](../windows/requestedit.md)   
