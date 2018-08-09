---
title: includelib — (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.includelib
dev_langs:
- C++
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d6f6a4dc4f23460b3661da4ed3775708cac9b6d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016180"
---
# <a name="includelib-c"></a>includelib (C++)
Powoduje, że pliku .idl lub .h, mają zostać uwzględnione w pliku .idl wygenerowany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[ includelib(  
   name.idl  
) ];  
```  
  
### <a name="parameters"></a>Parametry  
 *name.IDL*  
 Nazwa pliku .idl, którego mają być dołączane jako część pliku .idl wygenerowany.  
  
## <a name="remarks"></a>Uwagi  
 **Includelib —** atrybut C++ powoduje pliku .idl lub .h, mają zostać uwzględnione w pliku .idl wygenerowany po `importlib` instrukcji.  
  
## <a name="example"></a>Przykład  
 Poniższy kod jest pokazywana w pliku .cpp:  
  
```cpp  
// cpp_attr_ref_includelib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[includelib("includelib.idl")];  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Dowolne miejsce|  
|**Powtarzalne**|Tak|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Oddzielne atrybuty](../windows/stand-alone-attributes.md)   
 [Import](../windows/import.md)   
 [importidl —](../windows/importidl.md)   
 [Obejmują](../windows/include-cpp.md)   
 [importlib](../windows/importlib.md)   