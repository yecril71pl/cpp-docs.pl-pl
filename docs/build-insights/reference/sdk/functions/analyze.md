---
title: Analiza
description: Zestaw C++ SDK usługi Build Insights — informacje o funkcji.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 49161641d1cff1c64261d95bb2caace2f802543a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332867"
---
# <a name="analyze"></a>Analiza

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `Analyze` służy do analizowania wyników śledzenia zdarzeń systemu Windows (ETW) uzyskanych z MSVC podczas śledzenia C++ kompilacji. Zdarzenia w śledzeniu ETW są przekazywane sekwencyjnie do grupy analizatorów dostarczonej przez wywołującego. Ta funkcja obsługuje analizy wieloetapowe umożliwiające przekazywanie strumienia zdarzeń do grupy analizatorów wiele razy w wierszu.

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

*TAnalyzerGroupMembers*\
Ten parametr jest zawsze wywnioskowany.

*inputLogFile*\
Wejściowy ślad ETW, z którego mają być odczytywane zdarzenia.

*numberOfPasses*\
Liczba przebiegów analizy do uruchomienia na danych wejściowych śledzenia. Śledzenie jest przekazywane przez podaną grupę analizatora raz na przebieg analizy.

\ka *analizatora*
Grupa analizatorów użyta do analizy. Wywołaj [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) , aby utworzyć grupę analizatorów. Aby użyć dynamicznej grupy analizatora uzyskanej z [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), należy najpierw hermetyzować ją wewnątrz statycznej grupy analizatorów, przekazując jej adres do `MakeStaticAnalyzerGroup`.

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z wyliczenia [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
