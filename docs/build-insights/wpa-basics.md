---
title: 'C++Build Insights: podstawowe informacje dotyczące analizatora wydajności systemu Windows'
description: Samouczek dotyczący wykonywania podstawowych operacji w analizatorze wydajności systemu Windows.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4bd91698561175d876b7a3351a0ed6e85ef73a35
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633085"
---
# <a name="c-build-insights-windows-performance-analyzer-basics"></a>C++Build Insights: podstawowe informacje dotyczące analizatora wydajności systemu Windows

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

[Wprowadzenie do C++ usługi Build Insights](get-started-with-cpp-build-insights.md)\
[vcperf. exe — informacje referencyjne](vcperf-reference.md)\
[Informacje dotyczące widoków analizatora wydajności systemu Windows](wpa-views-reference.md)\
[Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
