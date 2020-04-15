---
title: TRACING_SESSION_MSVC_EVENT_FLAGS stałe
description: C++ Build Insights SDK TRACING_SESSION_MSVC_EVENT_FLAGS odwołania stałych.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_MSVC_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f7cf94221abc69f2069d02473d2ef1316ee8f0a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323478"
---
# <a name="tracing_session_msvc_event_flags-constants"></a>TRACING_SESSION_MSVC_EVENT_FLAGS stałe

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Stałe `TRACING_SESSION_MSVC_EVENT_FLAGS` są używane do opisania, które zdarzenia MSVC do zbierania podczas śledzenia. Użyj ich do zainicjowania `MsvcEventFlags` pola struktury [TRACING_SESSION_OPTIONS.](tracing-session-options-struct.md)

## <a name="syntax"></a>Składnia

```cpp
static const unsigned long long
    TRACING_SESSION_MSVC_EVENT_FLAGS_BASIC                                = 0x0001ULL;

static const unsigned long long
    TRACING_SESSION_MSVC_EVENT_FLAGS_FRONTEND_FILES                       = 0x0004ULL;

static const unsigned long long
    TRACING_SESSION_MSVC_EVENT_FLAGS_FRONTEND_TEMPLATE_INSTANTIATIONS     = 0x0008ULL;

static const unsigned long long
    TRACING_SESSION_MSVC_EVENT_FLAGS_BACKEND_FUNCTIONS                    = 0x1000ULL;

static const unsigned long long
    TRACING_SESSION_MSVC_EVENT_FLAGS_ALL                                  = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Elementy członkowskie

| Nazwa | Zdarzenia włączone przez tę flagę |
|--|--|
| `TRACING_SESSION_MSVC_EVENT_FLAGS_BASIC` | Ta flaga jest skojarzona z następującymi zdarzeniami. Jest domyślnie aktywowany przez SDK analizy kompilacji języka C++, nawet jeśli nie jest wyraźnie określony. Nie można wyłączyć tych zdarzeń.<br/><br/>[BACK_END_PASS](../event-table.md#back-end-pass)[BOTTOM_UP](../event-table.md#bottom-up)<br/>[C1_DLL](../event-table.md#c1-dll)<br/>[C2_DLL](../event-table.md#c2-dll)<br/>[CODE_GENERATION](../event-table.md#code-generation)<br/>[COMMAND_LINE](../event-table.md#command-line)<br/>[Kompilator](../event-table.md#compiler)<br/>[ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output)<br/>[EXP_OUTPUT](../event-table.md#exp-output)<br/>[FILE_INPUT](../event-table.md#file-input)<br/>[FRONT_END_PASS](../event-table.md#front-end-pass)<br/>[FRONT_END_PASS](../event-table.md#front-end-pass)<br/>[IMP_LIB_OUTPUT](../event-table.md#imp-lib-output)<br/>[LIB_OUTPUT](../event-table.md#lib-output)<br/>[Linker](../event-table.md#linker)<br/>[Ltcg](../event-table.md#ltcg)<br/>[OBJ_OUTPUT](../event-table.md#obj-output)<br/>[OPT_ICF](../event-table.md#opt-icf)<br/>[OPT_LBR](../event-table.md#opt-lbr)<br/>[OPT_REF](../event-table.md#opt-ref)<br/>[PRZEPUSTKA1](../event-table.md#pass1)<br/>[PRZEPUSTKA 2](../event-table.md#pass2)<br/>[PRE_LTCG_OPT_REF](../event-table.md#pre-ltcg-opt-ref)<br/>[Wątku](../event-table.md#thread)<br/>[TOP_DOWN](../event-table.md#top-down)<br/>[WHOLE_PROGRAM_ANALYSIS](../event-table.md#whole-program-analysis) |
| `TRACING_SESSION_MSVC_EVENT_FLAGS_FRONTEND_FILES` | [FRONT_END_FILE](../event-table.md#front-end-file) |
| `TRACING_SESSION_MSVC_EVENT_FLAGS_FRONTEND_TEMPLATE_INSTANTIATIONS` | [SYMBOL_NAME](../event-table.md#symbol-name)<br/>[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) |
| `TRACING_SESSION_MSVC_EVENT_FLAGS_BACKEND_FUNCTIONS` | [FORCE_INLINEE](../event-table.md#force-inlinee)<br/>[Funkcja](../event-table.md#function) |
| `TRACING_SESSION_MSVC_EVENT_FLAGS_ALL` | Ta flaga włącza wszystkie zdarzenia. |

::: moniker-end
