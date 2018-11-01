---
title: '&lt;Atomic&gt; Typy wyliczeniowe'
ms.date: 11/04/2016
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: 03247f6abd01b00fbbed3b33016cd4a12d8a13f8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543755"
---
# <a name="ltatomicgt-enums"></a>&lt;Atomic&gt; Typy wyliczeniowe

## <a name="memory_order_enum"></a>  memory_order wyliczenia

Dostarcza symbolicznych nazw dla operacji synchronizacji w lokalizacji pamięci. Operacje te wpływają na jak przydziały w jednym wątku stają się widoczne w innym.

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
|`memory_order_relaxed`|Kolejność nie wymagana.|
|`memory_order_consume`|Operacja ładowania działa jako operacja zużywania w lokalizacji pamięci.|
|`memory_order_acquire`|Operacja ładowania działa jako operacja nabywania w lokalizacji pamięci.|
|`memory_order_release`|Operacja magazynowania działa jako operacja zwalniania w lokalizacji pamięci.|
|`memory_order_acq_rel`|Łączy `memory_order_acquire` i `memory_order_release`.|
|`memory_order_seq_cst`|Łączy `memory_order_acquire` i `memory_order_release`. Dostępy do pamięci, które są oznaczone jako `memory_order_seq_cst` muszą być kolejno spójne.|

## <a name="see-also"></a>Zobacz także

[\<niepodzielne >](../standard-library/atomic.md)<br/>
