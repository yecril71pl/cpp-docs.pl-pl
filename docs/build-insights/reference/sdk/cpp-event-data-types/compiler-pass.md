---
title: Klasa CompilerPass
description: Odwołanie C++ do klasy CompilerPass zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c2fa1c2c4be8aaf5bec77b383f93a4b033ca8e3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333476"
---
# <a name="compilerpass-class"></a>Klasa CompilerPass

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `CompilerPass` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Użyj go, aby dopasować [BACK_END_PASS](../event-table.md#back-end-pass) lub [FRONT_END_PASS](../event-table.md#front-end-pass) zdarzenia.

## <a name="syntax"></a>Składnia

```cpp
class CompilerPass : public Activity
{
public:
    enum class PassCode
    {
        FRONT_END,
        BACK_END
    };

    CompilerPass(const RawEvent& event);

    PassCode       PassCode() const;
    const wchar_t* InputSourcePath() const;
    const wchar_t* OutputObjectPath() const;
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z dziedziczonymi elementami członkowskimi z klasy podstawowej [działania](activity.md) Klasa `CompilerPass` zawiera następujących członków:

### <a name="constructors"></a>Konstruktorów

[CompilerPass](#compiler-pass)

### <a name="enums"></a>Wyliczenia

#### <a name="passcode"></a>Kodem

|||
|-|-|
|FRONT_END|Fronton.|
|BACK_END|Przebieg zaplecza.|

### <a name="functions"></a>Funkcje

[InputSourcePath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
[Kod dostępu](#pass-code)\

## <a name="compiler-pass"></a>CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *zdarzeń*
Zdarzenie [BACK_END_PASS](../event-table.md#back-end-pass) lub [FRONT_END_PASS](../event-table.md#front-end-pass) .

## <a name="input-source-path"></a>InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>Wartość zwracana

Ścieżka bezwzględna do wejściowego pliku źródłowego przetworzonego przez ten przebieg kompilatora.

## <a name="output-object-path"></a>OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Wartość zwracana

Ścieżka bezwzględna do pliku obiektu wyjściowego utworzonego przez ten kompilator.

## <a name="pass-code"></a>Kodem

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Wartość zwracana

Kod wskazujący, który przebieg kompilatora jest reprezentowany przez ten obiekt CompilerPass.

::: moniker-end
