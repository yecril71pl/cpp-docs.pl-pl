---
title: Aplikacje dla Pulpitu MFC
ms.date: 07/28/2019
f1_keywords:
- MFC
helpviewer_keywords:
- libraries, MFC
- class libraries, MFC
- MFC, about MFC
ms.assetid: 7101cb18-a681-495c-8f2b-069ad20c72f7
ms.openlocfilehash: 3811fdcf278129ee72872ea489b42f8389957761
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359339"
---
# <a name="mfc-desktop-applications"></a>Aplikacje dla Pulpitu MFC

Biblioteka microsoft foundation class (MFC) udostępnia zorientowane obiektowo otokę nad większością interfejsów API win32 i COM. Chociaż może służyć do tworzenia bardzo prostych aplikacji klasycznych, jest to najbardziej przydatne, gdy trzeba opracować bardziej złożone interfejsy użytkownika z wielu formantów. Za pomocą MFC można tworzyć aplikacje za pomocą interfejsów użytkownika w stylu pakietu Office. Aby uzyskać dokumentację dotyczącą samej platformy Windows, zobacz [dokumentację systemu Windows](/windows/index). Aby uzyskać informacje na temat tworzenia aplikacji systemu Windows w języku C++ bez interfejsu MFC, zobacz [Tworzenie klasycznych aplikacji systemu Windows przy użyciu interfejsu API systemu Win32](/windows/win32/index).

Odwołanie MFC obejmuje klasy, funkcje globalne, zmienne globalne i makra, które tworzą bibliotekę klas Microsoft Foundation.

Poszczególne wykresy hierarchii dołączone do każdej klasy są przydatne do lokalizowania klas podstawowych. Odwołanie MFC zwykle nie opisuje odziedziczonych funkcji członkowskich lub operatorów dziedziczonych. Aby uzyskać informacje na temat tych funkcji, zapoznaj się z klasami podstawowymi przedstawionymi na diagramach hierarchii.

Dokumentacja dla każdej klasy zawiera przegląd klasy, podsumowanie elementu członkowskiego według kategorii i tematy dla funkcji członkowskich, przeciążonych operatorów i elementów członkowskich danych.

Elementy członkowskie klasy publicznej i chronionej są dokumentowane tylko wtedy, gdy są zwykle używane w programach aplikacji lub klasach pochodnych. Zobacz pliki nagłówka klasy dla pełnej listy członków klasy.

> [!IMPORTANT]
> Klasy MFC i ich elementy członkowskie nie mogą być używane w aplikacjach, które są wykonywane w środowisku środowiska wykonawczego systemu Windows.
>
> Biblioteki MFC (biblioteki DLL) do kodowania znaków wielobajtowych (MBCS) nie są już uwzględniane w programie Visual Studio, ale są dostępne jako dodatek visual studio. Aby uzyskać więcej informacji, zobacz [Dodatek DLL MFC MBCS](mfc-mbcs-dll-add-on.md).

## <a name="in-this-section"></a>W tej sekcji

[Pojęcia](mfc-concepts.md)<br/>
Artykuły koncepcyjne na tematy MFC.

[Wykres hierarchii](hierarchy-chart.md)<br/>
Wizualnie szczegóły relacji klas w bibliotece klas.

[Przegląd klas](class-library-overview.md)<br/>
Wyświetla listę klas w bibliotece MFC według kategorii.

[Wskazówki](walkthroughs-mfc.md)<br/>
Zawiera artykuły, które przechadzają się przez różne zadania skojarzone z funkcjami biblioteki MFC.

[Uwagi techniczne](mfc-technical-notes.md)<br/>
Zawiera łącza do tematów specjalistycznych, napisany przez zespół programistów MFC, w bibliotece klas.

[Dostosowywanie na potrzeby MFC](customization-for-mfc.md)<br/>
Zawiera kilka wskazówek dotyczących dostosowywania aplikacji MFC.

[Klasy](reference/mfc-classes.md)<br/>
Zawiera łącza do i informacje o pliku nagłówka dla klas MFC.

[Klasy wewnętrzne](reference/internal-classes.md)<br/>
Używany wewnętrznie w MFC. Dla kompletności w tej sekcji opisano te klasy wewnętrzne, ale nie są one przeznaczone do użycia bezpośrednio w kodzie.

[Makra i globals](reference/mfc-macros-and-globals.md)<br/>
Zawiera łącza do makr i funkcji globalnych w bibliotece MFC.

[Struktury, style, wywołania zwrotne i mapy komunikatów](reference/structures-styles-callbacks-and-message-maps.md)<br/>
Zawiera łącza do struktur, stylów, wywołań zwrotnych i map wiadomości używanych przez bibliotekę MFC.

[Kreatory i okna dialogowe MFC](reference/mfc-wizards-and-dialog-boxes.md)<br/>
Przewodnik po funkcjach w programie Visual Studio do tworzenia aplikacji MFC.

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
Jak używać plików zasobów do zarządzania statycznymi danymi interfejsu użytkownika, takimi jak ciągi interfejsu użytkownika i układ okna dialogowego.

## <a name="related-sections"></a>Sekcje pokrewne

[Kategorie diagramów hierarchii](hierarchy-chart-categories.md)<br/>
Opisuje wykres hierarchii MFC według kategorii.

[Klasy współdzielone ATL/MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
Zawiera łącza do klas, które są współużytkowane przez MFC i ATL.

[Próbki MFC](../overview/visual-cpp-samples.md#mfc-samples)<br/>
Zawiera łącza do przykładów, które pokazują, jak używać MFC.

[Odwołanie do bibliotek języka Visual C++](../standard-library/cpp-standard-library-reference.md)<br/>
Zawiera łącza do różnych bibliotek dostarczonych z visual C++, w tym ATL, MFC, szablony OLE DB, biblioteki wykonywania języka C i biblioteki standardowej języka C++.

[Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)<br/>
Zawiera łącza do korzystania z debugera programu Visual Studio, aby poprawić błędy logiczne w aplikacji lub procedur przechowywanych.

## <a name="see-also"></a>Zobacz też

[MFC i ATL](mfc-and-atl.md)
