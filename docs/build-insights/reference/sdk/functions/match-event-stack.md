---
title: MatchEventStack
description: Odwołanie C++ do funkcji MatchEventStack zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 445c2d00c24da10754d32256de0c691e82b557e1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332783"
---
# <a name="matcheventstack"></a>MatchEventStack

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MatchEventStack` jest używana do dopasowania stosu zdarzeń do określonej hierarchii zdarzeń. Dopasowane hierarchie są przekazywane do programu obsługi w celu dalszej obróbki. Aby dowiedzieć się więcej o zdarzeniach, stosach zdarzeń i hierarchiach, zobacz [tabela zdarzeń](../event-table.md).

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
Typ, który obsługuje `operator()`. Aby uzyskać więcej informacji na temat tego, które argumenty są przekazane do tego operatora, zobacz Opis możliwego do *uzyskania parametru.*

*TExtraArgs*\
Typy dodatkowych argumentów przekazane do `MatchEventStack`.

*eventStack*\
Stos zdarzeń do dopasowania względem hierarchii typów zdarzeń opisanych przez *TEvent* i *TEvents*.

*możliwy* do\
Po pomyślnym dopasowaniu stosu zdarzeń z hierarchią typów zdarzeń opisanymi przez *TEvent* i *TEvents*, *`MatchEventStack` wywołuje*wywoływanie. Przekazuje *on do* możliwego do przekroczenia jednego argumentu r-wartości dla każdego typu w hierarchii zdarzeń. Pakiet parametrów *extraArgs* jest idealnym przesłanym dalej w pozostałych parametrach *, które są wywoływane.*

*extraArgs*\
Argumenty, które uzyskują doskonałe utajnienie przekazywania *, wraz z* dopasowanym typem zdarzenia.

### <a name="return-value"></a>Wartość zwracana

Wartość **logiczna** , która jest **prawdziwa** , jeśli dopasowanie zakończyło się pomyślnie, lub **Fałsz** w przeciwnym razie.

## <a name="remarks"></a>Uwagi

Ostatnie zdarzenie w *eventStack* jest zawsze dopasowane do ostatniego wpisu na liście połączone \[*TEvent*, *TEvents...* \]. Wszystkie inne wpisy *TEvent* i *TEvents* mogą być zgodne z dowolnym pozycją w *eventStack* z wyjątkiem ostatniego, pod warunkiem, że znajdują się one w tej samej kolejności.

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
