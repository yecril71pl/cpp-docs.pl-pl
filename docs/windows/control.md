---
title: Formant | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.control
dev_langs: C++
helpviewer_keywords: Control attribute
ms.assetid: 3d046bb2-4afe-4cb8-a762-233b296e1975
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 72326b5ce7aedfd03f93688e7890fdfab9b827f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="control"></a>— formant
Określa, że typ zdefiniowany przez użytkownika jest formantu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[control]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Kontroli** atrybut oznacza [coclass](../windows/coclass.md) atrybutu. **Kontroli** atrybut C++ ma te same funkcje co [kontroli](http://msdn.microsoft.com/library/windows/desktop/aa366764) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
  
```  
// cpp_attr_ref_control.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="Test", control=true)];  
  
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
};  
  
[coclass, control, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]  
class CTest : public ICustom {};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**,`struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
