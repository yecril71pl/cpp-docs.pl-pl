---
title: "&lt;nowe&gt; definicje typów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: cbcc542095ad8b75bbe632f741f43206e436b5e4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltnewgt-typedefs"></a>&lt;nowe&gt; definicje typów
||  
|-|  
|[new_handler](#new_handler)|  
  
##  <a name="new_handler"></a>  new_handler  
 Użyj punktów typu odpowiednie dla funkcji jako nowy program obsługi.  
  
```
typedef void (*new_handler)();
```  
  
### <a name="remarks"></a>Uwagi  
 Ten typ funkcji obsługi jest wywoływana przez **operatornew** lub `operator new[]` po nie może spełnić żądania dodatkowego miejsca do magazynowania.  
  
### <a name="example"></a>Przykład  
  Zobacz [set_new_handler —](../standard-library/new-functions.md#set_new_handler) na przykład za pomocą `new_handler` jako do wartości zwracanej.  
  
## <a name="see-also"></a>Zobacz też  
 [\<new>](../standard-library/new.md)



