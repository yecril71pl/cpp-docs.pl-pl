---
title: "&lt;nowe&gt; definicje typów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
caps.latest.revision: "7"
manager: ghogen
ms.openlocfilehash: e23ea06002dc840997a0e7202f581cd81ef407c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltnewgt-typedefs"></a>&lt;nowe&gt; definicje typów
||  
|-|  
|[new_handler](#new_handler)|  
  
##  <a name="new_handler"></a>new_handler  
 Użyj punktów typu odpowiednie dla funkcji jako nowy program obsługi.  
  
```
typedef void (*new_handler)();
```  
  
### <a name="remarks"></a>Uwagi  
 Ten typ funkcji obsługi jest wywoływana przez **operatornew** lub `operator new[]` po nie może spełnić żądania dodatkowego miejsca do magazynowania.  
  
### <a name="example"></a>Przykład  
  Zobacz [set_new_handler —](../standard-library/new-functions.md#set_new_handler) na przykład za pomocą `new_handler` jako do wartości zwracanej.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Nowy >](../standard-library/new.md)



