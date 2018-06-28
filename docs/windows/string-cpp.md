---
title: ciąg (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.string
dev_langs:
- C++
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6bdcdc6557253f8be9c6ecb20300f2338ab35d07
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889023"
---
# <a name="string-c"></a>string (C++)
Oznacza to, że jednowymiarowej tablicy `char`, `wchar_t`, **bajtów** (lub równoważnego) tablicy lub wskaźnika do tablicy takie muszą być traktowane jako ciąg.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[string]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Ciąg** atrybut C++ ma te same funkcje co [ciąg](http://msdn.microsoft.com/library/windows/desktop/aa367270) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia **ciąg** w interfejsie i jako element typedef:  
  
```  
// cpp_attr_ref_string.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export, string] typedef char a[21];  
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   [id(1)] HRESULT Method3([in, string] char *pC);  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Tablicy lub wskaźnika do tablicy, interfejs parametrów, metody interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty tablicy](../windows/array-attributes.md)   
 [export](../windows/export.md)   
