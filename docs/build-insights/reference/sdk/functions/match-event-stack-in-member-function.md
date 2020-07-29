---
title: MatchEventStackInMemberFunction
description: Dokumentacja funkcji MatchEventStackInMemberFunction zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: db02ce5656bf8970ead7b49d5580f7d81bebb1b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224139"
---
# <a name="matcheventstackinmemberfunction"></a>MatchEventStackInMemberFunction

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEventStackInMemberFunction`Funkcja jest używana do dopasowania stosu zdarzeń do konkretnej hierarchii zdarzeń, opisanej przez listę parametrów funkcji składowej. Dopasowane hierarchie są przekazywane do funkcji składowej w celu dalszej obróbki. Aby dowiedzieć się więcej o zdarzeniach, stosach zdarzeń i hierarchiach, zobacz [tabela zdarzeń](../event-table.md).

## <a name="syntax"></a>Składnia

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, TExtraParams...),
    TExtraArgs&&...           extraArgs);

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, TExtraParams...),
    TExtraArgs&&...           extraArgs);

// Etc...

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename     T3,
    typename     T4,
    typename     T5,
    typename     T6,
    typename     T7,
    typename     T8,
    typename     T9,
    typename     T10,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, TExtraParams...),
    TExtraArgs&&...           extraArgs);
```

### <a name="parameters"></a>Parametry

*TInterface*\
Typ, który zawiera funkcję członkowską.

*TReturn*\
Zwracany typ funkcji składowej.

*T1*,..., *T10*\
Typy opisujące hierarchię zdarzeń do dopasowania.

*TExtraParams*\
Typy dodatkowych parametrów akceptowane przez funkcję członkowską i typy hierarchii zdarzeń.

*TExtraArgs*\
Typy dodatkowych argumentów, które zostały przekazane do `MatchEventStackInMemberFunction` .

*eventStack*\
Stos zdarzeń do dopasowania względem hierarchii typu zdarzenia opisanego przez *T1* za pomocą *T10*.

*objectPtr*\
Wskaźnik do obiektu, na którym wywoływany jest *memberFunc* .

*memberFunc*\
Funkcja członkowska opisująca hierarchię typów zdarzeń do dopasowania.

*extraArgs*\
Argumenty, które uzyskują doskonałe utajnienie przekazywania do *memberFunc* wraz z parametrami hierarchii typów zdarzeń.

### <a name="return-value"></a>Wartość zwracana

**`bool`** Wartość, która jest w **`true`** przypadku, gdy dopasowanie zakończyło się powodzeniem lub **`false`** w inny sposób.

## <a name="remarks"></a>Uwagi

Ostatnie zdarzenie w *eventStack* jest zawsze dopasowywane do ostatniego wpisu w hierarchii typów zdarzeń w celu dopasowania. Wszystkie inne typy w hierarchii typów zdarzeń mogą być zgodne z dowolnym pozycją w *eventStack* z wyjątkiem ostatniego, pod warunkiem, że znajdują się one w tej samej kolejności.

Typy zdarzeń, które mają być używane dla parametrów *T1* za pośrednictwem *T10* , są wybierane z listy *klas przechwytywania*. Aby zapoznać się z listą zdarzeń i klas przechwytywania, których można użyć do dopasowania, zobacz [tabela zdarzeń](../event-table.md).

## <a name="example"></a>Przykład

```cpp
void MyClass::Foo1(Compiler cl, BackEndPass bep, C2DLL c2,
    CodeGeneration cg, Thread t, Function f) { }

void MyClass::Foo2(Compiler cl, Function f) { }

void MyClass::Foo3(Thread t, Compiler cl, Function f) { }

void MyClass::Foo4(Compiler cl) { }

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo1);

    bool b2 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo2);

    bool b3 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo3);

    bool b4 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo4);

    // b1: true because the parameter types of Foo1 match the eventStack
    //     exactly.
    // b2: true because Function is the last entry in both the member
    //     function parameter list and 'eventStack', and also because
    //     Compiler comes before Function in 'eventStack' and in the
    //     parameter type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', the member function parameter
    //     list doesn't list them in the right order.
    // b4: false because the last entry in the member function parameter
    //     list is Compiler, which doesn't match the last entry in 'eventStack'
    //     (Function).
}
```

::: moniker-end
