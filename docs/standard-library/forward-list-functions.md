---
title: "&lt;forward_list —&gt; funkcje | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: 6696f42d2ba7cb6daabb8f2ff38093911838c1ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list —&gt; funkcji
||  
|-|  
|[swap](#swap)|  
  
##  <a name="swap"></a>swap  
 Zamienia elementy dwie listy do przodu.  
  
```
void swap(
    forward_list <Type, Allocator>& left,
    forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`left`|Obiekt typu `forward_list`.|  
|`right`|Obiekt typu `forward_list`.|  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja szablonu wykonuje `left.swap(right)`.  
  
## <a name="see-also"></a>Zobacz też  
 [< forward_list — >](../standard-library/forward-list.md)



