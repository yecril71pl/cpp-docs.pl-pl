---
title: MakeDynamicReloggerGroup
description: Dokumentacja funkcji MakeDynamicReloggerGroup zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c0d1348be8878e686aeba4a58c407264264c5bc4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224191"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`MakeDynamicReloggerGroup`Funkcja służy do tworzenia dynamicznej grupy rejestrowania. Członkowie grupy ponownego rejestrowania odbierają zdarzenia po jednym z lewej strony do prawej, dopóki wszystkie zdarzenia w śladach nie zostaną przetworzone.

## <a name="syntax"></a>Składnia

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>Parametry

*Rejestratory*\
Wektor wskaźników [IRelogger](../other-types/irelogger-class.md) uwzględnionych w grupie dynamicznego modułu rejestrującego. Te wskaźniki mogą być surowe, `std::unique_ptr` lub `std::shared_ptr` . Wskaźniki [IAnalyzer](../other-types/ianalyzer-class.md) są również uznawane za `IRelogger` wskaźniki ze względu na relację dziedziczenia.

### <a name="return-value"></a>Wartość zwracana

Dynamiczna grupa ponownego rejestrowania. Użyj **`auto`** słowa kluczowego, aby przechwycić wartość zwracaną.

## <a name="remarks"></a>Uwagi

W przeciwieństwie do grup statycznych ponownego rejestrowania, członkowie dynamicznej grupy ponownego rejestrowania nie muszą być znani w czasie kompilacji. Możesz wybrać kolejno elementy członkowskie grupy w czasie wykonywania w oparciu o dane wejściowe programu lub na podstawie innych wartości, które są nieznane w czasie kompilacji. W przeciwieństwie do grup statycznych rerejestratorów, [`IRelogger`](../other-types/irelogger-class.md) wskaźniki w grupie dynamicznego modułu rejestrującego mają zachowanie polimorficzne, a wywołania funkcji wirtualnych są wysyłane poprawnie. Ta elastyczność jest kosztem prawdopodobnie wolniejszego czasu przetwarzania zdarzeń. Gdy wszyscy członkowie grupy ponownego rejestrowania są znani w czasie kompilacji i jeśli nie potrzebujesz zachowań polimorficznych, rozważ użycie statycznej grupy rejestru. Aby użyć statycznej grupy ponownego rejestrowania, [`MakeStaticReloggerGroup`](make-static-relogger-group.md) zamiast tego wywołaj.

Dynamiczna grupa ponownego rejestrowania może być hermetyzowana wewnątrz statycznej grupy rejestrowania. Adres jest przekazywany do [`MakeStaticReloggerGroup`](make-static-relogger-group.md) . Ta technika umożliwia przekazanie grup dynamicznego ponownego rejestrowania do funkcji, takich jak [`Relog`](relog.md) , które akceptują tylko statyczne grupy rejestrujące.

::: moniker-end
