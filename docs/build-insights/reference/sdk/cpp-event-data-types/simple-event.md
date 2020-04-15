---
title: Klasa SimpleEvent
description: Odwołanie do klasy SimpleEvent aplikacji SDK SimpleEvent w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SimpleEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 414ff5c1af99acc612384c1ae39f6e12ab051275
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324369"
---
# <a name="simpleevent-class"></a>Klasa SimpleEvent

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `SimpleEvent` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować każde proste wydarzenie. Zapoznaj się z [tabelą zdarzeń,](../event-table.md) aby zobaczyć `SimpleEvent` wszystkie zdarzenia, które mogą być dopasowane przez klasę.

## <a name="syntax"></a>Składnia

```cpp
class SimpleEvent : public Event
{
public:
    SimpleEvent(const RawEvent& event);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych członków [Event](event.md) z jego `SimpleEvent` event klasy podstawowej, klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[ProsteVent](#simple-event)

## <a name="simpleevent"></a><a name="simple-event"></a>ProsteVent

```cpp
SimpleEvent(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Każde proste wydarzenie.

::: moniker-end
