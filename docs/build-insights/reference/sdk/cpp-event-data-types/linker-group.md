---
title: LinkerGroup, klasa
description: Odwołanie do klasy SDK SDK linkergroup w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c59d62938e5bd7b839ad12a321a03510e708e0fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324649"
---
# <a name="linkergroup-class"></a>LinkerGroup, klasa

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `LinkerGroup` jest używana z [funkcjami MatchEventStack](../functions/match-event-stack.md) i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować grupy zdarzeń [LINKER.](../event-table.md#linker)

## <a name="syntax"></a>Składnia

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonymi członkami z klasy podstawowej `LinkerGroup` [łącznika\<\> grupy zdarzeń](event-group.md) klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[Grupa konsoli](#linker-group)

## <a name="linkergroup"></a><a name="linker-group"></a>Grupa konsoli

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>Parametry

*Grupa*\
Grupa zdarzeń [LINKER.](../event-table.md#linker)

::: moniker-end
