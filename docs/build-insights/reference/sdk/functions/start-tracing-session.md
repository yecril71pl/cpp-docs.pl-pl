---
title: StartTracingSession (StartTracingSession)
description: Odwołanie do funkcji starttracingsession aplikacji kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6da81ce54948e5ddbacfc9af50f1be12736fdba7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323738"
---
# <a name="starttracingsession"></a>StartTracingSession (StartTracingSession)

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `StartTracingSession` rozpoczyna sesję śledzenia. Pliki wykonywalne wywołujące tę funkcję muszą mieć uprawnienia administratora.

## <a name="syntax"></a>Składnia

```cpp
RESULT_CODE StartTracingSession(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS& options);

RESULT_CODE StartTracingSession(
    const wchar_t*                 sessionName,
    const TRACING_SESSION_OPTIONS& options);
```

### <a name="parameters"></a>Parametry

*Nazwa_sesji*\
Nazwa sesji śledzenia, aby rozpocząć. Użyj tej samej nazwy podczas wywoływania [StopTracingSession](stop-tracing-session.md) lub innej funkcji śledzenia zatrzymania.

*Opcje*\
Wskaźnik do [obiektu TRACING_SESSION_OPTIONS.](../other-types/tracing-session-options-struct.md) Ten obiekt służy do wybierania zdarzeń, które mają być zbierane przez sesję śledzenia.

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z [RESULT_CODE](../other-types/result-code-enum.md) wyliczenia.

::: moniker-end
