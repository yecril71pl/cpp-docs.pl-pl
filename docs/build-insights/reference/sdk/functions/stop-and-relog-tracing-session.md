---
title: StopAndRelogTracingSession (StopAndRelogTracingSession)
description: Odwołanie do funkcji SDK StopAndRelogTracingSession w programie C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1f6f5af63d25504226707d977791430463374328
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323668"
---
# <a name="stopandrelogtracingsession"></a>StopAndRelogTracingSession (StopAndRelogTracingSession)

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `StopAndRelogTracingSession` zatrzymuje trwającą sesję śledzenia i zapisuje wynikowy ślad w pliku tymczasowym. Sesja ponownego rejestrowania jest natychmiast uruchamiana przy użyciu pliku tymczasowego jako danych wejściowych. Końcowy ślad ponownie zarejestrowany wyprodukowany przez sesję ponownego rejestrowania jest zapisywany w pliku określonym przez wywołującego. Pliki wykonywalne wywołujące tę funkcję muszą mieć uprawnienia administratora.

## <a name="syntax"></a>Składnia

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const char*                                   sessionName,
    const char*                                   outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const wchar_t*                                sessionName,
    const wchar_t*                                outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>Parametry

*Nazwa_sesji*\
Nazwa sesji śledzenia, aby zatrzymać. Użyj tej samej nazwy sesji, co nazwa przeniesiona do [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)lub [StartTracingSessionW](start-tracing-session-w.md).

*plik danych wyjściowych*\
Plik, w którym można zapisać relogged śledzenia produkowane przez sesji ponownego rejestrowania.

*Statystyki*\
Wskaźnik do [obiektu TRACING_SESSION_STATISTICS.](../other-types/tracing-session-statistics-struct.md) `StopAndRelogTracingSession`zapisuje statystyki kolekcji śledzenia w tym obiekcie przed zwróceniem.

*numerOfAnalysisPasses*\
Liczba przechodzi analizy do uruchomienia na śledzenia. Śledzenia pobiera przekazywane przez pod warunkiem grupy analizatorraz na przebieg analizy.

*systemEventsReentionSlags*\
Maska bitowa [RELOG_RETENTION_SYSTEM_EVENT_FLAGS,](../other-types/relog-retention-system-event-flags-constants.md) która określa, które zdarzenia ETW systemu należy przechowywać w ponownie zarejestrowanym śladu.

*grupa analizatorów*\
Grupa analizatorów używana do fazy analizy sesji ponownego rejestrowania. Wywołanie [MakeStaticAnalyzerGroup,](make-static-analyzer-group.md) aby utworzyć grupę analizatora. Jeśli chcesz użyć grupy analizatorów dynamicznych uzyskanej z [MakeDynamicAnalyzerGroup,](make-dynamic-analyzer-group.md)najpierw hermetyzuj ją `MakeStaticAnalyzerGroup`wewnątrz grupy analizatorów statycznych, przekazując jej adres do .

*grupa relogger*\
Grupa reloggera, która ponownie zasłania zdarzenia do pliku śledzenia określonego w *pliku outputLogFile*. Wywołanie [MakeStaticReloggerGroup,](make-static-relogger-group.md) aby utworzyć grupę relogger. Jeśli chcesz użyć dynamicznej grupy reloggera uzyskanej z [MakeDynamicReloggerGroup,](make-dynamic-relogger-group.md)najpierw hermetyzuj ją `MakeStaticReloggerGroup`wewnątrz statycznej grupy reloggerów, przekazując jej adres do .

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z [RESULT_CODE](../other-types/result-code-enum.md) wyliczenia.

### <a name="remarks"></a>Uwagi

Śledzenia danych wejściowych jest przekazywana przez numer grupy *analizatoraOfAnalysisPasses* razy. Nie ma podobnej opcji ponownego rejestrowania przebiegów. Śledzenie jest przekazywane koryta grupy relogger tylko raz, po zakończeniu wszystkich przebiegów analizy.

Ponowne rejestrowanie zdarzeń systemowych, takich jak próbki procesora CPU z klasy reloggera nie jest obsługiwane. Użyj *parametru systemEventsRetentionFlags,* aby zdecydować, które zdarzenia systemowe mają być utrzymywane w śledzenia danych wyjściowych.

::: moniker-end
