---
title: '&lt;typy wyliczeniowe&gt;ów niepodzielnych'
ms.date: 11/04/2016
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: 14b816177593a9f6dade60e36676a37f724fc209
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422011"
---
# <a name="ltatomicgt-enums"></a>&lt;typy wyliczeniowe&gt;ów niepodzielnych

## <a name="memory_order_enum"></a>memory_order Wyliczenie

Dostarcza symboliczne nazwy dla operacji synchronizacji w lokalizacjach pamięci. Te operacje wpływają na sposób, w jaki przypisania w jednym wątku stają się widoczne w innym.

```cpp
typedef enum memory_order {
    memory_order_relaxed,
    memory_order_consume,
    memory_order_acquire,
    memory_order_release,
    memory_order_acq_rel,
    memory_order_seq_cst,
} memory_order;
```

### <a name="enumeration-members"></a>Elementy członkowskie wyliczenia

|||
|-|-|
|`memory_order_relaxed`|Kolejność nie jest wymagana.|
|`memory_order_consume`|Operacja ładowania działa jako operacja użycia w lokalizacji pamięci.|
|`memory_order_acquire`|Operacja ładowania działa jako operacja pozyskiwania w lokalizacji pamięci.|
|`memory_order_release`|Operacja magazynu działa jako operacja zwolnienia w lokalizacji pamięci.|
|`memory_order_acq_rel`|Łączy `memory_order_acquire` i `memory_order_release`.|
|`memory_order_seq_cst`|Łączy `memory_order_acquire` i `memory_order_release`. Dostęp do pamięci, które są oznaczone jako `memory_order_seq_cst` musi być sekwencyjnie spójny.|

## <a name="see-also"></a>Zobacz też

[\<niepodzielne >](../standard-library/atomic.md)
