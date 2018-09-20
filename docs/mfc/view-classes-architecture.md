---
title: Wyświetl klasy (architektura) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.view
dev_langs:
- C++
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12987a7563b685018de64201d60d0447d3a5d4cc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393824"
---
# <a name="view-classes-architecture"></a>Klasy widoków (architektura)

`CView` i jej klasy pochodne są okien podrzędnych, które reprezentują obszaru klienckiego okna ramki. Widoki Pokaż dane i akceptuje dane wejściowe dla dokumentu.

Klasa widoku jest skojarzony z klasy dokumentów i klasę okna ramowego, za pomocą obiektu szablonu dokumentu.

[CView](../mfc/reference/cview-class.md)<br/>
Klasa bazowa dla określonych aplikacji widoków danych dokumentu. Widoki wyświetlania danych i akceptuje dane wejściowe użytkownika, aby edytować, lub wybierz dane. Pochodzi swojej klasy widoku z `CView`.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
Klasa bazowa dla widoków z możliwościami przewijania. Pochodzi z klasy widoku `CScrollView` automatycznego przewijania.

## <a name="form-and-record-views"></a>Formularz i widoków rekordów

Widoki formularzy są również przewijanie widoków. Są one oparte na szablonu okna dialogowego.

Widoki rekordów są uzyskiwane z Widoki formularzy. Oprócz szablonu okna dialogowego również mają połączenie z bazą danych.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Widok przewijania, którego układ jest definiowany w szablonu okna dialogowego. Wyprowadzić klasę z `CFormView` do zaimplementowania interfejsu użytkownika, w oparciu o szablonu okna dialogowego.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Formularz zawiera widok podłączone bezpośrednio do obiektu recordset obiekt DAO (Data Access). Wszystkich widokach formularza, takie jak `CDaoRecordView` opiera się na szablonu okna dialogowego.

[CHtmlView](../mfc/reference/chtmlview-class.md)<br/>
Obsługuje formant przeglądania sieci Web w obrębie aplikacji. Są obsługiwane przez kontrolkę dynamicznego HTML w MFC.

[COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)<br/>
Zapewnia obsługę MFC OLE DB w widokach formularza.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Formularz zawiera widok podłączone bezpośrednio do obiektu zestawu rekordów Open Database Connectivity (ODBC). Wszystkich widokach formularza, takie jak `CRecordView` opiera się na szablonu okna dialogowego.

## <a name="control-views"></a>Widoki kontrolne

Widoki kontrolne wyświetlany formantu jako swój widok.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Klasa bazowa dla wszystkich widoków związane z formantami Windows. Widoki oparte na formanty są opisane poniżej.

[Elementu CEditView](../mfc/reference/ceditview-class.md)<br/>
Widok, który zawiera standardowy Windows formantu edycyjnego (zobacz [CEdit](../mfc/reference/cedit-class.md)). Edytuj edycji tekstu pomocy technicznej formantów, wyszukiwanie, zastępowanie i możliwościami przewijania.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Widok, który zawiera bogaty Windows formantu edycyjnego (zobacz [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Oprócz możliwości formant edycji edycji wzbogaconej formantów Obsługa czcionek, kolorów, formatowanie akapitów i osadzonych obiektów OLE.

[CListView](../mfc/reference/clistview-class.md)<br/>
Widok, który zawiera kontrolkę listy Windows (zobacz [CListCtrl](../mfc/reference/clistctrl-class.md)). Kontrolka listy wyświetla ikon i ciągów w sposób podobny do prawego okienka Eksploratora plików.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Widok, który zawiera formant drzewa Windows (zobacz [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Kontrolka drzewa Wyświetla ikon i ciągów ułożone w hierarchii w sposób podobny do okienka po lewej stronie Eksploratora plików.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

