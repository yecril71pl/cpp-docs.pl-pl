---
title: Struktura RELOG_DESCRIPTOR
description: C++ Build Insights SDK RELOG_DESCRIPTOR odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c3aee49fe9f609ca37082693ddcfd5e838cc96a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328939"
---
# <a name="relog_descriptor-structure"></a>Struktura RELOG_DESCRIPTOR

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `RELOG_DESCRIPTOR` jest używana z [relogA](../functions/relog-a.md) i [RelogW](../functions/relog-w.md) funkcji. Opisano w nim, jak śledzenie zdarzeń dla systemu Windows (ETW) śledzenia powinny być ponownie rejestrowane.

## <a name="syntax"></a>Składnia

```cpp
typedef struct RELOG_DESCRIPTOR_TAG
{
    unsigned                NumberOfAnalysisPasses;
    ANALYSIS_CALLBACKS      AnalysisCallbacks;
    RELOG_CALLBACKS         RelogCallbacks;
    unsigned long long      SystemEventsRetentionFlags;
    void*                   AnalysisContext;
    void*                   RelogContext;
} RELOG_DESCRIPTOR;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `NumberOfAnalysisPasses` | Liczba przebiegów analizy, które powinny być wykonywane za połów ETW podczas fazy analizy sesji ponownego rejestrowania. |
| `AnalysisCallbacks` | [Obiekt ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) określający, które funkcje do wywołania podczas fazy analizy sesji ponownego rejestrowania. |
| `RelogCallbacks` | Obiekt [RELOG_CALLBACKS,](relog-callbacks-struct.md) który określa, które funkcje do wywołania podczas fazy ponownego rejestrowania sesji ponownego rejestrowania. |
| `SystemEventsRetentionFlags` | Maska bitowa [RELOG_RETENTION_SYSTEM_EVENT_FLAGS,](relog-retention-system-event-flags-constants.md) która określa, które zdarzenia ETW systemu należy przechowywać w ponownie zarejestrowanym śladu. |
| `AnalysisContext` | Kontekst dostarczony przez użytkownika, który jest przekazywany jako argument do wszystkich funkcji wywołania zwrotnego określonych w`AnalysisCallbacks` |
| `RelogContext` | Kontekst dostarczony przez użytkownika, który jest przekazywany jako argument do wszystkich funkcji wywołania zwrotnego określonych w`RelogCallbacks` |

## <a name="remarks"></a>Uwagi

Ponowne rejestrowanie zdarzeń ETW podczas sesji ponownego rejestrowania jest kontrolowane przez `RelogCallbacks`użytkownika za pomocą funkcji wywołania zwrotnego określonych w programie . Jednak zdarzenia ETW systemu, takie jak próbki procesora CPU nie są przekazywane do tych funkcji wywołania zwrotnego. Użyj `SystemEventsRetentionFlags` tego pola, aby kontrolować ponowne rejestrowanie zdarzeń ETW systemu.

I `AnalysisCallbacks` `RelogCallbacks` struktury akceptują tylko wskaźniki do funkcji innych niż elementy członkowskie. Można obejść to ograniczenie, ustawiając je na wskaźnik obiektu. Ten wskaźnik obiektu zostanie przekazany jako argument do wszystkich funkcji wywołania zwrotnego niebędących członkami. Ten wskaźnik służy do wywoływania funkcji członkowskich z funkcji wywołania zwrotnego niebędących członkami.

Faza analizy sesji ponownego rejestrowania jest zawsze wykonywana przed fazą ponownego rejestrowania.

::: moniker-end
