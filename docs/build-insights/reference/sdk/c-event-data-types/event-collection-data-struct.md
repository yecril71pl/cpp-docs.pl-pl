---
title: Struktura EVENT_COLLECTION_DATA
description: Informacje o strukturze EVENT_COLLECTION_DATA zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 58be46d31af154bfe7ecef5c440092eaafdcbb0f
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039602"
---
# <a name="event_collection_data-structure"></a>Struktura EVENT_COLLECTION_DATA

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`EVENT_COLLECTION_DATA`Struktura opisuje tablicę elementów [EVENT_DATA](event-data-struct.md) .

## <a name="syntax"></a>Składnia

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>Elementy członkowskie

| Nazwa | Opis |
|--|--|
| `Count` | Liczba `EVENT_DATA` elementów w tablicy. |
| `Elements` | Wskaźnik do pierwszego `EVENT_DATA` elementu w tablicy. |

::: moniker-end
