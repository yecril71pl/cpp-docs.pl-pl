---
title: MatchEvent
description: Dokumentacja funkcji MatchEvent zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8ec2c6bfcacf28998058dc66b5f363fbf1ea5d70
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224113"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEvent`Funkcja jest używana do dopasowania zdarzenia do listy typów zdarzeń. Jeśli zdarzenie jest zgodne z typem na liście, zostanie przekazane do procedury obsługi w celu dalszej obróbki.

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

*TEvent*\
Pierwszy typ zdarzenia, który ma być zgodny.

*TEvents*\
Pozostałe typy zdarzeń, które chcesz dopasować.

*TCallable*\
Typ, który obsługuje `operator()` . Aby uzyskać więcej informacji na temat tego, które argumenty są przekazane do tego operatora, zobacz Opis możliwego do *uzyskania parametru.*

*TExtraArgs*\
Typy dodatkowych argumentów, które zostały przekazane do `MatchEvent` .

*wydarzen*\
Zdarzenie, które ma być zgodne z typami zdarzeń opisanymi przez *TEvent* i *TEvents*.

*żądanie*\
`MatchEvent`wywołuje *callable* wywoływanie po pomyślnym dopasowaniu zdarzenia do dowolnego z typów zdarzeń opisanych przez *TEvent* i *TEvents*. Pierwszy argument przesłany do *wartości* wywoływanej jest wartością r dla dopasowanego typu zdarzenia. Pakiet parametrów *extraArgs* jest idealnym przesłanym dalej w pozostałych parametrach *, które są wywoływane.*  

*extraArgs*\
Argumenty, które uzyskują doskonałe utajnienie przekazywania *, wraz z* dopasowanym typem zdarzenia.

### <a name="return-value"></a>Wartość zwracana

**`bool`** Wartość, która jest w **`true`** przypadku, gdy dopasowanie zakończyło się powodzeniem lub **`false`** w inny sposób.

## <a name="remarks"></a>Uwagi

Typy zdarzeń do użycia dla parametrów *TEvent* i *TEvents* są wybierane z listy *klas przechwytywania*. Aby zapoznać się z listą zdarzeń i klas przechwytywania, których można użyć do dopasowania, zobacz [tabela zdarzeń](../event-table.md).

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
