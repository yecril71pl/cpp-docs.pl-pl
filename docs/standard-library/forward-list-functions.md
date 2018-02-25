---
title: "&lt;forward_list —&gt; funkcje | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: ce66354d2377e52043830925c3f4f880de996663
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list —&gt; funkcji
||  
|-|  
|[swap](#swap)|  
  
##  <a name="swap"></a>  Swap  
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
 [<forward_list>](../standard-library/forward-list.md)



