---
title: Struktura TRACING_SESSION_STATISTICS
description: C++ Build Insights SDK TRACING_SESSION_OPTIONS odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 96cff3a231fd515ec1c52a048b8350a63ba46a39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323384"
---
# <a name="tracing_session_statistics-structure"></a>Struktura TRACING_SESSION_STATISTICS

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `TRACING_SESSION_STATISTICS` opisuje statystyki śledzenia, który został zebrany. Jego pola są ustawiane podczas zatrzymywania sesji śledzenia.

## <a name="syntax"></a>Składnia

```cpp
typedef struct TRACING_SESSION_STATISTICS_TAG
{
    unsigned long MSVCEventsLost;
    unsigned long MSVCBuffersLost;
    unsigned long SystemEventsLost;
    unsigned long SystemBuffersLost;

} TRACING_SESSION_STATISTICS;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `MSVCEventsLost` | Liczba zdarzeń MSVC, które zostały usunięte. |
| `MSVCBuffersLost` | Liczba buforów zdarzeń MSVC, które zostały usunięte. |
| `SystemEventsLost` | Liczba zdarzeń systemowych, które zostały usunięte. |
| `SystemBuffersLost` | Liczba buforów zdarzeń systemowych, które zostały usunięte. |

## <a name="remarks"></a>Uwagi

Ta struktura jest wypełniona podczas wywoływania następujących funkcji:

- [StopTracingSession (StopTracingSession)](../functions/stop-tracing-session.md)
- [StopTracingSessionA](../functions/stop-tracing-session-a.md)
- [StopTracingSessionW](../functions/stop-tracing-session-w.md)
- [StopAndAnalyzeTracingSession (StopAndAnalyzeTracingSession)](../functions/stop-and-analyze-tracing-session.md)
- [StopAndAnalyzeTracingSessionA](../functions/stop-and-analyze-tracing-session-a.md)
- [StopAndAnalyzeTracingSessionW](../functions/stop-and-analyze-tracing-session-w.md)
- [StopAndRelogTracingSession (StopAndRelogTracingSession)](../functions/stop-and-relog-tracing-session.md)
- [StopAndRelogTracingSessionA](../functions/stop-and-relog-tracing-session-a.md)
- [StopAndRelogTracingSessionW](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
