---
title: Klasa wywołania
description: Odwołanie C++ do klasy grupy wywołań zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b9a2bbcd2b7649b9b5703adc08ed41b272e10276
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333238"
---
# <a name="invocationgroup-class"></a>Klasa wywołania

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `InvocationGroup` jest używana z funkcjami [MatchEventStack](../functions/match-event-stack.md) i [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Użyj go do dopasowania grup zawierających mieszanie zdarzeń [kompilatora](../event-table.md#compiler) i [konsolidatora](../event-table.md#linker) .

## <a name="syntax"></a>Składnia

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z dziedziczonymi elementami członkowskimi ze swej [\<wywołań\>](event-group.md) klasie bazowej Klasa `InvocationGroup` zawiera następujących członków:

### <a name="constructors"></a>Konstruktorów

[Wywołanie](#invocation-group)

## <a name="invocation-group"></a>Wywołanie

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>Parametry

\ *grupy*
Grupa zawierająca kombinację zdarzeń [kompilatora](../event-table.md#compiler) i [konsolidatora](../event-table.md#linker) .

::: moniker-end
