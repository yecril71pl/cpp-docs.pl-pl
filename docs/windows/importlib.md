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
ms.openlocfilehash: a4563d1b24b3af6e450a67a21d6a083f1839bc3e
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603071"
---
# <a name="importlib"></a>importlib
Sprawia, że typy, które już zostały skompilowane do do biblioteki typów, trwa tworzenie innej biblioteki typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ importlib(  
   "tlb_file"  
) ];  
```  
  
### <a name="parameters"></a>Parametry  
 *tlb_file*  
 Nazwa pliku .tlb w cudzysłowie, które mają zostać zaimportowany do biblioteki typów w bieżącym projekcie.  
  
## <a name="remarks"></a>Uwagi  
 **Importlib** atrybut C++ powoduje `importlib` instrukcji, które mają być umieszczone w bloku biblioteki pliku .idl wygenerowany. **Importlib** atrybut ma taką samą funkcjonalność jak [importlib](http://msdn.microsoft.com/library/windows/desktop/aa367050) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykład sposobu użycia **importlib**:  
  
```cpp  
// cpp_attr_ref_importlib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importlib("importlib.tlb")];  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Dowolne miejsce|  
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