---
title: Klasy okien dialogowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.dialog
dev_langs:
- C++
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60d33289d8025d7cdcaf4f6f69062230730b958c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351693"
---
# <a name="dialog-box-classes"></a>Klasy okien dialogowych
Klasa `CDialog` i pochodne Hermetyzowanie funkcji okno dialogowe. Ponieważ jest specjalnym rodzajem okna, okno dialogowe `CDialog` jest pochodną `CWnd`. Pochodzi z klasy okien dialogowych z `CDialog` lub użyj jednego z klasy wspólnych okien dialogowych dla standardowych oknach dialogowych, takich jak otwieranie lub zapisywanie pliku, drukowania, wybierając czcionek i kolorów, Inicjowanie operacji wyszukiwania i zamieniania lub przy użyciu różnych związane z mechanizmem OLE operacje.  
  
 [CDialog](../mfc/reference/cdialog-class.md)  
 Klasa podstawowa dla wszystkich okien dialogowych, zarówno modalne i niemodalne.  
  
 [CDataExchange](../mfc/reference/cdataexchange-class.md)  
 Udostępnia informacje o wymiana i Walidacja danych w oknach dialogowych.  
  
## <a name="common-dialogs"></a>Wspólne okna dialogowe  
 Te klasy okien dialogowych hermetyzacji wspólnych okien dialogowych systemu Windows. Udostępniają one implementacje łatwy w użyciu okien dialogowych skomplikowane.  
  
 [CCommonDialog](../mfc/reference/ccommondialog-class.md)  
 Klasa podstawowa dla wszystkich wspólne okna dialogowe.  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 Zawiera standardowe okno dialogowe Otwieranie lub zapisywanie pliku.  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 W tym temacie przedstawiono standardowe okno dialogowe wybierania koloru.  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 Udostępnia standardowego okna dialogowego wyboru czcionki.  
  
 [CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)  
 Zawiera standardowe okno dialogowe dla operacji wyszukiwania i zamieniania.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Zawiera standardowe okno dialogowe drukowania pliku.  
  
 [CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)  
 Udostępnia arkusz właściwości wydruku systemu Windows.  
  
 [CPageSetupDialog](../mfc/reference/cpagesetupdialog-class.md)  
 Hermetyzuje usług świadczonych przez okno dialogowe Ustawienia strony wspólne systemu Windows z obsługą dodatkowych ustawień i modyfikowania marginesów.  
  
## <a name="ole-common-dialogs"></a>Wspólne okna dialogowe OLE  
 OLE dodaje kilka wspólne okna dialogowe systemu Windows. Te klasy hermetyzacji wspólnych okien dialogowych OLE.  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 Używane przez platformę do przechowywania najczęściej występujące implementacje dla wszystkich okien dialogowych OLE. Wszystkie klasy okien dialogowych w kategorii interfejsu użytkownika są uzyskiwane z tej klasy podstawowej. `COleDialog` Nie można używać bezpośrednio.  
  
 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 Wyświetla okno dialogowe Wstaw obiekt standardowy interfejs użytkownika dla wstawiania nowych OLE połączone lub osadzone elementy.  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 Wyświetla okno dialogowe Wklej specjalne standardowy interfejs użytkownika dla wykonania polecenia Edytuj Wklej specjalne.  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 Wyświetla okno dialogowe Edytuj łącza standardowy interfejs użytkownika do modyfikowania informacji na temat połączone elementy.  
  
 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 Wyświetla okno dialogowe Zmienianie ikony, standardowy interfejs użytkownika dla zmiana, którą osadzonych ikon skojarzonych z OLE lub połączony element.  
  
 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 Wyświetla okno dialogowe Konwertowanie standardowy interfejs użytkownika do konwertowania elementy OLE z jednego typu.  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 Hermetyzuje okno dialogowe właściwości OLE wspólne systemu Windows. Wspólne okna dialogowe OLE właściwości umożliwiają łatwe do wyświetlanie i modyfikowanie właściwości elementu dokumentu OLE w sposób zgodny ze standardami systemu Windows.  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 Wyświetla okno dialogowe aktualizacji standardowy interfejs użytkownika aktualizacji wszystkich łączy w dokumencie. Okno dialogowe zawiera wskaźnik postępu, aby wskazać, jak blisko procedura aktualizacji zostanie do zakończenia.  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 Wyświetla okno dialogowe Zmienianie źródła standardowy interfejs użytkownika do zmiany docelowy lub źródłowy łącza.  
  
 [COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 Wyświetla oknach dialogowych serwer jest zajęty i serwer nie odpowiada, standardowy interfejs użytkownika do obsługi wywołań zajęty aplikacji. Zwykle wyświetlane automatycznie przez [COleMessageFilter](../mfc/reference/colemessagefilter-class.md) implementacji.  
  
## <a name="property-sheet-classes"></a>Klasy arkuszy właściwości  
 Klasy arkuszy właściwości Zezwalaj aplikacjom Użyj arkuszy właściwości, nazywane również z kartami okien dialogowych. Arkusze właściwości są wydajny sposób organizowania wielu formantów w oknie dialogowym pojedynczego.  
  
 [CPropertyPage](../mfc/reference/cpropertypage-class.md)  
 Udostępnia poszczególnych stron w arkuszu właściwości. Klasa wyprowadzona z `CPropertyPage` dla poszczególnych stron, które mają zostać dodane do Twojej arkusza właściwości.  
  
 [CPropertySheet](../mfc/reference/cpropertysheet-class.md)  
 Zawiera wiele stron właściwości ramki. Pochodzi z klasy arkusza właściwości `CPropertySheet` można szybko wdrożyć arkuszy właściwości.  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 Wyświetla właściwości OLE control interfejsu graficznego, podobnie do okna dialogowego.  
  
## <a name="html-based-dialog-classes"></a>Klasy oparte na języku HTML okien dialogowych  
 [CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)  
 Pozwala utworzyć okien dialogowych, które implementują interfejsu użytkownika z zasobami HTML zamiast okna dialogowego.  
  
 [CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)  
 Wyświetla wiele stron HTML sekwencyjnie i obsługuje zdarzenia z każdej strony.  
  
## <a name="related-classes"></a>Klasy pokrewne  
 Te klasy nie są okien dialogowych per se, ale korzystają z szablonów — okno dialogowe i mają podobne zachowania okien dialogowych.  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 Pasek sterowania, który jest oparty na szablonie — okno dialogowe.  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 Widok przewijania, którego układ jest zdefiniowany w szablonie — okno dialogowe. Klasa wyprowadzona z `CFormView` do zaimplementowania interfejsu użytkownika na podstawie szablonu — okno dialogowe.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Formularz zawiera widok podłączone bezpośrednio do obiektu zestawu rekordów obiekt DAO (Data Access). Wszystkie widoki formularzy, takich jak `CDaoRecordView` jest oparty na szablonie — okno dialogowe.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Formularz zawiera widok podłączone bezpośrednio do obiektu zestawu rekordów otwórz połączenie bazy danych (ODBC). Wszystkie widoki formularzy, takich jak `CRecordView` jest oparty na szablonie — okno dialogowe.  
  
 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)  
 Struktura zawierający informacje o zadaniu drukowania lub podglądu drukowania. Używane przez Architektura drukowania [CView](../mfc/reference/cview-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

