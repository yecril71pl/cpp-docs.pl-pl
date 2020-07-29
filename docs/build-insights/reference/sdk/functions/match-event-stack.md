---
title: MatchEventStack
description: Dokumentacja funkcji MatchEventStack zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ae476c402c3ea0cad558ce41a979b4233e0f1dd3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224126"
---
# <a name="matcheventstack"></a>MatchEventStack

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEventStack`Funkcja jest używana do dopasowania stosu zdarzeń do określonej hierarchii zdarzeń. Dopasowane hierarchie są przekazywane do programu obsługi w celu dalszej obróbki. Aby dowiedzieć się więcej o zdarzeniach, stosach zdarzeń i hierarchiach, zobacz [tabela zdarzeń](../event-table.md).

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

*TEvent*\
Typ elementu nadrzędnego eldest do dopasowania w stosie zdarzeń.

*TEvents*\
Pozostałe typy, które chcesz dopasować, w stosie zdarzeń.

*TCallable*\
Typ, który obsługuje `operator()` . Aby uzyskać więcej informacji na temat tego, które argumenty są przekazane do tego operatora, zobacz Opis możliwego do *uzyskania parametru.*

*TExtraArgs*\
Typy dodatkowych argumentów przekazane do `MatchEventStack` .

*eventStack*\
Stos zdarzeń do dopasowania względem hierarchii typów zdarzeń opisanych przez *TEvent* i *TEvents*.

*żądanie*\
Po pomyślnym dopasowaniu stosu zdarzeń z hierarchią typów zdarzeń opisanymi przez *TEvent* i *TEvents* `MatchEventStack` wywołuje wywołanie *callable*. Przekazuje *on do* możliwego do przekroczenia jednego argumentu r-wartości dla każdego typu w hierarchii zdarzeń. Pakiet parametrów *extraArgs* jest idealnym przesłanym dalej w pozostałych parametrach *, które są wywoływane.*

*extraArgs*\
Argumenty, które uzyskują doskonałe utajnienie przekazywania *, wraz z* dopasowanym typem zdarzenia.

### <a name="return-value"></a>Wartość zwracana

**`bool`** Wartość, która jest w **`true`** przypadku, gdy dopasowanie zakończyło się powodzeniem lub **`false`** w inny sposób.

## <a name="remarks"></a>Uwagi

Ostatnie zdarzenie w *eventStack* jest zawsze dopasowane do ostatniego wpisu na liście połączone \[ *TEvent*, *TEvents...* \] typu. Wszystkie inne wpisy *TEvent* i *TEvents* mogą być zgodne z dowolnym pozycją w *eventStack* z wyjątkiem ostatniego, pod warunkiem, że znajdują się one w tej samej kolejności.

Typy zdarzeń do użycia dla parametrów *TEvent* i *TEvents* są wybierane z listy *klas przechwytywania*. Aby zapoznać się z listą zdarzeń i klas przechwytywania, których można użyć do dopasowania, zobacz [tabela zdarzeń](../event-table.md).

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
