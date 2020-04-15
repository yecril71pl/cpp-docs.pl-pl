---
title: Reloga ( RelogA )
description: Odwołanie do funkcji reloga SDK SDK kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5a772b1156fc69eeef39514afe401c549c3b7c38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323847"
---
# <a name="reloga"></a>Reloga ( RelogA )

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `RelogA` służy do odczytywania zdarzeń MSVC z śledzenia zdarzeń dla systemu Windows (ETW) śledzenia i zapisu ich w nowym, zmodyfikowanym śladu ETW.

## <a name="syntax"></a>Składnia

```cpp
enum RESULT_CODE RelogA(
    const char*             inputLogFile,
    const char*             outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>Parametry

*inputLogFile*\
Śledzenia etw wejściowych, które mają być odczytywane zdarzenia z.

*plik danych wyjściowych*\
Plik, w którym można zapisać nowe zdarzenia.

*relogDeptor*\
Wskaźnik do [obiektu RELOG_DESCRIPTOR.](../other-types/relog-descriptor-struct.md) Ten obiekt służy do konfigurowania sesji ponownego rejestrowania.

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z [RESULT_CODE](../other-types/result-code-enum.md) wyliczenia.

::: moniker-end
