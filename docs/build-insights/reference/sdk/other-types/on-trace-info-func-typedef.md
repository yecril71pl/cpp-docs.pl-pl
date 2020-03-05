---
title: OnTraceInfoFunc typedef
description: Odwołanie C++ do zestawu SDK usługi Build Insights OnTraceInfoFunc.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b168d6783b31454f6a2837bcad1fc81199ce9054
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332349"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc typedef

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

`OnTraceInfoFunc` typedef jest jednym z podpisów funkcji używanych w strukturach [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) i [RELOG_CALLBACKS](relog-callbacks-struct.md) .

## <a name="syntax"></a>Składnia

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parametry

*traceInfo*\
Obiekt [TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md) , który zawiera informacje o aktualnie analizowanym lub zarejestrowanym śledzeniu.

*callbackContext*\
Wartość kontekstu ustawiona dla tego wywołania zwrotnego w [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) lub [RELOG_DESCRIPTOR](relog-descriptor-struct.md).

### <a name="return-value"></a>Wartość zwracana

Wartość [CALLBACK_CODE](callback-code-enum.md) , która kontroluje, co powinno się stać dalej.

::: moniker-end
