---
title: Klasa ExpOutput
description: Odwołanie do klasy SDK ExpOutput aplikacji C++ Build SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ExpOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4c8c5f2f260596c444df7841c2a3e0c65f5163f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324815"
---
# <a name="expoutput-class"></a>Klasa ExpOutput

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `ExpOutput` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie EXP_OUTPUT.](../event-table.md#exp-output)

## <a name="syntax"></a>Składnia

```cpp
class ExpOutput : public FileOutput
{
public:
    ExpOutput(const RawEvent& event);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych elementów członkowskich z jego `ExpOutput` [FileOutput](file-output.md) klasy podstawowej, klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[ExpOutput (ExpOutput)](#exp-output)

## <a name="expoutput"></a><a name="exp-output"></a>ExpOutput (ExpOutput)

```cpp
ExpOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Wydarzenie [EXP_OUTPUT.](../event-table.md#exp-output)

::: moniker-end
