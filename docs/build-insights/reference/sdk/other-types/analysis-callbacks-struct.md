---
title: Struktura ANALYSIS_CALLBACKS
description: C++ Build Insights SDK ANALYSIS_CALLBACKS odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c6de999b19657f999f884075ee53e21a4d2f2b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323505"
---
# <a name="analysis_callbacks-structure"></a>Struktura ANALYSIS_CALLBACKS

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `ANALYSIS_CALLBACKS` jest używana podczas inicjowania [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) lub [RELOG_DESCRIPTOR](relog-descriptor-struct.md) obiektu. Określa, które funkcje do wywołania podczas analizy lub ponownego rejestrowania śledzenia zdarzeń dla systemu Windows (ETW) śledzenia.

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

|  |  |
|--|--|
| `OnStartActivity` | Wywoływana do przetwarzania zdarzenia rozpoczęcia działania. |
| `OnStopActivity` | Wywoływana do przetwarzania zdarzenia zatrzymania działania. |
| `OnSimpleEvent` | Wywoływana do przetwarzania prostego zdarzenia. |
| `OnTraceInfo` | Dla sesji analizy, wywoływane na początku każdego przebiegu analizy. Do rejestrowania sesji, wywoływane na początku każdej analizy przebiegu i ponownie na początku przebiegu ponownego rejestrowania. Ta funkcja jest wywoływana tylko po wywołaniu OnBeginAnalysisPass. |
| `OnBeginAnalysis` | W przypadku sesji analizy, wywoływanych przed rozpoczęciem jakiegokolwiek przebiegu analizy. W przypadku sesji ponownego rejestrowania, wywoływanych dwa razy przed rozpoczęciem fazy analizy: raz ogłosić rozpoczęcie sesji ponownego rejestrowania i jeszcze raz ogłosić początek fazy analizy. |
| `OnEndAnalysis` | W przypadku sesji analizy ta funkcja jest wywoływana po zakończeniu wszystkich przebiegów analizy. W przypadku sesji ponownego rejestrowania ta funkcja jest wywoływana po zakończeniu wszystkich przebiegów analizy fazy analizy. Następnie jest wywoływana ponownie po zakończeniu przełęczy ponownego rejestrowania. |
| `OnBeginAnalysisPass` | Wywoływane podczas rozpoczynania przebiegu analizy lub przepięciem, przed przetworzeniem dowolnego zdarzenia. |
| `OnEndAnalysisPass` | Wywoływane podczas kończenia przebiegu analizy lub przepięciem, po przetworzeniu wszystkich zdarzeń. |

## <a name="remarks"></a>Uwagi

Faza analizy sesji ponownego rejestrowania jest uważana za część sesji ponownego rejestrowania i może zawierać wiele przebiegów analizy. Z tego `OnBeginAnalysis` powodu jest wywoływana dwa razy z rzędu na początku sesji ponownego rejestrowania. `OnEndAnalysis`jest wywoływana na końcu fazy analizy, przed rozpoczęciem fazy ponownego rejestrowania i ponownie na końcu fazy ponownego rejestrowania. Faza ponownego rejestrowania zawsze zawiera pojedynczy przebieg ponownego rejestrowania.

Jest możliwe dla analizatorów być częścią fazy analizy i ponownego rejestrowania sesji ponownego rejestrowania. Analizatory te można określić, która faza jest obecnie w toku, śledząc OnBeginanalysis i `OnEndAnalysis` pary wywołań. Dwa `OnBeginAnalysis` wywołania `OnEndAnalysis` bez połączenia oznacza, że trwa faza analizy. Dwa `OnBeginAnalysis` wywołania `OnEndAnalysis` i jedno wywołanie oznacza, że trwa faza ponownego rejestrowania. Dwa OnBeginAnalysis `OnEndAnalysis` i dwa połączenia oznacza, że obie fazy zostały zakończone.

Wszystkie elementy `ANALYSIS_CALLBACKS` członkowskie struktury muszą wskazywać prawidłową funkcję. Aby uzyskać więcej informacji na temat przyjętych podpisów funkcji, zobacz [OnAnalysisEventFunc](on-analysis-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)i [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
