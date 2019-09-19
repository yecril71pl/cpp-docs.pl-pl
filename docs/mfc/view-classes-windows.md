---
title: Klasy widoków (Windows)
ms.date: 09/17/2019
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
ms.openlocfilehash: f3e9ea2ebf3eb0ce04fde0339aaf0243686248a9
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096041"
---
# <a name="view-classes-windows"></a>Klasy widoków (Windows)

`CView`i jej klasy pochodne są oknami podrzędnymi, które reprezentują obszar klienta okna ramki. Widoki wyświetlają dane i akceptują dane wejściowe dla dokumentu.

Klasa widoku jest skojarzona z klasą dokumentu i klasą okna ramowego przy użyciu obiektu szablonu dokumentu.

[CView](../mfc/reference/cview-class.md)<br/>
Klasa bazowa dla widoków specyficznych dla aplikacji w danych dokumentu. Wyświetla dane i akceptują dane wejściowe użytkownika w celu edytowania lub zaznaczania danych. Utwórz klasę widoku lub klasy z `CView`.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
Klasa bazowa dla widoków z możliwościami przewijania. Utwórz klasę widoku od `CScrollView` do automatycznego przewijania.

## <a name="form-and-record-views"></a>Widoki formularzy i rekordów

Widoki formularzy są również przewijane. Są one oparte na szablonie okna dialogowego.

Widoki rekordów są wyprowadzane z widoków formularza. Oprócz szablonu okna dialogowego mają także połączenie z bazą danych.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Widok przewijania, którego układ jest zdefiniowany w szablonie okna dialogowego. Utwórz klasę z `CFormView` , aby zaimplementować interfejs użytkownika w oparciu o szablon okna dialogowego.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Udostępnia widok formularza bezpośrednio połączony z obiektem zestawu rekordów obiektu dostępu do danych (DAO). Podobnie jak w przypadku wszystkich widoków `CDaoRecordView` formularzy, jest oparty na szablonie okna dialogowego. Obiekty DAO są używane z bazami danych programu Access i są obsługiwane za pomocą pakietu Office 2013. 3,6 jest wersją ostateczną i jest uznawana za przestarzałą.

[Formularzy CRecordView](../mfc/reference/crecordview-class.md)<br/>
Udostępnia widok formularza połączony bezpośrednio z obiektem zestawu rekordów Open Database Connectivity (ODBC). Podobnie jak w przypadku wszystkich widoków `CRecordView` formularzy, jest oparty na szablonie okna dialogowego.

[CHtmlEditView](../mfc/reference/chtmleditview-class.md)<br/>
Widok formularza, który zapewnia funkcjonalność platformy edycji HTML przeglądarki WebBrowser.

## <a name="control-views"></a>Widoki formantów

Widoki formantów wyświetlają formant jako widok.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Klasa bazowa dla wszystkich widoków skojarzonych z kontrolkami systemu Windows. Poniżej opisano widoki oparte na kontrolkach.

[Elementu CEditView](../mfc/reference/ceditview-class.md)<br/>
Widok, który zawiera kontrolkę edycji standardowej systemu Windows (zobacz [CEdit](../mfc/reference/cedit-class.md)). Kontrolki edycji obsługują edytowanie tekstu, wyszukiwanie, zastępowanie i przewijanie.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Widok, który zawiera kontrolkę zaawansowanej edycji systemu Windows (zobacz [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Oprócz możliwości kontrolki edycji, formanty edycji wzbogaconej obsługują czcionki, kolory, formatowanie akapitu i osadzone obiekty OLE.

[CListView](../mfc/reference/clistview-class.md)<br/>
Widok zawierający formant listy systemu Windows (zobacz [CListCtrl](../mfc/reference/clistctrl-class.md)). Kontrolka listy wyświetla kolekcję elementów, z których każda składa się z ikony i etykiety, w sposób podobny do prawego okienka Eksploratora plików.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Widok, który zawiera kontrolkę drzewa systemu Windows (zobacz [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Kontrolka drzewa wyświetla hierarchiczną listę ikon i etykiet ułożone w sposób podobny do lewego okienka Eksploratora plików.

## <a name="related-classes"></a>Powiązane klasy

`CSplitterWnd`umożliwia korzystanie z wielu widoków w jednym oknie ramek. `CPrintDialog`i `CPrintInfo` obsługują Podgląd drukowania i podglądu wydruku w widokach. `CRichEditDoc`i `CRichEditCntrItem` są używane z `CRichEditView` programem w celu zaimplementowania funkcji kontenera OLE.

[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)<br/>
Okno, które użytkownik może podzielić na wiele okienek. Rozmiary tych okienek można zmieniać przez użytkownika lub stały rozmiar.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Udostępnia standardowe okno dialogowe do drukowania pliku.

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
Struktura zawierająca informacje o zadaniu drukowania lub podglądu wydruku. Używany przez `CView`architekturę drukowania.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Zachowuje listę elementów klienta OLE, które znajdują się w `CRichEditView`.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Zapewnia dostęp po stronie klienta do elementu OLE przechowywanego w `CRichEditView`.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../mfc/class-library-overview.md)
