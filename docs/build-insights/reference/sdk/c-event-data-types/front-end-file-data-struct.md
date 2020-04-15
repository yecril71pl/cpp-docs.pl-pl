---
title: Struktura FRONT_END_FILE_DATA
description: C++ Build Insights SDK FRONT_END_FILE_DATA odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FRONT_END_FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7fb6b6fff4f309a3539a290f279d1e31cb1ed76b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325548"
---
# <a name="front_end_file_data-structure"></a>Struktura FRONT_END_FILE_DATA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `FRONT_END_FILE_DATA` opisuje przetwarzanie pliku przez przód kompilatora.

## <a name="syntax"></a>Składnia

```cpp
typedef struct FRONT_END_FILE_DATA_TAG
{
    const char*         Path;

} FRONT_END_FILE_DATA;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `Path` | Ścieżka bezwzględna pliku, zakodowana w UTF-8. |

::: moniker-end
