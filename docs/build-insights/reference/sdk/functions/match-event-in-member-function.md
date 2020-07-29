---
title: MatchEventInMemberFunction
description: Dokumentacja funkcji MatchEventInMemberFunction zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d3fdc015b0744cb5d0f98a1c9025343b93489ed9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224152"
---
# <a name="matcheventinmemberfunction"></a>MatchEventInMemberFunction

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEventInMemberFunction`Funkcja jest używana do dopasowania zdarzenia do typu opisanego przez pierwszy parametr funkcji członkowskiej. Dopasowane zdarzenie jest przekazywane do funkcji składowej w celu dalszej obróbki.

## <a name="syntax"></a>Składnia

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     TEvent,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventInMemberFunction(
    const RawEvent&          event,
    TInterface*              objectPtr,
    TReturn (TInterface::*   memberFunc)(TEvent, TExtraParams...),
    TExtraArgs&&...          extraArgs);
```

### <a name="parameters"></a>Parametry

*TInterface*\
Typ, który zawiera funkcję członkowską.

*TReturn*\
Zwracany typ funkcji składowej.

*TEvent*\
Typ zdarzenia do dopasowania.

*TExtraParams*\
Typy dodatkowych parametrów akceptowane przez funkcję członkowską wraz z typem zdarzenia do dopasowania.

*TExtraArgs*\
Typy dodatkowych argumentów, które zostały przekazane do `MatchEventInMemberFunction` .

*wydarzen*\
Zdarzenie do dopasowania względem typu zdarzenia opisanego przez *TEvent*.

*objectPtr*\
Wskaźnik do obiektu, w którym wywołano *memberFunc* .

*memberFunc*\
Funkcja członkowska opisująca typ zdarzenia do dopasowania.

*extraArgs*\
Argumenty, które uzyskują doskonałe przesłanie dalej do *memberFunc* wraz z parametrem typu zdarzenia.

### <a name="return-value"></a>Wartość zwracana

**`bool`** Wartość, która jest w **`true`** przypadku, gdy dopasowanie zakończyło się powodzeniem lub **`false`** w inny sposób.

## <a name="remarks"></a>Uwagi

Typ zdarzenia do użycia dla parametru *TEvent* można wybrać z listy *klas przechwytywania*. Aby zapoznać się z listą zdarzeń i klas przechwytywania, których można użyć do dopasowania, zobacz [tabela zdarzeń](../event-table.md).

## <a name="example"></a>Przykład

```cpp
void MyClass::Foo1(Function f) {}

void MyClass::Foo2(Compiler cl) {}

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo1);

    bool b2 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo2);

    // b1: true because the first parameter of Foo1 is Function.
    // b2: false because the first parameter of Foo2 isn't Function.
}
```

::: moniker-end
