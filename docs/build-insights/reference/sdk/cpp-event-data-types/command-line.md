---
title: Klasa CommandLine
description: Odwołanie do klasy CommandLine aplikacji SDK kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b35d688acf06579cc27f2fee053ef58032e204e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325060"
---
# <a name="commandline-class"></a>Klasa CommandLine

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `CommandLine` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie COMMAND_LINE.](../event-table.md#command-line)

## <a name="syntax"></a>Składnia

```cpp
class CommandLine : public SimpleEvent
{
public:
    CommandLine(const RawEvent& event);

    const wchar_t* Value() const;
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych członków z jego [SimpleEvent](simple-event.md) klasy podstawowej, `CommandLine` klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[Commandline](#command-line)

### <a name="functions"></a>Funkcje

[Wartość](#value)

## <a name="commandline"></a><a name="command-line"></a>Commandline

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Wydarzenie [COMMAND_LINE.](../event-table.md#command-line)

## <a name="value"></a><a name="value"></a>Wartość

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg zawierający wiersz polecenia. Wartość zawiera argumenty, które zostały uzyskane z pliku odpowiedzi i \_\_ze zmiennych \_\_środowiskowych, takich jak CL, CL , Link i LINK .

::: moniker-end
