---
title: Struktura CL_PASS_DATA
description: C++ Build Insights SDK CL_PASS_DATA odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b0a41e59068ade285f1ffa1a9ce13734ef5f1f32
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325708"
---
# <a name="cl_pass_data-structure"></a>Struktura CL_PASS_DATA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `CL_PASS_DATA` opisuje przebieg kompilacji.

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

|  |  |
|--|--|
| `TranslationUnitPassCode` | Kod identyfikujący przebieg kompilacji jest wykonywany. Aby uzyskać więcej informacji, zobacz [TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md). |
| `InputSourcePath` | Plik źródłowy Języka C lub C++, na którym jest wykonywany ten przebieg kompilacji. |
| `OutputObjectPath` | Plik obiektu jest produkowany przez kompilator. |

::: moniker-end
