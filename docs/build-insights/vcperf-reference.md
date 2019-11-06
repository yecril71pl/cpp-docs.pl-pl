---
title: 'C++Build Insights: dokumentacja vcperf. exe'
description: Odwołanie do narzędzia wiersza polecenia vcperf. exe.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 195d115edae9947b39795440894e4f6bf0ee485e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633099"
---
# <a name="c-build-insights-vcperfexe-reference"></a>C++Build Insights: dokumentacja vcperf. exe

::: moniker range="<=vs-2017"

Narzędzia C++ Build Insights są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją tej wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

W tym artykule wymieniono i opisano polecenia dostępne w programie *vcperf. exe*oraz sposób ich używania.

## <a name="commands-to-start-and-stop-traces"></a>Polecenia do uruchamiania i zatrzymywania śledzenia

*Ważne: poniższe polecenia wymagają uprawnień administracyjnych.*

| Opcja           | Argumenty i opis |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]``<sessionName>` |
|                  | Nakazuje programowi *vcperf. exe* rozpoczęcie śledzenia pod daną nazwą sesji. Dla danego komputera może istnieć tylko jedna sesja aktywna. <br/><br/> Jeśli opcja `/nocpusampling` jest określona, *vcperf. exe* nie zbiera próbek procesora CPU. Uniemożliwia korzystanie z widoku użycie procesora CPU (próbkowany) w analizatorze wydajności systemu Windows, ale dane śledzenia są mniejsze. <br/><br/> Po rozpoczęciu śledzenia *vcperf. exe* wraca natychmiast. Zdarzenia są zbierane w całym systemie dla wszystkich procesów uruchomionych na komputerze. Oznacza to, że nie trzeba kompilować projektu z tego samego wiersza polecenia jak użyty do uruchomienia programu *vcperf. exe*. Na przykład można skompilować projekt z programu Visual Studio. |
| `/stop`          | `<sessionName>``<outputFile.etl>` |
|                  | Kończy śledzenie identyfikowane przez daną nazwę sesji. Uruchamia krok przetwarzania po wykonaniu śledzenia w celu wygenerowania pliku widocznego w usłudze Windows Performance Analyzer (WPA). Aby uzyskać najlepsze wyniki, użyj wersji WPA zawierającej dodatek C++ Build Insights. Aby uzyskać więcej informacji, zobacz Rozpoczynanie [pracy z usługą C++ Build Insights](get-started-with-cpp-build-insights.md). Parametr `<outputFile.etl>` określa miejsce zapisania pliku wyjściowego. |
| `/stopnoanalyze` | `<sessionName>``<rawOutputFile.etl>` |
|                  | Powoduje zatrzymanie śledzenia identyfikowanego przez daną nazwę sesji i zapisanie nieprzetworzonych, nieprzetworzonych danych w określonym pliku wyjściowym. Plik, który nie jest przeznaczony do wyświetlania w WPA. <br/><br/> Krok przetwarzania wykonywanego w poleceniu `/stop` może czasami być długi. Aby opóźnić ten krok przetwarzania końcowego, można użyć polecenia `/stopnoanalyze`. Użyj `/analyze` polecenia, gdy wszystko jest gotowe do utworzenia pliku dostępnego w analizatorze wydajności systemu Windows. |

## <a name="miscellaneous-commands"></a>Różne polecenia

| Opcja     | Argumenty i opis |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Akceptuje Nieprzetworzony plik śledzenia utworzony przez polecenie `/stopnoanalyze`. Uruchamia krok przetwarzania końcowego dla tego śladu w celu wygenerowania pliku widocznego w analizatorze wydajności systemu Windows. Aby uzyskać najlepsze wyniki, użyj wersji WPA zawierającej dodatek C++ Build Insights. Aby uzyskać więcej informacji, zobacz Rozpoczynanie [pracy z usługą C++ Build Insights](get-started-with-cpp-build-insights.md). |

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do C++ usługi Build Insights](get-started-with-cpp-build-insights.md)\
[Podstawy analizatora wydajności systemu Windows](wpa-basics.md)\
[Informacje dotyczące widoków analizatora wydajności systemu Windows](wpa-views-reference.md)\
[Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
