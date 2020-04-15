---
title: 'Samouczek: Podstawy analizatora wydajności systemu Windows'
description: Samouczek dotyczący wykonywania podstawowych operacji w analizatorze wydajności systemu Windows.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ae1050b9389527a12f5bdbea6d695c0f20510127
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323403"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>Samouczek: Podstawy analizatora wydajności systemu Windows

::: moniker range="<=vs-2017"

Narzędzia aplikacji Skompilowanie kompilacji języka C++ są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją dla tej wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range="vs-2019"

Za pomocą programu C++ Build Insights skutecznie wymaga pewnej wiedzy na temat analizatora wydajności systemu Windows (WPA). Ten artykuł ułatwia zapoznanie się z typowymi operacjami WPA. Aby uzyskać więcej informacji na temat korzystania z usługi WPA, zobacz dokumentację [analizatora wydajności systemu Windows.](/windows-hardware/test/wpt/windows-performance-analyzer)

## <a name="change-the-view-mode"></a>Zmienianie trybu widoku

WPA oferuje dwa podstawowe tryby wyświetlania, aby eksplorować swoje ślady:

- tryb wykresu, oraz
- w trybie tabeli.

Można przełączać się między nimi za pomocą ikon trybu widoku w górnej części okienka widoku:

![Przełączanie między trybem wykresu a trybem tabeli.](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>Zaznaczanie ustawień wstępnych

Większość widoków WPA kompilacji języka C++ ma wiele ustawień predefiniowanych do wyboru. Ustawienia predefiniowane można wybrać za pomocą menu rozwijanego w górnej części okienka widoku:

![Wybór ustawień wstępnych.](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>Powiększenie lub pomniejszenie

Niektóre ślady kompilacji są tak duże, że trudno jest ustalić szczegóły. Aby powiększyć obszar, który Cię interesuje, kliknij prawym przyciskiem myszy wykres i wybierz **polecenie Powiększ**. Zawsze możesz wrócić do poprzedniego ustawienia, wybierając pozycję **Cofnij powiększenie**. Ten obraz przedstawia przykład użycia zaznaczenia i polecenia **Powiększenie,** aby powiększyć sekcję wykresu:

![Powiększanie wykresu.](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>Grupowanie według różnych kolumn

Sposób wyświetlania śledzenia można dostosować. Kliknij ikonę koła zębatego u góry okienka widoku i zmień kolejność kolumn w Edytorze widoku Eksploratora kompilacji. Kolumny znajdujące się powyżej żółtej linii w tym oknie dialogowym są kolumnami, według których wiersze danych są pogrupowane. Kolumna tuż nad żółtą linią jest szczególna: w widoku wykresu jest wyświetlana na kolorowych paskach.

Na tym obrazie przedstawiono przykładowy wykres słupkowy wywołania łącza. Używamy ikony koła zębatego, aby otworzyć okno dialogowe Edytor widoku Eksploratora kompilacji. Następnie przeciągamy pozycje kolumny Komponent i Nazwa nad żółtą linią. Konfiguracja jest zmieniana, aby zwiększyć poziom szczegółowości i zobaczyć, co faktycznie wydarzyło się wewnątrz konsolidatora:

![Powiększanie wykresu.](media/wpa-grouping.gif)

## <a name="see-also"></a>Zobacz też

[Samouczek: vcperf i analizator wydajności systemu Windows](vcperf-and-wpa.md)\
[Referencje: polecenia vcperf](/cpp/build-insights/reference/vcperf-commands)\
[Odwołanie: Widoki analizatora wydajności systemu Windows](/cpp/build-insights/reference/wpa-views)\
[Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
