---
title: MakeStaticReloggerGroup
description: Dokumentacja funkcji MakeStaticReloggerGroup zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b74ee778ffafbcb4c292b4b36b309d5ff4d66c27
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224165"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`MakeStaticReloggerGroup`Funkcja służy do tworzenia statycznej grupy ponownego rejestrowania, która może być przenoszona do funkcji, takich jak [relog](relog.md). Członkowie grupy ponownego rejestrowania odbierają zdarzenia po jednym z lewej strony do prawej, dopóki wszystkie zdarzenia w śladach nie zostaną przetworzone.

## <a name="syntax"></a>Składnia

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>Parametry

*TReloggerPtrs*\
Ten parametr jest zawsze wywnioskowany.

*Rejestratory*\
Pakiet parametrów [`IRelogger`](../other-types/irelogger-class.md) wskaźników, które znajdują się w statycznej grupie rejestru. Te wskaźniki mogą być surowe, `std::unique_ptr` lub `std::shared_ptr` . [`IAnalyzer`](../other-types/ianalyzer-class.md)wskaźniki są również uznawane za `IRelogger` wskaźniki ze względu na relację dziedziczenia.

### <a name="return-value"></a>Wartość zwracana

Statyczna Grupa rejestru. Użyj **`auto`** słowa kluczowego, aby przechwycić wartość zwracaną.

## <a name="remarks"></a>Uwagi

W przeciwieństwie do grup dynamicznego ponownego rejestrowania, członkowie statycznej grupy ponownego rejestrowania muszą być znani w czasie kompilacji. Ponadto statyczna Grupa ponownego rejestrowania zawiera [`IRelogger`](../other-types/irelogger-class.md) wskaźniki, które nie mają zachowań polimorficznych. W przypadku korzystania z statycznej grupy ponownego rejestrowania do analizowania śledzenia zdarzeń systemu Windows (ETW), wywołania `IRelogger` interfejsu zawsze są rozpoznawane względem obiektu bezpośrednio wskazywanego przez członka grupy. Ta utrata elastyczności zapewnia szybszy czas przetwarzania zdarzeń. Jeśli członkowie grupy nie mogą być znani w czasie kompilacji lub Jeśli wymagasz zachowań polimorficznych na `IRelogger` wskaźnikach, rozważ użycie dynamicznej grupy ponownego rejestrowania. Możesz użyć dynamicznej grupy rejestrowania, wywołując [`MakeDynamicReloggerGroup`](make-dynamic-relogger-group.md) zamiast tego.

::: moniker-end
