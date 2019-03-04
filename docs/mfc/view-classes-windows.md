---
title: Klasy widoków (Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
ms.openlocfilehash: ad58fd6fa2548c2cf320baf75b8fc33a835ddd55
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267098"
---
# <a name="view-classes-windows"></a>Klasy widoków (Windows)

`CView` i jej klasy pochodne są okien podrzędnych, które reprezentują obszaru klienckiego okna ramki. Widoki Pokaż dane i akceptuje dane wejściowe dla dokumentu.

Klasa widoku jest skojarzony z klasy dokumentów i klasę okna ramowego, za pomocą obiektu szablonu dokumentu.

[CView](../mfc/reference/cview-class.md)<br/>
Klasa bazowa dla określonych aplikacji widoków danych dokumentu. Widoki wyświetlania danych i akceptuje dane wejściowe użytkownika, aby edytować, lub wybierz dane. Pochodzi z widoku klasy lub klas z `CView`.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
Klasa bazowa dla widoków z możliwościami przewijania. Pochodzi z klasy widoku `CScrollView` automatycznego przewijania.

## <a name="form-and-record-views"></a>Formularz i widoków rekordów

Widoki formularzy są również przewijanie widoków. Są one oparte na szablonu okna dialogowego.

Widoki rekordów są uzyskiwane z Widoki formularzy. Oprócz szablonu okna dialogowego również mają połączenie z bazą danych.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Widok przewijania, którego układ jest definiowany w szablonu okna dialogowego. Wyprowadzić klasę z `CFormView` do zaimplementowania interfejsu użytkownika, w oparciu o szablonu okna dialogowego.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Formularz zawiera widok podłączone bezpośrednio do obiektu recordset obiekt DAO (Data Access). Wszystkich widokach formularza, takie jak `CDaoRecordView` opiera się na szablonu okna dialogowego.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Formularz zawiera widok podłączone bezpośrednio do obiektu zestawu rekordów Open Database Connectivity (ODBC). Wszystkich widokach formularza, takie jak `CRecordView` opiera się na szablonu okna dialogowego.

[CHtmlEditView](../mfc/reference/chtmleditview-class.md)<br/>
Widok formularza, który udostępnia funkcjonalność platformy edycji WebBrowser w formacie HTML.

## <a name="control-views"></a>Widoki kontrolne

Widoki kontrolne wyświetlany formantu jako swój widok.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Klasa bazowa dla wszystkich widoków związane z formantami Windows. Widoki oparte na formanty są opisane poniżej.

[Elementu CEditView](../mfc/reference/ceditview-class.md)<br/>
Widok, który zawiera standardowy Windows formantu edycyjnego (zobacz [CEdit](../mfc/reference/cedit-class.md)). Edytuj edycji tekstu pomocy technicznej formantów, wyszukiwanie, zastępowanie i możliwościami przewijania.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Widok, który zawiera bogaty Windows formantu edycyjnego (zobacz [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Oprócz możliwości formant edycji edycji wzbogaconej formantów Obsługa czcionek, kolorów, formatowanie akapitów i osadzonych obiektów OLE.

[CListView](../mfc/reference/clistview-class.md)<br/>
Widok, który zawiera kontrolkę listy Windows (zobacz [CListCtrl](../mfc/reference/clistctrl-class.md)). Kontrolka listy wyświetla zbiór elementów składających się z ikony oraz etykiety, w sposób podobny do prawego okienka Eksploratora plików.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Widok, który zawiera formant drzewa Windows (zobacz [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Kontrolka drzewa Wyświetla listę hierarchiczną ikony oraz etykiety ułożone w sposób podobny do okienka po lewej stronie Eksploratora plików.

## <a name="related-classes"></a>Klasy pokrewne

`CSplitterWnd` można mieć wiele widoków, w ramach jednej ramki okna. `CPrintDialog` i `CPrintInfo` obsługuje drukowanie i Podgląd wydruku widoków. `CRichEditDoc` i `CRichEditCntrItem` są używane wraz z `CRichEditView` do zaimplementowania możliwości kontenerów OLE.

[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)<br/>
Okno, które użytkownik może być podzielony na wiele okienek. Te okienka może być zmieniana przez użytkownika lub o stałym rozmiarze.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Zawiera standardowe okno dialogowe drukowania pliku.

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
Struktury zawierającej informacje o zadaniu drukowania lub drukowania (wersja zapoznawcza). Używane przez `CView`na drukowanie architektury.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Przechowuje listę elementów klienta OLE, które znajdują się w `CRichEditView`.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Zapewnia dostęp klienta do elementu przechowywanego w OLE `CRichEditView`.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../mfc/class-library-overview.md)
