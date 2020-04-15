---
title: Klasa EnvironmentVariable
description: Odwołanie do klasy SDK Środowiska SDK kompilacji języka C++.The C++ Build Insights SDK EnvironmentVariable class reference.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 963c52e0ea9e048448c6f2b3ac62d9938817467e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325015"
---
# <a name="environmentvariable-class"></a>Klasa EnvironmentVariable

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `EnvironmentVariable` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie ENVIRONMENT_VARIABLE.](../event-table.md#environment-variable)

## <a name="syntax"></a>Składnia

```cpp
class EnvironmentVariable : public SimpleEvent
{
public:
    EnvironmentVariable(const RawEvent& event);

    const wchar_t* Name() const;
    const wchar_t* Value() const;
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych członków z jego [SimpleEvent](simple-event.md) klasy podstawowej, `EnvironmentVariable` klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[ŚrodowiskoWaralne](#environment-variable)

### <a name="functions"></a>Funkcje

[Wartość nazwy](#name)
[Value](#value)

## <a name="environmentvariable"></a><a name="environment-variable"></a>ŚrodowiskoWaralne

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Wydarzenie [ENVIRONMENT_VARIABLE.](../event-table.md#environment-variable)

## <a name="name"></a><a name="name"></a>Nazwa

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa zmiennej środowiskowej.

## <a name="value"></a><a name="value"></a>Wartość

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość zmiennej środowiskowej.

::: moniker-end
