---
title: Struktura ANALYSIS_DESCRIPTOR
description: Zestaw C++ SDK usługi Build insights ANALYSIS_DESCRIPTOR odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fc11ce11e1faaae02edb36aac447c18ea8107e35
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332482"
---
# <a name="analysis_descriptor-structure"></a>Struktura ANALYSIS_DESCRIPTOR

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `ANALYSIS_DESCRIPTOR` jest używana z funkcjami [Analizuj](../functions/analyze-a.md) i [AnalyzeW](../functions/analyze-w.md) . Opisano w nim, jak należy analizować śledzenie zdarzeń systemu Windows (ETW).

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
| `NumberOfPasses` | Liczba przebiegów analizy, które powinny być wykonywane przez śledzenie ETW. |
| `Callbacks` | Obiekt [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) , który określa funkcje, które mają być wywoływane podczas sesji analizy. |
| `Context` | Kontekst udostępniony przez użytkownika, który jest przekazywany jako argument do wszystkich funkcji wywołania zwrotnego określonych w `Callbacks` |

## <a name="remarks"></a>Uwagi

Struktura `Callbacks` akceptuje tylko wskaźniki do funkcji nienależących do elementu członkowskiego. Aby obejść to ograniczenie, należy ustawić `Context` na wskaźnik obiektu. Wskaźnik tego obiektu zostanie przekazaną jako argument do wszystkich funkcji wywołania zwrotnego, które nie są elementami członkowskimi. Ten wskaźnik służy do wywoływania funkcji Członkowskich z poziomu funkcji wywołania zwrotnego, które nie są elementami członkowskimi.

::: moniker-end
