---
title: scheduler_interface — Struktura
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: 99a3ea8b6ad1f23b4f3d54b7f2f406a3d115b374
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283374"
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

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
