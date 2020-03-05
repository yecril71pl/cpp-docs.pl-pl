---
title: MatchEvent
description: Odwołanie C++ do funkcji MatchEvent zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f8022953e2f56f7c8917f161b094c50e0c5ecbdf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332776"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MatchEvent` jest używana do dopasowania zdarzenia do listy typów zdarzeń. Jeśli zdarzenie jest zgodne z typem na liście, zostanie przekazane do procedury obsługi w celu dalszej obróbki.

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
Typ, który obsługuje `operator()`. Aby uzyskać więcej informacji na temat tego, które argumenty są przekazane do tego operatora, zobacz Opis możliwego do *uzyskania parametru.*

*TExtraArgs*\
Typy dodatkowych argumentów, które zostały przekazane do `MatchEvent`.

\ *zdarzeń*
Zdarzenie, które ma być zgodne z typami zdarzeń opisanymi przez *TEvent* i *TEvents*.

*możliwy* do\
`MatchEvent` wywołuje wywoływanie po pomyślnym dopasowaniu zdarzenia do dowolnego z typów zdarzeń opisanych przez *TEvent* i *TEvents*. Pierwszy argument przesłany do *wartości* wywoływanej jest wartością r dla dopasowanego typu zdarzenia. Pakiet parametrów *extraArgs* jest idealnym przesłanym dalej w pozostałych parametrach *, które są wywoływane.*  

*extraArgs*\
Argumenty, które uzyskują doskonałe utajnienie przekazywania *, wraz z* dopasowanym typem zdarzenia.

### <a name="return-value"></a>Wartość zwracana

Wartość **logiczna** , która jest **prawdziwa** , jeśli dopasowanie zakończyło się pomyślnie lub w przeciwnym razie **zwraca wartość false** .

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
