---
title: Grupa MakeDynamicRelogger
description: Odwołanie do funkcji SDK MakeDynamicReloggerGroup w programie C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f49e37f8e1a8b9ca9a800d20b2891a54453095ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323949"
---
# <a name="makedynamicreloggergroup"></a>Grupa MakeDynamicRelogger

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `MakeDynamicReloggerGroup` służy do tworzenia dynamicznej grupy reloggera. Członkowie grupy relogger odbierać zdarzenia jeden po drugim od lewej do prawej, aż wszystkie zdarzenia w śledzenia zostały przetworzone.

## <a name="syntax"></a>Składnia

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>Parametry

*reloggers*\
Wektor wskaźników [IRelogger](../other-types/irelogger-class.md) zawarte w grupie dynamicznego reloggera. Te wskaźniki mogą być `std::unique_ptr`surowe, lub `std::shared_ptr`. [Wskaźniki IAnalyzer](../other-types/ianalyzer-class.md) są `IRelogger` również uważane za wskaźniki ze względu na relację dziedziczenia.

### <a name="return-value"></a>Wartość zwracana

Dynamiczna grupa reloggerów. Użyj **automatycznego** słowa kluczowego, aby przechwycić wartość zwracaną.

## <a name="remarks"></a>Uwagi

W przeciwieństwie do statycznych grup reloggera członkowie grupy reloggera dynamicznego nie muszą być znani w czasie kompilacji. Można wybrać członków grupy relogger w czasie wykonywania na podstawie danych wejściowych programu lub na podstawie innych wartości, które są nieznane w czasie kompilacji. W przeciwieństwie do statycznych grup reloggera wskaźniki [IRelogger](../other-types/irelogger-class.md) w grupie dynamicznego reloggera mają zachowanie polimorficzne, a wywołania funkcji wirtualnych są wywoływane poprawnie. Ta elastyczność odbywa się kosztem prawdopodobnie wolniejszy czas przetwarzania zdarzeń. Gdy wszystkie relogger członków grupy są znane w czasie kompilacji, a jeśli nie potrzebujesz zachowania polimorficzne, należy rozważyć użycie statycznej grupy reloggera. Aby użyć statycznej grupy relogger, [wywołanie MakeStaticReloggerGroup](make-static-relogger-group.md) zamiast.

Dynamiczna grupa reloggera może być hermetyzowana wewnątrz statycznej grupy reloggera. Jego adres należy przekazać do [MakeStaticReloggerGroup](make-static-relogger-group.md). Ta technika służy do przekazywania dynamicznych grup reloggera do funkcji, takich jak [Relog](relog.md), które akceptują tylko statyczne grupy reloggera.

::: moniker-end
