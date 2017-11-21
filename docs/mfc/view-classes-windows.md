---
title: "Wyświetlanie klas (system Windows) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.view
dev_langs: C++
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0148ead7a978389f763efbe9ee6306ec7a5839cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="view-classes-windows"></a>Klasy widoków (Windows)
`CView`i jej klas pochodnych są okno podrzędne, które reprezentują obszar kliencki okno ramowe. Widoki Pokaż dane i akceptuje dane wejściowe dla dokumentu.  
  
 Klasa widoku jest skojarzony z klasy dokumentów i klasy okna ramki za pomocą obiektu szablonu dokumentu.  
  
 [Cview —](../mfc/reference/cview-class.md)  
 Klasa podstawowa dla określonych aplikacji widoki danych dokumentu. Widoki wyświetlania danych i akceptowanie danych wejściowych użytkownika do edycji lub wybierz dane. Pochodzi z widoku klasy lub klas z `CView`.  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 Klasa podstawowa dla widoków z możliwości przewijania. Pochodzi z klasy widoku `CScrollView` przewijania automatycznego.  
  
## <a name="form-and-record-views"></a>Formularz i widoki rekordów  
 Widoki formularzy są również przewijanie widoków. Są one oparte na szablonie okno dialogowe.  
  
 Widoki rekordów są uzyskiwane z widoków formularza. Oprócz szablonu okno dialogowe również mieć połączenie z bazą danych.  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 Widok przewijania, którego układ jest zdefiniowany w szablonie — okno dialogowe. Klasa wyprowadzona z `CFormView` do zaimplementowania interfejsu użytkownika na podstawie szablonu — okno dialogowe.  
  
 [Cdaorecordview —](../mfc/reference/cdaorecordview-class.md)  
 Formularz zawiera widok podłączone bezpośrednio do obiektu zestawu rekordów obiekt DAO (Data Access). Wszystkie widoki formularzy, takich jak `CDaoRecordView` jest oparty na szablonie — okno dialogowe.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Formularz zawiera widok podłączone bezpośrednio do obiektu zestawu rekordów otwórz połączenie bazy danych (ODBC). Wszystkie widoki formularzy, takich jak `CRecordView` jest oparty na szablonie — okno dialogowe.  
  
 [CHtmlEditView](../mfc/reference/chtmleditview-class.md)  
 Widok formularz, który udostępnia funkcjonalność platformy edycji WebBrowser HTML.  
  
## <a name="control-views"></a>Widoki kontrolne  
 Widoki kontrolne wyświetlić formant jako ich widoku.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 Klasa podstawowa dla wszystkich widoków skojarzonych z formantów systemu Windows. Widoki oparte na formanty są opisane poniżej.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Formant edycji widoku, który zawiera standardowe systemu Windows (zobacz [CEdit](../mfc/reference/cedit-class.md)). Edytuj edycji tekstu pomocy technicznej formantów, wyszukiwanie, zastępowanie i przewijanie możliwości.  
  
 [Cricheditview —](../mfc/reference/cricheditview-class.md)  
 Formant edycji widok zawierający sformatowanego systemu Windows (zobacz [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Oprócz możliwości edycji edycji wzbogaconej formanty Obsługa czcionek, kolorów, formatowanie akapitów i osadzonych obiektów OLE.  
  
 [Clistview —](../mfc/reference/clistview-class.md)  
 Widok zawierający formant listy systemu Windows (zobacz [CListCtrl](../mfc/reference/clistctrl-class.md)). Formant listy Wyświetla kolekcję elementów, każdy zawiera ikonę i etykietę, w sposób podobny do prawego okienka Eksploratora plików.  
  
 [CTreeView —](../mfc/reference/ctreeview-class.md)  
 Widok, który zawiera kontrolki drzewa systemu Windows (zobacz [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Formant drzewa Wyświetla listę hierarchiczną ikony i etykiety ułożone w sposób podobny do okienka po lewej stronie Eksploratora plików.  
  
## <a name="related-classes"></a>Klasy pokrewne  
 `CSplitterWnd`pozwala mieć wiele widoków w ramach jednej ramki okna. `CPrintDialog`i `CPrintInfo` obsługi drukowania i podglądu wydruku widoków. `CRichEditDoc`i `CRichEditCntrItem` są używane z `CRichEditView` wdrożenia funkcji kontenera OLE.  
  
 [CSplitterWnd](../mfc/reference/csplitterwnd-class.md)  
 Okno użytkownika można podzielić na wiele okienek. Te okienka może być o zmiennym rozmiarze przez użytkownika lub o stałym rozmiarze.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Zawiera standardowe okno dialogowe drukowania pliku.  
  
 [Cprintinfo —](../mfc/reference/cprintinfo-structure.md)  
 Struktura zawierający informacje o zadaniu drukowania lub podglądu drukowania. Używane przez `CView`na drukowanie architektury.  
  
 [Cricheditdoc —](../mfc/reference/cricheditdoc-class.md)  
 Przechowuje listę elementów OLE klienta, które są w `CRichEditView`.  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 Umożliwia dostęp klienta do OLE elementu przechowywane w `CRichEditView`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

