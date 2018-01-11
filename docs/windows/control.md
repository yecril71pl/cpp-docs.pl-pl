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
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 00e9ce0a3e310ad9d07f41b0053ed5249a35a339
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
 [Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)   
