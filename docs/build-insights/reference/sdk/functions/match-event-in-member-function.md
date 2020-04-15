---
title: Funkcja MatchEventInMemberFunction
description: Odwołanie do funkcji SDK MatchEventInMemberFunction aplikacji C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 522630da16e3f4a1294316d88140f4bc25dca2c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323898"
---
# <a name="matcheventinmemberfunction"></a>Funkcja MatchEventInMemberFunction

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MatchEventInMemberFunction` jest używana do dopasowania zdarzenia do typu opisanego przez pierwszy parametr funkcji elementu członkowskiego. Dopasowane zdarzenie jest przekazywane do funkcji elementu członkowskiego w celu dalszego przetwarzania.

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

*TInterface (Wzlot)*\
Typ, który zawiera funkcję elementu członkowskiego.

*TReturn (Powrót)*\
Zwracany typ funkcji elementu członkowskiego.

*TEvent ( TEvent )*\
Typ zdarzenia do dopasowania.

*TExtraParams*\
Typy dodatkowych parametrów zaakceptowanych przez funkcję elementu członkowskiego wraz z typem zdarzenia do dopasowania.

*TExtraArgs*\
Typy dodatkowych argumentów, które `MatchEventInMemberFunction`zostały przekazane do .

*Zdarzenie*\
Zdarzenie zgodne z typem zdarzenia opisanym przez *TEvent*.

*objectPtr (polecenie objectPtr)*\
Wskaźnik do obiektu, na którym *element memberFunc* zostanie wywołany.

*element członkowskiFunc*\
Funkcja elementu członkowskiego, która opisuje typ zdarzenia do dopasowania.

*extraArgs (extraArgs)*\
Argumenty, które uzyskać doskonałe przekazywane do *elementu memberFunc* wraz z parametrem typu zdarzenia.

### <a name="return-value"></a>Wartość zwracana

Wartość **bool,** która jest **true,** jeśli dopasowanie zakończyło się pomyślnie lub **false** w inny sposób.

## <a name="remarks"></a>Uwagi

Typ zdarzenia, który ma być używany dla parametru *TEvent,* można wybrać z listy *klas przechwytywania*. Aby uzyskać listę zdarzeń i klasy przechwytywania, których można użyć do ich dopasowania, zobacz [tabelę zdarzeń](../event-table.md).

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
