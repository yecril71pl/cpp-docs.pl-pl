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
ms.openlocfilehash: 1de680b2598a9439338986c283a4041482642fa0
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015761"
---
# <a name="importidl"></a>importidl
Wstawia pliku .idl określony w pliku .idl wygenerowany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[ importidl(  
   idl_file  
) ];  
```  
  
### <a name="parameters"></a>Parametry  
 *idl_file*  
 Określa nazwę pliku .idl, którego chcesz scalić z pliku .idl, którego zostanie wygenerowany dla aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 **Importidl —** atrybut C++ umieszcza sekcji poza blokiem biblioteki (w *idl_file*) w pliku .idl wygenerowanego programu i w sekcji biblioteki (w *idl_file*) w bibliotece części programu generowane pliku .idl.  
  
 Możesz chcieć użyć **importidl —**, na przykład, aby za pomocą pliku .idl wygenerowany przy użyciu pliku .idl kodowane ręcznie.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// cpp_attr_ref_importidl.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importidl("import.idl")];  
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
 [importlib](../windows/importlib.md)   
 [Obejmują](../windows/include-cpp.md)   
 [includelib —](../windows/includelib-cpp.md)   