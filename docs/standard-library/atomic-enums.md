---
title: '&lt;wyliczenia niepodzielne &gt;'
ms.date: 11/04/2016
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: d8a4e9196e27933c75a32c256114e968b55678a6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834898"
---
# <a name="ltatomicgt-enums"></a>&lt;wyliczenia niepodzielne &gt;

## <a name="memory_order-enum"></a><a name="memory_order_enum"></a> memory_order Wyliczenie

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

|Nazwa|Opis|
|-|-|
|`memory_order_relaxed`|Kolejność nie jest wymagana.|
|`memory_order_consume`|Operacja ładowania działa jako operacja użycia w lokalizacji pamięci.|
|`memory_order_acquire`|Operacja ładowania działa jako operacja pozyskiwania w lokalizacji pamięci.|
|`memory_order_release`|Operacja magazynu działa jako operacja zwolnienia w lokalizacji pamięci.|
|`memory_order_acq_rel`|Łączy `memory_order_acquire` i `memory_order_release` .|
|`memory_order_seq_cst`|Łączy `memory_order_acquire` i `memory_order_release` . Dostęp do pamięci oznaczony jako `memory_order_seq_cst` musi być sekwencyjnie spójny.|

## <a name="see-also"></a>Zobacz też

[\<atomic>](../standard-library/atomic.md)
