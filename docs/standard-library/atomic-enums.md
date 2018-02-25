---
title: '&lt;Atomic&gt; wyliczenia | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
caps.latest.revision: 
helpviewer_keywords:
- std::memory_order
manager: ghogen
ms.openlocfilehash: 5f5c286375699d233d1bc9dadd3f44992309fa0a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltatomicgt-enums"></a>&lt;Atomic&gt; wyliczenia
  
##  <a name="memory_order_enum"></a>  memory_order wyliczenia  
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



