---
title: 'Reference: polecenia vcperf'
description: Odwołanie do narzędzia wiersza polecenia vcperf. exe.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b85320ce4517eb41410c59a11bd79553405b8402
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332223"
---
# <a name="reference-vcperf-commands"></a>Reference: polecenia vcperf

::: moniker range="<=vs-2017"

Narzędzia C++ Build Insights są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją tej wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

W tym artykule wymieniono i opisano polecenia dostępne w programie *vcperf. exe*oraz sposób ich używania.

## <a name="commands-to-start-and-stop-traces"></a>Polecenia do uruchamiania i zatrzymywania śledzenia

*Ważne: poniższe polecenia wymagają uprawnień administracyjnych.*

| Opcja           | Argumenty i opis |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | Nakazuje programowi *vcperf. exe* rozpoczęcie śledzenia pod daną nazwą sesji. Dla danego komputera może istnieć tylko jedna sesja aktywna. <br/><br/> Jeśli opcja `/nocpusampling` jest określona, *vcperf. exe* nie zbiera próbek procesora CPU. Uniemożliwia korzystanie z widoku użycie procesora CPU (próbkowany) w analizatorze wydajności systemu Windows, ale dane śledzenia są mniejsze. <br/><br/> Po rozpoczęciu śledzenia *vcperf. exe* wraca natychmiast. Zdarzenia są zbierane w całym systemie dla wszystkich procesów uruchomionych na komputerze. Oznacza to, że nie trzeba kompilować projektu z tego samego wiersza polecenia jak użyty do uruchomienia programu *vcperf. exe*. Na przykład można skompilować projekt z programu Visual Studio. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | Kończy śledzenie identyfikowane przez daną nazwę sesji. Uruchamia krok przetwarzania po wykonaniu śledzenia w celu wygenerowania pliku widocznego w usłudze Windows Performance Analyzer (WPA). Aby uzyskać najlepsze wyniki, użyj wersji WPA zawierającej dodatek C++ Build Insights. Aby uzyskać więcej informacji, zobacz Rozpoczynanie [pracy z usługą C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). Parametr `<outputFile.etl>` określa miejsce zapisania pliku wyjściowego. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | Powoduje zatrzymanie śledzenia identyfikowanego przez daną nazwę sesji i zapisanie nieprzetworzonych, nieprzetworzonych danych w określonym pliku wyjściowym. Plik, który nie jest przeznaczony do wyświetlania w WPA. <br/><br/> Krok przetwarzania wykonywanego w poleceniu `/stop` może czasami być długi. Aby opóźnić ten krok przetwarzania końcowego, można użyć polecenia `/stopnoanalyze`. Użyj `/analyze` polecenia, gdy wszystko jest gotowe do utworzenia pliku dostępnego w analizatorze wydajności systemu Windows. |

## <a name="miscellaneous-commands"></a>Inne polecenia

| Opcja     | Argumenty i opis |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Akceptuje Nieprzetworzony plik śledzenia utworzony przez polecenie `/stopnoanalyze`. Uruchamia krok przetwarzania końcowego dla tego śladu w celu wygenerowania pliku widocznego w analizatorze wydajności systemu Windows. Aby uzyskać najlepsze wyniki, użyj wersji WPA zawierającej dodatek C++ Build Insights. Aby uzyskać więcej informacji, zobacz Rozpoczynanie [pracy z usługą C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). |

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do C++ usługi Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Samouczek: podstawowe informacje na temat analizatora wydajności systemu Windows](/cpp/build-insights/tutorials/wpa-basics)\
[Odwołanie: widoki Analizatora wydajności systemu Windows](wpa-views.md)\
[Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
