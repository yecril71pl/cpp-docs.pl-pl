---
title: Struktura FUNCTION_DATA
description: Informacje o strukturze FUNCTION_DATA zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1034ce01bba6422d0c47fc34b308cafcc113e32b
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041747"
---
# <a name="function_data-structure"></a>Struktura FUNCTION_DATA

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`FUNCTION_DATA`Struktura opisuje funkcję.

## <a name="syntax"></a>Składnia

```cpp
typedef struct FUNCTION_DATA_TAG
{
    const char*         Name;

} FUNCTION_DATA;
```

## <a name="members"></a>Elementy członkowskie

| Nazwa | Opis |
|--|--|
| `Name` | Nazwa funkcji zakodowana w formacie UTF-8. |

::: moniker-end
