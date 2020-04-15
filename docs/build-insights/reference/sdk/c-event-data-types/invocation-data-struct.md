---
title: Struktura INVOCATION_DATA
description: C++ Build Insights SDK INVOCATION_DATA odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4e1f428facac413d7a4a5c059452dd8cdb07be4c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325487"
---
# <a name="invocation_data-structure"></a>Struktura INVOCATION_DATA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `INVOCATION_DATA` opisuje wywołanie kompilatora lub konsolidatora.

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

|  |  |
|--|--|
| `MSVCToolCode` | Kod identyfikujący typ wywołania. Aby uzyskać więcej informacji, zobacz [MSVC_TOOL_CODE](msvc-tool-code-enum.md). |
| `ToolVersion` | Obiekt, który przechowuje wersję wywoływanego narzędzia jako grupę wartości całkowitych. |
| `ToolVersionString` | Opisuje wersję wywoływane narzędzie w postaci tekstowej. |
| `WorkingDirectory` | Katalog, z którego zostało wykonane wywołanie. |
| `ToolPath` | Ścieżka bezwzględna wywoływane narzędzie. |

::: moniker-end
