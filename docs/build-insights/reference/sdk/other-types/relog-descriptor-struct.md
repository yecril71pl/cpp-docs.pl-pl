---
title: Struktura RELOG_DESCRIPTOR
description: Informacje o strukturze RELOG_DESCRIPTOR zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 802e51ec4246f5ee95e3d204290743ffbd03be69
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041396"
---
# <a name="relog_descriptor-structure"></a>Struktura RELOG_DESCRIPTOR

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`RELOG_DESCRIPTOR`Struktura jest używana z funkcjami [RelogA](../functions/relog-a.md) i [RelogW](../functions/relog-w.md) . Opisano w nim, jak należy rejestrować śledzenie zdarzeń dla systemu Windows (ETW).

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

| Nazwa | Opis |
|--|--|
| `NumberOfAnalysisPasses` | Liczba przebiegów analizy, które powinny zostać wykonane przez śledzenie ETW w fazie analizy sesji rejestrowania. |
| `AnalysisCallbacks` | Obiekt [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) , który określa funkcje, które mają być wywoływane podczas fazy analizy sesji rejestrowania. |
| `RelogCallbacks` | Obiekt [RELOG_CALLBACKS](relog-callbacks-struct.md) , który określa funkcje, które mają być wywoływane w fazie rejestrowania sesji rejestrowania. |
| `SystemEventsRetentionFlags` | [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md) maski bitowej, która określa, które systemowe zdarzenia ETW zachować w rejestrowanym śladzie. |
| `AnalysisContext` | Kontekst udostępniony przez użytkownika, który jest przekazywany jako argument do wszystkich funkcji wywołania zwrotnego określonych w `AnalysisCallbacks` |
| `RelogContext` | Kontekst udostępniony przez użytkownika, który jest przekazywany jako argument do wszystkich funkcji wywołania zwrotnego określonych w `RelogCallbacks` |

## <a name="remarks"></a>Uwagi

Rejestrowanie zdarzeń ETW w trakcie sesji rejestrowania jest kontrolowane przez użytkownika przez funkcje wywołania zwrotnego określone w `RelogCallbacks` . Jednak zdarzenia ETW systemu, takie jak przykłady procesora, nie są przekazywane do tych funkcji wywołania zwrotnego. Użyj `SystemEventsRetentionFlags` pola, aby sterować rejestracją zdarzeń ETW systemu.

`AnalysisCallbacks`Struktury i `RelogCallbacks` akceptują tylko wskaźniki do funkcji nienależących do elementu członkowskiego. Aby obejść to ograniczenie, można ustawić wskaźnik obiektu. Wskaźnik tego obiektu zostanie przekazaną jako argument do wszystkich funkcji wywołania zwrotnego, które nie są elementami członkowskimi. Ten wskaźnik służy do wywoływania funkcji Członkowskich z poziomu funkcji wywołania zwrotnego, które nie są elementami członkowskimi.

Faza analizy sesji rejestrowania jest zawsze wykonywana przed etapem ponownych rejestracji.

::: moniker-end
