---
title: Klasa C2DLL
description: Odwołanie do klasy C++ Build SDK C2DLL.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- C2DLL
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7711acf800999d4e97c3ae56fa2100a632a245b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325075"
---
# <a name="c2dll-class"></a>Klasa C2DLL

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `C2DLL` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie C2_DLL.](../event-table.md#c2-dll)

## <a name="syntax"></a>Składnia

```cpp
class C2DLL : public Activity
{
public:
    C2DLL(const RawEvent& event);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych elementów członkowskich z `C2DLL` jego [działania](activity.md) klasy podstawowej, klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[Biblioteka C2DLL](#c2-dll)

## <a name="c2dll"></a><a name="c2-dll"></a>Biblioteka C2DLL

```cpp
C2DLL(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Wydarzenie [C2_DLL.](../event-table.md#c2-dll)

::: moniker-end
