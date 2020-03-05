---
title: Struktura INVOCATION_DATA
description: Zestaw C++ SDK usługi Build insights INVOCATION_DATA odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b2e8ddcf79201d8bcbbb8eb298b96b5c7680f90e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333693"
---
# <a name="invocation_data-structure"></a>Struktura INVOCATION_DATA

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

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
| `MSVCToolCode` | Kod, który identyfikuje typ wywołania. Aby uzyskać więcej informacji, zobacz [MSVC_TOOL_CODE](msvc-tool-code-enum.md). |
| `ToolVersion` | Obiekt, w którym jest przechowywana wywołana wersja narzędzia jako Grupa wartości całkowitych. |
| `ToolVersionString` | Opisuje wersję wywoływanego narzędzia w postaci tekstowej. |
| `WorkingDirectory` | Katalog, z którego wykonano wywołanie. |
| `ToolPath` | Ścieżka bezwzględna narzędzia wywoływanego. |

::: moniker-end
