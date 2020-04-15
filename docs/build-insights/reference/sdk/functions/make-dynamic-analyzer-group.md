---
title: Grupa MakeDynamicAnalyzer
description: Odwołanie do funkcji SDK MakeDynamicAnalyzerGroup w programie C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 148eeea41f29ac6dd75653feed7f3f3f8c301911
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323964"
---
# <a name="makedynamicanalyzergroup"></a>Grupa MakeDynamicAnalyzer

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MakeDynamicAnalyzerGroup` służy do tworzenia grupy analizatorów dynamicznych. Członkowie grupy analizatorów odbierają zdarzenia jeden po drugim od lewej do prawej, dopóki wszystkie zdarzenia w śledzeniu nie będą analizowane.

## <a name="syntax"></a>Składnia

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>Parametry

*Analizatory*\
Wektor wskaźników [IAnalyzer](../other-types/ianalyzer-class.md) zawarte w grupie analizatora dynamicznego. Te wskaźniki mogą być `std::unique_ptr`surowe, lub `std::shared_ptr`.

### <a name="return-value"></a>Wartość zwracana

Dynamiczna grupa analizatorów. Użyj **automatycznego** słowa kluczowego, aby przechwycić wartość zwracaną.

## <a name="remarks"></a>Uwagi

W przeciwieństwie do grup analizatorów statycznych członkowie grupy analizatorów dynamicznych nie muszą być znani w czasie kompilacji. Można wybrać członków grupy analizatora w czasie wykonywania na podstawie danych wejściowych programu lub na podstawie innych wartości, które są nieznane w czasie kompilacji. W przeciwieństwie do grup analizatorów statycznych wskaźniki [IAnalyzer](../other-types/ianalyzer-class.md) w grupie analizatorów dynamicznych mają zachowanie polimorficzne, a wywołania funkcji wirtualnych są wywoływane poprawnie. Ta elastyczność odbywa się kosztem prawdopodobnie wolniejszy czas przetwarzania zdarzeń. Gdy wszystkie elementy członkowskie grupy analizatora są znane w czasie kompilacji, a jeśli nie potrzebujesz zachowania polimorficznego, należy rozważyć użycie grupy analizatorów statycznych. Aby użyć grupy analizatora statycznego, należy [wywołać MakeStaticAnalyzerGroup](make-static-analyzer-group.md) zamiast tego.

Grupa analizatorów dynamicznych może być hermetyzowana wewnątrz grupy analizatorów statycznych. Odbywa się to poprzez przekazanie jego adres do [MakeStaticAnalyzerGroup](make-static-analyzer-group.md). Ta technika służy do przekazywania grup analizatorów dynamicznych do funkcji, takich jak [Analiza](analyze.md), które akceptują tylko grupy analizatorów statycznych.

::: moniker-end
