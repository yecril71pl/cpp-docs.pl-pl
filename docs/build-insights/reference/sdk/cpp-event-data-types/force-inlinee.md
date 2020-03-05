---
title: Klasa ForceInlinee
description: Odwołanie C++ do klasy ForceInlinee zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7d3cce13601a0b3edbcd2b57664b2d0d94a7d3df
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333336"
---
# <a name="forceinlinee-class"></a>Klasa ForceInlinee

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `ForceInlinee` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Użyj go, aby dopasować zdarzenie [FORCE_INLINEE](../event-table.md#force-inlinee) .

## <a name="syntax"></a>Składnia

```cpp
class ForceInlinee : public SimpleEvent
{
public:
    ForceInlinee(const RawEvent& event);

    const char*             Name() const;
    const unsigned short&   Size() const;
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z dziedziczonymi elementami członkowskimi z klasy bazowej [SimpleEvent](simple-event.md) , Klasa `ForceInlinee` zawiera następujących członków:

### <a name="constructors"></a>Konstruktorów

[ForceInlinee](#force-inlinee)

### <a name="functions"></a>Funkcje

[Nazwa](#name)
[rozmiar](#size)

## <a name="force-inlinee"></a>ForceInlinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *zdarzeń*
Zdarzenie [FORCE_INLINEE](../event-table.md#force-inlinee) .

## <a name="name"></a>Nazwij

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa funkcji wymuszonej, zakodowana w UTF-8.

## <a name="size"></a>Zmienia

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar funkcji bezwierszowej w postaci liczby instrukcji pośrednich.

::: moniker-end
