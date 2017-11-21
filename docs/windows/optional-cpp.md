---
title: opcjonalne (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.optional
dev_langs: C++
helpviewer_keywords: optional attribute
ms.assetid: 86656a66-8e11-4589-8e30-9b0f34eeed03
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fb1ae05d7b674f3f1d2c984792bb2bd53dd3de30
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="optional-c"></a>optional (C++)
Określa opcjonalny parametr dla funkcji członkowskiej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[optional]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Opcjonalne** atrybut C++ ma te same funkcje co [opcjonalne](http://msdn.microsoft.com/library/windows/desktop/aa367132) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób **opcjonalne** może być używany:  
  
```  
// cpp_attr_ref_optional.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl : IDispatch  
{  
   [id(1)] long procedure ([in, optional] VARIANT i);  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Parametr — interfejs|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty parametrów](../windows/parameter-attributes.md)   
