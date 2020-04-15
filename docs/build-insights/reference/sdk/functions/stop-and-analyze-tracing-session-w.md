---
title: StopAndAnalyzeTracingSessionW
description: Odwołanie do funkcji SDK StopAndAnalyzeTracingSessionW w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2f5f232c3e58c66bc36099d954d97a8f945187ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323717"
---
# <a name="stopandanalyzetracingsessionw"></a>StopAndAnalyzeTracingSessionW

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `StopAndAnalyzeTracingSessionW` zatrzymuje trwającą sesję śledzenia i zapisuje wynikowy ślad w pliku tymczasowym. Sesja analizy jest następnie natychmiast uruchamiana przy użyciu pliku tymczasowego jako danych wejściowych. Pliki wykonywalne wywołujące tę funkcję muszą mieć uprawnienia administratora.

## <a name="syntax"></a>Składnia

```cpp
enum RESULT_CODE StopAndAnalyzeTracingSessionW(
    const wchar_t*              sessionName,
    TRACING_SESSION_STATISTICS* statistics,
    const ANALYSIS_DESCRIPTOR*  analysisDescriptor);
```

### <a name="parameters"></a>Parametry

*Nazwa_sesji*\
Nazwa sesji śledzenia, aby zatrzymać. Użyj tej samej nazwy sesji, co nazwa przeniesiona do [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)lub [StartTracingSessionW](start-tracing-session-w.md).

*Statystyki*\
Wskaźnik do [obiektu TRACING_SESSION_STATISTICS.](../other-types/tracing-session-statistics-struct.md) `StopAndAnalyzeTracingSessionW`zapisuje statystyki kolekcji śledzenia w tym obiekcie przed zwróceniem.

*analysisDeptor*\
Wskaźnik do [obiektu ANALYSIS_DESCRIPTOR.](../other-types/analysis-descriptor-struct.md) Ten obiekt służy do konfigurowania sesji analizy, która jest uruchamiana przez `StopAndAnalyzeTracingSessionW`program .

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z [RESULT_CODE](../other-types/result-code-enum.md) wyliczenia.

::: moniker-end
