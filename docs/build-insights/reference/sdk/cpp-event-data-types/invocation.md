---
title: Klasa wywołania
description: Odwołanie do klasy wywołania SDK invocation aplikacji C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fcb087d46ea445251b0108f811545a44c26f421e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324644"
---
# <a name="invocation-class"></a>Klasa wywołania

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `Invocation` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie kompilatora](../event-table.md#compiler) lub [konsolidatora.](../event-table.md#linker)

## <a name="syntax"></a>Składnia

```cpp
class Invocation : public Activity
{
    const INVOCATION_DATA* data_;

public:
    enum class Type
    {
        CL      = MSVC_TOOL_CODE_CL,
        LINK    = MSVC_TOOL_CODE_LINK
    };

    Invocation(const RawEvent& event);

    Type             Type() const;
    const char*      ToolVersionString() const;
    const wchar_t*   WorkingDirectory() const;
    const wchar_t*   ToolPath() const;

    const INVOCATION_VERSION_DATA& ToolVersion() const;
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych elementów członkowskich z `Invocation` jego [działania](activity.md) klasy podstawowej, klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[Wywołania](#invocation)

### <a name="functions"></a>Funkcje

[ToolPath](#tool-path)
[ToolVersion](#tool-version)
[ToolVersionString](#tool-version-string)
Typ[WorkingDirectory](#working-directory) [Type](#type)


## <a name="invocation"></a><a name="invocation"></a>Wywołania

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Zdarzenie [kompilatora](../event-table.md#compiler) lub [konsolidatora.](../event-table.md#linker)

## <a name="toolpath"></a><a name="tool-path"></a>Toolpath

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>Wartość zwracana

Bezwzględna ścieżka do narzędzia, które zostało wywołane.

## <a name="toolversion"></a><a name="tool-version"></a>ToolVersion (Wersja narzędzia)

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>Wartość zwracana

Wersja narzędzia, który został wywołany, jako odwołanie [INVOCATION_VERSION_DATA.](../c-event-data-types/invocation-version-data-struct.md)

## <a name="toolversionstring"></a><a name="tool-version-string"></a>ToolVersionString (NarzędzieSciąg

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>Wartość zwracana

Wersja narzędzia, które zostało wywołane, jako ciąg ANSI.

## <a name="type"></a><a name="type"></a>Typu

```cpp
Type Type() const;
```

### <a name="return-value"></a>Wartość zwracana

Kod wskazujący narzędzie, które zostało wywołane.

## <a name="workingdirectory"></a><a name="working-directory"></a>Workingdirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>Wartość zwracana

Bezwzględna ścieżka do katalogu, w którym narzędzie zostało wywołane.

::: moniker-end
