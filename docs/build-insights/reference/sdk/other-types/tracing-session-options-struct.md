---
title: Struktura TRACING_SESSION_OPTIONS
description: Zestaw C++ SDK usługi Build insights TRACING_SESSION_OPTIONS odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3f02552d5df4ffe71bc4be5c46e4b5239f25d73c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332209"
---
# <a name="tracing_session_options-structure"></a>Struktura TRACING_SESSION_OPTIONS

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `TRACING_SESSION_OPTIONS` jest używana podczas inicjowania struktury [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) lub [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Opisuje zdarzenia, które mają być przechwytywane podczas zbierania śladu.

## <a name="syntax"></a>Składnia

```cpp
typedef struct TRACING_SESSION_OPTIONS_TAG
{
    unsigned long long SystemEventFlags;
    unsigned long long MsvcEventFlags;

} TRACING_SESSION_OPTIONS;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `SystemEventFlags` | Maska bitów opisująca zdarzenia systemowe do przechwycenia. Aby uzyskać więcej informacji, zobacz [TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md). |
| `MsvcEventFlags` | Maska bitów opisująca zdarzenia MSVC do przechwycenia. Aby uzyskać więcej informacji, zobacz [TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md). |

::: moniker-end
