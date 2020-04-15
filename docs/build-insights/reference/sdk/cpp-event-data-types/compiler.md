---
title: Klasa kompilatora
description: Odwołanie do klasy kompilatora SDK kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Compiler
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9b0a2622c4bc0bc19d7222977fe24c060ee8709e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325031"
---
# <a name="compiler-class"></a>Klasa kompilatora

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `Compiler` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie kompilatora.](../event-table.md#compiler)

## <a name="syntax"></a>Składnia

```cpp
class Compiler : public Invocation
{
public:
    Compiler(const RawEvent& event);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonymi członkami z jego klasy `Compiler` podstawowej [wywoływania](invocation.md) klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[Kompilator](#compiler)

## <a name="compiler"></a><a name="compiler"></a>Kompilator

```cpp
Compiler(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Zdarzenie [kompilatora.](../event-table.md#compiler)

::: moniker-end
