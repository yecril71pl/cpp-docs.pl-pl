---
title: AnalizaW
description: Odwołanie do funkcji SDK analizy analizy W kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 64d68e4c10c0b77c3e6b08b1ec23735e38a377a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324158"
---
# <a name="analyzew"></a>AnalizaW

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `AnalyzeW` służy do analizowania zdarzeń MSVC odczytanych z śledzenia zdarzeń wejściowych dla systemu Windows (ETW).

## <a name="syntax"></a>Składnia

```cpp
enum RESULT_CODE AnalyzeW(
    const wchar_t*             inputLogFile,
    const ANALYSIS_DESCRIPTOR* analysisDescriptor);
```

### <a name="parameters"></a>Parametry

*inputLogFile*\
Śledzenia etw wejściowych, które mają być odczytywane zdarzenia z.

*analysisDeptor*\
Wskaźnik do [obiektu ANALYSIS_DESCRIPTOR.](../other-types/analysis-descriptor-struct.md) Ten obiekt służy do konfigurowania analizy.

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z [RESULT_CODE](../other-types/result-code-enum.md) wyliczenia.

::: moniker-end
