---
title: Klasa wyliczeniowa AnalysisControl
description: Odwołanie do wyliczenia zestawu SDK usługi Build Insights AnalysisControl.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a7b7fc0ce404f414b3ec07449bdc110d578fa101
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042020"
---
# <a name="analysiscontrol-enum-class"></a>Klasa wyliczeniowa AnalysisControl

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`AnalysisControl`Klasa enum służy do sterowania przepływem analizy lub sesji ponownego rejestrowania. Zwróć `AnalysisControl` kod z funkcji składowej [IAnalyzer](ianalyzer-class.md) lub [IRelogger](irelogger-class.md) , aby kontrolować, co powinno się stać dalej.

## <a name="members"></a>Elementy członkowskie

| Nazwa | Opis |
|--|--|
| `BLOCK` | Zapobiega dalszemu propagowaniu bieżącego zdarzenia w analizatorze lub grupie rejestratora. |
| `CANCEL` | Anuluj bieżącą analizę lub przerejestrowanie. |
| `CONTINUE` | Kontynuuj bieżącą analizę lub rejestrowanie w normalnym sesji. Propaguj bieżące zdarzenie do następnego elementu członkowskiego analizatora lub grupy ponownego rejestrowania. |
| `FAILURE` | Anuluj bieżącą analizę lub przerejestrowanie sesji i sygnalizuj błąd. |

::: moniker-end
