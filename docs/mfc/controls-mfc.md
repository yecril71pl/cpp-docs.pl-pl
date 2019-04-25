---
title: Formanty (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
ms.openlocfilehash: c0738128d20839046e0885e7489b494d84349e4d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297271"
---
# <a name="controls-mfc"></a>Formanty (MFC)

Formanty są obiekty, które użytkownicy mogą wchodzić w interakcje z wprowadzać ani wykonywać operacje na danych. Często pojawiają się w oknach dialogowych lub na paskach narzędzi. Ten temat rodziny obejmuje trzy główne rodzaje formantów:

- Wspólnych formantów Windows, w tym formanty rysowane przez właściciela

- Kontrolki ActiveX

- Inne klasy kontrolek dostarczony przez Microsoft Foundation Class Library (MFC)

## <a name="windows-common-controls"></a>Typowe kontrolki Windows

System operacyjny Windows zawsze oferowała szereg wspólnych formantów Windows. Obiekty te kontrolki są programowalne, a Edytor okien dialogowych Visual C++ obsługuje, dodając je do swojej okien dialogowych. Biblioteka Microsoft Foundation Class (MFC) dostarcza klas, które zapewniają każdego z tych kontrolek, jak pokazano w tabeli [wspólnych formantów Windows i klasy MFC](#_core_windows_common_controls_and_mfc_classes). (Niektóre elementy w tabeli z powiązanymi tematów opisujących je dalej. Dla formantów, które nie mają tematów zobacz dokumentację klasy MFC).

Klasa [CWnd](../mfc/reference/cwnd-class.md) jest klasą bazową wszystkich klas okna, w tym wszystkie klasy kontrolki.

## <a name="activex-controls"></a>Kontrolki ActiveX

Kontrolki ActiveX, znana wcześniej jako formantów OLE może służyć w oknach dialogowych w swoich aplikacjach dla Windows lub w formacie HTML stron w sieci World Wide Web. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md).

## <a name="other-mfc-control-classes"></a>Innych klas formantów biblioteki MFC

Oprócz klas, które zapewniają wszystkich wspólnych formantów Windows i tej obsługi programowania własnych kontrolek ActiveX (lub korzystanie z kontrolek ActiveX dostarczane przez inne osoby) MFC dostarcza następujące klasy formantu własnych:

- [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)

- [CCheckListBox](../mfc/reference/cchecklistbox-class.md)

- [CDragListBox](../mfc/reference/cdraglistbox-class.md)

##  <a name="_core_finding_information_about_windows_common_controls"></a> Znajdowanie informacji o wspólnych formantów Windows

W poniższej tabeli krótko opisano każdy wspólnych formantów Windows, łącznie z klasy otoki MFC formantu.

### <a name="_core_windows_common_controls_and_mfc_classes"></a>  Typowe kontrolki Windows i klasy MFC

|formant|Klasy MFC|Opis|Nowość w wersji Windows 95|
|-------------|---------------|-----------------|------------------------|
|[Animacja](../mfc/using-canimatectrl.md)|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Wyświetla kolejnych klatek AVI klipu wideo|Tak|
|Przycisk|[CButton](../mfc/reference/cbutton-class.md)|Przyciski, które powodują akcję; używane również do pola wyboru, przyciski radiowe i pola grupy|Nie|
|pole kombi|[CComboBox](../mfc/reference/ccombobox-class.md)|Kombinacja pole edycji i pole listy|Nie|
|[Wybór daty i godziny](../mfc/using-cdatetimectrl.md)|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|Umożliwia użytkownikowi wybierz określoną datę lub godzinę|Yes|
|Pole edycji|[CEdit](../mfc/reference/cedit-class.md)|Pola wprowadzania tekstu|Nie|
|[pole kombi rozszerzone](../mfc/using-ccomboboxex.md)|[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)|Kontrolka pola kombi, możliwość wyświetlania obrazów|Tak|
|[header](../mfc/using-cheaderctrl.md)|[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)|Przycisk, który pojawia się powyżej kolumny tekstu. Określa szerokość wyświetlanego tekstu|Tak|
|[hotkey](../mfc/using-chotkeyctrl.md)|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Okno, który umożliwia użytkownikowi utworzenie "klawisza dostępu" szybko wykonać akcję|Yes|
|[listy obrazów](../mfc/using-cimagelist.md)|[CImageList](../mfc/reference/cimagelist-class.md)|Kolekcja obrazów, używane do zarządzania dużymi zestawami ikony lub mapy bitowe (listy obrazów nie jest tak naprawdę kontrolki; obsługuje używane przez inne formanty listy)|Tak|
|[list](../mfc/using-clistctrl.md)|[CListCtrl](../mfc/reference/clistctrl-class.md)|Okno, które wyświetla listę wartości tekstowych z ikonami|Yes|
|Pole listy|[CListBox](../mfc/reference/clistbox-class.md)|Pole, które zawiera listę ciągów|Nie|
|[Kalendarza miesięcznego](../mfc/using-cmonthcalctrl.md)|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|Formant, który wyświetla informacje o dacie|Tak|
|[progress](../mfc/using-cprogressctrl.md)|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Okno, które wskazuje postęp długotrwałej operacji|Tak|
|[paska pomocniczego](../mfc/using-crebarctrl.md)|[CRebarCtrl](../mfc/reference/crebarctrl-class.md)|Pasek narzędzi, który może zawierać dodatkowe elementu podrzędnym MDI w formie formantów|Tak|
|[Edycji wzbogaconej](../mfc/using-cricheditctrl.md)|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|Okno w użytkownika, który można edytować przy użyciu znaku i formatowanie akapitów (zobacz [klasy pokrewne formanty edycji wzbogaconej](../mfc/classes-related-to-rich-edit-controls.md))|Tak|
|pasek przewijania|[CScrollBar](../mfc/reference/cscrollbar-class.md)|Pasek przewijania służyć jako metoda kontrolowania wewnątrz okno dialogowe, (a nie w oknie)|Nie|
|[slider](../mfc/using-csliderctrl.md)|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|Okno zawierające kontrolki suwaka z opcjonalnymi znaczniki|Tak|
|[przycisk pokrętła](../mfc/using-cspinbuttonctrl.md)|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Para użytkownika przycisków strzałek kliknąć na Przyrostowy lub zmniejszanie wartości|Yes|
|tekst statyczny|[CStatic](../mfc/reference/cstatic-class.md)|Tekst dla innych formantów etykiet|Nie|
|[Pasek stanu](../mfc/using-cstatusbarctrl.md)|[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)|Okno do wyświetlania informacji o stanie, podobny do klasy MFC `CStatusBar`|Tak|
|[Karta](../mfc/using-ctabctrl.md)|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Odpowiednikiem separatorów w notesie; używane w "zakładki okna dialogowego" lub arkusze właściwości|Tak|
|[Pasek narzędzi](../mfc/using-ctoolbarctrl.md)|[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)|Okno w generowaniu polecenia przycisków, podobny do klasy MFC `CToolBar`|Tak|
|[Etykietka narzędzia](../mfc/using-ctooltipctrl.md)|[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)|Niewielkie okno podręczne, opisujący przeznaczenie przycisku paska narzędzi lub innemu narzędziu|Tak|
|[tree](../mfc/using-ctreectrl.md)|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Okno, które wyświetla hierarchiczną listę elementów|Tak|

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- Poszczególnych kontrolek: znajdują się w tabeli [wspólnych formantów Windows i klasy MFC](#_core_windows_common_controls_and_mfc_classes) tego tematu zawiera linki do wszystkich formantów

- [Tworzenie i używanie formantów](../mfc/making-and-using-controls.md)

- [Używanie edytora okien dialogowych do dodawania formantów](../mfc/using-the-dialog-editor-to-add-controls.md)

- [Ręczne dodawanie formantów do okna dialogowego](../mfc/adding-controls-by-hand.md)

- [Wyprowadzanie klasy kontrolek z klas formantów biblioteki MFC](../mfc/deriving-controls-from-a-standard-control.md)

- [Używanie formantów wspólnych jako okien podrzędnych](../mfc/using-a-common-control-as-a-child-window.md)

- [Powiadomienia od formantów wspólnych](../mfc/receiving-notification-from-common-controls.md)

- [Dodawanie formantów wspólnych w oknie dialogowym](../mfc/using-common-controls-in-a-dialog-box.md).

- [Pochodzi kontrolki z formantu standardowego Windows](../mfc/deriving-controls-from-a-standard-control.md)

- [Dostęp do formantów okno dialogowe z bezpieczeństwo typów](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Odbieranie powiadomienia od formantów wspólnych](../mfc/receiving-notification-from-common-controls.md)

- [Przykłady](../mfc/common-control-sample-list.md)

Aby uzyskać informacje o wspólnych formantów Windows w zestawie Windows SDK, zobacz [wspólnych formantów](/windows/desktop/Controls/common-controls-intro).

## <a name="see-also"></a>Zobacz także

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)<br/>
[Edytor okien dialogowych](../windows/dialog-editor.md)
