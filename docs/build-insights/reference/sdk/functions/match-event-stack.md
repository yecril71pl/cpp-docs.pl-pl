---
title: MatchEventStack (własnik dopasowywki)
description: Odwołanie do funkcji SDK MatchEventStack aplikacji C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a223d420e8c48667fbd1c6569f02d0486f597b5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323873"
---
# <a name="matcheventstack"></a>MatchEventStack (własnik dopasowywki)

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MatchEventStack` jest używana do dopasowania stosu zdarzeń do hierarchii zdarzeń określonych. Dopasowane hierarchie są przekazywane do programu obsługi w celu dalszego przetwarzania. Aby dowiedzieć się więcej o zdarzeniach, stosach zdarzeń i hierarchiach, zobacz [tabelę zdarzeń](../event-table.md).

## <a name="syntax"></a>Składnia

```cpp
template <
    typename          TEvent,
    typename...       TEvents,
    typename          TCallable,
    typename...       TExtraArgs>
bool MatchEventStack(
    const EventStack& eventStack,
    TCallable&&       callable,
    TExtraArgs&&...   extraArgs);
```

### <a name="parameters"></a>Parametry

*TEvent ( TEvent )*\
Typ najstarszego rodzica do dopasowania w stosie zdarzeń.

*TEvents (WYCHO.*\
Pozostałe typy, które chcesz dopasować w stosie zdarzeń.

*TCallable (Można się do systemu)*\
Typ, który `operator()`obsługuje . Aby uzyskać więcej informacji na temat argumentów, które są przekazywane do tego operatora, zobacz opis parametru *wywoływane.*

*TExtraArgs*\
Typy dodatkowych argumentów `MatchEventStack`przekazywane do .

*eventStack (własówce wydarzenia)*\
Stos zdarzeń zgodny z hierarchią typów zdarzeń opisaną przez *TEvent* i *TEvents*.

*Nieopłacona*\
Po pomyślnym dopasowaniu stosu zdarzeń do hierarchii typów zdarzeń opisanej `MatchEventStack` przez *TEvent* i *TEvents,* wywołuje *wywoływane*. Przekazuje do *wywoływania* jeden argument wartości r dla każdego typu w hierarchii zdarzeń. Pakiet *parametrów extraArgs* jest idealnie przekierowywany w pozostałych parametrach *wywoływanych.*

*extraArgs (extraArgs)*\
Argumenty, które są perfekcyjnie przekazywane do *wywoływania* wraz z dopasowanym typem zdarzenia.

### <a name="return-value"></a>Wartość zwracana

Wartość **bool,** która jest **true,** jeśli dopasowanie zakończyło się pomyślnie lub **false** w inny sposób.

## <a name="remarks"></a>Uwagi

Ostatnie wydarzenie w *eventStack* jest zawsze dopasowane do ostatniego \[wpisu w konkapacji *TEvent*, *TEvents ...* \] listy typów. Wszystkie inne wpisy *TEvent* i *TEvents* mogą pasować do dowolnej pozycji w *eventStack* z wyjątkiem ostatniego, pod warunkiem, że są w tej samej kolejności.

Typy zdarzeń, które mają być używane dla parametrów *TEvent* i *TEvents,* są wybierane z listy *klas przechwytywania.* Aby uzyskać listę zdarzeń i klasy przechwytywania, których można użyć do ich dopasowania, zobacz [tabelę zdarzeń](../event-table.md).

## <a name="example"></a>Przykład

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStack<Compiler, BackEndPass, C2DLL,
                CodeGeneration, Thread, Function>(
        eventStack, [](Compiler cl, BackEndPass bep, C2DLL c2,
            CodeGeneration cg, Thread t, Function f){ /* Do something ... */ });

    bool b2 = MatchEventStack<Compiler, Function>(
        eventStack, [](Compiler cl, Function f){ /* Do something... */ });

    bool b3 = MatchEventStack<Thread, Compiler, Function>(
        eventStack, [](Thread t, Compiler cl Function f){ /* Do something... */ });

    bool b4 = MatchEventStack<Compiler>(
        eventStack, [](Compiler cl){ /* Do something... */ });


    // b1: true because the list of types matches the eventStack exactly.
    // b2: true because Function is the last entry in both the type list
    //     and 'eventStack', and also because Compiler comes before
    //     Function in 'eventStack' and in the type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', they aren't listed in the
    //     right order in the type list.
    // b4: false because the last entry in the type list is Compiler,
    //     which doesn't match the last entry in 'eventStack' (Function).
}
```

::: moniker-end
