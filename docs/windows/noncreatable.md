---
title: "noncreatable — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.noncreatable
dev_langs: C++
helpviewer_keywords: noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb9f67b4efac28a1cacd6301c8ca849246f9a481
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="noncreatable"></a>noncreatable
Definiuje obiekt, który nie może występować samodzielnie.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[noncreatable]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Noncreatable —** atrybut C++ ma te same funkcje co [noncreatable —](http://msdn.microsoft.com/library/windows/desktop/aa367118) atrybutu MIDL i automatycznie jest przekazywana do wygenerowany. Plik IDL przez kompilator.  
  
 Jeśli ten atrybut jest używany w projekcie, który używa ATL, zachowanie zmiany atrybutów. Oprócz powyższych zachowanie również injects atrybut [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makra. To makro wskazuje ATL, że nie można utworzyć obiektu zewnętrznie.  
  
## <a name="example"></a>Przykład  
  
```  
// cpp_attr_ref_noncreatable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("11111111-1111-1111-1111-111111111111")]  
__interface A   
{  
};  
  
[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]  
class CMyClass : public A   
{  
   HRESULT xx();  
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
