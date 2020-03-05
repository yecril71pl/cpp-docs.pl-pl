---
title: Klasa wyliczeniowa AnalysisControl
description: AnalysisControl C++ zestawienia SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: cf162c11e0a7109b8d733dab79df80782398e14d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332503"
---
# <a name="analysiscontrol-enum-class"></a>Klasa wyliczeniowa AnalysisControl

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa wyliczeniowa `AnalysisControl` służy do sterowania przepływem analizy lub sesji ponownego rejestrowania. Zwróć kod `AnalysisControl` z funkcji składowej [IAnalyzer](ianalyzer-class.md) lub [IRelogger](irelogger-class.md) , aby kontrolować, co należy zrobić dalej.

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `BLOCK` | Zapobiega dalszemu propagowaniu bieżącego zdarzenia w analizatorze lub grupie rejestratora. |
| `CANCEL` | Anuluj bieżącą analizę lub przerejestrowanie. |
| `CONTINUE` | Kontynuuj bieżącą analizę lub rejestrowanie w normalnym sesji. Propaguj bieżące zdarzenie do następnego elementu członkowskiego analizatora lub grupy ponownego rejestrowania. |
| `FAILURE` | Anuluj bieżącą analizę lub przerejestrowanie sesji i sygnalizuj błąd. |

::: moniker-end
