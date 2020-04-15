---
title: StartTracingSessionA
description: Odwołanie do funkcji SDK StartTracingSessiona w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1c184e214c7f55bb7eaa6eb03f21e792ef90fa40
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323762"
---
# <a name="starttracingsessiona"></a>StartTracingSessionA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `StartTracingSessionA` rozpoczyna sesję śledzenia. Pliki wykonywalne wywołujące tę funkcję muszą mieć uprawnienia administratora.

## <a name="syntax"></a>Składnia

```cpp
enum RESULT_CODE StartTracingSessionA(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>Parametry

*Nazwa_sesji*\
Nazwa sesji śledzenia, aby rozpocząć. Użyj tej samej nazwy podczas wywoływania [StopTracingSessionA](stop-tracing-session.md) lub innej funkcji śledzenia zatrzymania.

*Opcje*\
Wskaźnik do [obiektu TRACING_SESSION_OPTIONS.](../other-types/tracing-session-options-struct.md) Ten obiekt służy do wybierania zdarzeń, które mają być zbierane przez sesję śledzenia.

### <a name="return-value"></a>Wartość zwracana

Kod wyniku z [RESULT_CODE](../other-types/result-code-enum.md) wyliczenia.

::: moniker-end
