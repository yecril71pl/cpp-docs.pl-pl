---
title: "includelib — (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.includelib
dev_langs: C++
helpviewer_keywords: includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 31b9abdb8795d5814afe73fd7d48fb0e62ac8802
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="includelib-c"></a>includelib (C++)
Powoduje, że pliku .idl lub .h do uwzględnienia w pliku .idl wygenerowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ includelib(  
   name.idl  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *name.IDL*  
 Nazwa pliku .idl, które mają być dołączane jako część pliku .idl wygenerowany.  
  
## <a name="remarks"></a>Uwagi  
 `includelib` Atrybut C++ powoduje pliku .idl lub .h do uwzględnienia w pliku .idl wygenerowanego po `importlib` instrukcji.  
  
## <a name="example"></a>Przykład  
 Poniższy kod jest wyświetlany w pliku .cpp:  
  
```  
// cpp_attr_ref_includelib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[includelib("includelib.idl")];  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Dowolnego miejsca|  
|**Powtarzalne**|Tak|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Oddzielne atrybuty](../windows/stand-alone-attributes.md)   
 [Import](../windows/import.md)   
 [importidl —](../windows/importidl.md)   
 [obejmują](../windows/include-cpp.md)   
 [importlib](../windows/importlib.md)   
