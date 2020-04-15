---
title: Struktura FILE_DATA
description: C++ Build Insights SDK FILE_DATA odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6b7b0129c54fa4b1d5285bafb38761da45bab4e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325590"
---
# <a name="file_data-structure"></a>Struktura FILE_DATA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `FILE_DATA` opisuje dane wejściowe lub wyjściowe pliku.

## <a name="syntax"></a>Składnia

```cpp
typedef struct FILE_DATA_TAG
{
    const wchar_t*      Path;
    int                 TypeCode;

} FILE_DATA;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `Path` | Ścieżka bezwzględna pliku |
| `TypeCode` | Kod opisujący typ pliku. Aby uzyskać więcej informacji, zobacz [FILE_TYPE_CODE](file-type-code-enum.md). |

::: moniker-end
