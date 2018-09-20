---
title: Aplikacje klasyczne MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MFC
- mfc
dev_langs:
- C++
helpviewer_keywords:
- libraries, MFC
- class libraries, MFC
- MFC, about MFC
ms.assetid: 7101cb18-a681-495c-8f2b-069ad20c72f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3168057527eb1df6d87bd8f5aefe3403b7467bd9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406701"
---
# <a name="mfc-desktop-applications"></a>Aplikacje dla Pulpitu MFC

Biblioteka Microsoft Foundation Class (MFC) zapewnia otok obiektowy przez większość Win32 i COM, interfejsów API. Chociaż może służyć do tworzenia bardzo prostej aplikacji pulpitu, jest najbardziej użyteczna gdy trzeba tworzyć bardziej złożone interfejsy użytkownika z wieloma formantami. MFC można użyć do tworzenia aplikacji za pomocą interfejsów użytkownika w stylu pakietu Office.

Odwołanie MFC obejmuje klasy, funkcje globalne, zmienne globalne i makra, które tworzą bibliotekę Microsoft Foundation Class.

Wykresy poszczególnych hierarchii dołączonych do każdej klasy są przydatne do lokalizowania klas podstawowych. Odwołanie MFC zwykle nie opisuje funkcji odziedziczonego członka lub odziedziczonych operatorów. Aby uzyskać informacje na temat tych funkcji zapoznaj się z podstawowe klasy przedstawiony na diagramach hierarchii.

Dokumentacja dla każdej klasy zawiera omówienie klasy, podsumowanie członków według kategorii i tematy dotyczące funkcji elementów członkowskich, przeciążone operatory i elementy członkowskie danych.

Elementy członkowskie klasy publicznej i chronionej są udokumentowane tylko wtedy, gdy są normalnie używane w programach aplikacji lub klasach pochodnych. Zobacz pliki nagłówkowe klasy, aby uzyskać pełną listę elementów członkowskich klas.

> [!IMPORTANT]
>  Klasy MFC i ich członków nie można użyć w aplikacjach, które są wykonywane w środowisku Windows Runtime.
>
>  Biblioteki MFC (dll) dla znaków wielobajtowych (MBCS) kodowania znajdują się już w programie Visual Studio, ale są dostępne jako dodatek programu Visual Studio. Aby uzyskać więcej informacji, zobacz [dodatku DLL MBCS MFC](mfc-mbcs-dll-add-on.md).

## <a name="in-this-section"></a>W tej sekcji

[Pojęcia](mfc-concepts.md)<br/>
Artykuły koncepcyjne dotyczące biblioteki MFC, tematów.

[Wykres hierarchii](hierarchy-chart.md)<br/>
Wizualnie wyszczególnia relacje klas w bibliotece klas.

[Klasa — Przegląd](class-library-overview.md)<br/>
Wyświetla listę klas w bibliotece MFC według kategorii.

[Przewodniki](walkthroughs-mfc.md)<br/>
Zawiera artykuły, które zawierają wzięte różnych zadaniach związanych z funkcjami biblioteki MFC.

[Uwagi techniczne](mfc-technical-notes.md)<br/>
Zawiera łącza do tematów specjalistycznych, napisanych przez zespół projektowy MFC w bibliotece klas.

[Dostosowywanie na potrzeby MFC](customization-for-mfc.md)<br/>
Zawiera pewne wskazówki dotyczące dostosowywania aplikacji MFC.

[Klasy](reference/mfc-classes.md)<br/>
Zawiera łącza do i informacje o plikach nagłówka dla klas MFC.

[Klasy wewnętrzne](reference/internal-classes.md)<br/>
Stosowane wewnętrznie w MFC. Aby informacje były kompletne w tej sekcji opisano te klasy wewnętrznej, ale nie są przeznaczone do użycia bezpośrednio w kodzie.

[Makra i funkcje globalne](reference/mfc-macros-and-globals.md)<br/>
Zawiera łącza do makr i funkcje globalne w bibliotece MFC.

[Struktury, style, wywołania zwrotne i mapy komunikatów](reference/structures-styles-callbacks-and-message-maps.md)<br/>
Zawiera łącza do struktury, style, wywołania zwrotne i mapy komunikatów używany przez bibliotekę MFC.

[Kreatory i okna dialogowe MFC](reference/mfc-wizards-and-dialog-boxes.md)<br/>
Przewodnik po funkcjach programu Visual Studio do tworzenia aplikacji MFC.

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
Jak używać plików zasobów do zarządzania danymi interfejsu użytkownika statycznych, takich jak ciągi interfejsu użytkownika i układ okna dialogowego.

## <a name="related-sections"></a>Sekcje pokrewne

[Kategorie wykresów hierarchii](hierarchy-chart-categories.md)<br/>
Opisuje MFC wykresu hierarchii według kategorii.

[Klasy współdzielone ATL/MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
Oferuje łącza do klas, które są wspólne dla MFC i ATL.

[Przykłady MFC](../visual-cpp-samples.md)<br/>
Zawiera łącza do przykładów, które przedstawiają sposoby użycia klas MFC.

[Odwołania do bibliotek języka Visual C++](../standard-library/cpp-standard-library-reference.md)<br/>
Zawiera łącza do różnych bibliotek dostarczanych z programem Visual C++, włączając biblioteki ATL, MFC, szablony OLE DB, biblioteki wykonawczej C i standardowej biblioteki języka C++.

[Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio.md)<br/>
Zawiera łącza do przy użyciu debugera programu Visual Studio, aby poprawić błędy logiczne w aplikacji lub procedur składowanych.

## <a name="see-also"></a>Zobacz też

[MFC i ATL](mfc-and-atl.md)
