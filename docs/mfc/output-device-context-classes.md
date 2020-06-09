---
title: Klasy wyjściowe (kontekst urządzenia)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.output
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
ms.openlocfilehash: b15f5034604f9d6b67574288140b79b144692478
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615361"
---
# <a name="output-device-context-classes"></a>Klasy wyjściowe (kontekst urządzenia)

Klasy te hermetyzują różne typy kontekstów urządzeń dostępne w systemie Windows.

Większość następujących klas hermetyzuje dojście do kontekstu urządzenia z systemem Windows. Kontekst urządzenia to obiekt systemu Windows, który zawiera informacje o atrybutach rysowania urządzenia, takich jak wyświetlacz lub drukarka. Wszystkie wywołania rysowania są wykonywane za pomocą obiektu kontekstu urządzenia. Dodatkowe klasy pochodzące od `CDC` hermetyzacji wyspecjalizowanych funkcji kontekstu urządzenia, w tym obsługa plików Windows.

[CDC](reference/cdc-class.md)<br/>
Klasa bazowa dla kontekstów urządzenia. Używane bezpośrednio do uzyskiwania dostępu do całego ekranu oraz do uzyskiwania dostępu do niewyświetlanych kontekstów, takich jak drukarki.

[CPaintDC](reference/cpaintdc-class.md)<br/>
Kontekst wyświetlania używany w `OnPaint` funkcjach składowych systemu Windows. Automatycznie wywołuje `BeginPaint` podczas tworzenia i `EndPaint` niszczenia.

[CClientDC —](reference/cclientdc-class.md)<br/>
Kontekst wyświetlania dla obszarów klienta systemu Windows. Używane na przykład do narysowania natychmiastowej odpowiedzi na zdarzenia myszy.

[CWindowDC](reference/cwindowdc-class.md)<br/>
Kontekst wyświetlania dla całego systemu Windows, w tym obszary klienta i nieklienckiego.

[CMetaFileDC](reference/cmetafiledc-class.md)<br/>
Kontekst urządzenia dla plików Windows. Metaplik systemu Windows zawiera sekwencję poleceń GDI (Graphics Device Interface), które mogą być odtwarzane w celu utworzenia obrazu. Wywołania wykonane do funkcji składowych a `CMetaFileDC` są rejestrowane w metapliku.

## <a name="related-classes"></a>Powiązane klasy

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Przechowuje pary współrzędnych (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Utrzymuje odległość, położenie względne lub sparowane wartości.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Utrzymuje współrzędne obszarów prostokątów.

[CRgn](reference/crgn-class.md)<br/>
Hermetyzuje region GDI na potrzeby manipulowania obszarem eliptycznym, wielobokówowym lub nieregularnym w oknie. Używane w połączeniu z przyciętymi elementami członkowskimi w klasie `CDC` .

[CRectTracker](reference/crecttracker-class.md)<br/>
Wyświetla i obsługuje interfejs użytkownika służący do zmiany rozmiarów i przesuwania prostokątnych obiektów.

[CColorDialog](reference/ccolordialog-class.md)<br/>
Udostępnia standardowe okno dialogowe do wybierania koloru.

[CFontDialog](reference/cfontdialog-class.md)<br/>
Udostępnia standardowe okno dialogowe do wybierania czcionki.

[CPrintDialog](reference/cprintdialog-class.md)<br/>
Udostępnia standardowe okno dialogowe do drukowania pliku.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
