---
title: helpstringdll — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringdll
dev_langs:
- C++
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d7cb3ab5fc624494d3292cd7a47031782ce7da70
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877348"
---
# <a name="helpstringdll"></a>helpstringdll
Określa nazwę biblioteki DLL, aby wykonać wyszukiwanie ciągu dokumentu (lokalizacja).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ helpstringdll(  
   "string"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `string`  
 Biblioteki DLL, wykonać dokumentu ciąg wyszukiwania.  
  
## <a name="remarks"></a>Uwagi  
 **Helpstringdll —** atrybut C++ ma te same funkcje co [helpstringdll —](http://msdn.microsoft.com/library/windows/desktop/aa366860) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
  
```  
// cpp_attr_ref_helpstringdll.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib", helpstringdll="xx.dll")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI   
{  
   HRESULT xxx();  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, `interface`, interfejsu — metoda|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Atrybuty metody](../windows/method-attributes.md)   
