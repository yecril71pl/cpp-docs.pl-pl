---
title: helpstringcontext — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringcontext
dev_langs:
- C++
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 16f113610beb4c6427af5627ea8dfd725e02600d
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570002"
---
# <a name="helpstringcontext"></a>helpstringcontext
Określa identyfikator tematu pomocy w pliku hlp lub chm.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ helpstringcontext(  
   contextID  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Identyfikator kontekstu*  
 32-bitowy identyfikator kontekstu pomocy w pliku pomocy.  
  
## <a name="remarks"></a>Uwagi  
 **Helpstringcontext —** atrybut C++ ma taką samą funkcjonalność jak [helpstringcontext —](http://msdn.microsoft.com/library/windows/desktop/aa366858) odl — atrybut.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// cpp_attr_ref_helpstringcontext.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[   object,   
   helpstring("help string"),   
   helpstringcontext(1),   
   uuid="11111111-1111-1111-1111-111111111111"  
]  
__interface IMyI   
{  
   HRESULT xx();  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, **interfejsu**, interfejs — metoda|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Atrybuty metody](../windows/method-attributes.md)   
 [Moduł](../windows/module-cpp.md)   