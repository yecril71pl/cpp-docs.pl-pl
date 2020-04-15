---
title: Ponownego zarejestrowania
description: Odwołanie do funkcji ponownegologowania kompilacji języka C++ Build SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28b290d2bf2880ce2f534fa1cd91750890e2fead
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323779"
---
# <a name="relog"></a>Ponownego zarejestrowania

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `Relog` służy do odczytywania zdarzeń MSVC z śledzenia zdarzeń dla systemu Windows (ETW) śledzenia i zapisu ich w nowym, zmodyfikowanym śladu ETW.

## <a name="syntax"></a>Składnia

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const char*                                   inputLogFile,
    const char*                                   outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const wchar_t*                                inputLogFile,
    const wchar_t*                                outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>Parametry

*Członkowie grupy TAnalyzer*\
Ten parametr jest zawsze wydedukowany.

*Członkowie grupy TRelogger*\
Ten parametr jest zawsze wydedukowany.

*inputLogFile*\
Śledzenia etw wejściowych, które mają być odczytywane zdarzenia z.

*plik danych wyjściowych*\
Plik, w którym można zapisać nowe zdarzenia.

*numerOfAnalysisPasses*\
Liczba przechodzi analizy do uruchomienia na śledzenia wejściowego. Śledzenia pobiera przekazywane przez pod warunkiem grupy analizatorraz na przebieg analizy.

*systemEventsReentionSlags*\
Maska bitowa określająca, które zdarzenia ETW systemu należy przechowywać w ponownie zarejestrowanym śladu. Aby uzyskać więcej informacji, zobacz [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md).

*grupa analizatorów*\
Grupa analizatorów używana do fazy analizy sesji ponownego rejestrowania. Wywołanie [MakeStaticAnalyzerGroup,](make-static-analyzer-group.md) aby utworzyć grupę analizatora. Aby użyć grupy analizatorów dynamicznych uzyskanej z [MakeDynamicAnalyzerGroup,](make-dynamic-analyzer-group.md)najpierw hermetyzuj `MakeStaticAnalyzerGroup`ją wewnątrz statycznej grupy analizatorów, przekazując jej adres do .

*grupa relogger*\
Grupa reloggera, która ponownie zasłania zdarzenia do pliku śledzenia określonego w *pliku outputLogFile*. Wywołanie [MakeStaticReloggerGroup,](make-static-relogger-group.md) aby utworzyć grupę relogger. Aby użyć dynamicznej grupy reloggera uzyskanej z [MakeDynamicReloggerGroup,](make-dynamic-relogger-group.md)najpierw hermetyzuj ją `MakeStaticReloggerGroup`wewnątrz statycznej grupy reloggerów, przekazując jej adres do .

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z [RESULT_CODE](../other-types/result-code-enum.md) wyliczenia.

### <a name="remark"></a>Uwaga

Śledzenia danych wejściowych jest przekazywana przez numer grupy *analizatoraOfAnalysisPasses* razy. Nie ma podobnej opcji ponownego rejestrowania przebiegów. Śledzenie jest przekazywane koryta grupy relogger tylko raz, po zakończeniu wszystkich przebiegów analizy.

Ponowne rejestrowanie zdarzeń systemowych, takich jak próbki procesora CPU z klasy reloggera nie jest obsługiwane. Użyj *parametru systemEventsRetentionFlags,* aby zdecydować, które zdarzenia systemowe mają być utrzymywane w śledzenia danych wyjściowych.

::: moniker-end
