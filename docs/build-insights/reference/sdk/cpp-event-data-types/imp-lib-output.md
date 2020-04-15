---
title: Klasa ImpLibOutput
description: Odwołanie do klasy SDK ImpLibOutput w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ImpLibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 98905dfe75484e98e14a0fa575e75fe3ab284559
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324703"
---
# <a name="impliboutput-class"></a>Klasa ImpLibOutput

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `ImpLibOutput` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie IMP_LIB_OUTPUT.](../event-table.md#imp-lib-output)

## <a name="syntax"></a>Składnia

```cpp
class ImpLibOutput : public FileOutput
{
public:
    ImpLibOutput(const RawEvent& event);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych elementów członkowskich z jego `ImpLibOutput` [FileOutput](file-output.md) klasy podstawowej, klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[ImpLibOutput (ImpLibOutput)](#imp-lib-output)

## <a name="impliboutput"></a><a name="imp-lib-output"></a>ImpLibOutput (ImpLibOutput)

```cpp
ImpLibOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Wydarzenie [IMP_LIB_OUTPUT.](../event-table.md#imp-lib-output)

::: moniker-end
