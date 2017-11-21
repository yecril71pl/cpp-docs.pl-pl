---
title: "Wyświetlanie klas (architektura) | Dokumentacja firmy Microsoft"
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
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 184245411f44a9aa9a6747adda0aafa5a8f68010
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="view-classes-architecture"></a>Klasy widoków (architektura)
`CView`i jej klas pochodnych są okno podrzędne, które reprezentują obszar kliencki okno ramowe. Widoki Pokaż dane i akceptuje dane wejściowe dla dokumentu.  
  
 Klasa widoku jest skojarzony z klasy dokumentów i klasy okna ramki za pomocą obiektu szablonu dokumentu.  
  
 [Cview —](../mfc/reference/cview-class.md)  
 Klasa podstawowa dla określonych aplikacji widoki danych dokumentu. Widoki wyświetlania danych i akceptowanie danych wejściowych użytkownika do edycji lub wybierz dane. Pochodzi z klasy widoku z `CView`.  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 Klasa podstawowa dla widoków z możliwości przewijania. Pochodzi z klasy widoku `CScrollView` przewijania automatycznego.  
  
## <a name="form-and-record-views"></a>Formularz i widoki rekordów  
 Widoki formularzy są również przewijanie widoków. Są one oparte na szablonie okno dialogowe.  
  
 Widoki rekordów są uzyskiwane z widoków formularza. Oprócz szablonu okno dialogowe również mieć połączenie z bazą danych.  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 Widok przewijania, którego układ jest zdefiniowany w szablonie — okno dialogowe. Klasa wyprowadzona z `CFormView` do zaimplementowania interfejsu użytkownika na podstawie szablonu — okno dialogowe.  
  
 [Cdaorecordview —](../mfc/reference/cdaorecordview-class.md)  
 Formularz zawiera widok podłączone bezpośrednio do obiektu zestawu rekordów obiekt DAO (Data Access). Wszystkie widoki formularzy, takich jak `CDaoRecordView` jest oparty na szablonie — okno dialogowe.  
  
 [CHtmlView](../mfc/reference/chtmlview-class.md)  
 Obsługuje formantu do przeglądania sieci Web w aplikacji. Formant obsługuje DHTML w MFC.  
  
 [Coledbrecordview —](../mfc/reference/coledbrecordview-class.md)  
 Zapewnia obsługę MFC OLE DB dla widoków formularza.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Formularz zawiera widok podłączone bezpośrednio do obiektu zestawu rekordów otwórz połączenie bazy danych (ODBC). Wszystkie widoki formularzy, takich jak `CRecordView` jest oparty na szablonie — okno dialogowe.  
  
## <a name="control-views"></a>Widoki kontrolne  
 Widoki kontrolne wyświetlić formant jako ich widoku.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 Klasa podstawowa dla wszystkich widoków skojarzonych z formantów systemu Windows. Widoki oparte na formanty są opisane poniżej.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Formant edycji widoku, który zawiera standardowe systemu Windows (zobacz [CEdit](../mfc/reference/cedit-class.md)). Edytuj edycji tekstu pomocy technicznej formantów, wyszukiwanie, zastępowanie i przewijanie możliwości.  
  
 [Cricheditview —](../mfc/reference/cricheditview-class.md)  
 Formant edycji widok zawierający sformatowanego systemu Windows (zobacz [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Oprócz możliwości edycji edycji wzbogaconej formanty Obsługa czcionek, kolorów, formatowanie akapitów i osadzonych obiektów OLE.  
  
 [Clistview —](../mfc/reference/clistview-class.md)  
 Widok zawierający formant listy systemu Windows (zobacz [CListCtrl](../mfc/reference/clistctrl-class.md)). Formant listy wyświetla ikony i ciągi w sposób podobny do prawego okienka Eksploratora plików.  
  
 [CTreeView —](../mfc/reference/ctreeview-class.md)  
 Widok, który zawiera kontrolki drzewa systemu Windows (zobacz [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Formant drzewa Wyświetla ikony i ciągi ułożone w hierarchii w sposób podobny do okienka po lewej stronie Eksploratora plików.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

