---
title: Struktura CL_PASS_DATA
description: Zestaw C++ SDK usługi Build insights CL_PASS_DATA odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3df5b5bc1cddbadc4a4d432ae021dd8b338c532e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333826"
---
# <a name="cl_pass_data-structure"></a>Struktura CL_PASS_DATA

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `CL_PASS_DATA` zawiera opis przebiegu kompilacji.

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
| `TranslationUnitPassCode` | Kod identyfikujący przebieg kompilacji. Aby uzyskać więcej informacji, zobacz [TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md). |
| `InputSourcePath` | Plik C lub C++ źródłowy, w którym jest wykonywane wykonywanie kompilacji. |
| `OutputObjectPath` | Plik obiektu tworzony przez kompilator. |

::: moniker-end
