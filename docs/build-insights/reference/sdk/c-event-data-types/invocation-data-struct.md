---
title: Struktura INVOCATION_DATA
description: Informacje o strukturze INVOCATION_DATA zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 48b4c28d3c01d61a31343894312a54ba2ab17a70
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041643"
---
# <a name="invocation_data-structure"></a>Struktura INVOCATION_DATA

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`INVOCATION_DATA`Struktura opisuje wywołanie kompilatora lub konsolidatora.

## <a name="syntax"></a>Składnia

```cpp
typedef struct INVOCATION_DATA_TAG
{
    int                         MSVCToolCode;

    INVOCATION_VERSION_DATA     ToolVersion;

    const char*                 ToolVersionString;
    const wchar_t*              WorkingDirectory;
    const wchar_t*              ToolPath;

} INVOCATION_DATA;
```

## <a name="members"></a>Elementy członkowskie

| Nazwa | Opis |
|--|--|
| `MSVCToolCode` | Kod, który identyfikuje typ wywołania. Aby uzyskać więcej informacji, zobacz [MSVC_TOOL_CODE](msvc-tool-code-enum.md). |
| `ToolVersion` | Obiekt, w którym jest przechowywana wywołana wersja narzędzia jako Grupa wartości całkowitych. |
| `ToolVersionString` | Opisuje wersję wywoływanego narzędzia w postaci tekstowej. |
| `WorkingDirectory` | Katalog, z którego wykonano wywołanie. |
| `ToolPath` | Ścieżka bezwzględna narzędzia wywoływanego. |

::: moniker-end
