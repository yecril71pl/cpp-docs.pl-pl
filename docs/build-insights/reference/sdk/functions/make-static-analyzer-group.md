---
title: MakeStaticAnalyzerGroup
description: Odwołanie C++ do funkcji MakeStaticAnalyzerGroup zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5eabb0fcbb0a0bb0eea0f4e6bbf27b8e4c53c3ab
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332818"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MakeStaticAnalyzerGroup` służy do tworzenia statycznej grupy analizatorów, która może być przenoszona do funkcji, takich jak [Analizuj](analyze.md) lub [relog](relog.md). Członkowie grupy analizatora odbierają zdarzenia jeden od lewej do prawej, dopóki wszystkie zdarzenia w śladach nie zostaną przeanalizowane.

## <a name="syntax"></a>Składnia

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>Parametry

*TAnalyzerPtrs*\
Ten parametr jest zawsze wywnioskowany.

*analizatory*\
Pakiet parametrów wskaźników [IAnalyzer](../other-types/ianalyzer-class.md) uwzględnionych w grupie analizatorów statycznych. Te wskaźniki mogą być surowe, `std::unique_ptr`lub `std::shared_ptr`.

### <a name="return-value"></a>Wartość zwracana

Statyczna Grupa analizatorów. Użyj słowa kluczowego słowo kluczowe, aby przechwycić wartość zwracaną.

## <a name="remarks"></a>Uwagi

W przeciwieństwie do grup analizatorów dynamicznych, członkowie grupy analizatorów statycznych muszą być znani w czasie kompilacji. Ponadto statyczna Grupa analizatorów zawiera [IAnalyzer](../other-types/ianalyzer-class.md) wskaźniki, które nie mają zachowań polimorficznych. W przypadku używania statycznej grupy analizatorów do analizowania śledzenia zdarzeń dla systemu Windows (ETW), wywołania interfejsu `IAnalyzer` zawsze są rozwiązywane do obiektu bezpośrednio wskazywanym przez członka grupy analizatorów. Ta utrata elastyczności zapewnia szybszy czas przetwarzania zdarzeń. Jeśli członkowie grupy analizatorów nie mogą być znani w czasie kompilacji lub jeśli wymagane jest zachowanie polimorficzne na wskaźnikach `IAnalyzer`, rozważ użycie dynamicznej grupy analizatorów. Aby użyć dynamicznej grupy analizatorów, wywołaj [MakeDynamicAnalyzerGroup](make-static-analyzer-group.md) zamiast.

::: moniker-end
