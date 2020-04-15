---
title: Struktura TRACING_SESSION_OPTIONS
description: C++ Build Insights SDK TRACING_SESSION_OPTIONS odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5aeb6299aea8dc0661b9469ee524e7aa4d010aca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323425"
---
# <a name="tracing_session_options-structure"></a>Struktura TRACING_SESSION_OPTIONS

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `TRACING_SESSION_OPTIONS` jest używana podczas inicjowania [struktury ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) lub [RELOG_DESCRIPTOR.](relog-descriptor-struct.md) Opisano w nim zdarzenia do przechwycenia podczas kolekcji śledzenia.

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
| `SystemEventFlags` | Maska bitowa opisująca zdarzenia systemowe do przechwycenia. Aby uzyskać więcej informacji, zobacz [TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md). |
| `MsvcEventFlags` | Maska bitowa opisująca zdarzenia MSVC do przechwycenia. Aby uzyskać więcej informacji, zobacz [TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md). |

::: moniker-end
