---
title: Formanty (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
ms.openlocfilehash: 3155889f2fd4002286340ccec7f4a35d1a6a9c20
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508796"
---
# <a name="controls-mfc"></a>Formanty (MFC)

Formanty to obiekty, z którymi użytkownicy mogą korzystać w celu wprowadzania danych lub manipulowania nimi. Często pojawiają się one w oknach dialogowych lub na paskach narzędzi. Ta rodzina tematów obejmuje trzy główne rodzaje kontroli:

- Formanty standardowe systemu Windows, łącznie z kontrolkami rysowanymi przez właściciela

- Kontrolki ActiveX

- Inne klasy sterujące dostarczone przez biblioteka MFC (MFC)

## <a name="windows-common-controls"></a>Formanty standardowe systemu Windows

System operacyjny Windows zawsze dostarczył wiele standardowych formantów systemu Windows. Te obiekty sterujące są programowalne, a Edytor C++ okna dialogowego wizualizacji obsługuje dodawanie ich do okien dialogowych. Biblioteka MFC (MFC) dostarcza klasy, które hermetyzują poszczególne z tych kontrolek, jak pokazano w tabeli [typowe formanty systemu Windows i klasy MFC](#_core_windows_common_controls_and_mfc_classes). (Niektóre elementy w tabeli zawierają Tematy pokrewne, które w dalszej części opisują je. W przypadku kontrolek, które nie mają tematów, zobacz dokumentację klasy MFC.

Klasa [CWnd](../mfc/reference/cwnd-class.md) jest klasą bazową wszystkich klas okien, łącznie z wszystkimi klasami formantów.

## <a name="activex-controls"></a>Kontrolki ActiveX

Kontrolki ActiveX, wcześniej nazywane kontrolkami OLE, mogą być używane w oknach dialogowych aplikacji dla systemu Windows lub w stronach HTML na World Wide Web. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md).

## <a name="other-mfc-control-classes"></a>Inne klasy formantów MFC

Oprócz klas, które hermetyzują wszystkie formanty standardowe systemu Windows i obsługują programowanie własnych kontrolek ActiveX (lub Używanie formantów ActiveX dostarczonych przez inne osoby), MFC dostarcza następujące klasy kontroli:

- [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)

- [CCheckListBox](../mfc/reference/cchecklistbox-class.md)

- [CDragListBox](../mfc/reference/cdraglistbox-class.md)

##  <a name="_core_finding_information_about_windows_common_controls"></a>Znajdowanie informacji o typowych formantach systemu Windows

W poniższej tabeli przedstawiono krótki opis wszystkich formantów wspólnych systemu Windows, w tym klasy otoki MFC kontrolki.

### <a name="_core_windows_common_controls_and_mfc_classes"></a>Formanty standardowe systemu Windows i klasy MFC

|formant|Klasa MFC|Opis|Nowość w systemie Windows 95|
|-------------|---------------|-----------------|------------------------|
|[odtwarzania](../mfc/using-canimatectrl.md)|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Wyświetla kolejne klatki klipu wideo AVI|Tak|
|przycisk|[CButton](../mfc/reference/cbutton-class.md)|Skutki, które powodują akcję; używane również dla pól wyboru, przycisków radiowych i grup|Nie|
|pole kombi|[CComboBox](../mfc/reference/ccombobox-class.md)|Kombinacja pola edycji i pola listy|Nie|
|[Selektor daty i godziny](../mfc/using-cdatetimectrl.md)|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|Zezwala użytkownikowi na wybranie określonej wartości daty lub godziny|Tak|
|pole edycji|[CEdit](../mfc/reference/cedit-class.md)|Pola do wprowadzania tekstu|Nie|
|[rozszerzone pole kombi](../mfc/using-ccomboboxex.md)|[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)|Kontrolka pola kombi z możliwością wyświetlania obrazów|Tak|
|[header](../mfc/using-cheaderctrl.md)|[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)|Przycisk, który pojawia się powyżej kolumny tekstu; kontroluje szerokość wyświetlanego tekstu|Tak|
|[sekwencj](../mfc/using-chotkeyctrl.md)|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Okno, które umożliwia użytkownikowi tworzenie "klawisza gorąca", aby szybko wykonać akcję|Tak|
|[Lista obrazów](../mfc/using-cimagelist.md)|[CImageList](../mfc/reference/cimagelist-class.md)|Kolekcja obrazów używanych do zarządzania dużymi zestawami ikon lub map bitowych (lista obrazów nie jest w rzeczywistości kontrolką; obsługuje ona listy używane przez inne kontrolki).|Tak|
|[list](../mfc/using-clistctrl.md)|[CListCtrl](../mfc/reference/clistctrl-class.md)|Okno, w którym jest wyświetlana lista tekstów z ikonami|Tak|
|pole listy|[CListBox](../mfc/reference/clistbox-class.md)|Pole zawierające listę ciągów|Nie|
|[Kalendarz miesięczny](../mfc/using-cmonthcalctrl.md)|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|Kontrolka wyświetlająca informacje o dacie|Tak|
|[wykonywane](../mfc/using-cprogressctrl.md)|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Okno, które wskazuje postęp długotrwałej operacji|Tak|
|[paska pomocniczego](../mfc/using-crebarctrl.md)|[CRebarCtrl](../mfc/reference/crebarctrl-class.md)|Pasek narzędzi, który może zawierać dodatkowe okna podrzędne w formie formantów|Tak|
|[Edycja wzbogacona](../mfc/using-cricheditctrl.md)|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|Okno, w którym użytkownik może edytować za pomocą formatowania znaków i akapitów (zobacz [klasy związane z kontrolkami edycji wzbogaconej](../mfc/classes-related-to-rich-edit-controls.md))|Tak|
|pasek przewijania|[CScrollBar](../mfc/reference/cscrollbar-class.md)|Pasek przewijania używany jako formant wewnątrz okna dialogowego (nie w oknie)|Nie|
|[slider](../mfc/using-csliderctrl.md)|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|Okno zawierające kontrolkę suwaka z opcjonalnymi znacznikami osi|Tak|
|[przycisk pokrętła](../mfc/using-cspinbuttonctrl.md)|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Para przycisków strzałek, które użytkownik może kliknąć, aby zwiększyć lub zmniejszyć wartość|Tak|
|tekst statyczny|[CStatic](../mfc/reference/cstatic-class.md)|Tekst do etykietowania innych kontrolek|Nie|
|[pasek stanu](../mfc/using-cstatusbarctrl.md)|[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)|Okno do wyświetlania informacji o stanie, podobnie jak Klasa MFC`CStatusBar`|Tak|
|[tabulator](../mfc/using-ctabctrl.md)|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Analogiczne do dzielników w notesie; używane w "oknach dialogowych kart" lub arkuszach właściwości|Tak|
|[pasku narzędzi](../mfc/using-ctoolbarctrl.md)|[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)|Okno z przyciskami generującymi polecenia, podobnymi do klasy MFC`CToolBar`|Tak|
|[etykietka narzędzia](../mfc/using-ctooltipctrl.md)|[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)|Małe okno podręczne, które opisuje przeznaczenie przycisku paska narzędzi lub innego narzędzia|Tak|
|[drzewa](../mfc/using-ctreectrl.md)|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Okno, które wyświetla hierarchiczną listę elementów|Tak|

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- Indywidualny formant: zobacz tabelę [formanty wspólne systemu Windows i klasy MFC](#_core_windows_common_controls_and_mfc_classes) w tym temacie, aby uzyskać linki do wszystkich kontrolek

- [Tworzenie i używanie kontrolek](../mfc/making-and-using-controls.md)

- [Używanie edytora okien dialogowych do dodawania kontrolek](../mfc/using-the-dialog-editor-to-add-controls.md)

- [Ręczne dodawanie kontrolek do okna dialogowego](../mfc/adding-controls-by-hand.md)

- [Wyprowadzanie klas kontroli z klas formantów MFC](../mfc/deriving-controls-from-a-standard-control.md)

- [Używanie formantów wspólnych jako okien podrzędnych](../mfc/using-a-common-control-as-a-child-window.md)

- [Powiadomienia od formantów wspólnych](../mfc/receiving-notification-from-common-controls.md)

- [Dodaj typowe formanty do okna dialogowego](../mfc/using-common-controls-in-a-dialog-box.md).

- [Uzyskuje formant ze standardowego formantu systemu Windows](../mfc/deriving-controls-from-a-standard-control.md)

- [Kontrolki okna dialogowego dostępu z bezpieczeństwem typu](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Odbieraj komunikaty powiadomień z formantów wspólnych](../mfc/receiving-notification-from-common-controls.md)

- [Przykłady](../mfc/common-control-sample-list.md)

Aby uzyskać informacje o typowych kontrolkach systemu Windows w Windows SDK, zobacz temat [typowe formanty](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Zobacz także

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)<br/>
[Edytor okien dialogowych](../windows/dialog-editor.md)
