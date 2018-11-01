---
title: scheduler_interface — Struktura
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: 9fa51aa5bd1fdea4eb1c35488654f0b5003e2efe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612774"
---
# <a name="schedulerinterface-structure"></a>scheduler_interface — Struktura

Interfejs harmonogramu

## <a name="syntax"></a>Składnia

```
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[scheduler_interface::schedule](#schedule)||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`scheduler_interface`

## <a name="requirements"></a>Wymagania

**Nagłówek:** pplinterface.h

**Namespace:** współbieżności

##  <a name="schedule"></a>  scheduler_interface::Schedule — metoda

```
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
