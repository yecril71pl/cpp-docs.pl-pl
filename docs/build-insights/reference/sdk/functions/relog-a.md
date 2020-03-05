---
title: RelogA
description: Odwołanie C++ do funkcji RelogA zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c4427aa0ac85e34bfb9d569913a8ccf6ab264f52
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332734"
---
# <a name="reloga"></a>RelogA

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `RelogA` służy do odczytywania zdarzeń MSVC z śladu śledzenia zdarzeń systemu Windows (ETW) i zapisywania ich w nowym, zmodyfikowanym śledzeniu ETW.

## <a name="syntax"></a>Składnia

```cpp
enum RESULT_CODE RelogA(
    const char*             inputLogFile,
    const char*             outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>Parametry

*inputLogFile*\
Wejściowy ślad ETW, z którego mają być odczytywane zdarzenia.

*outputLogFile*\
Plik, w którym mają zostać zapisane nowe zdarzenia.

*relogDescriptor*\
Wskaźnik do obiektu [RELOG_DESCRIPTOR](../other-types/relog-descriptor-struct.md) . Ten obiekt służy do konfigurowania sesji ponownego rejestrowania.

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z wyliczenia [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
