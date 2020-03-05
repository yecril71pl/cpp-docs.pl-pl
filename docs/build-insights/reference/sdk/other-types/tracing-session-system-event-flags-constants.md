---
title: Stałe TRACING_SESSION_SYSTEM_EVENT_FLAGS
description: Zestaw C++ SDK usługi Build insights TRACING_SESSION_SYSTEM_EVENT_FLAGS informacje stałe.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ce0b0ea373ec53f0d5bcf228269299d69b49bb95
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332356"
---
# <a name="tracing_session_system_event_flags-constants"></a>Stałe TRACING_SESSION_SYSTEM_EVENT_FLAGS

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Stałe `TRACING_SESSION_SYSTEM_EVENT_FLAGS` są używane do opisywania, które zdarzenia systemowe mają być zbierane podczas śledzenia. Użyj ich, aby zainicjować pole `SystemEventFlags` struktury [TRACING_SESSION_OPTIONS](tracing-session-options-struct.md) .

## <a name="syntax"></a>Składnia

```cpp
static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT      = 0x1ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES  = 0x2ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL          = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Elementy członkowskie

| Nazwa | Zdarzenia włączone przez tę flagę |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | Ta flaga jest uaktywniana domyślnie przez zestaw C++ SDK usługi Build Insights, nawet jeśli nie została określona jawnie. Umożliwia ona podstawowe zdarzenia systemowe, które są wymagane C++ przez funkcję tworzenia szczegółowych informacji w celu poprawnego działania. Zdarzenia włączone przez tę flagę zawierają informacje dotyczące procesów, wątków i ładowania obrazu. Nie można wyłączyć tych zdarzeń. |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Przykłady użycia procesora CPU |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | Ta flaga włącza wszystkie zdarzenia systemowe. |

::: moniker-end
