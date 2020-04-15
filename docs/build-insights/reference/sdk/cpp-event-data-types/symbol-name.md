---
title: Klasa SymbolName
description: Odwołanie do klasy SDK SymbolName aplikacji C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1306fb43d6c2140a75b36c5f142532916cf26ae4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324355"
---
# <a name="symbolname-class"></a>Klasa SymbolName

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `SymbolName` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie SYMBOL_NAME.](../event-table.md#symbol-name)

## <a name="syntax"></a>Składnia

```cpp
class SymbolName : public SimpleEvent
{
public:
    SymbolName(const RawEvent& event);

    const unsigned long long&  Key() const;
    const char*                Name() const;
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych członków z jego [SimpleEvent](simple-event.md) klasy podstawowej, `SymbolName` klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[Nazwa symbolu](#symbol-name)

### <a name="functions"></a>Funkcje

[Key](#key)
[Nazwa klucza](#name)

## <a name="key"></a><a name="key"></a>Klucz

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator numeryczny dla typu reprezentowanego przez ten symbol. Ten identyfikator jest unikatowy w ramach przebiegu front-end kompilatora.

## <a name="name"></a><a name="name"></a>Nazwa

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa typu reprezentowanego przez symbol, zakodowana w UTF-8.

## <a name="symbolname"></a><a name="symbol-name"></a>Nazwa symbolu

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Zdarzenie [SYMBOL_NAME.](../event-table.md#symbol-name)

::: moniker-end
