---
title: Struktura INVOCATION_VERSION_DATA
description: C++ Build Insights SDK INVOCATION_VERSION_DATA odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1211b4eb999fd63767af71c6884d7d20d6920df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325468"
---
# <a name="invocation_version_data-structure"></a>Struktura INVOCATION_VERSION_DATA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `INVOCATION_VERSION_DATA` opisuje numer wersji jako grupę wartości całkowitych.

## <a name="syntax"></a>Składnia

```cpp
typedef struct INVOCATION_VERSION_DATA_TAG
{
    unsigned short VersionMajor;
    unsigned short VersionMinor;
    unsigned short BuildNumberMajor;
    unsigned short BuildNumberMinor;

} INVOCATION_VERSION_DATA;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `VersionMajor` | Główny numer wersji. |
| `VersionMinor` | Numer pomocniczy wersji. |
| `BuildNumberMajor` | Główna liczba kompilacji. |
| `BuildNumberMinor` | Numer pomocniczy kompilacji. |

::: moniker-end
