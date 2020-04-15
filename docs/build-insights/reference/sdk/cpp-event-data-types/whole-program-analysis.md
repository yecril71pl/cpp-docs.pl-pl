---
title: Klasa WholeProgramAnalysis
description: Odwołanie do klasy SDK WholeProgramAnalysis aplikacji C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- WholeProgramAnalysis
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c68441b7da09f9880bbb2f97544b1ad8da2f631f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324114"
---
# <a name="wholeprogramanalysis-class"></a>Klasa WholeProgramAnalysis

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `WholeProgramAnalysis` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie WHOLE_PROGRAM_ANALYSIS.](../event-table.md#whole-program-analysis)

## <a name="syntax"></a>Składnia

```cpp
class WholeProgramAnalysis : public Activity
{
public:
    WholeProgramAnalysis(const RawEvent& event);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych elementów członkowskich z `WholeProgramAnalysis` jego [działania](activity.md) klasy podstawowej, klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[WholeProgramAnalysis](#whole-program-analysis)

## <a name="wholeprogramanalysis"></a><a name="whole-program-analysis"></a>WholeProgramAnalysis

```cpp
WholeProgramAnalysis(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Wydarzenie [WHOLE_PROGRAM_ANALYSIS.](../event-table.md#whole-program-analysis)

::: moniker-end
