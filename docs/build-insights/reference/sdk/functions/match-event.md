---
title: MatchEvent ( MatchEvent )
description: Odwołanie do funkcji SDK MatchEvent aplikacji C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c60653641c676716bcdd60865433773da79325f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323856"
---
# <a name="matchevent"></a>MatchEvent ( MatchEvent )

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MatchEvent` jest używana do dopasowania zdarzenia do listy typów zdarzeń. Jeśli zdarzenie pasuje do typu na liście, jest przekazywane do programu obsługi do dalszego przetwarzania.

## <a name="syntax"></a>Składnia

```cpp
template <
    typename        TEvent,
    typename...     TEvents,
    typename        TCallable,
    typename...     TExtraArgs>
bool MatchEvent(
    const RawEvent& event,
    TCallable&&     callable,
    TExtraArgs&&... extraArgs);
```

### <a name="parameters"></a>Parametry

*TEvent ( TEvent )*\
Pierwszy typ zdarzenia, który chcesz dopasować.

*TEvents (WYCHO.*\
Pozostałe typy zdarzeń, które chcesz dopasować.

*TCallable (Można się do systemu)*\
Typ, który `operator()`obsługuje . Aby uzyskać więcej informacji na temat argumentów, które są przekazywane do tego operatora, zobacz opis parametru *wywoływane.*

*TExtraArgs*\
Typy dodatkowych argumentów, które `MatchEvent`zostały przekazane do .

*Zdarzenie*\
Zdarzenie, które ma być zgodne z typami zdarzeń opisanymi przez *TEvent* i *TEvents*.

*Nieopłacona*\
`MatchEvent`wywołuje *wywoływane* po pomyślnym dopasowaniu zdarzenia do dowolnego z typów zdarzeń opisanych przez *TEvent* i *TEvents*. Pierwszy argument przekazany do *wywoływania* jest r-wartość dopasowanego typu zdarzenia. Pakiet *parametrów extraArgs* jest idealnie przekierowywany w pozostałych parametrach *wywoływanych.*  

*extraArgs (extraArgs)*\
Argumenty, które są perfekcyjnie przekazywane do *wywoływania* wraz z dopasowanym typem zdarzenia.

### <a name="return-value"></a>Wartość zwracana

Wartość **bool,** która **jest prawdziwa,** jeśli dopasowanie zakończyło się pomyślnie lub **false** w inny sposób.

## <a name="remarks"></a>Uwagi

Typy zdarzeń, które mają być używane dla parametrów *TEvent* i *TEvents,* są wybierane z listy *klas przechwytywania.* Aby uzyskać listę zdarzeń i klasy przechwytywania, których można użyć do ich dopasowania, zobacz [tabelę zdarzeń](../event-table.md).

## <a name="example"></a>Przykład

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEvent<Function, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});

    bool b2 = MatchEvent<CodeGeneration, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});


    // b1: true because the list of types contains Function, which is
    //     the type of the event we are trying to match.
    // b2: false because the list of types doesn't contain Function.
}
```

::: moniker-end
