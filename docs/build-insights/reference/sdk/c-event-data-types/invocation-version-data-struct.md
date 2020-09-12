---
title: Struktura INVOCATION_VERSION_DATA
description: Informacje o strukturze INVOCATION_VERSION_DATA zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ec54c560dd408dc3beecbc20eaac69d389c7ec37
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041562"
---
# <a name="invocation_version_data-structure"></a>Struktura INVOCATION_VERSION_DATA

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`INVOCATION_VERSION_DATA`Struktura opisuje numer wersji jako grupę wartości całkowitych.

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

| Nazwa | Opis |
|--|--|
| `VersionMajor` | Numer główny wersji. |
| `VersionMinor` | Numer pomocniczy wersji. |
| `BuildNumberMajor` | Numer główny kompilacji. |
| `BuildNumberMinor` | Numer pomocniczy kompilacji. |

::: moniker-end
