---
title: Klasa BackEndPass
description: Odwołanie do klasy SDK BackEndPass kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BackEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2b4b1a219abdbe418efaab4537f1c6dc9a22afb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325238"
---
# <a name="backendpass-class"></a>Klasa BackEndPass

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `BackEndPass` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie BACK_END_PASS.](../event-table.md#back-end-pass)

## <a name="syntax"></a>Składnia

```cpp
class BackEndPass : public CompilerPass
{
public:
    BackEndPass(const RawEvent& event);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych elementów członkowskich z jego `BackEndPass` [CompilerPass](compiler-pass.md) klasy podstawowej, klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[BackEndPass (BackEndPass)](#back-end-pass)

## <a name="backendpass"></a><a name="back-end-pass"></a>BackEndPass (BackEndPass)

```cpp
BackEndPass(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Wydarzenie [BACK_END_PASS.](../event-table.md#back-end-pass)

::: moniker-end
