---
title: Funkcja MatchEventStackInMember
description: Odwołanie do funkcji SDK MatchEventStackInMemberFunction w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28842a02e7edc2e00266d8c7941798f4ce714ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323887"
---
# <a name="matcheventstackinmemberfunction"></a>Funkcja MatchEventStackInMember

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MatchEventStackInMemberFunction` jest używana do dopasowania stosu zdarzeń do hierarchii określonych zdarzeń, opisanej przez listę parametrów funkcji elementu członkowskiego. Dopasowane hierarchie są przekazywane do funkcji elementu członkowskiego w celu dalszego przetwarzania. Aby dowiedzieć się więcej o zdarzeniach, stosach zdarzeń i hierarchiach, zobacz [tabelę zdarzeń](../event-table.md).

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

*TInterface (Wzlot)*\
Typ, który zawiera funkcję elementu członkowskiego.

*TReturn (Powrót)*\
Zwracany typ funkcji elementu członkowskiego.

*T1*, ..., *T10*\
Typy opisujące hierarchię zdarzeń do dopasowania.

*TExtraParams*\
Typy dodatkowych parametrów akceptowanych przez funkcję elementu członkowskiego i typy hierarchii zdarzeń.

*TExtraArgs*\
Typy dodatkowych argumentów, które `MatchEventStackInMemberFunction`zostały przekazane do .

*eventStack (własówce wydarzenia)*\
Stos zdarzeń zgodny z hierarchią typów zdarzeń opisaną przez *T1* do *T10*.

*objectPtr (polecenie objectPtr)*\
Wskaźnik do obiektu, na którym wywoływany jest *element członkowskiFunc.*

*element członkowskiFunc*\
Funkcja elementu członkowskiego, która opisuje hierarchię typów zdarzeń do dopasowania.

*extraArgs (extraArgs)*\
Argumenty, które są doskonałe przekazywane do *elementu członkowskiegoFunc* wraz z parametrami hierarchii typów zdarzeń.

### <a name="return-value"></a>Wartość zwracana

Wartość **bool,** która jest **true,** jeśli dopasowanie zakończyło się pomyślnie lub **false** w inny sposób.

## <a name="remarks"></a>Uwagi

Ostatnie zdarzenie w *eventStack* jest zawsze dopasowywać do ostatniego wpisu w hierarchii typów zdarzeń, aby dopasować. Wszystkie inne typy w hierarchii typów zdarzeń można dopasować dowolną pozycję w *eventStack* z wyjątkiem ostatniego, pod warunkiem, że są one w tej samej kolejności.

Typy zdarzeń, które mają być używane dla parametrów *od T1* do *T10,* są wybierane z listy *klas przechwytywania.* Aby uzyskać listę zdarzeń i klasy przechwytywania, których można użyć do ich dopasowania, zobacz [tabelę zdarzeń](../event-table.md).

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
