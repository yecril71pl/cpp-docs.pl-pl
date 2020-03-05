---
title: Struktura ANALYSIS_CALLBACKS
description: Zestaw C++ SDK usługi Build insights ANALYSIS_CALLBACKS odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8c35e740d97488969a6b69467d54412297e49227
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332531"
---
# <a name="analysis_callbacks-structure"></a>Struktura ANALYSIS_CALLBACKS

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `ANALYSIS_CALLBACKS` jest używana podczas inicjowania obiektu [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) lub [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Określa funkcje, które mają być wywoływane podczas analizy lub rejestrowania śledzenia zdarzeń systemu Windows (ETW).

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
| `OnStartActivity` | Wywołuje się, by przetworzyć zdarzenie uruchomienia działania. |
| `OnStopActivity` | Wywołuje się, by przetworzyć zdarzenie zatrzymania działania. |
| `OnSimpleEvent` | Wywołuje się, by przetworzyć zdarzenie proste. |
| `OnTraceInfo` | W przypadku sesji analizy wywoływana na początku każdego przebiegu analizy. W przypadku sesji ponownego rejestrowania, wywoływana na początku każdego przebiegu analizy i ponownie na początku przebiegu ponownej rejestracji. Ta funkcja jest wywoływana tylko po wywołaniu OnBeginAnalysisPass. |
| `OnBeginAnalysis` | Dla sesji analizy wywoływana przed rozpoczęciem dowolnego przebiegu analizy. W przypadku sesji ponownego rejestrowania wywołano dwa razy przed rozpoczęciem fazy analizy: raz, aby ogłosić początek sesji ponownego rejestrowania, a jeszcze więcej ogłaszać początek fazy analizy. |
| `OnEndAnalysis` | W przypadku sesji analizy ta funkcja jest wywoływana po zakończeniu wszystkich przebiegów analizy. W przypadku sesji rerejestrowania ta funkcja jest wywoływana po zakończeniu wszystkich przebiegów analizy fazy analizy. Następnie zostanie on wywołany ponownie po zakończeniu przebiegu ponownego rejestrowania. |
| `OnBeginAnalysisPass` | Wywoływana przy rozpoczynaniu przebiegu analizy lub przebiegu rejestrowania przed przetworzeniem dowolnego zdarzenia. |
| `OnEndAnalysisPass` | Wywoływana podczas kończenia przebiegu analizy lub przebiegu rejestrowania po przetworzeniu wszystkich zdarzeń. |

## <a name="remarks"></a>Uwagi

Faza analizy sesji rejestrowania jest uważana za część sesji rejestrowania i może zawierać wiele przebiegów analizy. Z tego powodu `OnBeginAnalysis` jest wywoływana dwa razy w wierszu na początku sesji rejestrowania. `OnEndAnalysis` jest wywoływana na końcu fazy analizy przed rozpoczęciem fazy ponownego rejestrowania, a raz na końcu fazy ponownego rejestrowania. Faza rerejestrowania zawsze zawiera pojedyncze przebiegu rejestrowania.

Możliwe jest, że analizatory będą częścią zarówno analizy, jak i w fazie rejestrowania w sesji rejestrowania. Analizatory te mogą ustalić, która faza jest obecnie wykonywana przez śledzenie par wywołań OnBeginAnalysis i `OnEndAnalysis`. Dwa wywołania `OnBeginAnalysis` bez żadnego wywołania `OnEndAnalysis` to trwa faza analizy. Dwa wywołania `OnBeginAnalysis` i jedno wywołanie `OnEndAnalysis`e oznacza, że etap rejestrowania jest ciągły. Dwa OnBeginAnalysis i dwa wywołania `OnEndAnalysis` oznacza, że obie fazy zakończyły się.

Wszystkie elementy członkowskie struktury `ANALYSIS_CALLBACKS` muszą wskazywać na prawidłową funkcję. Aby uzyskać więcej informacji na temat zaakceptowanych podpisów funkcji, zobacz [OnAnalysisEventFunc](on-analysis-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)i [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
