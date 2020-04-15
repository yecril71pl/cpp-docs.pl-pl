---
title: RESULT_CODE wyliczenia
description: C++ Build Insights SDK RESULT_CODE odwołanie wyliczenia.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 62874e176c3f3e8f9df1ca64e7b593b7a0ef5c01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323622"
---
# <a name="result_code-enum"></a>RESULT_CODE wyliczenia

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Wyliczenia `RESULT_CODE` opisuje warunki sukcesu i awarii.

## <a name="members"></a>Elementy członkowskie

| Nazwa | Wartość | Opis |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0 (0x00000000) | Operacja zakończyła się pomyślnie. |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | Jedną z funkcji wywołania zwrotnego w [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) lub `CALLBACK_CODE_ANALYSIS_FAILURE` [RELOG_DESCRIPTOR](relog-descriptor-struct.md) zwrócona wartość. Ta wartość jest członkiem [CALLBACK_CODE](callback-code-enum.md) wyliczenia. |
| `RESULT_CODE_FAILURE_CANCELLED` | 2 (0x00000002) | Jedną z funkcji wywołania zwrotnego w [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) lub `CALLBACK_CODE_ANALYSIS_CANCEL` [RELOG_DESCRIPTOR](relog-descriptor-struct.md) zwrócona wartość. Ta wartość jest członkiem [CALLBACK_CODE](callback-code-enum.md) wyliczenia. |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3 (0x00000003) | Określony śledzenia zdarzeń wejściowych dla systemu Windows (ETW) jest nieprawidłowy. |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4 (0x00000004) | Określony wynikowy ślad ETW jest nieprawidłowy. |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5 (0x00000005) | Struktura [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) nie została poprawnie zainicjowana. |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6 (0x00000006) | Struktura [RELOG_CALLBACKS](relog-callbacks-struct.md) nie została poprawnie zainicjowana. |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7 (0x00000007) | Nie można otworzyć wejściowego śledzenia ETW. |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8 (0x00000008) | Wystąpił błąd podczas przetwarzania wejściowego śledzenia ETW. |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9 (0x00000009) | Wystąpił błąd podczas próby uruchomienia sesji ponownego rejestrowania. |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10 (0x0000000A) | Śledzenia ETW wejścia brakuje ważnych zdarzeń. |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11 (0x0000000B) | Aplikacja C++ Build Insights jest korzystać z nieobsługiconej wersji systemu Windows. |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12 (0x000000C) | Podana nazwa sesji jest nieprawidłowa. |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13 (0x0000000D) | Ta operacja wymaga uprawnień administratora. |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14 (0x0000000E) | Wystąpił błąd podczas generowania identyfikatora GUID. |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15 (0x000000F) | Wystąpił błąd podczas próby określenia ścieżki katalogu tymczasowego. |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16 (0x00000010) | Wystąpił błąd podczas próby utworzenia katalogu tymczasowego dla rozpoczętej sesji śledzenia. |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17 (0x00000011) | Wystąpił błąd podczas próby uruchomienia śledzenia systemu. |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18 (0x00000012) | Wystąpił błąd podczas próby uruchomienia śledzenia MSVC. |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19 (0x00000013) | Wystąpił błąd podczas próby zatrzymania śledzenia MSVC. |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20 (0x00000014) | Wystąpił błąd podczas próby uruchomienia śledzenia systemu. |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21 (0x00000015) | Śledzenie zostało zatrzymane, ale nie można odnaleźć katalogu tymczasowego sesji śledzenia. |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22 (0x00000016) | Nie można odnaleźć pliku śledzenia dla zatrzymanego śledzenia MSVC. |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23 (0x00000017) | Wystąpił błąd podczas scalania śladów przy użyciu kontroli śledzenia jądra. |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24 (0x00000018) | Wystąpił nieznany błąd. |

::: moniker-end
