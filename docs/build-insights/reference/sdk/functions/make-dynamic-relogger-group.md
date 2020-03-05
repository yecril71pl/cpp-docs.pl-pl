---
title: MakeDynamicReloggerGroup
description: Odwołanie C++ do funkcji MakeDynamicReloggerGroup zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4ad394d3ba2982e7ee4f2a497fef2ea65a3c1769
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332825"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MakeDynamicReloggerGroup` służy do tworzenia dynamicznej grupy rejestrowania. Członkowie grupy ponownego rejestrowania odbierają zdarzenia po jednym z lewej strony do prawej, dopóki wszystkie zdarzenia w śladach nie zostaną przetworzone.

## <a name="syntax"></a>Składnia

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>Parametry

*rejestratory*\
Wektor wskaźników [IRelogger](../other-types/irelogger-class.md) uwzględnionych w grupie dynamicznego modułu rejestrującego. Te wskaźniki mogą być surowe, `std::unique_ptr`lub `std::shared_ptr`. [IAnalyzer](../other-types/ianalyzer-class.md) wskaźniki są również uznawane za wskaźniki `IRelogger` ze względu na relację dziedziczenia.

### <a name="return-value"></a>Wartość zwracana

Dynamiczna grupa ponownego rejestrowania. Użyj słowa kluczowego słowo kluczowe, aby przechwycić wartość zwracaną.

## <a name="remarks"></a>Uwagi

W przeciwieństwie do grup statycznych ponownego rejestrowania, członkowie dynamicznej grupy ponownego rejestrowania nie muszą być znani w czasie kompilacji. Możesz wybrać kolejno elementy członkowskie grupy w czasie wykonywania w oparciu o dane wejściowe programu lub na podstawie innych wartości, które są nieznane w czasie kompilacji. W przeciwieństwie do grup statycznych rerejestratorów, wskaźniki [IRelogger](../other-types/irelogger-class.md) w grupie dynamicznego modułu rejestrującego mają zachowanie polimorficzne, a wywołania funkcji wirtualnych są wysyłane poprawnie. Ta elastyczność jest kosztem prawdopodobnie wolniejszego czasu przetwarzania zdarzeń. Gdy wszyscy członkowie grupy ponownego rejestrowania są znani w czasie kompilacji i jeśli nie potrzebujesz zachowań polimorficznych, rozważ użycie statycznej grupy rejestru. Aby użyć statycznej grupy ponownego rejestrowania, wywołaj [MakeStaticReloggerGroup](make-static-relogger-group.md) .

Dynamiczna grupa ponownego rejestrowania może być hermetyzowana wewnątrz statycznej grupy rejestrowania. Adres jest przekazywany do [MakeStaticReloggerGroup](make-static-relogger-group.md). Ta technika umożliwia przekazanie grup dynamicznego ponownego rejestrowania do funkcji takich jak [relog](relog.md), które akceptują tylko statyczne grupy rejestrujące.

::: moniker-end
