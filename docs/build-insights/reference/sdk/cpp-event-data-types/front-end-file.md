---
title: Klasa FrontEndFile
description: Odwołanie C++ do klasy FrontEndFile zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFile
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 094b1326765e0e8edb00534ecb3d94c46702d4ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333287"
---
# <a name="frontendfile-class"></a>Klasa FrontEndFile

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `FrontEndFile` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Użyj go, aby dopasować zdarzenie [FRONT_END_FILE](../event-table.md#front-end-file) .

## <a name="syntax"></a>Składnia

```cpp
class FrontEndFile : public Activity
{
public:
    FrontEndFile(const RawEvent& event);

    const char* Path() const;
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z dziedziczonymi elementami członkowskimi z klasy podstawowej [działania](activity.md) Klasa `FrontEndFile` zawiera następujących członków:

### <a name="constructors"></a>Konstruktorów

[FrontEndFile](#front-end-file)

### <a name="functions"></a>Funkcje

[Ścieżka](#path)

## <a name="front-end-file"></a>FrontEndFile

```cpp
FrontEndFile(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *zdarzeń*
Zdarzenie [FRONT_END_FILE](../event-table.md#front-end-file) .

## <a name="path"></a>Ścieżka

```cpp
const char* Path() const;
```

### <a name="return-value"></a>Wartość zwracana

Ścieżka bezwzględna do pliku zakodowana w formacie UTF-8.

::: moniker-end
