---
title: Klasa LTCG
description: Odwołanie do klasy SDK LTCG kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LTCG
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 47faaeb8428a28feab2eb27342e6a68d052d2dd4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324587"
---
# <a name="ltcg-class"></a>Klasa LTCG

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `LTCG` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować zdarzenie [LTCG.](../event-table.md#ltcg)

## <a name="syntax"></a>Składnia

```cpp
class LTCG : public Activity
{
public:
    LTCG(const RawEvent& event);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych elementów członkowskich z `LTCG` jego [działania](activity.md) klasy podstawowej, klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[Ltcg](#ltcg)

## <a name="ltcg"></a><a name="ltcg"></a>Ltcg

```cpp
LTCG(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Zdarzenie [LTCG.](../event-table.md#ltcg)

::: moniker-end
