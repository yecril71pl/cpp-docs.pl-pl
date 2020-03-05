---
title: MakeStaticReloggerGroup
description: Odwołanie C++ do funkcji MakeStaticReloggerGroup zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 06927af89b16d9de1148e555868dd2022c59b171
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332811"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MakeStaticReloggerGroup` służy do tworzenia statycznej grupy ponownego rejestrowania, która może być przenoszona do funkcji, takich jak [relog](relog.md). Członkowie grupy ponownego rejestrowania odbierają zdarzenia po jednym z lewej strony do prawej, dopóki wszystkie zdarzenia w śladach nie zostaną przetworzone.

## <a name="syntax"></a>Składnia

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>Parametry

*TReloggerPtrs*\
Ten parametr jest zawsze wywnioskowany.

*rejestratory*\
Pakiet parametrów wskaźników [IRelogger](../other-types/irelogger-class.md) , które znajdują się w statycznej grupie rejestru. Te wskaźniki mogą być surowe, `std::unique_ptr`lub `std::shared_ptr`. [IAnalyzer](../other-types/ianalyzer-class.md) wskaźniki są również uznawane za wskaźniki `IRelogger` ze względu na relację dziedziczenia.

### <a name="return-value"></a>Wartość zwracana

Statyczna Grupa rejestru. Użyj słowa kluczowego słowo kluczowe, aby przechwycić wartość zwracaną.

## <a name="remarks"></a>Uwagi

W przeciwieństwie do grup dynamicznego ponownego rejestrowania, członkowie statycznej grupy ponownego rejestrowania muszą być znani w czasie kompilacji. Ponadto statyczna Grupa ponownego rejestrowania zawiera [IRelogger](../other-types/irelogger-class.md) wskaźniki, które nie mają zachowań polimorficznych. W przypadku korzystania z statycznej grupy ponownego rejestrowania do analizowania śledzenia zdarzeń systemu Windows (ETW), wywołania interfejsu `IRelogger` zawsze są rozwiązywane do obiektu bezpośrednio wskazywanym przez członka grupy. Ta utrata elastyczności zapewnia szybszy czas przetwarzania zdarzeń. Jeśli członkowie grupy nie mogą być znani w czasie kompilacji lub Jeśli wymagasz zachowań polimorficznych na `IRelogger` wskaźników, rozważ użycie dynamicznej grupy rejestru. Możesz użyć dynamicznej grupy ponownego rejestrowania, wywołując [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md) zamiast.

::: moniker-end
