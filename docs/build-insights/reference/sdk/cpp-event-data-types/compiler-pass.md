---
title: Klasa CompilerPass
description: Odwołanie do klasy CompilerPass zestawu SDK kompilacji C++ build.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 054bdf75dcfca42b8c202565fb44df671f17f912
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831622"
---
# <a name="compilerpass-class"></a>Klasa CompilerPass

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`CompilerPass`Klasa jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Użyj go, aby dopasować [BACK_END_PASS](../event-table.md#back-end-pass) lub [FRONT_END_PASS](../event-table.md#front-end-pass) zdarzenia.

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

Wraz z dziedziczonymi elementami członkowskimi z klasy podstawowej [działania](activity.md) `CompilerPass` Klasa zawiera następujących członków:

### <a name="constructors"></a>Konstruktory

[CompilerPass](#compiler-pass)

### <a name="enums"></a>Wyliczenia

#### <a name="passcode"></a>Kodem

|Wartość|Opis|
|-|-|
|FRONT_END|Fronton.|
|BACK_END|Przebieg zaplecza.|

### <a name="functions"></a>Functions

[InputSourcePath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
[Kodem](#pass-code)\

## <a name="compilerpass"></a><a name="compiler-pass"></a> CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*wydarzen*\
Zdarzenie [BACK_END_PASS](../event-table.md#back-end-pass) lub [FRONT_END_PASS](../event-table.md#front-end-pass) .

## <a name="inputsourcepath"></a><a name="input-source-path"></a> InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>Wartość zwracana

Ścieżka bezwzględna do wejściowego pliku źródłowego przetworzonego przez ten przebieg kompilatora.

## <a name="outputobjectpath"></a><a name="output-object-path"></a> OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Wartość zwracana

Ścieżka bezwzględna do pliku obiektu wyjściowego utworzonego przez ten kompilator.

## <a name="passcode"></a><a name="pass-code"></a> Kodem

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Wartość zwracana

Kod wskazujący, który przebieg kompilatora jest reprezentowany przez ten obiekt CompilerPass.

::: moniker-end
