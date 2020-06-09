---
title: Klasy okien dialogowych
ms.date: 11/04/2016
f1_keywords:
- vc.classes.dialog
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
ms.openlocfilehash: 2399b27fc081dcc810277079729b0e62ef80d603
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616942"
---
# <a name="dialog-box-classes"></a>Klasy okien dialogowych

Klasa `CDialog` i jej klasy pochodne hermetyzują funkcję okna dialogowego. Ponieważ okno dialogowe jest specjalnym rodzajem okna, pochodzi `CDialog` od `CWnd` . Utwórz klasy okien dialogowych z `CDialog` lub użyj jednej z wspólnych klas okna dialogowego dla standardowych okien dialogowych, takich jak otwieranie lub zapisywanie pliku, drukowanie, wybieranie czcionki lub koloru, inicjowanie operacji wyszukiwania i zamieniania lub wykonywanie różnych operacji związanych z OLE.

[CDialog](reference/cdialog-class.md)<br/>
Klasa bazowa dla wszystkich okien dialogowych, zarówno modalne, jak i niemodalne.

[CDataExchange](reference/cdataexchange-class.md)<br/>
Dostarcza informacje o wymianie danych i weryfikacji dla okien dialogowych.

## <a name="common-dialogs"></a>Wspólne okna dialogowe

Te klasy okna dialogowego hermetyzują wspólne okna dialogowe systemu Windows. Zapewniają one łatwą w użyciu implementacje skomplikowanych okien dialogowych.

[CCommonDialog](reference/ccommondialog-class.md)<br/>
Klasa bazowa dla wszystkich wspólnych okien dialogowych.

[CFileDialog](reference/cfiledialog-class.md)<br/>
Zawiera standardowe okno dialogowe umożliwiające otwarcie lub zapisanie pliku.

[CColorDialog](reference/ccolordialog-class.md)<br/>
Udostępnia standardowe okno dialogowe do wybierania koloru.

[CFontDialog](reference/cfontdialog-class.md)<br/>
Udostępnia standardowe okno dialogowe do wybierania czcionki.

[Okno CFindReplaceDialog](reference/cfindreplacedialog-class.md)<br/>
Udostępnia standardowe okno dialogowe dla operacji wyszukiwania i zamieniania.

[CPrintDialog](reference/cprintdialog-class.md)<br/>
Udostępnia standardowe okno dialogowe do drukowania pliku.

[CPrintDialogEx](reference/cprintdialogex-class.md)<br/>
Udostępnia arkusz właściwości drukowania systemu Windows.

[CPageSetupDialog](reference/cpagesetupdialog-class.md)<br/>
Hermetyzuje usługi zapewniane przez okno dialogowe Ustawienia typowej strony systemu Windows z dodatkową obsługą ustawiania i modyfikowania marginesów wydruku.

## <a name="ole-common-dialogs"></a>Wspólne okna dialogowe OLE

OLE dodaje kilka wspólnych okien dialogowych do systemu Windows. Te klasy hermetyzują wspólne okna dialogowe OLE.

[COleDialog](reference/coledialog-class.md)<br/>
Używane przez platformę do przechowywania wspólnych implementacji dla wszystkich okien dialogowych OLE. Wszystkie klasy okien dialogowych w kategorii interfejs użytkownika są wyprowadzane z tej klasy bazowej. `COleDialog`nie można używać bezpośrednio.

[COleInsertDialog](reference/coleinsertdialog-class.md)<br/>
Wyświetla okno dialogowe Wstawianie obiektu, standardowy interfejs użytkownika służący do wstawiania nowych połączonych lub osadzonych elementów OLE.

[COlePasteSpecialDialog](reference/colepastespecialdialog-class.md)<br/>
Wyświetla okno dialogowe wklejanie specjalne, standardowy interfejs użytkownika do implementowania polecenia Edytuj Wklej specjalnie.

[COleLinksDialog](reference/colelinksdialog-class.md)<br/>
Wyświetla okno dialogowe Edytowanie linków, standardowy interfejs użytkownika służący do modyfikowania informacji o połączonych elementach.

[COleChangeIconDialog](reference/colechangeicondialog-class.md)<br/>
Wyświetla okno dialogowe Zmień ikonę, standardowy interfejs użytkownika służący do zmiany ikony skojarzonej z elementem OLE osadzonym lub połączonym.

[COleConvertDialog](reference/coleconvertdialog-class.md)<br/>
Wyświetla okno dialogowe Konwersja, standardowy interfejs użytkownika służący do konwertowania elementów OLE z jednego typu na drugi.

[COlePropertiesDialog](reference/colepropertiesdialog-class.md)<br/>
Hermetyzuje okno dialogowe właściwości typowego interfejsu OLE systemu Windows. Okna dialogowe wspólne właściwości OLE zapewniają łatwy sposób wyświetlania i modyfikowania właściwości elementu dokumentu OLE w sposób zgodny ze standardami systemu Windows.

[COleUpdateDialog](reference/coleupdatedialog-class.md)<br/>
Wyświetla okno dialogowe Aktualizacja, standardowy interfejs użytkownika do aktualizowania wszystkich linków w dokumencie. Okno dialogowe zawiera wskaźnik postępu, aby wskazać, w jaki sposób zamykana jest procedura aktualizacji.

[COleChangeSourceDialog](reference/colechangesourcedialog-class.md)<br/>
Wyświetla okno dialogowe Zmień źródło, standardowy interfejs użytkownika służący do zmiany miejsca docelowego lub źródła łącza.

[COleBusyDialog](reference/colebusydialog-class.md)<br/>
Wyświetla okna dialogowe zajęty serwer i serwer nie odpowiada, standardowy interfejs użytkownika do obsługi wywołań do zajętych aplikacji. Zwykle jest automatycznie wyświetlana przez implementację [COleMessageFilter](reference/colemessagefilter-class.md) .

## <a name="property-sheet-classes"></a>Klasy arkuszy właściwości

Klasy arkuszy właściwości umożliwiają aplikacjom korzystanie z arkuszy właściwości, znanych również jako okna dialogowe z kartami. Arkusze właściwości to wydajny sposób organizowania dużej liczby kontrolek w jednym oknie dialogowym.

[CPropertyPage](reference/cpropertypage-class.md)<br/>
Udostępnia poszczególne strony w arkuszu właściwości. Utwórz klasę z `CPropertyPage` dla każdej strony, która ma zostać dodana do arkusza właściwości.

[CPropertySheet](reference/cpropertysheet-class.md)<br/>
Udostępnia ramkę dla wielu stron właściwości. Utwórz klasę arkusza właściwości z `CPropertySheet` , aby szybko zaimplementować arkusze właściwości.

[COlePropertyPage](reference/colepropertypage-class.md)<br/>
Wyświetla właściwości kontrolki OLE w interfejsie graficznym podobnym do okna dialogowego.

## <a name="html-based-dialog-classes"></a>Klasy okien dialogowych opartych na języku HTML

[CDHtmlDialog](reference/cdhtmldialog-class.md)<br/>
Służy do tworzenia okien dialogowych, które implementują interfejs użytkownika przy użyciu języka HTML, a nie zasobów okna dialogowego.

[CMultiPageDHtmlDialog](reference/cmultipagedhtmldialog-class.md)<br/>
Wyświetla wiele stron HTML sekwencyjnie i obsługuje zdarzenia z poszczególnych stron.

## <a name="related-classes"></a>Powiązane klasy

Te klasy nie są okna dialogowe na SE, ale używają szablonów okien dialogowych i ma wiele zachowań okien dialogowych.

[CDialogBar](reference/cdialogbar-class.md)<br/>
Pasek sterowania, który jest oparty na szablonie okna dialogowego.

[CFormView](reference/cformview-class.md)<br/>
Widok przewijania, którego układ jest zdefiniowany w szablonie okna dialogowego. Utwórz klasę z `CFormView` , aby zaimplementować interfejs użytkownika w oparciu o szablon okna dialogowego.

[CDaoRecordView](reference/cdaorecordview-class.md)<br/>
Udostępnia widok formularza bezpośrednio połączony z obiektem zestawu rekordów obiektu dostępu do danych (DAO). Podobnie jak w przypadku wszystkich widoków formularzy, `CDaoRecordView` jest oparty na szablonie okna dialogowego.

[Formularzy CRecordView](reference/crecordview-class.md)<br/>
Udostępnia widok formularza połączony bezpośrednio z obiektem zestawu rekordów Open Database Connectivity (ODBC). Podobnie jak w przypadku wszystkich widoków formularzy, `CRecordView` jest oparty na szablonie okna dialogowego.

[CPrintInfo](reference/cprintinfo-structure.md)<br/>
Struktura zawierająca informacje o zadaniu drukowania lub podglądu wydruku. Używany przez architekturę drukowania [CView](reference/cview-class.md).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
