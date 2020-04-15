---
title: Analiza
description: Odwołanie do funkcji analizy sdk analizy kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 08b3643270cc785b3fbea36720d192b4a1473104
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324107"
---
# <a name="analyze"></a>Analiza

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `Analyze` jest używana do analizowania śledzenia zdarzeń dla systemu Windows (ETW) śledzenia uzyskanego z MSVC podczas śledzenia kompilacji C++. Zdarzenia w śledzenia ETW są przekazywane sekwencyjnie do grupy analizatora dostarczone przez obiektu wywołującego. Ta funkcja obsługuje analizy wieloprzebiegowe, które umożliwiają przekazywanie strumienia zdarzeń do grupy analizatorów wiele razy z rzędu.

## <a name="syntax"></a>Składnia

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const char*                                   inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const wchar_t*                                inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>Parametry

*Członkowie grupy TAnalyzer*\
Ten parametr jest zawsze wydedukowany.

*inputLogFile*\
Śledzenia etw wejściowych, które mają być odczytywane zdarzenia z.

*numberOfPasses*\
Liczba przechodzi analizy do uruchomienia na śledzenia wejściowego. Śledzenia pobiera przekazywane przez pod warunkiem grupy analizatorraz na przebieg analizy.

*grupa analizatorów*\
Grupa analizatorów używana do analizy. Wywołanie [MakeStaticAnalyzerGroup,](make-static-analyzer-group.md) aby utworzyć grupę analizatora. Aby użyć grupy analizatorów dynamicznych uzyskanej z [MakeDynamicAnalyzerGroup,](make-dynamic-analyzer-group.md)najpierw hermetyzuj `MakeStaticAnalyzerGroup`ją wewnątrz statycznej grupy analizatorów, przekazując jej adres do .

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z [RESULT_CODE](../other-types/result-code-enum.md) wyliczenia.

::: moniker-end
