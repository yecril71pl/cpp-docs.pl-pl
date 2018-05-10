---
title: źródło (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.source
dev_langs:
- C++
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 11ee58fb2d500a7194fb08ee18b1af5cc7897830
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="source-c"></a>source (C++)
W klasie określa interfejsów źródłowego obiektu COM dla punkty połączenia. W właściwości lub metody oznacza, że element członkowski zwraca obiekt lub Typ VARIANT, który jest źródłem zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ source(  
   interfaces  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `interfaces`  
 Jeden lub więcej interfejsów, określanie po zastosowaniu źródło atrybutu do klasy. Ten parametr nie jest używany, gdy źródło jest stosowany do właściwości lub metody.  
  
## <a name="remarks"></a>Uwagi  
 **Źródła** atrybut C++ ma te same funkcje co [źródła](http://msdn.microsoft.com/library/windows/desktop/aa367166) MIDL atrybutu.  
  
 Można użyć [domyślne](../windows/default-cpp.md) atrybutu, aby określić domyślny interfejs źródłowy dla obiekt.  
  
## <a name="example"></a>Przykład  
  
```  
// cpp_attr_ref_source.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid(11111111-1111-1111-1111-111111111111)]  
__interface b  
{  
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]  
   HRESULT get_I([out, retval]long *i);  
};  
  
[object, uuid(11111111-1111-1111-1111-111111111131)]  
__interface c  
{  
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]   
   HRESULT et_I([out, retval]long *i);  
};  
  
[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]  
class N : public b  
{  
};  
  
[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]  
class NN : public b  
{  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, `struct`, `interface`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|**coclass** (gdy są stosowane do klasy lub struktury)|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Atrybuty — metoda](../windows/method-attributes.md)   
 [coclass](../windows/coclass.md)   
