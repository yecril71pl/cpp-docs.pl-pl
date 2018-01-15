---
title: "appobject — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.appobject
dev_langs: C++
helpviewer_keywords: appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19462987cf4f9b5cc295766a694f01b8b4fac8ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="appobject"></a>appobject
Identyfikuje coclass jako obiekt aplikacji, który jest skojarzony z aplikacją pełne .exe i wskazuje, że właściwości klasy coclass i funkcje są ogólnie dostępna w tym [biblioteki typów](../mfc/automation-clients-using-type-libraries.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[appobject]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Appobject —** atrybut C++ ma te same funkcje co [appobject —](http://msdn.microsoft.com/library/windows/desktop/aa366726) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia definicję prostą klasę poprzedzone blok atrybutu, która obejmuje **appobject —**:  
  
```  
// cpp_attr_ref_appobject.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];  
  
[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]  
__interface ICustom {};  
  
[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]  
class A : public ICustom {  
   int i;  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**,`struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|**coclass**|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)   
