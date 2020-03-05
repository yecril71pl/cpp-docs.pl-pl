---
title: Struktura FRONT_END_FILE_DATA
description: Zestaw C++ SDK usługi Build insights FRONT_END_FILE_DATA odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FRONT_END_FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 33232a0f83566e58e64964e84961a7ade2de7b7c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333742"
---
# <a name="front_end_file_data-structure"></a>Struktura FRONT_END_FILE_DATA

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `FRONT_END_FILE_DATA` opisuje przetwarzanie pliku przez fronton kompilatora.

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
| `Path` | Ścieżka bezwzględna pliku zakodowana w formacie UTF-8. |

::: moniker-end
