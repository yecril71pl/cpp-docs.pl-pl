---
title: Struktura EVENT_COLLECTION_DATA
description: C++ Build Insights SDK EVENT_COLLECTION_DATA odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 88ba39ede8c86f47c2e6458332ae005eddc06fda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325689"
---
# <a name="event_collection_data-structure"></a>Struktura EVENT_COLLECTION_DATA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `EVENT_COLLECTION_DATA` opisuje tablicę [EVENT_DATA](event-data-struct.md) elementów.

## <a name="syntax"></a>Składnia

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `Count` | Liczba `EVENT_DATA` elementów w tablicy. |
| `Elements` | Wskaźnik do `EVENT_DATA` pierwszego elementu w tablicy. |

::: moniker-end
