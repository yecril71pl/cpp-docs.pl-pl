---
title: StopAndAnalyzeTracingSession (StopAndAnalyzeTracingSession)
description: Odwołanie do funkcji SDK StopAndAnalyzeTracingSession w programie C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9c9bd4a092c22dfcdfb6d463b74207ec11ee6d64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323703"
---
# <a name="stopandanalyzetracingsession"></a>StopAndAnalyzeTracingSession (StopAndAnalyzeTracingSession)

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `StopAndAnalyzeTracingSession` zatrzymuje trwającą sesję śledzenia i zapisuje wynikowy ślad w pliku tymczasowym. Sesja analizy jest następnie natychmiast uruchamiana przy użyciu pliku tymczasowego jako danych wejściowych. Pliki wykonywalne wywołujące tę funkcję muszą mieć uprawnienia administratora.

## <a name="syntax"></a>Składnia

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const char*                                   sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const wchar_t*                                sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>Parametry

*Nazwa_sesji*\
Nazwa sesji śledzenia, aby zatrzymać. Użyj tej samej nazwy sesji, co nazwa przeniesiona do [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)lub [StartTracingSessionW](start-tracing-session-w.md).

*numerOfAnalysisPasses*\
Liczba przechodzi analizy do uruchomienia na śledzenia. Śledzenia pobiera przekazywane przez pod warunkiem grupy analizatorraz na przebieg analizy.

*Statystyki*\
Wskaźnik do [obiektu TRACING_SESSION_STATISTICS.](../other-types/tracing-session-statistics-struct.md) `StopAndAnalyzeTracingSession`zapisuje statystyki kolekcji śledzenia w tym obiekcie przed zwróceniem.

*grupa analizatorów*\
Grupa analizatorów używana do analizy. Wywołanie [MakeStaticAnalyzerGroup,](make-static-analyzer-group.md) aby utworzyć grupę analizatora. Jeśli chcesz użyć grupy analizatorów dynamicznych uzyskanej z [MakeDynamicAnalyzerGroup,](make-dynamic-analyzer-group.md)najpierw hermetyzuj ją `MakeStaticAnalyzerGroup`wewnątrz grupy analizatorów statycznych, przekazując jej adres do .

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z [RESULT_CODE](../other-types/result-code-enum.md) wyliczenia.

::: moniker-end
