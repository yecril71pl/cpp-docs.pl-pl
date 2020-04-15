---
title: ForceInlinee, klasa
description: Odwołanie do klasy SDK ForceInlinee aplikacji C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c6a1af0384197a0a3b6062ad9ef30537c348190d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324781"
---
# <a name="forceinlinee-class"></a>ForceInlinee, klasa

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `ForceInlinee` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie FORCE_INLINEE.](../event-table.md#force-inlinee)

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

Wraz z odziedziczonych członków z jego [SimpleEvent](simple-event.md) klasy podstawowej, `ForceInlinee` klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[ForceInlinee (Linia siłowa)](#force-inlinee)

### <a name="functions"></a>Funkcje

[Name](#name)
[Rozmiar](#size) nazwy

## <a name="forceinlinee"></a><a name="force-inlinee"></a>ForceInlinee (Linia siłowa)

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Wydarzenie [FORCE_INLINEE.](../event-table.md#force-inlinee)

## <a name="name"></a><a name="name"></a>Nazwa

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa funkcji force-inlined, zakodowana w UTF-8.

## <a name="size"></a><a name="size"></a>Rozmiar

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar funkcji force-inlined jako liczba instrukcji pośrednich.

::: moniker-end
