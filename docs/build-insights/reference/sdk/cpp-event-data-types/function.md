---
title: Klasa funkcyjna
description: Odwołanie do klasy funkcji SDK kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 69acbe4d6630de37120aec89a24a9f33d447009e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324723"
---
# <a name="function-class"></a>Klasa funkcyjna

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `Function` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować zdarzenie [FUNCTION.](../event-table.md#function)

## <a name="syntax"></a>Składnia

```cpp
class Function : public Activity
{
public:
    Function(const RawEvent& event);

    const char* Name() const;
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych elementów członkowskich z `Function` jego [działania](activity.md) klasy podstawowej, klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[Funkcja](#function)

### <a name="functions"></a>Funkcje

[Nazwa](#name)

## <a name="function"></a><a name="function"></a>Funkcja

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Zdarzenie [FUNCTION.](../event-table.md#function)

## <a name="name"></a><a name="name"></a>Nazwa

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa funkcji zakodowana w UTF-8.

::: moniker-end
