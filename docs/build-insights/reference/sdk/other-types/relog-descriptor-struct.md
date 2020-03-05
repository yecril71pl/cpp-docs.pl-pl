---
title: Struktura RELOG_DESCRIPTOR
description: Zestaw C++ SDK usługi Build insights RELOG_DESCRIPTOR odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f6f20835ed6535dd05def629200c113772e8f077
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332328"
---
# <a name="relog_descriptor-structure"></a>Struktura RELOG_DESCRIPTOR

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `RELOG_DESCRIPTOR` jest używana z funkcjami [RelogA](../functions/relog-a.md) i [RelogW](../functions/relog-w.md) . Opisano w nim, jak należy rejestrować śledzenie zdarzeń dla systemu Windows (ETW).

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
| `NumberOfAnalysisPasses` | Liczba przebiegów analizy, które powinny zostać wykonane przez śledzenie ETW w fazie analizy sesji rejestrowania. |
| `AnalysisCallbacks` | Obiekt [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) , który określa funkcje, które mają być wywoływane podczas fazy analizy sesji rejestrowania. |
| `RelogCallbacks` | Obiekt [RELOG_CALLBACKS](relog-callbacks-struct.md) , który określa funkcje, które mają być wywoływane w fazie rejestrowania sesji rejestrowania. |
| `SystemEventsRetentionFlags` | [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md) maski bitowej, która określa, które systemowe zdarzenia ETW zachować w rejestrowanym śladzie. |
| `AnalysisContext` | Kontekst udostępniony przez użytkownika, który jest przekazywany jako argument do wszystkich funkcji wywołania zwrotnego określonych w `AnalysisCallbacks` |
| `RelogContext` | Kontekst udostępniony przez użytkownika, który jest przekazywany jako argument do wszystkich funkcji wywołania zwrotnego określonych w `RelogCallbacks` |

## <a name="remarks"></a>Uwagi

Rejestrowanie zdarzeń ETW w trakcie sesji rejestrowania jest kontrolowane przez użytkownika za pomocą funkcji wywołania zwrotnego określonych w `RelogCallbacks`. Jednak zdarzenia ETW systemu, takie jak przykłady procesora, nie są przekazywane do tych funkcji wywołania zwrotnego. Użyj pola `SystemEventsRetentionFlags`, aby sterować rejestracją zdarzeń ETW systemu.

Struktury `AnalysisCallbacks` i `RelogCallbacks` akceptują tylko wskaźniki do funkcji nienależących do elementu członkowskiego. Aby obejść to ograniczenie, można ustawić wskaźnik obiektu. Wskaźnik tego obiektu zostanie przekazaną jako argument do wszystkich funkcji wywołania zwrotnego, które nie są elementami członkowskimi. Ten wskaźnik służy do wywoływania funkcji Członkowskich z poziomu funkcji wywołania zwrotnego, które nie są elementami członkowskimi.

Faza analizy sesji rejestrowania jest zawsze wykonywana przed etapem ponownych rejestracji.

::: moniker-end
