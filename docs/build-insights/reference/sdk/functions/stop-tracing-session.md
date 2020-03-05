---
title: StopTracingSession
description: Odwołanie C++ do funkcji StopTracingSession zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a4be229dcfddef0624869b789ee35e51336ac78e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332552"
---
# <a name="stoptracingsession"></a>StopTracingSession

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `StopTracingSession` przerywa trwającą sesję śledzenia i tworzy Nieprzetworzony plik śledzenia. Nieprzetworzone pliki śledzenia można przesłać do funkcji [Analizuj](analyze.md), [AnalzeA](analyze-a.md)i [AnalyzeW](analyze-w.md) , aby rozpocząć sesję analizy. Nieprzetworzone pliki śledzenia można także przesłać do funkcji [relog](relog.md), [RelogA](relog-a.md)i [RelogW](relog-w.md) , aby rozpocząć sesję ponownego rejestrowania. Pliki wykonywalne wywołujące `StopTracingSession` muszą mieć uprawnienia administratora.

## <a name="syntax"></a>Składnia

```cpp
inline RESULT_CODE StopTracingSession(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);

inline RESULT_CODE StopTracingSession(
    const wchar_t*              sessionName
    const wchar_t*              outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>Parametry

*Nazwa sesji*\
Nazwa sesji śledzenia, która ma zostać zatrzymana. Użyj tej samej nazwy sesji, która została przeniesiona do [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)lub [StartTracingSessionW](start-tracing-session-w.md).

*outputLogFile*\
Ścieżka do końcowego pliku dziennika wyjściowego, w którym ma zostać zapisany nieprzetworzony wynik śledzenia.

\ *statystyk*
Wskaźnik do obiektu [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . `StopTracingSession` zapisuje statystyki kolekcji śledzenia w tym obiekcie przed zwróceniem.

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z wyliczenia [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
