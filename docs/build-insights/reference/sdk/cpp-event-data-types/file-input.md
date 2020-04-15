---
title: Klasa FileInput
description: Odwołanie do klasy SDK FileInput aplikacji SDK programu C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileInput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 642236d3e67465ed38508cb24c8cd698ae880065
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324798"
---
# <a name="fileinput-class"></a>Klasa FileInput

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `FileInput` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie FILE_INPUT.](../event-table.md#file-input)

## <a name="syntax"></a>Składnia

```cpp
class FileInput : public SimpleEvent
{
public:
    enum class Type
    {
        OTHER               = FILE_TYPE_CODE_OTHER,
        OBJ                 = FILE_TYPE_CODE_OBJ,
        EXECUTABLE_IMAGE    = FILE_TYPE_CODE_EXECUTABLE_IMAGE,
        LIB                 = FILE_TYPE_CODE_LIB,
        IMP_LIB             = FILE_TYPE_CODE_IMP_LIB,
        EXP                 = FILE_TYPE_CODE_EXP
    };

    FileInput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych członków z jego [SimpleEvent](simple-event.md) klasy podstawowej, `FileInput` klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[FileInput (Plucie pliku)](#file-input)

### <a name="functions"></a>Funkcje

[Path](#path)
[Typ](#type) ścieżki

## <a name="fileinput"></a><a name="file-input"></a>FileInput (Plucie pliku)

```cpp
FileInput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Wydarzenie [FILE_INPUT.](../event-table.md#file-input)

## <a name="path"></a><a name="path"></a>Ścieżka

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Wartość zwracana

Bezwzględna ścieżka do pliku wejściowego.

## <a name="type"></a><a name="type"></a>Typu

```cpp
Type Type() const;
```

### <a name="return-value"></a>Wartość zwracana

Kod opisujący typ pliku wejściowego.

::: moniker-end
