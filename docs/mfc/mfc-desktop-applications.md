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
ms.openlocfilehash: e9921d18e9ec060f61959278b68906338f02b5b7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447711"
---
# <a name="mfc-desktop-applications"></a>Aplikacje dla Pulpitu MFC

Biblioteka Microsoft Foundation Class (MFC) zapewnia otokę zorientowaną obiektowo na wiele interfejsów API Win32 i COM. Chociaż może służyć do tworzenia bardzo prostych aplikacji klasycznych, jest najbardziej przydatne, gdy trzeba będzie opracowywać bardziej złożone interfejsy użytkownika z wieloma kontrolkami. Można użyć MFC do tworzenia aplikacji z interfejsami użytkownika w stylu pakietu Office. Aby uzyskać dokumentację dotyczącą platformy Windows, zobacz [dokumentację systemu Windows](/windows/index). Aby uzyskać informacje na temat tworzenia aplikacji C++ systemu Windows w programie bez MFC, zobacz [Kompilowanie aplikacji klasycznych systemu windows przy użyciu Win32 API](/windows/win32/index).

Dokumentacja MFC obejmuje klasy, funkcje globalne, zmienne globalne i makra, które tworzą biblioteka MFC.

Poszczególne wykresy hierarchii dołączone do poszczególnych klas są przydatne do lokalizowania klas bazowych. Odwołanie MFC zazwyczaj nie opisuje dziedziczonych funkcji Członkowskich lub dziedziczonych operatorów. Aby uzyskać informacje o tych funkcjach, zapoznaj się z klasami podstawowymi przedstawionymi na diagramach hierarchii.

Dokumentacja dla każdej klasy zawiera przegląd klasy, podsumowanie elementu członkowskiego według kategorii i tematy dotyczące funkcji Członkowskich, przeciążonych operatorów i członków danych.

Publiczne i chronione składowe klasy są dokumentowane tylko wtedy, gdy są zwykle używane w programach aplikacji lub klasach pochodnych. Zobacz pliki nagłówkowe klasy, aby uzyskać pełną listę elementów członkowskich klasy.

> [!IMPORTANT]
>  Klas MFC i ich członków nie można używać w aplikacjach, które są wykonywane w środowisku środowisko wykonawcze systemu Windows.
>
>  Biblioteki MFC (dll) dla kodowania znaków wielobajtowych (MBCS) nie są już dołączone do programu Visual Studio, ale są dostępne jako dodatek Visual Studio. Aby uzyskać więcej informacji, zobacz [MFC MBCS dll Add-on](mfc-mbcs-dll-add-on.md).

## <a name="in-this-section"></a>W tej sekcji

[Pojęcia](mfc-concepts.md)<br/>
Artykuły koncepcyjne w temacie dotyczące MFC.

[Wykres hierarchii](hierarchy-chart.md)<br/>
Wizualnie szczegóły relacji klas w bibliotece klas.

[Przegląd klas](class-library-overview.md)<br/>
Wyświetla listę klas w bibliotece MFC zgodnie z kategorią.

[Przewodniki](walkthroughs-mfc.md)<br/>
Zawiera artykuły, które przeprowadzą Cię przez różne zadania związane z funkcjami biblioteki MFC.

[Uwagi techniczne](mfc-technical-notes.md)<br/>
Oferuje linki do specjalistycznych tematów, które są zapisywane przez zespół programistyczny MFC w bibliotece klas.

[Dostosowywanie na potrzeby MFC](customization-for-mfc.md)<br/>
Zawiera wskazówki dotyczące dostosowywania aplikacji MFC.

[Klasy](reference/mfc-classes.md)<br/>
Zawiera łącza do i informacje o pliku nagłówka klas MFC.

[Klasy wewnętrzne](reference/internal-classes.md)<br/>
Używane wewnętrznie w MFC. W tej sekcji opisano te klasy wewnętrzne, ale nie są one przeznaczone do użycia bezpośrednio w kodzie.

[Makra i Globals](reference/mfc-macros-and-globals.md)<br/>
Zawiera łącza do makr i funkcji globalnych w bibliotece MFC.

[Struktury, style, wywołania zwrotne i mapy komunikatów](reference/structures-styles-callbacks-and-message-maps.md)<br/>
Oferuje linki do struktur, stylów, wywołań zwrotnych i map komunikatów używanych przez bibliotekę MFC.

[Kreatory i okna dialogowe MFC](reference/mfc-wizards-and-dialog-boxes.md)<br/>
Przewodnik dotyczący funkcji w programie Visual Studio do tworzenia aplikacji MFC.

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
Jak używać plików zasobów do zarządzania danymi statycznego interfejsu użytkownika, takimi jak ciągi interfejsu użytkownika i układ okna dialogowego.

## <a name="related-sections"></a>Sekcje pokrewne

[Kategorie wykresów hierarchii](hierarchy-chart-categories.md)<br/>
Opisuje wykres hierarchii MFC według kategorii.

[Klasy udostępnione ATL/MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
Oferuje linki do klas, które są współużytkowane przez MFC i ATL.

[Przykłady MFC](../overview/visual-cpp-samples.md)<br/>
Zawiera łącza do przykładów, które pokazują, jak używać MFC.

[Dokumentacja C++ bibliotek wizualnych](../standard-library/cpp-standard-library-reference.md)<br/>
Oferuje łącza do różnych bibliotek dostarczanych z wizualizacją C++, w tym ATL, MFC, OLE DB szablonów, biblioteki wykonawczej C i biblioteki C++ standardowej.

[Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)<br/>
Oferuje linki do korzystania z debugera programu Visual Studio w celu poprawienia błędów logiki w aplikacji lub procedurach składowanych.

## <a name="see-also"></a>Zobacz też

[MFC i ATL](mfc-and-atl.md)
