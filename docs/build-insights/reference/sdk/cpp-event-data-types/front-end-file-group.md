---
title: Klasa FrontEndFileGroup
description: Odwołanie do klasy SDK FrontEndFileGroup aplikacji SDK aplikacji C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d2eebb650e59e750e5ebde74914dca5f0ef4779d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324774"
---
# <a name="frontendfilegroup-class"></a>Klasa FrontEndFileGroup

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `FrontEndFileGroup` jest używana z [funkcjami MatchEventStack](../functions/match-event-stack.md) i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować grupy [FRONT_END_FILE](../event-table.md#front-end-file) zdarzeń.

## <a name="syntax"></a>Składnia

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych członków z [jego EventGroup\<FrontEndFile\> ](event-group.md) klasy podstawowej, `FrontEndFileGroup` klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[Grupa plików frontu](#front-end-file-group)

## <a name="frontendfilegroup"></a><a name="front-end-file-group"></a>Grupa plików frontu

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>Parametry

*Grupa*\
Grupa [FRONT_END_FILE](../event-table.md#front-end-file) zdarzeń.

::: moniker-end
