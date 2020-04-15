---
title: StopAndRelogTracingSessionA
description: Odwołanie do funkcji SDK StopAndRelogTracingSessiona w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fa70d50ba79a7829adb985ab4d884b5773b5d40f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323680"
---
# <a name="stopandrelogtracingsessiona"></a>StopAndRelogTracingSessionA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `StopAndRelogTracingSessionA` zatrzymuje trwającą sesję śledzenia i zapisuje wynikowy ślad w pliku tymczasowym. Sesja ponownego rejestrowania jest natychmiast uruchamiana przy użyciu pliku tymczasowego jako danych wejściowych. Końcowy ślad ponownie zarejestrowany wyprodukowany przez sesję ponownego rejestrowania jest zapisywany w pliku określonym przez wywołującego. Pliki wykonywalne wywołujące tę funkcję muszą mieć uprawnienia administratora.

## <a name="syntax"></a>Składnia

```cpp
enum RESULT_CODE StopAndRelogTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>Parametry

*Nazwa_sesji*\
Nazwa sesji śledzenia, aby zatrzymać. Użyj tej samej nazwy sesji, co nazwa przeniesiona do [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)lub [StartTracingSessionW](start-tracing-session-w.md).

*plik danych wyjściowych*\
Plik, w którym można zapisać relogged śledzenia produkowane przez sesji ponownego rejestrowania.

*Statystyki*\
Wskaźnik do [obiektu TRACING_SESSION_STATISTICS.](../other-types/tracing-session-statistics-struct.md) `StopAndRelogTracingSessionA`zapisuje statystyki kolekcji śledzenia w tym obiekcie przed zwróceniem.

*analysisDeptor*\
Wskaźnik do [obiektu RELOG_DESCRIPTOR.](../other-types/analysis-descriptor-struct.md) Użyj tego obiektu, aby skonfigurować sesję ponownego `StopAndRelogTracingSessionA`rejestrowania, która jest uruchamiana przez program .

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z [RESULT_CODE](../other-types/result-code-enum.md) wyliczenia.

::: moniker-end
