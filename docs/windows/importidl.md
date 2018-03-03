---
title: "importidl — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.importidl
dev_langs:
- C++
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cd3fb56898107b1eca7cd30e06d75d253a02655e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="importidl"></a>importidl
Wstawia pliku .idl określony w pliku .idl wygenerowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ importidl(  
   idl_file  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 `idl_file`  
 Określa nazwę pliku .idl, którego chcesz scalić z pliku .idl zostanie wygenerowany dla aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 **Importidl —** atrybutu C++ umieszcza sekcji poza blokiem biblioteki (w `idl_file`) w pliku .idl wygenerowanego programu i w sekcji biblioteki (w `idl_file`) w sekcji biblioteki programu .idl wygenerowanego pliku.  
  
 Chcesz użyć **importidl —**, na przykład, jeśli chcesz użyć pliku .idl kodowane ręcznie z pliku .idl wygenerowanego.  
  
## <a name="example"></a>Przykład  
  
```  
// cpp_attr_ref_importidl.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importidl("import.idl")];  
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
 [Import](../windows/import.md)   
 [importlib](../windows/importlib.md)   
 [obejmują](../windows/include-cpp.md)   
 [includelib —](../windows/includelib-cpp.md)   
