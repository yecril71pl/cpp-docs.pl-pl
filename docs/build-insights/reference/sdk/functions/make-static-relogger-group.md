---
title: Grupa MakeStaticRelogger
description: Odwołanie do funkcji SDK MakeStaticReloggerGroup w programie C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75b638537cb8e0cdeeb5476a3f5277e8e90d9baf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323911"
---
# <a name="makestaticreloggergroup"></a>Grupa MakeStaticRelogger

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MakeStaticReloggerGroup` służy do tworzenia statycznej grupy reloggera, która może być przekazywana do funkcji, takich jak [Relog](relog.md). Członkowie grupy relogger odbierać zdarzenia jeden po drugim od lewej do prawej, aż wszystkie zdarzenia w śledzenia zostały przetworzone.

## <a name="syntax"></a>Składnia

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>Parametry

*TReloggerPtrs (Włazów)*\
Ten parametr jest zawsze wydedukowany.

*reloggers*\
Pakiet parametrów wskaźników [IRelogger,](../other-types/irelogger-class.md) który jest zawarty w statycznej grupie reloggera. Te wskaźniki mogą być `std::unique_ptr`surowe, lub `std::shared_ptr`. [Wskaźniki IAnalyzer](../other-types/ianalyzer-class.md) są `IRelogger` również uważane za wskaźniki ze względu na relację dziedziczenia.

### <a name="return-value"></a>Wartość zwracana

Statyczna grupa reloggera. Użyj **automatycznego** słowa kluczowego, aby przechwycić wartość zwracaną.

## <a name="remarks"></a>Uwagi

W przeciwieństwie do grup dynamicznego reloggera członkowie statycznej grupy reloggera muszą być znani w czasie kompilacji. Ponadto statyczna grupa reloggera zawiera wskaźniki [IRelogger,](../other-types/irelogger-class.md) które nie mają zachowania polimorficznego. Podczas korzystania ze statycznej grupy relogger do analizy śledzenia zdarzeń dla systemu `IRelogger` Windows (ETW) śledzenia, wywołania interfejsu zawsze rozpoznać do obiektu bezpośrednio wskazane przez członka grupy reloggera. Ta utrata elastyczności wiąże się z możliwością krótszym czasem przetwarzania zdarzeń. Jeśli członkowie grupy relogger nie mogą być znane w czasie kompilacji lub jeśli wymagają `IRelogger` zachowania polimorficzne na wskaźniki, należy rozważyć użycie dynamicznej grupy relogger. Dynamiczną grupę reloggera można użyć, wywołując [makedynamicreloggergroup](make-dynamic-relogger-group.md) zamiast.

::: moniker-end
