---
title: '&lt;Atomic&gt; wyliczenia | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
caps.latest.revision: "11"
helpviewer_keywords: std::memory_order
manager: ghogen
ms.openlocfilehash: 4d0c60a908d795d8bf9fa7643471c6c9f29cc1cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltatomicgt-enums"></a>&lt;Atomic&gt; wyliczenia
  
##  <a name="memory_order_enum"></a>memory_order wyliczenia  
 Dostarcza nazw symbolicznych dla operacji synchronizacji w lokalizacji pamięci. Te operacje mają wpływ na sposób przydziały w jeden wątek stają się widoczne w innym.  
  
```
typedef enum memory_order {
    memory_order_relaxed,
    memory_order_consume,
    memory_order_acquire,
    memory_order_release,
    memory_order_acq_rel,
    memory_order_seq_cst,
} memory_order;
```  
  
### <a name="remarks"></a>Uwagi  
  
|||  
|-|-|  
|`memory_order_relaxed`|Kolejność nie wymagane.|  
|`memory_order_consume`|Operacja obciążenia działa jako operacją consume w lokalizacji pamięci.|  
|`memory_order_acquire`|Operacja obciążenia działa jako operację pobierania w lokalizacji pamięci.|  
|`memory_order_release`|Operacja magazynu działa jako operacja wersji w lokalizacji pamięci.|  
|`memory_order_acq_rel`|Łączy `memory_order_acquire` i `memory_order_release`.|  
|`memory_order_seq_cst`|Łączy `memory_order_acquire` i `memory_order_release`. Uzyskuje dostęp do pamięci, które są oznaczone jako `memory_order_seq_cst` musi być spójna sekwencyjnie.|  
  
## <a name="see-also"></a>Zobacz też  
 [\<niepodzielne >](../standard-library/atomic.md)



