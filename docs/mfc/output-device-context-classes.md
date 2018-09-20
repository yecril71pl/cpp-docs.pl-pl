---
title: Dane wyjściowe (kontekst urządzenia) klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.output
dev_langs:
- C++
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40b1406e8c788554d549ee1bdaa1adc21070d994
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373558"
---
# <a name="output-device-context-classes"></a>Klasy wyjściowe (kontekst urządzenia)

W ramach tych zajęć Hermetyzowanie różnych rodzajów konteksty urządzenia dostępne w Windows.

Większość następujące klasy hermetyzować dojścia do kontekstu urządzenia Windows. Kontekst urządzenia jest obiektem Windows, który zawiera informacje o atrybuty rysowania urządzenia, takie jak drukarka lub wyświetlania. Wszystkie wywołania rysowania są wykonywane za pośrednictwem obiektów kontekstu urządzenia. Dodatkowe klasy pochodne `CDC` hermetyzacji funkcje specjalne kontekstu urządzenia, w tym obsługa metapliki Windows.

[PRZECHWYTYWANIE ZMIAN DANYCH](../mfc/reference/cdc-class.md)<br/>
Klasa bazowa konteksty urządzenia. Używane bezpośrednio do uzyskania dostępu do całego ekranu oraz do uzyskiwania dostępu do nondisplay kontekstach, takich jak drukarki.

[CPaintDC](../mfc/reference/cpaintdc-class.md)<br/>
Używane w kontekście wyświetlania `OnPaint` funkcji elementów członkowskich systemu windows. Automatycznie wywołuje `BeginPaint` w konstrukcji i `EndPaint` w chwili zniszczenia.

[Cclientdc —](../mfc/reference/cclientdc-class.md)<br/>
Kontekst wyświetlania obszarów klienckich systemu windows. Używany, na przykład, aby narysować w natychmiastowej reakcji na zdarzenia myszy.

[CWindowDC](../mfc/reference/cwindowdc-class.md)<br/>
Kontekst wyświetlania dla całego systemu windows, w tym obszary zarówno klient, jak i nieklienckie.

[CMetaFileDC](../mfc/reference/cmetafiledc-class.md)<br/>
Kontekst urządzenia dla metapliki Windows. Metaplik Windows zawiera sekwencję poleceń interface (GDI) urządzenia grafiki, które można odtworzyć do utworzenia obrazu. Wywołania funkcji składowych `CMetaFileDC` są rejestrowane w metaplik.

## <a name="related-classes"></a>Klasy pokrewne

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Przechowują pary współrzędne (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Przechowuje odległość, położenie względne lub par wartości.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Zawiera współrzędne programu prostokątnych obszarów.

[CRgn](../mfc/reference/crgn-class.md)<br/>
Hermetyzuje region GDI do manipulowania obszar elipsy, wielokątne lub nieprawidłowo, w tym oknie. Używane w połączeniu z wycinka funkcje elementów członkowskich w klasie `CDC`.

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
Wyświetla i obsługuje interfejs użytkownika, zmienianie rozmiaru i przenoszenie obiektów prostokątny.

[CColorDialog](../mfc/reference/ccolordialog-class.md)<br/>
W tym temacie przedstawiono standardowe okno dialogowe wybierania kolorów.

[CFontDialog](../mfc/reference/cfontdialog-class.md)<br/>
W tym temacie przedstawiono standardowe okno dialogowe wybierania czcionki.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Zawiera standardowe okno dialogowe drukowania pliku.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

