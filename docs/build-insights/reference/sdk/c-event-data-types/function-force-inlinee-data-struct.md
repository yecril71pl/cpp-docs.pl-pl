---
title: Struktura FUNCTION_FORCE_INLINEE_DATA
description: C++ Build Insights SDK FUNCTION_FORCE_INLINEE_DATA odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_FORCE_INLINEE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a4781c9157130cb46e92906017af98710f5637b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325491"
---
# <a name="function_force_inlinee_data-structure"></a>Struktura FUNCTION_FORCE_INLINEE_DATA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `FUNCTION_FORCE_INLINEE_DATA` opisuje funkcję inlined siły.

## <a name="syntax"></a>Składnia

```cpp
typedef struct FUNCTION_FORCE_INLINEE_DATA_TAG
{
    const char*         Name;
    unsigned short      Size;

} FUNCTION_FORCE_INLINEE_DATA;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `Name` | Nazwa funkcji, zakodowana w UTF-8. |
| `Size` | Rozmiar funkcji, jako liczba instrukcji pośrednich. |

::: moniker-end
