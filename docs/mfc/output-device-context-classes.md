---
title: "Dane wyjściowe (kontekst urządzenia) klasy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.output
dev_langs: C++
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db7080c263ee6e98d458381d59446263490dfd7a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="output-device-context-classes"></a>Klasy wyjściowe (kontekst urządzenia)
Te klasy Hermetyzowanie różnych typów konteksty urządzenia jest dostępna w systemie Windows.  
  
 Większość następujące klasy hermetyzować dojścia do kontekstu urządzenia z systemem Windows. Kontekst urządzenia jest obiekt systemu Windows, który zawiera informacje na temat atrybuty rysowania urządzeniami, takimi jak ekranu lub drukarki. Wszystkie wywołania rysowania są wykonywane za pośrednictwem obiektu kontekstu urządzenia. Dodatkowe klasy wyprowadzone z `CDC` Hermetyzowanie funkcje specjalne kontekst urządzenia, w tym obsługę metapliki systemu Windows.  
  
 [CDC](../mfc/reference/cdc-class.md)  
 Klasa podstawowa dla kontekstów urządzenia. Używany bezpośrednio w celu uzyskania dostępu do całej wyświetlana i uzyskiwania dostępu do kontekstów nondisplay, takie jak drukarki.  
  
 [Cpaintdc —](../mfc/reference/cpaintdc-class.md)  
 Używane w kontekście wyświetlania `OnPaint` funkcje Członkowskie systemu windows. Automatycznie wywołuje `BeginPaint` w konstrukcji i `EndPaint` w chwili zniszczenia.  
  
 [Cclientdc —](../mfc/reference/cclientdc-class.md)  
 Kontekst wyświetlania obszarów klienta systemu windows. Używany, na przykład do rysowania natychmiastowe odpowiedzi na zdarzenia myszy.  
  
 [CWindowDC](../mfc/reference/cwindowdc-class.md)  
 Kontekst wyświetlania dla całego systemu windows, w tym klienta i nieklienckim obszary.  
  
 [Cmetafiledc —](../mfc/reference/cmetafiledc-class.md)  
 Kontekst urządzenia metapliki systemu Windows. Windows metafile zawiera sekwencję grafiki urządzenia (GDI) interfejsu poleceń, które można odtworzyć do utworzenia obrazu. Wywołania funkcji Członkowskich `CMetaFileDC` są rejestrowane w metaplik.  
  
## <a name="related-classes"></a>Klasy pokrewne  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 Blokad pary współrzędne (x, y).  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 Przechowuje odległość, położenia lub par wartości.  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 Zawiera współrzędne obszary prostokątne.  
  
 [CRgn](../mfc/reference/crgn-class.md)  
 Hermetyzuje region GDI do manipulowania eliptycznej, wielokątne lub nieprawidłowo obszarze okna. Używane w połączeniu z wycinka funkcji elementów członkowskich w klasie `CDC`.  
  
 [Crecttracker —](../mfc/reference/crecttracker-class.md)  
 Wyświetla i obsługuje interfejs użytkownika do zmiany rozmiaru i przenoszenia prostokątne obiekty.  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 W tym temacie przedstawiono standardowe okno dialogowe wybierania koloru.  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 Udostępnia standardowego okna dialogowego wyboru czcionki.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Zawiera standardowe okno dialogowe drukowania pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

