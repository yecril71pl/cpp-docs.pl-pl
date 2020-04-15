---
title: Klasa OptRef
description: Odwołanie do klasy OptRef aplikacji SDK OptRef w języku C++ Build.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptRef
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dca8cc62eed4b7136f88ed5ba6a1a168b2de56c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324447"
---
# <a name="optref-class"></a>Klasa OptRef

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `OptRef` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie OPT_REF.](../event-table.md#opt-ref)

## <a name="syntax"></a>Składnia

```cpp
class OptRef : public Activity
{
public:
    OptRef(const RawEvent& event);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych elementów członkowskich z `OptRef` jego [działania](activity.md) klasy podstawowej, klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[OptRef (Odz.](#opt-ref)

## <a name="optref"></a><a name="opt-ref"></a>OptRef (Odz.

```cpp
OptRef(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Wydarzenie [OPT_REF.](../event-table.md#opt-ref)

::: moniker-end
