---
title: CALLBACK_CODE Wyliczenie
description: Zestaw C++ SDK usługi Build insights CALLBACK_CODE Wyliczenie.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 68eaa9aa04d2f0a55ac12fb7dde14a080188a38d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332468"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE Wyliczenie

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Wyliczenie `CALLBACK_CODE` służy do sterowania przepływem analizy lub sesji ponownego rejestrowania. Zwróć CALLBACK_CODE wartość z funkcji w [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) lub [RELOG_CALLBACKS](relog-callbacks-struct.md) , aby kontrolować, co należy zrobić dalej.

## <a name="members"></a>Elementy członkowskie

| Nazwa | Wartość | Opis |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | Kontynuuj bieżącą analizę lub rejestrowanie w normalnym sesji. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | Anuluj bieżącą analizę lub przerejestrowanie sesji i sygnalizuj błąd. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | Anuluj bieżącą analizę lub przerejestrowanie. |

::: moniker-end
