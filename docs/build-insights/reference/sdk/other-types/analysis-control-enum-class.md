---
title: Klasa wyliczenia AnalysisControl
description: Odwołanie do wyliczenia Wyliczenia SDK AnalysisControl w ramach kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e9431f878390127f2cefbe8f0ee42ca509e147de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323643"
---
# <a name="analysiscontrol-enum-class"></a>Klasa wyliczenia AnalysisControl

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `AnalysisControl` wyliczenia jest używana kontrolować przepływ analizy lub sesji ponownego rejestrowania. Zwraca `AnalysisControl` kod z funkcji elementu członkowskiego [IAnalyzer](ianalyzer-class.md) lub [IRelogger,](irelogger-class.md) aby kontrolować, co powinno się zdarzyć dalej.

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `BLOCK` | Zapobiega dalszego propagowania bieżącego zdarzenia w grupie analizatora lub reloggera. |
| `CANCEL` | Anuluj bieżącą sesję analizy lub ponownego rejestrowania. |
| `CONTINUE` | Kontynuować bieżącą sesję analizy lub ponownego rejestrowania normalnie. Propagacji bieżącego zdarzenia do następnego analizatora lub relogger członka grupy. |
| `FAILURE` | Anuluj bieżącą analizę lub ponowne rejestrowanie sesji i sygnalizuj błąd. |

::: moniker-end
