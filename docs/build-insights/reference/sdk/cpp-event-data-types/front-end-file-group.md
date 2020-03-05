---
title: Klasa FrontEndFileGroup
description: Odwołanie C++ do klasy FrontEndFileGroup zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 343a5a0d798d6c719088bd49668e70b10fba6d1a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333329"
---
# <a name="frontendfilegroup-class"></a>Klasa FrontEndFileGroup

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `FrontEndFileGroup` jest używana z funkcjami [MatchEventStack](../functions/match-event-stack.md) i [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Użyj go, aby dopasować grupy zdarzeń [FRONT_END_FILE](../event-table.md#front-end-file) .

## <a name="syntax"></a>Składnia

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z dziedziczonymi elementami członkowskimi [\<FrontEndFile\>](event-group.md) klasy bazowej Klasa `FrontEndFileGroup` zawiera następujących członków:

### <a name="constructors"></a>Konstruktorów

[FrontEndFileGroup](#front-end-file-group)

## <a name="front-end-file-group"></a>FrontEndFileGroup

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>Parametry

\ *grupy*
Grupa zdarzeń [FRONT_END_FILE](../event-table.md#front-end-file) .

::: moniker-end
