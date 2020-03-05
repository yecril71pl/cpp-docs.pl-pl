---
title: Symbolname — Klasa
description: Odwołanie C++ do klasy symbol zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b5e9a9b22db99c099b9f7dc1813fb335358a83e8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333000"
---
# <a name="symbolname-class"></a>Symbolname — Klasa

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `SymbolName` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Użyj go, aby dopasować zdarzenie [SYMBOL_NAME](../event-table.md#symbol-name) .

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

Wraz z dziedziczonymi elementami członkowskimi z klasy bazowej [SimpleEvent](simple-event.md) , Klasa `SymbolName` zawiera następujących członków:

### <a name="constructors"></a>Konstruktorów

[Symbolname](#symbol-name)

### <a name="functions"></a>Funkcje

[Nazwa](#name)
[klucza](#key)

## <a name="key"></a>Głównych

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator liczbowy typu reprezentowanego przez ten symbol. Ten identyfikator jest unikatowy w ramach przebiegu frontonu kompilatora.

## <a name="name"></a>Nazwij

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa typu reprezentowanego przez symbol zakodowana w UTF-8.

## <a name="symbol-name"></a>Symbolname

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *zdarzeń*
Zdarzenie [SYMBOL_NAME](../event-table.md#symbol-name) .

::: moniker-end
