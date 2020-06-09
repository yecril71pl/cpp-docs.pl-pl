---
title: Formanty (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
ms.openlocfilehash: accbee66cdee4e7b849da2b034d253b1c206d8f1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617181"
---
# <a name="controls-mfc"></a>Formanty (MFC)

Formanty to obiekty, z którymi użytkownicy mogą korzystać w celu wprowadzania danych lub manipulowania nimi. Często pojawiają się one w oknach dialogowych lub na paskach narzędzi. Ta rodzina tematów obejmuje trzy główne rodzaje kontroli:

- Formanty standardowe systemu Windows, łącznie z kontrolkami rysowanymi przez właściciela

- Kontrolki ActiveX

- Inne klasy sterujące dostarczone przez biblioteka MFC (MFC)

## <a name="windows-common-controls"></a>Formanty standardowe systemu Windows

System operacyjny Windows zawsze dostarczył wiele standardowych formantów systemu Windows. Te obiekty sterujące są programowalne, a Edytor okna dialogowego Visual C++ obsługuje dodawanie ich do okien dialogowych. Biblioteka MFC (MFC) dostarcza klasy, które hermetyzują poszczególne z tych kontrolek, jak pokazano w tabeli [typowe formanty systemu Windows i klasy MFC](#_core_windows_common_controls_and_mfc_classes). (Niektóre elementy w tabeli zawierają Tematy pokrewne, które w dalszej części opisują je. W przypadku kontrolek, które nie mają tematów, zobacz dokumentację klasy MFC.

Klasa [CWnd](reference/cwnd-class.md) jest klasą bazową wszystkich klas okien, łącznie z wszystkimi klasami formantów.

## <a name="activex-controls"></a>Kontrolki ActiveX

Kontrolki ActiveX, wcześniej nazywane kontrolkami OLE, mogą być używane w oknach dialogowych aplikacji dla systemu Windows lub w stronach HTML na World Wide Web. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC](mfc-activex-controls.md).

## <a name="other-mfc-control-classes"></a>Inne klasy formantów MFC

Oprócz klas, które hermetyzują wszystkie formanty standardowe systemu Windows i obsługują programowanie własnych kontrolek ActiveX (lub Używanie formantów ActiveX dostarczonych przez inne osoby), MFC dostarcza następujące klasy kontroli:

- [CBitmapButton](reference/cbitmapbutton-class.md)

- [CCheckListBox](reference/cchecklistbox-class.md)

- [CDragListBox](reference/cdraglistbox-class.md)

## <a name="finding-information-about-windows-common-controls"></a><a name="_core_finding_information_about_windows_common_controls"></a>Znajdowanie informacji o typowych formantach systemu Windows

W poniższej tabeli przedstawiono krótki opis wszystkich formantów wspólnych systemu Windows, w tym klasy otoki MFC kontrolki.

### <a name="windows-common-controls-and-mfc-classes"></a><a name="_core_windows_common_controls_and_mfc_classes"></a>Formanty standardowe systemu Windows i klasy MFC

|Kontrola|Klasa MFC|Opis|Nowość w systemie Windows 95|
|-------------|---------------|-----------------|------------------------|
|[odtwarzania](using-canimatectrl.md)|[Korzystanie CAnimateCtrl](reference/canimatectrl-class.md)|Wyświetla kolejne klatki klipu wideo AVI|Tak|
|button|[CButton](reference/cbutton-class.md)|Skutki, które powodują akcję; używane również dla pól wyboru, przycisków radiowych i grup|Nie|
|pole kombi|[CComboBox](reference/ccombobox-class.md)|Kombinacja pola edycji i pola listy|Nie|
|[Selektor daty i godziny](using-cdatetimectrl.md)|[Korzystanie CDateTimeCtrl](reference/cdatetimectrl-class.md)|Zezwala użytkownikowi na wybranie określonej wartości daty lub godziny|Tak|
|pole edycji|[CEdit](reference/cedit-class.md)|Pola do wprowadzania tekstu|Nie|
|[rozszerzone pole kombi](using-ccomboboxex.md)|[Korzystanie CComboBoxEx](reference/ccomboboxex-class.md)|Kontrolka pola kombi z możliwością wyświetlania obrazów|Tak|
|[header](using-cheaderctrl.md)|[CHeaderCtrl](reference/cheaderctrl-class.md)|Przycisk, który pojawia się powyżej kolumny tekstu; kontroluje szerokość wyświetlanego tekstu|Tak|
|[sekwencj](using-chotkeyctrl.md)|[CHotKeyCtrl](reference/chotkeyctrl-class.md)|Okno, które umożliwia użytkownikowi tworzenie "klawisza gorąca", aby szybko wykonać akcję|Tak|
|[Lista obrazów](using-cimagelist.md)|[Korzystanie CImageList](reference/cimagelist-class.md)|Kolekcja obrazów używanych do zarządzania dużymi zestawami ikon lub map bitowych (lista obrazów nie jest w rzeczywistości kontrolką; obsługuje ona listy używane przez inne kontrolki).|Tak|
|[list](using-clistctrl.md)|[CListCtrl](reference/clistctrl-class.md)|Okno, w którym jest wyświetlana lista tekstów z ikonami|Tak|
|pole listy|[CListBox](reference/clistbox-class.md)|Pole zawierające listę ciągów|Nie|
|[Kalendarz miesięczny](using-cmonthcalctrl.md)|[CMonthCalCtrl](reference/cmonthcalctrl-class.md)|Kontrolka wyświetlająca informacje o dacie|Tak|
|[wykonywane](using-cprogressctrl.md)|[Korzystanie CProgressCtrl](reference/cprogressctrl-class.md)|Okno, które wskazuje postęp długotrwałej operacji|Tak|
|[paska pomocniczego](using-crebarctrl.md)|[Korzystanie CReBarCtrl](reference/crebarctrl-class.md)|Pasek narzędzi, który może zawierać dodatkowe okna podrzędne w formie formantów|Tak|
|[Edycja wzbogacona](using-cricheditctrl.md)|[CRichEditCtrl](reference/cricheditctrl-class.md)|Okno, w którym użytkownik może edytować za pomocą formatowania znaków i akapitów (zobacz [klasy związane z kontrolkami edycji wzbogaconej](classes-related-to-rich-edit-controls.md))|Tak|
|pasek przewijania|[CScrollBar](reference/cscrollbar-class.md)|Pasek przewijania używany jako formant wewnątrz okna dialogowego (nie w oknie)|Nie|
|[skakując](using-csliderctrl.md)|[Korzystanie CSliderCtrl](reference/csliderctrl-class.md)|Okno zawierające kontrolkę suwaka z opcjonalnymi znacznikami osi|Tak|
|[przycisk pokrętła](using-cspinbuttonctrl.md)|[Korzystanie CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)|Para przycisków strzałek, które użytkownik może kliknąć, aby zwiększyć lub zmniejszyć wartość|Tak|
|tekst statyczny|[CStatic](reference/cstatic-class.md)|Tekst do etykietowania innych kontrolek|Nie|
|[pasek stanu](using-cstatusbarctrl.md)|[CStatusBarCtrl](reference/cstatusbarctrl-class.md)|Okno do wyświetlania informacji o stanie, podobnie jak Klasa MFC`CStatusBar`|Tak|
|[tabulator](using-ctabctrl.md)|[CTabCtrl](reference/ctabctrl-class.md)|Analogiczne do dzielników w notesie; używane w "oknach dialogowych kart" lub arkuszach właściwości|Tak|
|[pasku narzędzi](using-ctoolbarctrl.md)|[CToolBarCtrl](reference/ctoolbarctrl-class.md)|Okno z przyciskami generującymi polecenia, podobnymi do klasy MFC`CToolBar`|Tak|
|[etykietka narzędzia](using-ctooltipctrl.md)|[CToolTipCtrl](reference/ctooltipctrl-class.md)|Małe okno podręczne, które opisuje przeznaczenie przycisku paska narzędzi lub innego narzędzia|Tak|
|[tree](using-ctreectrl.md)|[CTreeCtrl](reference/ctreectrl-class.md)|Okno, które wyświetla hierarchiczną listę elementów|Tak|

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- Indywidualny formant: zobacz tabelę [formanty wspólne systemu Windows i klasy MFC](#_core_windows_common_controls_and_mfc_classes) w tym temacie, aby uzyskać linki do wszystkich kontrolek

- [Tworzenie i używanie kontrolek](making-and-using-controls.md)

- [Używanie edytora okien dialogowych do dodawania kontrolek](using-the-dialog-editor-to-add-controls.md)

- [Ręczne dodawanie kontrolek do okna dialogowego](adding-controls-by-hand.md)

- [Wyprowadzanie klas kontroli z klas formantów MFC](deriving-controls-from-a-standard-control.md)

- [Używanie formantów wspólnych jako okien podrzędnych](using-a-common-control-as-a-child-window.md)

- [Powiadomienia od formantów wspólnych](receiving-notification-from-common-controls.md)

- [Dodaj typowe formanty do okna dialogowego](using-common-controls-in-a-dialog-box.md).

- [Uzyskuje formant ze standardowego formantu systemu Windows](deriving-controls-from-a-standard-control.md)

- [Kontrolki okna dialogowego dostępu z bezpieczeństwem typu](type-safe-access-to-controls-in-a-dialog-box.md)

- [Odbieraj komunikaty powiadomień z formantów wspólnych](receiving-notification-from-common-controls.md)

- [Samples](common-control-sample-list.md)

Aby uzyskać informacje o typowych kontrolkach systemu Windows w Windows SDK, zobacz temat [typowe formanty](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](user-interface-elements-mfc.md)<br/>
[Edytor okien dialogowych](../windows/dialog-editor.md)
