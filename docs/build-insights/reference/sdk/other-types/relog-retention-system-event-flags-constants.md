---
title: Stałe RELOG_RETENTION_SYSTEM_EVENT_FLAGS
description: Zestaw C++ SDK usługi Build insights RELOG_RETENTION_SYSTEM_EVENT_FLAGS informacje stałe.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 74afc10faa26ba39a669a05aa3e3cabd1a211293
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332321"
---
# <a name="relog_retention_system_event_flags-constants"></a>Stałe RELOG_RETENTION_SYSTEM_EVENT_FLAGS

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Stałe `RELOG_RETENTION_SYSTEM_EVENT_FLAGS` są używane do opisania zdarzeń systemowych, które mają być przechowywane w ponownie zarejestrowanym śledzeniu. Użyj ich, aby zainicjować pole `SystemEventsRetentionFlags` struktury [RELOG_DESCRIPTOR](relog-descriptor-struct.md) .

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
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Zachowaj Przykładowe zdarzenia systemowe dotyczące procesora podczas ponownego rejestrowania śledzenia. |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | Zachowaj wszystkie zdarzenia systemowe w rejestrowanym śladzie. |

## <a name="remarks"></a>Uwagi

::: moniker-end
