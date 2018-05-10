---
title: importlib | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importlib
dev_langs:
- C++
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c21b97e50fa03861245a0c0881963387dd8a3102
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="importlib"></a>importlib
Powoduje, że typy, które już zostały skompilowane w innej bibliotece typu dostępne do tworzenia biblioteki typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ importlib(  
   "tlb_file"  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *tlb_file*  
 Nazwa pliku .tlb w cudzysłowie, które mają zostać zaimportowane do bieżącego projektu biblioteki typów.  
  
## <a name="remarks"></a>Uwagi  
 **Importlib** atrybut C++ powoduje `importlib` instrukcji, które mają być umieszczone w bloku biblioteki pliku .idl wygenerowany. **Importlib** atrybut ma te same funkcje co [importlib](http://msdn.microsoft.com/library/windows/desktop/aa367050) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykład sposobu użycia **importlib**:  
  
```  
// cpp_attr_ref_importlib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importlib("importlib.tlb")];  
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
 [importidl —](../windows/importidl.md)   
 [Obejmują](../windows/include-cpp.md)   
 [includelib —](../windows/includelib-cpp.md)