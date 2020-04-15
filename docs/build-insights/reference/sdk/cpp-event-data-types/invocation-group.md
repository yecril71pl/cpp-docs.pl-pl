---
title: Klasa InvocationGroup
description: Odwołanie do klasy SDK InvocationGroup w programie C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff5a73d5304a21c314c0fc5ce442e0ffc23b28fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324688"
---
# <a name="invocationgroup-class"></a>Klasa InvocationGroup

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `InvocationGroup` jest używana z [funkcjami MatchEventStack](../functions/match-event-stack.md) i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować grupy zawierające kombinację [zdarzeń kompilatora](../event-table.md#compiler) i [konsolidatora.](../event-table.md#linker)

## <a name="syntax"></a>Składnia

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonymi członkami z klasy podstawowej [\<invocation\> grupy zdarzeń](event-group.md) `InvocationGroup` klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[Grupa invocation](#invocation-group)

## <a name="invocationgroup"></a><a name="invocation-group"></a>Grupa invocation

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>Parametry

*Grupa*\
Grupa zawierająca kombinację [zdarzeń kompilatora](../event-table.md#compiler) i [konsolidatora.](../event-table.md#linker)

::: moniker-end
