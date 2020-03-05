---
title: Struktura INVOCATION_VERSION_DATA
description: Zestaw C++ SDK usługi Build insights INVOCATION_VERSION_DATA odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 040b0f90b14133ec2b25f7a12d35b88d382c4f7a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333679"
---
# <a name="invocation_version_data-structure"></a>Struktura INVOCATION_VERSION_DATA

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

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
| `VersionMajor` | Numer główny wersji. |
| `VersionMinor` | Numer pomocniczy wersji. |
| `BuildNumberMajor` | Numer główny kompilacji. |
| `BuildNumberMinor` | Numer pomocniczy kompilacji. |

::: moniker-end
