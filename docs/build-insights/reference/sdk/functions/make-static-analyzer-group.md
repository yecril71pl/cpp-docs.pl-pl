---
title: Grupa MakeStaticAnalyzer
description: Odwołanie do funkcji SDK MakeStaticAnalyzerGroup w programie C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72f7f5d7a408436902394451a52dd66efe1d93f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323939"
---
# <a name="makestaticanalyzergroup"></a>Grupa MakeStaticAnalyzer

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MakeStaticAnalyzerGroup` służy do tworzenia grupy analizatorów statycznych, które mogą być przekazywane do funkcji, takich jak [Analiza](analyze.md) lub [Relog](relog.md). Członkowie grupy analizatorów odbierają zdarzenia jeden po drugim od lewej do prawej, dopóki wszystkie zdarzenia w śledzeniu nie będą analizowane.

## <a name="syntax"></a>Składnia

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>Parametry

*TAnalyzerPtrs (TAnalyzerPtrs)*\
Ten parametr jest zawsze wydedukowany.

*Analizatory*\
Pakiet parametrów wskaźników [IAnalyzer](../other-types/ianalyzer-class.md) zawarte w grupie analizatorów statycznych. Te wskaźniki mogą być `std::unique_ptr`surowe, lub `std::shared_ptr`.

### <a name="return-value"></a>Wartość zwracana

Grupa analizatorów statycznych. Użyj **automatycznego** słowa kluczowego, aby przechwycić wartość zwracaną.

## <a name="remarks"></a>Uwagi

W przeciwieństwie do grup analizatorów dynamicznych członkowie grupy analizatorów statycznych muszą być znani w czasie kompilacji. Ponadto grupa analizatora statycznego zawiera wskaźniki [IAnalyzer,](../other-types/ianalyzer-class.md) które nie mają zachowania polimorficzne. Podczas korzystania z grupy analizatora statycznego do analizowania śledzenia zdarzeń dla `IAnalyzer` systemu Windows (ETW) śledzenia, wywołania interfejsu zawsze rozpoznać do obiektu bezpośrednio wskazane przez członka grupy analizatora. Ta utrata elastyczności wiąże się z możliwością krótszym czasem przetwarzania zdarzeń. Jeśli członkowie grupy analizatorów nie mogą być znani w czasie kompilacji lub jeśli potrzebujesz `IAnalyzer` zachowania polimorficznego na wskaźnikach, należy rozważyć użycie grupy analizatorów dynamicznych. Aby użyć grupy analizatora dynamicznego, należy [wywołać MakeDynamicAnalyzerGroup](make-static-analyzer-group.md) zamiast.

::: moniker-end
