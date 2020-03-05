---
title: Struktura EVENT_COLLECTION_DATA
description: Zestaw C++ SDK usługi Build insights EVENT_COLLECTION_DATA odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1a622a8459b6aa6d9dcbe0faaf90ae545b449466
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333812"
---
# <a name="event_collection_data-structure"></a>Struktura EVENT_COLLECTION_DATA

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `EVENT_COLLECTION_DATA` opisuje tablicę elementów [EVENT_DATA](event-data-struct.md) .

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
| `Elements` | Wskaźnik do pierwszego elementu `EVENT_DATA` w tablicy. |

::: moniker-end
