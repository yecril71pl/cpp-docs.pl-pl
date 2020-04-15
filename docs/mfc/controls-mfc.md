---
title: Formanty (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
ms.openlocfilehash: 454a76e8fdf55f43d75abb63d7d98a9fe4926127
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365324"
---
# <a name="controls-mfc"></a>Formanty (MFC)

Formanty to obiekty, z którymi użytkownicy mogą wchodzić w interakcje w celu wprowadzania danych lub manipulowania nimi. Często pojawiają się one w oknach dialogowych lub na paskach narzędzi. Ta rodzina tematu obejmuje trzy główne rodzaje formantów:

- Typowe formanty systemu Windows, w tym kontrolki rysowane przez właściciela

- Kontrolki ActiveX

- Inne klasy kontroli dostarczane przez bibliotekę klas Microsoft Foundation (MFC)

## <a name="windows-common-controls"></a>Typowe formanty systemu Windows

System operacyjny Windows zawsze zapewniał szereg typowych formantów systemu Windows. Te obiekty sterujące są programowalne, a edytor okien dialogowych języka Visual C++ obsługuje dodawanie ich do okien dialogowych. Biblioteka klas Microsoft Foundation (MFC) dostarcza klasy, które hermetyzują każdy z tych formantów, jak pokazano w tabeli [Typowe formanty systemu Windows i klasy MFC](#_core_windows_common_controls_and_mfc_classes). (Niektóre elementy w tabeli mają powiązane tematy, które opisują je dalej. Formanty, które nie mają tematów, zobacz dokumentację dla klasy MFC.)

Klasa [CWnd](../mfc/reference/cwnd-class.md) jest klasą podstawową wszystkich klas okien, w tym wszystkich klas kontrolnych.

## <a name="activex-controls"></a>Kontrolki ActiveX

Formanty ActiveX, wcześniej znane jako formanty OLE, mogą być używane w oknach dialogowych w aplikacjach dla systemu Windows lub na stronach HTML w sieci World Wide Web. Aby uzyskać więcej informacji, zobacz [MFC ActiveX Controls](../mfc/mfc-activex-controls.md).

## <a name="other-mfc-control-classes"></a>Inne klasy sterowania MFC

Oprócz klas, które hermetyzują wszystkie typowe formanty systemu Windows i obsługują programowanie własnych formantów ActiveX (lub przy użyciu formantów ActiveX dostarczanych przez inne podmioty), MFC dostarcza następujące klasy kontroli:

- [Cbitmapbutton](../mfc/reference/cbitmapbutton-class.md)

- [Skrzynka CCheckListBox](../mfc/reference/cchecklistbox-class.md)

- [Skrzynka CDragListBox](../mfc/reference/cdraglistbox-class.md)

## <a name="finding-information-about-windows-common-controls"></a><a name="_core_finding_information_about_windows_common_controls"></a>Znajdowanie informacji o typowych formantych systemu Windows

W poniższej tabeli pokrótce opisano każdy z typowych formantów systemu Windows, w tym klasy otoki MFC formantu.

### <a name="windows-common-controls-and-mfc-classes"></a><a name="_core_windows_common_controls_and_mfc_classes"></a>Typowe formanty systemu Windows i klasy MFC

|Kontrola|Klasa MFC|Opis|Nowość w systemie Windows 95|
|-------------|---------------|-----------------|------------------------|
|[Animacji](../mfc/using-canimatectrl.md)|[Canimatectrl](../mfc/reference/canimatectrl-class.md)|Wyświetla kolejne klatki klipu wideo AVI|Tak|
|button|[Cbutton](../mfc/reference/cbutton-class.md)|Przyciski, które powodują działanie; używane również w polach wyboru, przyciskach radiowych i polach grupowych|Nie|
|pole kombi|[Ccombobox](../mfc/reference/ccombobox-class.md)|Kombinacja pola edycji i pola listy|Nie|
|[selektor daty i godziny](../mfc/using-cdatetimectrl.md)|[Cdatetimectrl](../mfc/reference/cdatetimectrl-class.md)|Umożliwia użytkownikowi wybranie określonej wartości daty lub godziny|Tak|
|edytuj pole|[Cedit](../mfc/reference/cedit-class.md)|Pola wprowadzania tekstu|Nie|
|[rozszerzone pole kombi](../mfc/using-ccomboboxex.md)|[Ccomboboxex](../mfc/reference/ccomboboxex-class.md)|Kontrolka pola kombi z możliwością wyświetlania obrazów|Tak|
|[Nagłówka](../mfc/using-cheaderctrl.md)|[Cheaderctrl](../mfc/reference/cheaderctrl-class.md)|Przycisk wyświetlany nad kolumną tekstu; steruje szerokością wyświetlanego tekstu|Tak|
|[Hotkey](../mfc/using-chotkeyctrl.md)|[Chotkeyctrl](../mfc/reference/chotkeyctrl-class.md)|Okno umożliwiające użytkownikowi utworzenie "skrótu klawiszowego" w celu szybkiego wykonania akcji|Tak|
|[lista obrazów](../mfc/using-cimagelist.md)|[Cimagelist](../mfc/reference/cimagelist-class.md)|Zbieranie obrazów używanych do zarządzania dużymi zestawami ikon lub map bitowych (lista obrazów nie jest tak naprawdę formantem; obsługuje listy używane przez inne formanty)|Tak|
|[list](../mfc/using-clistctrl.md)|[Clistctrl](../mfc/reference/clistctrl-class.md)|Okno wyświetlace listę tekstu z ikonami|Tak|
|pole listy|[Clistbox](../mfc/reference/clistbox-class.md)|Pole zawierające listę ciągów znaków|Nie|
|[kalendarz miesiąca](../mfc/using-cmonthcalctrl.md)|[Cmonthcalctrl](../mfc/reference/cmonthcalctrl-class.md)|Sterowanie wyświetlanie informacji o dacie|Tak|
|[Postępu](../mfc/using-cprogressctrl.md)|[CProgressCtrl (CProgressCtrl)](../mfc/reference/cprogressctrl-class.md)|Okno wskazujące postęp długiej operacji|Tak|
|[Prętów zbrojeniowych](../mfc/using-crebarctrl.md)|[Crebarctrl](../mfc/reference/crebarctrl-class.md)|Pasek narzędzi, który może zawierać dodatkowe okna podrzędne w postaci formantów|Tak|
|[edycja bogata](../mfc/using-cricheditctrl.md)|[Cricheditctrl](../mfc/reference/cricheditctrl-class.md)|Okno, w którym użytkownik może edytować za pomocą formatowania znaków i akapitów (zobacz [Klasy związane z formantami edycji rozszerzonej)](../mfc/classes-related-to-rich-edit-controls.md)|Tak|
|pasek przewijania|[Cscrollbar](../mfc/reference/cscrollbar-class.md)|Pasek przewijania używany jako formant wewnątrz okna dialogowego (nie w oknie)|Nie|
|[Suwak](../mfc/using-csliderctrl.md)|[Csliderctrl](../mfc/reference/csliderctrl-class.md)|Okno zawierające kontrolkę suwaka z opcjonalnymi znacznikami osi|Tak|
|[przycisk spin](../mfc/using-cspinbuttonctrl.md)|[CSpinButtonCtrl (Polski)](../mfc/reference/cspinbuttonctrl-class.md)|Para przycisków strzałek, które użytkownik może kliknąć, aby zwiększać lub zmniejszać wartość|Tak|
|tekst statyczny|[Cstatic](../mfc/reference/cstatic-class.md)|Tekst do etykietowania innych formantów|Nie|
|[pasek stanu](../mfc/using-cstatusbarctrl.md)|[Cstatusbarctrl](../mfc/reference/cstatusbarctrl-class.md)|Okno wyświetlania informacji o stanie, podobne do klasy MFC`CStatusBar`|Tak|
|[Zakładka](../mfc/using-ctabctrl.md)|[Ctabctrl](../mfc/reference/ctabctrl-class.md)|Analogicznie do dzielników w notatniku; używane w "oknach dialogowych kart" lub arkuszach właściwości|Tak|
|[Pasku narzędzi](../mfc/using-ctoolbarctrl.md)|[Ctoolbarctrl](../mfc/reference/ctoolbarctrl-class.md)|Okno z przyciskami generowania poleceń, podobne do klasy MFC`CToolBar`|Tak|
|[Etykietka narzędzia](../mfc/using-ctooltipctrl.md)|[Ctooltipctrl](../mfc/reference/ctooltipctrl-class.md)|Małe okno podręczne opisujące cel przycisku paska narzędzi lub innego narzędzia|Tak|
|[drzewo](../mfc/using-ctreectrl.md)|[Ctreectrl](../mfc/reference/ctreectrl-class.md)|Okno z hierarchiczną listą elementów|Tak|

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- Pojedynczy formant: zobacz tabelę [Typowe formanty systemu Windows i klasy MFC](#_core_windows_common_controls_and_mfc_classes) w tym temacie, aby uzyskać łącza do wszystkich formantów

- [Tworzenie i używanie elementów sterujących](../mfc/making-and-using-controls.md)

- [Dodawanie kontrolek za pomocą edytora dialogów](../mfc/using-the-dialog-editor-to-add-controls.md)

- [Ręczne dodawanie kontrolek do okna dialogowego](../mfc/adding-controls-by-hand.md)

- [Wyprowadzanie klas kontrolnych z klas kontroli MFC](../mfc/deriving-controls-from-a-standard-control.md)

- [Używanie typowych kontrolek jako okien podrzędnych](../mfc/using-a-common-control-as-a-child-window.md)

- [Powiadomienia ze wspólnych formantów](../mfc/receiving-notification-from-common-controls.md)

- [Dodawanie typowych kontrolek do okna dialogowego](../mfc/using-common-controls-in-a-dialog-box.md).

- [Wyprowadzanie formantu ze standardowego formantu systemu Windows](../mfc/deriving-controls-from-a-standard-control.md)

- [Kontrolki okna dialogowego dostępu z bezpieczeństwem typu](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Odbieranie komunikatów powiadomień ze wspólnych formantów](../mfc/receiving-notification-from-common-controls.md)

- [Samples](../mfc/common-control-sample-list.md)

Aby uzyskać informacje na temat typowych formantów systemu Windows w programie Windows SDK, zobacz [Typowe formanty](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)<br/>
[Edytor okien dialogowych](../windows/dialog-editor.md)
