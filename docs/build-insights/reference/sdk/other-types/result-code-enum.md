---
title: RESULT_CODE Wyliczenie
description: Zestaw C++ SDK usługi Build insights RESULT_CODE Wyliczenie.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ee563d148b3456b288bc418255ec46f8cbade7ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332300"
---
# <a name="result_code-enum"></a>RESULT_CODE Wyliczenie

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Wyliczenie `RESULT_CODE` zawiera opis warunków sukcesu i niepowodzenia.

## <a name="members"></a>Elementy członkowskie

| Nazwa | Wartość | Opis |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0 (0x00000000) | Operacja zakończyła się pomyślnie. |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | Jedna z funkcji wywołania zwrotnego w [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) lub [RELOG_DESCRIPTOR](relog-descriptor-struct.md) zwróciła wartość `CALLBACK_CODE_ANALYSIS_FAILURE`. Ta wartość jest elementem członkowskim wyliczenia [CALLBACK_CODE](callback-code-enum.md) . |
| `RESULT_CODE_FAILURE_CANCELLED` | 2 (0x00000002) | Jedna z funkcji wywołania zwrotnego w [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) lub [RELOG_DESCRIPTOR](relog-descriptor-struct.md) zwróciła wartość `CALLBACK_CODE_ANALYSIS_CANCEL`. Ta wartość jest elementem członkowskim wyliczenia [CALLBACK_CODE](callback-code-enum.md) . |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3 (0x00000003) | Określony ślad śledzenia zdarzeń wejściowych systemu Windows (ETW) jest nieprawidłowy. |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4 (0x00000004) | Określony wynik śledzenia ETW jest nieprawidłowy. |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5 (0x00000005) | Struktura [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) nie została poprawnie zainicjowana. |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6 (0x00000006) | Struktura [RELOG_CALLBACKS](relog-callbacks-struct.md) nie została poprawnie zainicjowana. |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7 (0x00000007) | Nie można otworzyć wejściowego śledzenia ETW. |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8 (0x00000008) | Wystąpił błąd podczas przetwarzania wejściowego śledzenia ETW. |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9 (0x00000009) | Wystąpił błąd podczas próby uruchomienia sesji ponownego rejestrowania. |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10 (0x0000000A) | W wejściowym śledzeniu ETW brakuje ważnych zdarzeń. |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11 (0x0000000B) | Korzystasz C++ z usługi Build Insights w nieobsługiwanej wersji systemu Windows. |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12 (0x0000000C) | Podana nazwa sesji jest nieprawidłowa. |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13 (0x0000000D) | Ta operacja wymaga uprawnień administratora. |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14 (0x0000000E) | Wystąpił błąd podczas generowania identyfikatora GUID. |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15 (0x0000000F) | Wystąpił błąd podczas próby określenia ścieżki katalogu tymczasowego. |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16 (0x00000010) | Wystąpił błąd podczas próby utworzenia katalogu tymczasowego dla rozpoczętej sesji śledzenia. |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17 (0x00000011) | Wystąpił błąd podczas próby uruchomienia śledzenia systemu. |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18 (0x00000012) | Wystąpił błąd podczas próby uruchomienia śledzenia MSVC. |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19 (0x00000013) | Wystąpił błąd podczas próby zatrzymania śledzenia MSVC. |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20 (0x00000014) | Wystąpił błąd podczas próby uruchomienia śledzenia systemu. |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21 (0x00000015) | Śledzenie zostało zatrzymane, ale nie można odnaleźć katalogu tymczasowego sesji śledzenia. |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22 (0x00000016) | Nie można znaleźć pliku śledzenia dla zatrzymania MSVC śledzenia. |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23 (0x00000017) | Wystąpił błąd podczas scalania śladów przy użyciu kontrolki śledzenia jądra. |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24 (0x00000018) | Wystąpił nieznany błąd. |

::: moniker-end
