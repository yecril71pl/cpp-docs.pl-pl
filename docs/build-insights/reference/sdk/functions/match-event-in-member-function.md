---
title: MatchEventInMemberFunction
description: Odwołanie C++ do funkcji MatchEventInMemberFunction zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eabbb8a91609b1447ebcc19af32df2ffed347c24
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332804"
---
# <a name="matcheventinmemberfunction"></a>MatchEventInMemberFunction

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MatchEventInMemberFunction` jest używana do dopasowania zdarzenia do typu opisanego przez pierwszy parametr funkcji członkowskiej. Dopasowane zdarzenie jest przekazywane do funkcji składowej w celu dalszej obróbki.

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
Typy dodatkowych argumentów, które zostały przekazane do `MatchEventInMemberFunction`.

\ *zdarzeń*
Zdarzenie do dopasowania względem typu zdarzenia opisanego przez *TEvent*.

*objectPtr*\
Wskaźnik do obiektu, w którym wywołano *memberFunc* .

*memberFunc*\
Funkcja członkowska opisująca typ zdarzenia do dopasowania.

*extraArgs*\
Argumenty, które uzyskują doskonałe przesłanie dalej do *memberFunc* wraz z parametrem typu zdarzenia.

### <a name="return-value"></a>Wartość zwracana

Wartość **logiczna** , która jest **prawdziwa** , jeśli dopasowanie zakończyło się pomyślnie, lub **Fałsz** w przeciwnym razie.

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
