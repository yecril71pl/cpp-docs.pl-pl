---
title: 'Samouczek: podstawowe informacje dotyczące analizatora wydajności systemu Windows'
description: Samouczek dotyczący wykonywania podstawowych operacji w analizatorze wydajności systemu Windows.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f197e7dfd852cd66039f7279f90e42b0cf75fd86
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332230"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>Samouczek: podstawowe informacje dotyczące analizatora wydajności systemu Windows

::: moniker range="<=vs-2017"

Narzędzia C++ Build Insights są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją tej wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

Efektywne C++ korzystanie z usługi Build Insights wymaga pewnej znajomości analizatora wydajności systemu Windows. Ten artykuł ułatwia zapoznanie się z typowymi operacjami WPA. Więcej informacji o sposobach korzystania z protokołu WPA znajduje się w dokumentacji [analizatora wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer) .

## <a name="change-the-view-mode"></a>Zmień tryb widoku

WPA oferuje dwa podstawowe tryby widoku umożliwiające Eksplorowanie śladów:

- Tryb grafu i
- tryb tabeli.

Można przełączać się między nimi przy użyciu ikon trybu widoku w górnej części okienka widok:

![Przełączanie między trybem grafu a trybem tabeli.](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>Wybieranie ustawień wstępnych

Większość C++ widoków usługi Build Insights ma wiele ustawień wstępnych, które można wybrać. Możesz wybrać odpowiednie ustawienie wstępne za pomocą menu rozwijanego w górnej części okienka widok:

![Wybieranie ustawień wstępnych.](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>Powiększanie i pomniejszanie

Niektóre ślady kompilacji są bardzo duże, dlatego trudno jest wprowadzić szczegóły. Aby powiększyć obszar, który Cię interesuje, kliknij prawym przyciskiem myszy wykres i wybierz pozycję **Powiększ**. Zawsze możesz wrócić do poprzedniego ustawienia, wybierając polecenie **Cofnij powiększenie**. Ten obraz pokazuje przykład użycia zaznaczenia i **powiększania** w celu powiększania w sekcji grafu:

![Powiększanie w grafie.](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>Grupuj według różnych kolumn

Możesz dostosować sposób wyświetlania śladu. Kliknij ikonę koła zębatego w górnej części okienka widok i ponownie Rozmieść kolumny w edytorze widoku programu Build Explorer. Kolumny znalezione powyżej żółtego wiersza w tym oknie dialogowym to te, które są pogrupowane według wierszy danych. Kolumna znajdująca się nad żółtym wierszem jest specjalna: w widoku wykresu jest wyświetlana na kolorowym pasku.

Ten obraz przedstawia przykładowy wykres słupkowy wywołania linku. Używamy ikony koła zębatego, aby otworzyć okno dialogowe edytora programu Build Explorer. Następnie przeciągniemy wpisy kolumny Component i Name powyżej żółtej linii. Konfiguracja została zmieniona, aby zwiększyć poziom szczegółowości i zobaczyć, co faktycznie się stało wewnątrz konsolidatora:

![Powiększanie w grafie.](media/wpa-grouping.gif)

## <a name="see-also"></a>Zobacz także

[Samouczek: vcperf i Analizator wydajności systemu Windows](vcperf-and-wpa.md)\
[Reference: polecenia vcperf](/cpp/build-insights/reference/vcperf-commands)\
[Odwołanie: widoki Analizatora wydajności systemu Windows](/cpp/build-insights/reference/wpa-views)\
[Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
