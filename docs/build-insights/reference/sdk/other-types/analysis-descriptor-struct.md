---
title: struktura ANALYSIS_DESCRIPTOR
description: C++ Build Insights SDK ANALYSIS_DESCRIPTOR odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1de7f2a5bc3f02a327daaecf8c2cebc44687ba43
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323614"
---
# <a name="analysis_descriptor-structure"></a>struktura ANALYSIS_DESCRIPTOR

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `ANALYSIS_DESCRIPTOR` jest używana z [funkcjami AnalyzeA](../functions/analyze-a.md) i [AnalyzeW.](../functions/analyze-w.md) Opisano w nim, jak śledzenia zdarzeń dla systemu Windows (ETW) śledzenia powinny być analizowane.

## <a name="syntax"></a>Składnia

```cpp
typedef struct ANALYSIS_DESCRIPTOR_TAG
{
    unsigned                NumberOfPasses;
    ANALYSIS_CALLBACKS      Callbacks;
    void*                   Context;
} ANALYSIS_DESCRIPTOR;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `NumberOfPasses` | Liczba przebiegów analizy, które powinny być wykonane za połów ETW. |
| `Callbacks` | [Obiekt ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) określający, które funkcje należy wywołać podczas sesji analizy. |
| `Context` | Kontekst dostarczony przez użytkownika, który jest przekazywany jako argument do wszystkich funkcji wywołania zwrotnego określonych w`Callbacks` |

## <a name="remarks"></a>Uwagi

Struktura `Callbacks` akceptuje tylko wskaźniki do funkcji innych niż elementy członkowskie. Można obejść to ograniczenie, ustawiając `Context` wskaźnik obiektu. Ten wskaźnik obiektu zostanie przekazany jako argument do wszystkich funkcji wywołania zwrotnego niebędących członkami. Ten wskaźnik służy do wywoływania funkcji członkowskich z funkcji wywołania zwrotnego niebędących członkami.

::: moniker-end
