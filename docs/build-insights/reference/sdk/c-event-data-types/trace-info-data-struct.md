---
title: Struktura TRACE_INFO_DATA
description: Informacje o strukturze TRACE_INFO_DATA zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 38683ff2c5c5165b5fe2a1969ccf80fbfca3693f
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040460"
---
# <a name="trace_info_data-structure"></a>Struktura TRACE_INFO_DATA

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`TRACE_INFO_DATA`Struktura opisuje przeanalizowane lub ponownie zarejestrowane ślady.

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

| Nazwa | Opis |
|--|--|
| `LogicalProcessorCount` | Liczba procesorów logicznych na komputerze, na którym zebrano dane śledzenia. |
| `TickFrequency` | Liczba taktów na sekundę do użycia podczas oceniania czasu trwania mierzoną w taktach. |
| `StartTimestamp` | To pole jest ustawione na wartość takt przechwyconą w momencie rozpoczęcia śledzenia. |
| `StopTimestamp` | To pole jest ustawione na wartość takt przechwyconą w momencie zatrzymania śledzenia. |

## <a name="remarks"></a>Uwagi

Odejmij `StartTimestamp` od `StopTimestamp` , aby uzyskać liczbę taktów, które upłynęły podczas całego śledzenia. Służy `TickFrequency` do konwertowania wartości wyniku na jednostkę czasu. Aby zapoznać się z przykładem, który konwertuje Takty na jednostki czasu, zobacz [EVENT_DATA](event-data-struct.md).

::: moniker-end
