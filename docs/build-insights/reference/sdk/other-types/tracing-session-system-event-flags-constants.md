---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS stałe
description: C++ Build Insights SDK TRACING_SESSION_SYSTEM_EVENT_FLAGS odwołania stałych.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 264d697cc905eb6b44c8ec7de835a552976f0eb8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323269"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS stałe

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Stałe `TRACING_SESSION_SYSTEM_EVENT_FLAGS` są używane do opisania, które zdarzenia systemowe do zbierania podczas śledzenia. Użyj ich do zainicjowania `SystemEventFlags` pola struktury [TRACING_SESSION_OPTIONS.](tracing-session-options-struct.md)

## <a name="syntax"></a>Składnia

```cpp
static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT      = 0x1ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES  = 0x2ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL          = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Elementy członkowskie

| Nazwa | Zdarzenia włączone przez tę flagę |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | Ta flaga jest domyślnie aktywowana przez SDK aplikacji C++ Build Insights, nawet jeśli nie jest ona wyraźnie określona. Umożliwia podstawowe zdarzenia systemowe, które są wymagane przez C++ Build Insights do poprawnego działania. Zdarzenia włączone przez tę flagę zawierają informacje o procesach, wątkach i ładowaniu obrazu. Nie można wyłączyć tych zdarzeń. |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Próbki procesora |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | Ta flaga włącza wszystkie zdarzenia systemowe. |

::: moniker-end
