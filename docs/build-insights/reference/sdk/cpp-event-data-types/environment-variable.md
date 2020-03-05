---
title: Klasa zmiennych środowiskowych
description: Odwołanie C++ do klasy zmiennych środowiskowych zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 19e9278e76fb2116dac30a0e790fba86c6c56484
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333441"
---
# <a name="environmentvariable-class"></a>Klasa zmiennych środowiskowych

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `EnvironmentVariable` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Użyj go, aby dopasować zdarzenie [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) .

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

Wraz z dziedziczonymi elementami członkowskimi z klasy bazowej [SimpleEvent](simple-event.md) , Klasa `EnvironmentVariable` zawiera następujących członków:

### <a name="constructors"></a>Konstruktorów

[Zmiennych środowiskowych](#environment-variable)

### <a name="functions"></a>Funkcje

[Nazwa](#name)
[wartość](#value)

## <a name="environment-variable"></a>Zmiennych środowiskowych

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *zdarzeń*
Zdarzenie [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) .

## <a name="name"></a>Nazwij

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa zmiennej środowiskowej.

## <a name="value"></a>Wartościami

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość zmiennej środowiskowej.

::: moniker-end
