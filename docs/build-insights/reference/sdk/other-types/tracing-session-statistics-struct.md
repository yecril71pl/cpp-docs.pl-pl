---
title: Struktura TRACING_SESSION_STATISTICS
description: Dowiedz się więcej o zestawie SDK usługi Build Insights dla programu C++ TRACING_SESSION_STATISTICS.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c1db302d9e816591624f0fc63633351d32684097
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742765"
---
# <a name="tracing_session_statistics-structure"></a>Struktura TRACING_SESSION_STATISTICS

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`TRACING_SESSION_STATISTICS`Struktura zawiera informacje statystyczne na temat zebranych śladów. Jego pola są ustawiane podczas zatrzymywania sesji śledzenia.

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

| Nazwa | Opis |
|--|--|
| `MSVCEventsLost` | Liczba porzuconych zdarzeń MSVC. |
| `MSVCBuffersLost` | Liczba porzuconych buforów zdarzeń MSVC. |
| `SystemEventsLost` | Liczba porzuconych zdarzeń systemowych. |
| `SystemBuffersLost` | Liczba porzuconych buforów zdarzeń systemu. |

## <a name="remarks"></a>Uwagi

Ta struktura jest wypełniana podczas wywoływania następujących funkcji:

- [StopTracingSession](../functions/stop-tracing-session.md)
- [StopTracingSessionA](../functions/stop-tracing-session-a.md)
- [StopTracingSessionW](../functions/stop-tracing-session-w.md)
- [StopAndAnalyzeTracingSession](../functions/stop-and-analyze-tracing-session.md)
- [StopAndAnalyzeTracingSessionA](../functions/stop-and-analyze-tracing-session-a.md)
- [StopAndAnalyzeTracingSessionW](../functions/stop-and-analyze-tracing-session-w.md)
- [StopAndRelogTracingSession](../functions/stop-and-relog-tracing-session.md)
- [StopAndRelogTracingSessionA](../functions/stop-and-relog-tracing-session-a.md)
- [StopAndRelogTracingSessionW](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
