---
title: Klasa konsolidatora
description: Odwołanie C++ do klasy KONSOLIDATORA zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 95b0dcc3a771ec07ee60185a79a5ddbc29434b5d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333210"
---
# <a name="linkergroup-class"></a>Klasa konsolidatora

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `LinkerGroup` jest używana z funkcjami [MatchEventStack](../functions/match-event-stack.md) i [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Użyj go, aby dopasować grupy zdarzeń [konsolidatora](../event-table.md#linker) .

## <a name="syntax"></a>Składnia

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z dziedziczonymi elementami członkowskimi [\<konsolidatora\>](event-group.md) klasę bazową, Klasa `LinkerGroup` zawiera następujących członków:

### <a name="constructors"></a>Konstruktorów

[Konsolidator](#linker-group)

## <a name="linker-group"></a>Konsolidator

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>Parametry

\ *grupy*
Grupa zdarzeń [konsolidatora](../event-table.md#linker) .

::: moniker-end
