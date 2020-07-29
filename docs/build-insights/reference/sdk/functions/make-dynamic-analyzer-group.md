---
title: MakeDynamicAnalyzerGroup
description: Dokumentacja funkcji MakeDynamicAnalyzerGroup zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c4c244066b41837a8dd95b44bab2b096134ed5d4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224204"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`MakeDynamicAnalyzerGroup`Funkcja służy do tworzenia grupy analizatorów dynamicznych. Członkowie grupy analizatora odbierają zdarzenia jeden od lewej do prawej, dopóki wszystkie zdarzenia w śladach nie zostaną przeanalizowane.

## <a name="syntax"></a>Składnia

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>Parametry

*Analizatory*\
Wektor wskaźników [IAnalyzer](../other-types/ianalyzer-class.md) znajdujących się w grupie analizatorów dynamicznych. Te wskaźniki mogą być surowe, `std::unique_ptr` lub `std::shared_ptr` .

### <a name="return-value"></a>Wartość zwracana

Dynamiczna grupa analizatorów. Użyj **`auto`** słowa kluczowego, aby przechwycić wartość zwracaną.

## <a name="remarks"></a>Uwagi

W przeciwieństwie do grup analizatorów statycznych, członkowie dynamicznej grupy analizatorów nie muszą być znani w czasie kompilacji. Możesz wybrać elementy członkowskie grupy analizatora w czasie wykonywania w oparciu o dane wejściowe programu lub na podstawie innych wartości, które są nieznane w czasie kompilacji. W przeciwieństwie do grup analizatorów statycznych, [`IAnalyzer`](../other-types/ianalyzer-class.md) wskaźniki w grupie analizatorów dynamicznych mają zachowanie polimorficzne i wywołania funkcji wirtualnych są wysyłane poprawnie. Ta elastyczność jest kosztem prawdopodobnie wolniejszego czasu przetwarzania zdarzeń. Gdy wszystkie elementy członkowskie grupy analizatorów są znane w czasie kompilacji, a jeśli nie potrzebujesz zachowań polimorficznych, należy rozważyć użycie statycznej grupy analizatorów. Aby użyć statycznej grupy analizatora, [`MakeStaticAnalyzerGroup`](make-static-analyzer-group.md) zamiast tego wywołaj.

Dynamiczna grupa analizatorów może być hermetyzowana wewnątrz statycznej grupy analizatorów. Jest to wykonywane przez przekazanie jego adresu do [`MakeStaticAnalyzerGroup`](make-static-analyzer-group.md) . Ta technika umożliwia przekazanie grup analizatorów dynamicznych do funkcji takich jak [`Analyze`](analyze.md) , które akceptują tylko statyczne grupy analizatorów.

::: moniker-end
