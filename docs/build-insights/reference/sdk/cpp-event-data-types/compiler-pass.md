---
title: KompilatorPass, klasa
description: Odwołanie do klasy SDK CompilerPass kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 11af981b647d5183f88dad024d90c0ef4f8a28bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325043"
---
# <a name="compilerpass-class"></a>KompilatorPass, klasa

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `CompilerPass` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie BACK_END_PASS](../event-table.md#back-end-pass) lub [FRONT_END_PASS.](../event-table.md#front-end-pass)

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

Wraz z odziedziczonych elementów członkowskich z `CompilerPass` jego [działania](activity.md) klasy podstawowej, klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[KompilatorPrzechajnik](#compiler-pass)

### <a name="enums"></a>Wyliczenia

#### <a name="passcode"></a>Kod

|||
|-|-|
|FRONT_END|Przełęcz front-end.|
|BACK_END|Back-end pass.|

### <a name="functions"></a>Funkcje

[Ścieżka źródła danych wejścia](#input-source-path)\
[Ścieżka ktorawy](#output-object-path)\
[Kod](#pass-code)\

## <a name="compilerpass"></a><a name="compiler-pass"></a>KompilatorPrzechajnik

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Zdarzenie [BACK_END_PASS](../event-table.md#back-end-pass) lub [FRONT_END_PASS.](../event-table.md#front-end-pass)

## <a name="inputsourcepath"></a><a name="input-source-path"></a>Ścieżka źródła danych wejścia

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>Wartość zwracana

Ścieżka bezwzględna do pliku źródłowego danych wejściowych przetwarzane przez ten przebieg kompilatora.

## <a name="outputobjectpath"></a><a name="output-object-path"></a>Ścieżka ktorawy

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Wartość zwracana

Ścieżka bezwzględna do pliku obiektu wyjściowego produkowanego przez ten przebieg kompilatora.

## <a name="passcode"></a><a name="pass-code"></a>Kod

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Wartość zwracana

Kod wskazujący, który przebieg kompilatora jest reprezentowany przez ten obiekt CompilerPass.

::: moniker-end
