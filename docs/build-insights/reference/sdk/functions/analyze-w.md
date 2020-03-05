---
title: AnalyzeW
description: Odwołanie C++ do funkcji AnalyzeW zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bd9b401f08941134d3c267df5c23c5d9e981cb86
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332930"
---
# <a name="analyzew"></a>AnalyzeW

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `AnalyzeW` służy do analizowania zdarzeń MSVC odczytanych przez śledzenie zdarzeń wejściowych systemu Windows (ETW).

## <a name="syntax"></a>Składnia

```cpp
enum RESULT_CODE AnalyzeW(
    const wchar_t*             inputLogFile,
    const ANALYSIS_DESCRIPTOR* analysisDescriptor);
```

### <a name="parameters"></a>Parametry

*inputLogFile*\
Wejściowy ślad ETW, z którego mają być odczytywane zdarzenia.

*analysisDescriptor*\
Wskaźnik do obiektu [ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) . Ten obiekt służy do konfigurowania analizy.

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z wyliczenia [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
