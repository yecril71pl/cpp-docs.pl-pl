---
title: '&lt;wyliczenia atomowe&gt;'
ms.date: 11/04/2016
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: f41c5b238f74e85bc18e9ff5c3aa6a0050fe27e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376920"
---
# <a name="ltatomicgt-enums"></a>&lt;wyliczenia atomowe&gt;

## <a name="memory_order-enum"></a><a name="memory_order_enum"></a>Wyliczenie memory_order

Dostarcza symboliczne nazwy operacji synchronizacji w lokalizacjach pamięci. Te operacje wpływają na sposób przypisywania w jednym wątku stają się widoczne w innym.

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

### <a name="enumeration-members"></a>Członkowie wyliczenia

|||
|-|-|
|`memory_order_relaxed`|Nie jest wymagane zamawianie.|
|`memory_order_consume`|Operacja ładowania działa jako operacja zużywania w lokalizacji pamięci.|
|`memory_order_acquire`|Operacja ładowania działa jako operacja nabycia w lokalizacji pamięci.|
|`memory_order_release`|Operacja magazynu działa jako operacja zwalniania w lokalizacji pamięci.|
|`memory_order_acq_rel`|Łączy `memory_order_acquire` i `memory_order_release`.|
|`memory_order_seq_cst`|Łączy `memory_order_acquire` i `memory_order_release`. Dostęp do pamięci, `memory_order_seq_cst` które są oznaczone jako muszą być sekwencyjnie spójne.|

## <a name="see-also"></a>Zobacz też

[\<>atomowy](../standard-library/atomic.md)
