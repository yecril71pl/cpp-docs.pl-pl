---
title: importidl — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importidl
dev_langs:
- C++
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5284c631813271f5682343c74cff693d1ea785e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877478"
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
 [Obejmują](../windows/include-cpp.md)   
 [includelib —](../windows/includelib-cpp.md)   
