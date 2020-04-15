---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS stałe
description: C++ Build Insights SDK RELOG_RETENTION_SYSTEM_EVENT_FLAGS odwołania stałych.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7110f809a819357b31951c203c1fa6ac9fb9f42e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323469"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS stałe

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Stałe `RELOG_RETENTION_SYSTEM_EVENT_FLAGS` są używane do opisania, które zdarzenia systemowe należy zachować w śladu ponownie rejestrowane. Użyj ich do zainicjowania `SystemEventsRetentionFlags` pola struktury [RELOG_DESCRIPTOR.](relog-descriptor-struct.md)

## <a name="syntax"></a>Składnia

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Zachowaj zdarzenia systemu próbki procesora CPU w ponownie zarejestrowanym śladu. |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | Zachowaj wszystkie zdarzenia systemowe w ponownie zarejestrowanym śladu. |

## <a name="remarks"></a>Uwagi

::: moniker-end
