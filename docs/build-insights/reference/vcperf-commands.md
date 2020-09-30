---
title: 'Reference: polecenia vcperf'
description: Informacje dotyczące vcperf.exe narzędzia wiersza polecenia.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c251d93ce7e9e7325a7146f5697150344cb02d96
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508822"
---
# <a name="reference-vcperf-commands"></a>Reference: polecenia vcperf

::: moniker range="<=vs-2017"

Narzędzia do tworzenia szczegółowych danych w języku C++ są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją tej wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range="vs-2019"

W tym artykule wymieniono i opisano polecenia dostępne w *vcperf.exe*oraz sposób ich używania.

## <a name="commands-to-start-and-stop-traces"></a>Polecenia do uruchamiania i zatrzymywania śledzenia

*Ważne: poniższe polecenia wymagają uprawnień administracyjnych.*

| Opcja           | Argumenty i opis |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | Informuje *vcperf.exe* o rozpoczęciu śledzenia pod daną nazwą sesji. Dla danego komputera może istnieć tylko jedna sesja aktywna. <br/><br/> Jeśli ta `/nocpusampling` opcja jest określona, *vcperf.exe* nie zbiera próbek procesora CPU. Uniemożliwia korzystanie z widoku użycie procesora CPU (próbkowany) w analizatorze wydajności systemu Windows, ale dane śledzenia są mniejsze. <br/><br/> Po rozpoczęciu śledzenia *vcperf.exe* zwraca natychmiast. Zdarzenia są zbierane w całym systemie dla wszystkich procesów uruchomionych na komputerze. Oznacza to, że nie trzeba kompilować projektu z tego samego wiersza polecenia jak ten, który został użyty do uruchomienia *vcperf.exe*. Na przykład można skompilować projekt z programu Visual Studio. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | Kończy śledzenie identyfikowane przez daną nazwę sesji. Uruchamia krok przetwarzania po wykonaniu śledzenia w celu wygenerowania pliku widocznego w usłudze Windows Performance Analyzer (WPA). Aby uzyskać najlepsze wyniki, użyj wersji WPA, która zawiera dodatek do wglądu w szczegółowe dane w języku C++. Aby uzyskać więcej informacji, zobacz Rozpoczynanie [pracy ze szczegółowymi kompilacjami w języku C++](../get-started-with-cpp-build-insights.md). `<outputFile.etl>`Parametr określa miejsce zapisania pliku wyjściowego. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | Powoduje zatrzymanie śledzenia identyfikowanego przez daną nazwę sesji i zapisanie nieprzetworzonych, nieprzetworzonych danych w określonym pliku wyjściowym. Plik, który nie jest przeznaczony do wyświetlania w WPA. <br/><br/> Krok przetwarzania wykonywanego w `/stop` poleceniu może czasami być długi. Możesz użyć polecenia, `/stopnoanalyze` aby opóźnić ten krok przetwarzania końcowego. Użyj `/analyze` polecenia, gdy wszystko jest gotowe do utworzenia pliku dostępnego w analizatorze wydajności systemu Windows. |

## <a name="miscellaneous-commands"></a>Różne polecenia

| Opcja     | Argumenty i opis |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Akceptuje Nieprzetworzony plik śledzenia utworzony przez `/stopnoanalyze` polecenie. Uruchamia krok przetwarzania końcowego dla tego śladu w celu wygenerowania pliku widocznego w analizatorze wydajności systemu Windows. Aby uzyskać najlepsze wyniki, użyj wersji WPA, która zawiera dodatek do wglądu w szczegółowe dane w języku C++. Aby uzyskać więcej informacji, zobacz Rozpoczynanie [pracy ze szczegółowymi kompilacjami w języku C++](../get-started-with-cpp-build-insights.md). |

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do usługi C++ build Insights](../get-started-with-cpp-build-insights.md)\
[Samouczek: podstawowe informacje dotyczące analizatora wydajności systemu Windows](../tutorials/wpa-basics.md)\
[Odwołanie: widoki Analizatora wydajności systemu Windows](wpa-views.md)\
[Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
