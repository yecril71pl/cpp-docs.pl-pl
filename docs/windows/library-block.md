---
title: "library_block — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.library_block
dev_langs:
- C++
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab7c4c8c65d23dc252fb3ce228313fb36aa7e032
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="libraryblock"></a>library_block
Umieszcza konstrukcję wewnątrz bloku bibliotekę IDL.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[library_block]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Po umieszczeniu konstrukcję wewnątrz bloku biblioteki upewnieniu się, że zostaną przekazane do biblioteki typów, niezależnie od tego, czy odwołuje się do. Domyślnie tylko konstrukcje zmodyfikowany przez [coclass](../windows/coclass.md), [dispinterface](../windows/dispinterface.md), i [idl_module](../windows/idl-module.md) atrybuty są umieszczane w bloku biblioteki.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie niestandardowy interfejs jest umieszczony wewnątrz bloku biblioteki.  
  
```  
// cpp_attr_ref_library_block.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib")];  
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface IMyInterface {  
   HRESULT f1();  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Dowolnego miejsca|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty kompilatora](../windows/compiler-attributes.md)   
 [Oddzielne atrybuty](../windows/stand-alone-attributes.md)   
