---
title: Struktura CL_PASS_DATA
description: Informacje o strukturze CL_PASS_DATA zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 52ee5fdaae12784c2f59d2c47ac9a2fd80649f27
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040538"
---
# <a name="cl_pass_data-structure"></a>Struktura CL_PASS_DATA

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`CL_PASS_DATA`Struktura zawiera opis przebiegu kompilacji.

## <a name="syntax"></a>Składnia

```cpp
typedef struct CL_PASS_DATA_TAG
{
    int                         TranslationUnitPassCode;
    const wchar_t*              InputSourcePath;
    const wchar_t*              OutputObjectPath;

} CL_PASS_DATA;
```

## <a name="members"></a>Elementy członkowskie

| Nazwa | Opis |
|--|--|
| `TranslationUnitPassCode` | Kod identyfikujący przebieg kompilacji. Aby uzyskać więcej informacji, zobacz [TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md). |
| `InputSourcePath` | Plik źródłowy C lub C++, w którym jest wykonywane wykonywanie kompilacji. |
| `OutputObjectPath` | Plik obiektu tworzony przez kompilator. |

::: moniker-end
