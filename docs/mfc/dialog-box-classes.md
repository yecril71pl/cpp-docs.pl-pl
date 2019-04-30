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
ms.openlocfilehash: 5747e4450816b803f97ad5ff6338b9e01ad41bca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394614"
---
# <a name="dialog-box-classes"></a>Klasy okien dialogowych

Klasa `CDialog` i jej klasy pochodne hermetyzacji funkcji okno dialogowe. Ponieważ jest specjalnym rodzajem okna, okno dialogowe `CDialog` jest tworzony na podstawie `CWnd`. Pochodzi z klasy okien dialogowych z `CDialog` lub użyj jednego z klasy wspólnych okien dialogowych dla okien dialogowych standardowego, takich jak otwieranie lub zapisywanie pliku, drukowanie, zaznaczając, czcionek i kolorów, Inicjowanie operacji wyszukiwania i zamieniania lub wykonywanie różnych związane z mechanizmem OLE operacje.

[CDialog](../mfc/reference/cdialog-class.md)<br/>
Klasa bazowa dla wszystkich okien dialogowych, zarówno modalne i niemodalne.

[CDataExchange](../mfc/reference/cdataexchange-class.md)<br/>
Dostarcza informacje o wymiana i Walidacja danych dla okien dialogowych.

## <a name="common-dialogs"></a>Wspólne okna dialogowe

Te klasy okien dialogowych hermetyzować wspólne okna dialogowe Windows. Zapewniają one łatwe w użyciu implementacji okna dialogowe skomplikowane.

[CCommonDialog](../mfc/reference/ccommondialog-class.md)<br/>
Klasa bazowa dla wszystkich wspólne okna dialogowe.

[CFileDialog](../mfc/reference/cfiledialog-class.md)<br/>
Zawiera standardowe okno dialogowe Otwieranie lub zapisywanie pliku.

[CColorDialog](../mfc/reference/ccolordialog-class.md)<br/>
W tym temacie przedstawiono standardowe okno dialogowe wybierania kolorów.

[CFontDialog](../mfc/reference/cfontdialog-class.md)<br/>
W tym temacie przedstawiono standardowe okno dialogowe wybierania czcionki.

[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)<br/>
Zawiera standardowe okno dialogowe dla operacji wyszukiwania i zamieniania.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Zawiera standardowe okno dialogowe drukowania pliku.

[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)<br/>
Udostępnia arkusz własności drukowania Windows.

[CPageSetupDialog](../mfc/reference/cpagesetupdialog-class.md)<br/>
Hermetyzuje usługi świadczone przez wspólne okno dialogowe Ustawienia strony Windows z obsługą dodatkowgoe ustawienie i modyfikowania marginesów wydruku.

## <a name="ole-common-dialogs"></a>Wspólne okna dialogowe OLE

OLE dodaje kilka typowych okien dialogowych Windows. W ramach tych zajęć hermetyzować wspólne okna dialogowe OLE.

[COleDialog](../mfc/reference/coledialog-class.md)<br/>
Używane przez architekturę, aby zawierała najczęściej występujące implementacje dla wszystkich okien dialogowych OLE. Wszystkie klasy okien dialogowych w kategorii interfejsu użytkownika są uzyskiwane z tej klasy bazowej. `COleDialog` Nie można używać bezpośrednio.

[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)<br/>
Wyświetla okno dialogowe Wstawianie obiektu standardowy interfejs użytkownika, wstawianie nowych OLE połączone lub osadzone elementy.

[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)<br/>
Wyświetla okno dialogowe Wklej specjalne standardowy interfejs użytkownika wykonywania polecenia Edytuj Wklej specjalne.

[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)<br/>
Wyświetla okno dialogowe Edytuj linki standardowy interfejs użytkownika do modyfikowania informacji na temat połączone elementy.

[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)<br/>
Wyświetla okno dialogowe Zmienianie ikony, standardowy interfejs użytkownika dla zmiany, które osadzone ikon skojarzonych z OLE lub połączony element.

[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)<br/>
Wyświetla okno dialogowe Konwertowanie standardowy interfejs użytkownika do konwertowania jeden typ elementów OLE.

[COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)<br/>
Hermetyzuje wspólne okno dialogowe właściwości OLE Windows. Wspólne okna dialogowe OLE właściwości zapewniają prosty sposób wyświetlania i modyfikacji właściwości elementu dokumentu OLE w sposób zgodny ze standardami Windows.

[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)<br/>
Wyświetla okno dialogowe aktualizacji standardowy interfejs użytkownika aktualizacji wszystkie linki w dokumencie. Okno dialogowe zawiera wskaźnik postępu, aby wskazać, jak blisko procedura aktualizacji zostanie ukończone.

[COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)<br/>
Wyświetla okno dialogowe Zmień źródło standardowy interfejs użytkownika do zmiany przeznaczenia lub źródłem linku.

[COleBusyDialog](../mfc/reference/colebusydialog-class.md)<br/>
Wyświetla oknach dialogowych serwer jest zajęty i serwer nie odpowiada, standardowy interfejs użytkownika do obsługi wywołań zajęty aplikacji. Zwykle jest wyświetlany automatycznie przez [COleMessageFilter](../mfc/reference/colemessagefilter-class.md) implementacji.

## <a name="property-sheet-classes"></a>Klasy arkuszy właściwości

Klasy arkuszy właściwości umożliwia aplikacjom korzystać arkuszy właściwości, nazywane również z kartami w oknach dialogowych. Arkusze właściwości są wydajny sposób organizowania wielu formantów w oknie dialogowym pojedynczego.

[CPropertyPage](../mfc/reference/cpropertypage-class.md)<br/>
Udostępnia poszczególnych stron w arkuszu właściwości. Wyprowadzić klasę z `CPropertyPage` dla każdej strony, które mają zostać dodane do Twojego arkusza właściwości.

[CPropertySheet](../mfc/reference/cpropertysheet-class.md)<br/>
Zawiera wiele stron właściwości ramki. Pochodzi z klasy arkusza właściwości `CPropertySheet` szybko wdrożyć arkuszy właściwości.

[COlePropertyPage](../mfc/reference/colepropertypage-class.md)<br/>
Wyświetla właściwości OLE control w interfejsie graficznym, zbliżonym do okna dialogowego.

## <a name="html-based-dialog-classes"></a>Klasy oparte na języku HTML okien dialogowych

[CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)<br/>
Używane do utworzenia okien dialogowych, które implementują interfejsu użytkownika za pomocą kodu HTML, a nie w oknie dialogowym zasobów.

[CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)<br/>
Kolejno wyświetla wiele stron HTML i obsługuje zdarzenia z każdej strony.

## <a name="related-classes"></a>Klasy pokrewne

Te klasy nie są okna dialogowe per se, ale korzystanie z szablonów okno dialogowe i mają wiele zachowanie okien dialogowych.

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
Pasek sterowania, który jest oparty na szablonu okna dialogowego.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Widok przewijania, którego układ jest definiowany w szablonu okna dialogowego. Wyprowadzić klasę z `CFormView` do zaimplementowania interfejsu użytkownika, w oparciu o szablonu okna dialogowego.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Formularz zawiera widok podłączone bezpośrednio do obiektu recordset obiekt DAO (Data Access). Wszystkich widokach formularza, takie jak `CDaoRecordView` opiera się na szablonu okna dialogowego.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Formularz zawiera widok podłączone bezpośrednio do obiektu zestawu rekordów Open Database Connectivity (ODBC). Wszystkich widokach formularza, takie jak `CRecordView` opiera się na szablonu okna dialogowego.

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
Struktury zawierającej informacje o zadaniu drukowania lub drukowania (wersja zapoznawcza). Używane przez architekturę drukowania [CView](../mfc/reference/cview-class.md).

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../mfc/class-library-overview.md)
