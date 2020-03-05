---
title: Struktura FUNCTION_FORCE_INLINEE_DATA
description: Zestaw C++ SDK usługi Build insights FUNCTION_FORCE_INLINEE_DATA odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_FORCE_INLINEE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3d6929f2f16e9b1bd79b7fb8b383b40e031268bf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333700"
---
# <a name="function_force_inlinee_data-structure"></a>Struktura FUNCTION_FORCE_INLINEE_DATA

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `FUNCTION_FORCE_INLINEE_DATA` opisuje funkcję wymuszoną.

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
| `Name` | Nazwa funkcji zakodowana w formacie UTF-8. |
| `Size` | Rozmiar funkcji, jako szereg instrukcji pośrednich. |

::: moniker-end
