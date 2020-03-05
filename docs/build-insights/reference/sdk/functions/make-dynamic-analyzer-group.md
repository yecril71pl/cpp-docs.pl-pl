---
title: MakeDynamicAnalyzerGroup
description: Odwołanie C++ do funkcji MakeDynamicAnalyzerGroup zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f409d685c6af6514b73cd837d668a962c1a0d01a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332832"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MakeDynamicAnalyzerGroup` służy do tworzenia grupy analizatorów dynamicznych. Członkowie grupy analizatora odbierają zdarzenia jeden od lewej do prawej, dopóki wszystkie zdarzenia w śladach nie zostaną przeanalizowane.

## <a name="syntax"></a>Składnia

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>Parametry

*analizatory*\
Wektor wskaźników [IAnalyzer](../other-types/ianalyzer-class.md) znajdujących się w grupie analizatorów dynamicznych. Te wskaźniki mogą być surowe, `std::unique_ptr`lub `std::shared_ptr`.

### <a name="return-value"></a>Wartość zwracana

Dynamiczna grupa analizatorów. Użyj słowa kluczowego słowo kluczowe, aby przechwycić wartość zwracaną.

## <a name="remarks"></a>Uwagi

W przeciwieństwie do grup analizatorów statycznych, członkowie dynamicznej grupy analizatorów nie muszą być znani w czasie kompilacji. Możesz wybrać elementy członkowskie grupy analizatora w czasie wykonywania w oparciu o dane wejściowe programu lub na podstawie innych wartości, które są nieznane w czasie kompilacji. W przeciwieństwie do grup analizatorów statycznych, wskaźniki [IAnalyzer](../other-types/ianalyzer-class.md) w grupie analizatorów dynamicznych mają zachowanie polimorficzne, a wywołania funkcji wirtualnych są wysyłane poprawnie. Ta elastyczność jest kosztem prawdopodobnie wolniejszego czasu przetwarzania zdarzeń. Gdy wszystkie elementy członkowskie grupy analizatorów są znane w czasie kompilacji, a jeśli nie potrzebujesz zachowań polimorficznych, należy rozważyć użycie statycznej grupy analizatorów. Aby użyć statycznej grupy analizatorów, wywołaj [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) zamiast.

Dynamiczna grupa analizatorów może być hermetyzowana wewnątrz statycznej grupy analizatorów. Jest to wykonywane przez przekazanie jego adresu do [MakeStaticAnalyzerGroup](make-static-analyzer-group.md). Ta technika umożliwia przekazywanie grup analizatorów dynamicznych do funkcji, takich jak [Analizowanie](analyze.md), które akceptują tylko statyczne grupy analizatorów.

::: moniker-end
