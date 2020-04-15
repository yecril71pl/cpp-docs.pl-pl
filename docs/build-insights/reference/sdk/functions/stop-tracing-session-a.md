---
title: StopTracingSessionA
description: Odwołanie do funkcji SDK StopTracingSessiona w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 15560ecf4959ccda0d617c09d3645750210f331a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323501"
---
# <a name="stoptracingsessiona"></a>StopTracingSessionA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `StopTracingSessionA` zatrzymuje trwającą sesję śledzenia i tworzy plik śledzenia nieprzetworzonego. Nieprzetworzone pliki śledzenia mogą być przekazywane do [funkcji Analiza,](analyze.md) [AnalzeA](analyze-a.md)i [AnalyzeW](analyze-w.md) w celu rozpoczęcia sesji analizy. Nieprzetworzone pliki śledzenia mogą być również przekazywane do [funkcji Relog](relog.md), [RelogA](relog-a.md)i [RelogW,](relog-w.md) aby rozpocząć sesję ponownego rejestrowania. Pliki wykonywalne wywołujące `StopTracingSessionA` muszą mieć uprawnienia administratora.

## <a name="syntax"></a>Składnia

```cpp
enum RESULT_CODE StopTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>Parametry

*Nazwa_sesji*\
Nazwa sesji śledzenia, aby zatrzymać. Użyj tej samej nazwy sesji, co nazwa przeniesiona do [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)lub [StartTracingSessionW](start-tracing-session-w.md).

*plik danych wyjściowych*\
Ścieżka do końcowego pliku dziennika wyjściowego, w którym należy zapisać nieprzetworzony ślad.

*Statystyki*\
Wskaźnik do [obiektu TRACING_SESSION_STATISTICS.](../other-types/tracing-session-statistics-struct.md) `StopTracingSessionA`zapisuje statystyki kolekcji śledzenia w tym obiekcie przed zwróceniem.

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z [RESULT_CODE](../other-types/result-code-enum.md) wyliczenia.

::: moniker-end
