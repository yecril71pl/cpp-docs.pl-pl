---
title: Struktura ANALYSIS_CALLBACKS
description: Informacje o strukturze ANALYSIS_CALLBACKS zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a24755befdd446051ae376b49d3dca06c7bc3320
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041045"
---
# <a name="analysis_callbacks-structure"></a>Struktura ANALYSIS_CALLBACKS

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`ANALYSIS_CALLBACKS`Struktura jest używana podczas inicjowania obiektu [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) lub [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Określa funkcje, które mają być wywoływane podczas analizy lub rejestrowania śledzenia zdarzeń systemu Windows (ETW).

## <a name="syntax"></a>Składnia

```cpp
typedef struct ANALYSIS_CALLBACKS_TAG
{
    OnAnalysisEventFunc     OnStartActivity;
    OnAnalysisEventFunc     OnStopActivity;
    OnAnalysisEventFunc     OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginAnalysis;
    OnBeginEndPassFunc      OnEndAnalysis;
    OnBeginEndPassFunc      OnBeginAnalysisPass;
    OnBeginEndPassFunc      OnEndAnalysisPass;
} ANALYSIS_CALLBACKS;
```

## <a name="members"></a>Elementy członkowskie

| Nazwa | Opis |
|--|--|
| `OnStartActivity` | Wywołuje się, by przetworzyć zdarzenie uruchomienia działania. |
| `OnStopActivity` | Wywołuje się, by przetworzyć zdarzenie zatrzymania działania. |
| `OnSimpleEvent` | Wywołuje się, by przetworzyć zdarzenie proste. |
| `OnTraceInfo` | W przypadku sesji analizy wywoływana na początku każdego przebiegu analizy. W przypadku sesji ponownego rejestrowania, wywoływana na początku każdego przebiegu analizy i ponownie na początku przebiegu ponownej rejestracji. Ta funkcja jest wywoływana tylko po wywołaniu OnBeginAnalysisPass. |
| `OnBeginAnalysis` | Dla sesji analizy wywoływana przed rozpoczęciem dowolnego przebiegu analizy. W przypadku sesji ponownego rejestrowania wywołano dwa razy przed rozpoczęciem fazy analizy: raz, aby ogłosić początek sesji ponownego rejestrowania, a jeszcze więcej ogłaszać początek fazy analizy. |
| `OnEndAnalysis` | W przypadku sesji analizy ta funkcja jest wywoływana po zakończeniu wszystkich przebiegów analizy. W przypadku sesji rerejestrowania ta funkcja jest wywoływana po zakończeniu wszystkich przebiegów analizy fazy analizy. Następnie zostanie on wywołany ponownie po zakończeniu przebiegu ponownego rejestrowania. |
| `OnBeginAnalysisPass` | Wywoływana przy rozpoczynaniu przebiegu analizy lub przebiegu rejestrowania przed przetworzeniem dowolnego zdarzenia. |
| `OnEndAnalysisPass` | Wywoływana podczas kończenia przebiegu analizy lub przebiegu rejestrowania po przetworzeniu wszystkich zdarzeń. |

## <a name="remarks"></a>Uwagi

Faza analizy sesji rejestrowania jest uważana za część sesji rejestrowania i może zawierać wiele przebiegów analizy. Z tego powodu `OnBeginAnalysis` występuje dwa razy w wierszu na początku sesji rejestrowania. `OnEndAnalysis` jest wywoływana na końcu fazy analizy przed rozpoczęciem fazy ponownego rejestrowania, a raz na końcu fazy ponownego rejestrowania. Faza rerejestrowania zawsze zawiera pojedyncze przebiegu rejestrowania.

Możliwe jest, że analizatory będą częścią zarówno analizy, jak i w fazie rejestrowania w sesji rejestrowania. Analizatory te mogą ustalić, która faza aktualnie trwa, śledząc OnBeginAnalysis i `OnEndAnalysis` pary wywołań. Dwa `OnBeginAnalysis` wywołania bez `OnEndAnalysis` wywołania to trwa faza analizy. Dwa `OnBeginAnalysis` wywołania i jedno `OnEndAnalysis` wywołanie oznacza, że faza rejestrowania jest w toku. Dwie OnBeginAnalysis i dwa `OnEndAnalysis` wywołania oznaczają, że obie fazy zakończyły się.

Wszystkie elementy członkowskie `ANALYSIS_CALLBACKS` struktury muszą wskazywać na prawidłową funkcję. Aby uzyskać więcej informacji na temat zaakceptowanych podpisów funkcji, zobacz [OnAnalysisEventFunc](on-analysis-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)i [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
