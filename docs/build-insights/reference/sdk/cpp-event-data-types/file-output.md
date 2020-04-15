---
title: Klasa FileOutput
description: Odwołanie do klasy SDK FileOutput w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 37823da8a4aaac0ce4094583b8aee8ac1eb04aaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324804"
---
# <a name="fileoutput-class"></a>Klasa FileOutput

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `FileOutput` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie EXECUTABLE_IMAGE_OUTPUT,](../event-table.md#executable-image-output) [EXP_OUTPUT,](../event-table.md#exp-output) [IMP_LIB_OUTPUT,](../event-table.md#imp-lib-output) [LIB_OUTPUT](../event-table.md#lib-output)lub [OBJ_OUTPUT.](../event-table.md#obj-output)

## <a name="syntax"></a>Składnia

```cpp
class FileOutput : public SimpleEvent
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

    FileOutput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych członków z jego [SimpleEvent](simple-event.md) klasy podstawowej, `FileOutput` klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[FileOutput (FileOutput)](#file-output)

### <a name="functions"></a>Funkcje

[Path](#path)
[Typ](#type) ścieżki

## <a name="fileoutput"></a><a name="file-output"></a>FileOutput (FileOutput)

```cpp
FileOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
[Wydarzenie EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT,](../event-table.md#exp-output) [IMP_LIB_OUTPUT,](../event-table.md#imp-lib-output) [LIB_OUTPUT](../event-table.md#lib-output)lub [OBJ_OUTPUT.](../event-table.md#obj-output)

## <a name="path"></a><a name="path"></a>Ścieżka

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Wartość zwracana

Bezwzględna ścieżka do pliku wyjściowego.

## <a name="type"></a><a name="type"></a>Typu

```cpp
Type Type() const;
```

### <a name="return-value"></a>Wartość zwracana

Kod opisujący typ pliku wyjściowego.

::: moniker-end
