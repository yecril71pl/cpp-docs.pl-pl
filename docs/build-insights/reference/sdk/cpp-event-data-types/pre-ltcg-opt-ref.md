---
title: Klasa PreLTCGOptRef
description: Odwołanie C++ do klasy PreLTCGOptRef zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- PreLTCGOptRef
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4690feddcf615a82226ce5ad2f3ee242749db04a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333070"
---
# <a name="preltcgoptref-class"></a>Klasa PreLTCGOptRef

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `PreLTCGOptRef` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Użyj go, aby dopasować zdarzenie [PRE_LTCG_OPT_REF](../event-table.md#pre-ltcg-opt-ref) .

## <a name="syntax"></a>Składnia

```cpp
class PreLTCGOptRef : public Activity
{
public:
    PreLTCGOptRef(const RawEvent& event);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z dziedziczonymi elementami członkowskimi z klasy podstawowej [działania](activity.md) Klasa `PreLTCGOptRef` zawiera następujących członków:

### <a name="constructors"></a>Konstruktorów

[PreLTCGOptRef](#pre-ltcg-opt-ref)

## <a name="pre-ltcg-opt-ref"></a>PreLTCGOptRef

```cpp
PreLTCGOptRef(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *zdarzeń*
Zdarzenie [PRE_LTCG_OPT_REF](../event-table.md#pre-ltcg-opt-ref) .

::: moniker-end
