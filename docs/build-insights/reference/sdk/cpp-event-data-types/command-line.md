---
title: CommandLine — Klasa
description: Odwołanie C++ do klasy wiersza polecenia zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff16646920fe77f7f3b4cb8a194a38984c3e6c32
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333511"
---
# <a name="commandline-class"></a>CommandLine — Klasa

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `CommandLine` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Użyj go, aby dopasować zdarzenie [COMMAND_LINE](../event-table.md#command-line) .

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

Wraz z dziedziczonymi elementami członkowskimi z klasy bazowej [SimpleEvent](simple-event.md) , Klasa `CommandLine` zawiera następujących członków:

### <a name="constructors"></a>Konstruktorów

[Wiersza polecenia](#command-line)

### <a name="functions"></a>Funkcje

[Wartość](#value)

## <a name="command-line"></a>Wiersza polecenia

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *zdarzeń*
Zdarzenie [COMMAND_LINE](../event-table.md#command-line) .

## <a name="value"></a>Wartościami

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg zawierający wiersz polecenia. Wartość zawiera argumenty, które zostały uzyskane z pliku odpowiedzi i ze zmiennych środowiskowych, takich jak CL, \_CL\_, link i \_łącza\_.

::: moniker-end
