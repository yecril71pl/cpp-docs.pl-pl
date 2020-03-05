---
title: Struktura TRACE_INFO_DATA
description: Zestaw C++ SDK usługi Build insights TRACE_INFO_DATA odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 04cb5c013bca8879507983d169b38e5af0f1322b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333588"
---
# <a name="trace_info_data-structure"></a>Struktura TRACE_INFO_DATA

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `TRACE_INFO_DATA` opisuje przeanalizowane lub ponownie zarejestrowane ślady.

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
| `LogicalProcessorCount` | Liczba procesorów logicznych na komputerze, na którym zebrano dane śledzenia. |
| `TickFrequency` | Liczba taktów na sekundę do użycia podczas oceniania czasu trwania mierzoną w taktach. |
| `StartTimestamp` | To pole jest ustawione na wartość takt przechwyconą w momencie rozpoczęcia śledzenia. |
| `StopTimestamp` | To pole jest ustawione na wartość takt przechwyconą w momencie zatrzymania śledzenia. |

## <a name="remarks"></a>Uwagi

Odejmij `StartTimestamp` od `StopTimestamp`, aby uzyskać liczbę taktów, które upłynęły podczas całego śledzenia. Użyj `TickFrequency`, aby przekonwertować wartość wyniku na jednostkę czasu. Aby zapoznać się z przykładem, który konwertuje Takty na jednostki czasu, zobacz [EVENT_DATA](event-data-struct.md).

::: moniker-end
