---
title: OnRelogEventFunc typedef
description: Odwołanie do funkcji SDK onRelogEventFunc typedef w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2df8646d530c089b1239978d716b2b619a5b4b61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329069"
---
# <a name="onrelogeventfunc-typedef"></a>OnRelogEventFunc typedef

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Typedef `OnRelogEventFunc` jest jednym z podpisów funkcji używanych w [strukturze RELOG_CALLBACKS.](relog-callbacks-struct.md)

## <a name="syntax"></a>Składnia

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnRelogEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    const void*                     relogSession,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parametry

*eventStack (własówce wydarzenia)*\
Stos zdarzeń dla bieżącego zdarzenia. Aby uzyskać więcej informacji na temat stosów zdarzeń, zobacz [Zdarzenia](../event-table.md).

*relogSesja*\
Wskaźnik sesji ponownego rejestrowania do użycia podczas wywoływania [injectevent](../functions/inject-event.md).

*callbackContext*\
Wartość kontekstu ustawiona dla tego wywołania zwrotnego w [RELOG_DESCRIPTOR](analysis-descriptor-struct.md).

### <a name="return-value"></a>Wartość zwracana

Wartość [CALLBACK_CODE,](callback-code-enum.md) która kontroluje, co powinno się wydarzyć dalej.

::: moniker-end
