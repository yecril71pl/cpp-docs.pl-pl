---
title: CALLBACK_CODE wyliczenia
description: C++ Build Insights SDK CALLBACK_CODE odwołanie wyliczenia.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0d3dcc70040f562cd40755188e545f709a807b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329189"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE wyliczenia

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Wyliczenia `CALLBACK_CODE` jest używany kontrolować przepływ analizy lub sesji ponownego rejestrowania. Zwraca wartość CALLBACK_CODE z funkcji w [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) lub [RELOG_CALLBACKS,](relog-callbacks-struct.md) aby kontrolować, co powinno się zdarzyć dalej.

## <a name="members"></a>Elementy członkowskie

| Nazwa | Wartość | Opis |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | Kontynuować bieżącą sesję analizy lub ponownego rejestrowania normalnie. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | Anuluj bieżącą analizę lub ponowne rejestrowanie sesji i sygnalizuj błąd. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | Anuluj bieżącą sesję analizy lub ponownego rejestrowania. |

::: moniker-end
