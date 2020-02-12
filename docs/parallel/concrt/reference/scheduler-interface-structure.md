---
title: scheduler_interface — Struktura
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: 36feff80cab1c5d301c009a581b869d5c2bad5e9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142147"
---
# <a name="scheduler_interface-structure"></a>scheduler_interface — Struktura

Interfejs usługi Scheduler

## <a name="syntax"></a>Składnia

```cpp
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[scheduler_interface:: Schedule](#schedule)||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`scheduler_interface`

## <a name="requirements"></a>Wymagania

**Nagłówek:** pplinterface. h

**Przestrzeń nazw:** współbieżność

## <a name="schedule"></a>scheduler_interface:: Schedule — Metoda

```cpp
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
