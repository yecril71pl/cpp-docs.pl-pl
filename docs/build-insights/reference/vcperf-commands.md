---
title: 'Referencje: polecenia vcperf'
description: Odwołanie do narzędzia wiersza polecenia vcperf.exe.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9d3b0a9dbdfe922dc87f91006441e1f65d54c8a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323250"
---
# <a name="reference-vcperf-commands"></a>Referencje: polecenia vcperf

::: moniker range="<=vs-2017"

Narzędzia aplikacji Skompilowanie kompilacji języka C++ są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją dla tej wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range="vs-2019"

W tym artykule wymieniono i opisano polecenia dostępne w *pliku vcperf.exe*oraz sposób ich używania.

## <a name="commands-to-start-and-stop-traces"></a>Polecenia uruchamiania i zatrzymywania śladów

*WAŻNE: wszystkie następujące polecenia wymagają uprawnień administracyjnych.*

| Opcja           | Argumenty i opis |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | Mówi *vcperf.exe,* aby rozpocząć śledzenie pod daną nazwą sesji. Na danym komputerze może istnieć tylko jedna aktywna sesja na danym komputerze. <br/><br/> Jeśli `/nocpusampling` opcja jest określona, *vcperf.exe* nie zbiera próbek procesora CPU. Zapobiega użyciu widoku użycie procesora CPU (Próbkowane) w analizatorze wydajności systemu Windows, ale zmniejsza liczbę zebranych śladów. <br/><br/> Po uruchomieniu śledzenia *vcperf.exe* zwraca natychmiast. Zdarzenia są zbierane w całym systemie dla wszystkich procesów uruchomionych na komputerze. Oznacza to, że nie trzeba tworzyć projektu z tego samego wiersza polecenia, który był używany do uruchamiania *pliku vcperf.exe*. Na przykład można utworzyć projekt z programu Visual Studio. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | Zatrzymuje ślad identyfikowany przez nazwę danej sesji. Uruchamia krok przetwarzania końcowego na śledzenia do generowania pliku widoczne w analizatorze wydajności systemu Windows (WPA). Aby uzyskać najlepsze środowisko wyświetlania, należy użyć wersji usługi WPA, która zawiera dodatek Usługi W++ Build Insights. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do usługi C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). Parametr `<outputFile.etl>` określa, gdzie zapisać plik wyjściowy. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | Zatrzymuje ślad identyfikowany przez nazwę danej sesji i zapisuje nieprzetworzone, nieprzetworzone dane w określonym pliku wyjściowym. Wynikowy plik nie jest przeznaczony do wyświetlania w WPA. <br/><br/> Krok przetwarzania końcowego zaangażowany `/stop` w polecenie może czasami być długi. Za pomocą `/stopnoanalyze` polecenia można opóźnić ten krok przetwarzania końcowego. Użyj `/analyze` polecenia, gdy chcesz utworzyć plik widoczny w analizatorze wydajności systemu Windows. |

## <a name="miscellaneous-commands"></a>Różne polecenia

| Opcja     | Argumenty i opis |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Akceptuje nieprzetworzony plik `/stopnoanalyze` śledzenia wyprodukowany przez polecenie. Uruchamia krok przetwarzania końcowego na tym śledzenia do generowania pliku widoczne w analizatorze wydajności systemu Windows. Aby uzyskać najlepsze środowisko wyświetlania, należy użyć wersji usługi WPA, która zawiera dodatek Usługi W++ Build Insights. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do usługi C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). |

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do usługi C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Samouczek: Podstawy analizatora wydajności systemu Windows](/cpp/build-insights/tutorials/wpa-basics)\
[Odwołanie: Widoki analizatora wydajności systemu Windows](wpa-views.md)\
[Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
