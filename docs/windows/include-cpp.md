---
title: obejmują (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.include
dev_langs:
- C++
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c21bb7cf58c3c397237768942d60f79958f3278a
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013564"
---
# <a name="include-c"></a>include (C++)
Określa jeden lub więcej plików nagłówka do uwzględnienia w pliku .idl wygenerowany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[ include(  
   header_file  
) ];  
```  
  
### <a name="parameters"></a>Parametry  
 *header_file*  
 Nazwa pliku, którego chcesz zawarte w pliku .idl wygenerowany.  
  
## <a name="remarks"></a>Uwagi  
 **Obejmują** atrybut C++ powoduje `#include` instrukcję, aby umieszczona pod `import "docobj.idl"` instrukcja w pliku .idl wygenerowany.  
  
 **Obejmują** atrybut C++ ma taką samą funkcjonalność jak [obejmują](http://msdn.microsoft.com/library/windows/desktop/aa367052) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykład sposobu użycia **obejmują**. W tym przykładzie include.h plik zawiera tylko `#include` instrukcji.  
  
```cpp  
// cpp_attr_ref_include.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[include(cpp_attr_ref_include.h)];  
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
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Oddzielne atrybuty](../windows/stand-alone-attributes.md)   
 [Import](../windows/import.md)   
 [importidl —](../windows/importidl.md)   
 [includelib —](../windows/includelib-cpp.md)   
 [importlib](../windows/importlib.md)   