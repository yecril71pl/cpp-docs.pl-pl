---
title: struktura TRACE_INFO_DATA
description: C++ Build Insights SDK TRACE_INFO_DATA odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 70ae17a376f79cad7a669d81e482f551afd0ec62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325276"
---
# <a name="trace_info_data-structure"></a>struktura TRACE_INFO_DATA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `TRACE_INFO_DATA` opisuje śledzenia analizowane lub ponownie rejestrowane.

## <a name="syntax"></a>Składnia

```cpp
typedef struct TRACE_INFO_DATA_TAG
{
    unsigned long           LogicalProcessorCount;
    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;

} TRACE_INFO_DATA;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `LogicalProcessorCount` | Liczba procesorów logicznych na komputerze, na którym zebrano ślad. |
| `TickFrequency` | Liczba znaczników na sekundę do użycia podczas oceny czasu trwania mierzonego w kleszczach. |
| `StartTimestamp` | To pole jest ustawione na wartość znacznika przechwyconą w momencie rozpoczęcia śledzenia. |
| `StopTimestamp` | To pole jest ustawione na wartość znacznika przechwyconą w momencie zatrzymania śledzenia. |

## <a name="remarks"></a>Uwagi

`StartTimestamp` Odejmij `StopTimestamp` od uzyskania liczby kleszczy, które upłynęło podczas całego śladu. Służy `TickFrequency` do konwertowania wartości wynikowej na jednostkę czasu. Na przykład, który konwertuje znaczniki na jednostki czasu, zobacz [EVENT_DATA](event-data-struct.md).

::: moniker-end
