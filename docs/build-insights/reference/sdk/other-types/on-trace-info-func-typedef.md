---
title: OnTraceInfoFunc typedef
description: Odwołanie do funkcji SDK ontraceinfoFunc typedef w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b987d4db9852c2e52c148bb91015ad414c04d41b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329018"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc typedef

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Typedef `OnTraceInfoFunc` jest jednym z podpisów funkcji używanych w [strukturach ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) i [RELOG_CALLBACKS.](relog-callbacks-struct.md)

## <a name="syntax"></a>Składnia

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parametry

*Traceinfo*\
Obiekt [TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md) zawierający informacje o aktualnie analizowanym lub ponownym zarejestrowaniu śledzenia.

*callbackContext*\
Wartość kontekstu ustawiona dla tego wywołania zwrotnego w [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) lub [RELOG_DESCRIPTOR](relog-descriptor-struct.md).

### <a name="return-value"></a>Wartość zwracana

Wartość [CALLBACK_CODE,](callback-code-enum.md) która kontroluje, co powinno się wydarzyć dalej.

::: moniker-end
