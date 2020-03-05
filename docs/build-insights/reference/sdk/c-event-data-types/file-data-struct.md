---
title: Struktura FILE_DATA
description: Zestaw C++ SDK usługi Build insights FILE_DATA odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72cae8c8eb81bdb8d94897c46c5af90c89e92ab4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333756"
---
# <a name="file_data-structure"></a>Struktura FILE_DATA

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `FILE_DATA` opisuje dane wejściowe lub wyjściowe.

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
