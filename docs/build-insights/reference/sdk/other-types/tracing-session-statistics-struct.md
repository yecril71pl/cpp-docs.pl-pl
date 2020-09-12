---
title: Struktura TRACING_SESSION_STATISTICS
description: Informacje o strukturze TRACING_SESSION_OPTIONS zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5f6126fb469dc13b814b91942fe9f7bc480ba3f1
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041188"
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
