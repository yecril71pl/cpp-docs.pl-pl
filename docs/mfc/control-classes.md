---
title: Klasy formantów
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
helpviewer_keywords:
- static display controls [MFC]
- control classes [MFC]
- buttons, MFC control classes
- controls [MFC], MFC control classes
- controls [MFC]
- list boxes [MFC], MFC control classes
- control classes [MFC], MFC
- text, controls for input [MFC]
- user input [MFC], MFC control classes
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
ms.openlocfilehash: 277802bff3e4833396c4bf114ff8880fcd26343d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623001"
---
# <a name="control-classes"></a>Klasy formantów

Klasy formantów hermetyzują szeroką gamę standardowych kontrolek systemu Windows od formantów tekstu statycznego do kontrolek drzewa. Ponadto MFC udostępnia niektóre nowe kontrolki, w tym przyciski zawierające mapy bitowe i paski sterowania.

Kontrolki, których nazwy klas kończą się znakiem "**Ctrl**", były Nowość w systemach Windows 95 i Windows NT w wersji 3,51.

## <a name="static-display-controls"></a>Statyczne kontrolki wyświetlania

[CStatic](reference/cstatic-class.md)<br/>
Okno statycznego wyświetlania. Formanty statyczne służą do etykietowania, pól i oddzielania innych kontrolek w oknie dialogowym lub w oknach. Mogą również wyświetlać obrazy graficzne zamiast tekstu lub pola.

## <a name="text-controls"></a>Kontrolki tekstu

[CEdit](reference/cedit-class.md)<br/>
Okno kontrolki tekstu edytowalnego. Kontrolki edycji służą do akceptowania danych tekstowych od użytkownika.

[CIPAddressCtrl](reference/cipaddressctrl-class.md)<br/>
Obsługuje pole edycji do manipulowania adresem protokołu internetowego (IP).

[CRichEditCtrl](reference/cricheditctrl-class.md)<br/>
Kontrolka, w której użytkownik może wprowadzać i edytować tekst. W przeciwieństwie do kontrolki kapsułowane w `CEdit` , formant edycji wzbogaconej obsługuje formatowanie znaków i akapitów oraz obiekty OLE.

## <a name="controls-that-represent-numbers"></a>Kontrolki reprezentujące liczby

[Korzystanie CSliderCtrl](reference/csliderctrl-class.md)<br/>
Kontrolka zawierająca suwak, do którego użytkownik przechodzi w celu wybrania wartości lub zestawu wartości.

[Korzystanie CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)<br/>
Para przycisków strzałek, które użytkownik może kliknąć, aby zwiększyć lub zmniejszyć wartość.

[Korzystanie CProgressCtrl](reference/cprogressctrl-class.md)<br/>
Wyświetla prostokąt, który jest stopniowo wypełniany od lewej do prawej, aby wskazać postęp operacji.

[CScrollBar](reference/cscrollbar-class.md)<br/>
Okno kontrolne paska przewijania. Klasa zawiera funkcje paska przewijania, do użycia jako kontrolka w oknie dialogowym lub okna, za pomocą którego użytkownik może określić pozycję w obrębie zakresu.

## <a name="buttons"></a>Przyciski

[CButton](reference/cbutton-class.md)<br/>
Okno kontrolne przycisku. Klasa udostępnia interfejs programistyczny przycisku wypchnięcia, pole wyboru lub przycisk radiowy w oknie dialogowym lub okno.

[CBitmapButton](reference/cbitmapbutton-class.md)<br/>
Przycisk z mapą bitową, a nie podpisem tekstowym.

## <a name="lists"></a>Listy

[CListBox](reference/clistbox-class.md)<br/>
Okno kontrolne w polu listy. W polu listy zostanie wyświetlona lista elementów, które użytkownik może wyświetlać i wybrać.

[CDragListBox](reference/cdraglistbox-class.md)<br/>
Oferuje funkcje pola listy systemu Windows; zezwala użytkownikowi na przenoszenie elementów pola listy, takich jak nazwy plików i literały ciągu, w polu listy. Pola listy z tą funkcją są przydatne dla listy elementów w kolejności innej niż alfabetyczna, na przykład do dołączania nazw ścieżek lub plików w projekcie.

[CComboBox](reference/ccombobox-class.md)<br/>
Okno kontrolne pola kombi. Pole kombi składa się z kontrolki edycji i pola listy.

[Korzystanie CComboBoxEx](reference/ccomboboxex-class.md)<br/>
Rozszerza formant pola kombi, dostarczając obsługę list obrazów.

[CCheckListBox](reference/cchecklistbox-class.md)<br/>
Wyświetla listę elementów z polami wyboru, które użytkownik może sprawdzić lub wyczyścić obok każdego elementu.

[CListCtrl](reference/clistctrl-class.md)<br/>
Wyświetla kolekcję elementów, z których każda składa się z ikony i etykiety, w sposób podobny do prawego okienka Eksploratora plików.

[CTreeCtrl](reference/ctreectrl-class.md)<br/>
Wyświetla hierarchiczną listę ikon i etykiet ułożone w sposób podobny do lewego okienka Eksploratora plików.

## <a name="toolbars-and-status-bars"></a>Paski narzędzi i paski stanu

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
Oferuje funkcje formantu typowego paska narzędzi systemu Windows. Większość programów MFC używa [CToolBar](reference/ctoolbar-class.md) zamiast tej klasy.

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
Okno poziome, zwykle podzielone na okienka, w którym aplikacja może wyświetlać informacje o stanie. Większość programów MFC używa [CStatusBar](reference/cstatusbar-class.md) zamiast tej klasy.

## <a name="miscellaneous-controls"></a>Różne kontrolki

[Korzystanie CAnimateCtrl](reference/canimatectrl-class.md)<br/>
Wyświetla prosty klip wideo.

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
Małe okno podręczne wyświetlające pojedynczy wiersz tekstu opisujący przeznaczenie narzędzia w aplikacji.

[Korzystanie CDateTimeCtrl](reference/cdatetimectrl-class.md)<br/>
Obsługuje rozszerzoną kontrolkę edycji lub prostą kontrolkę interfejsu kalendarza, która umożliwia użytkownikowi wybranie określonej wartości daty lub godziny.

[CHeaderCtrl](reference/cheaderctrl-class.md)<br/>
Wyświetla tytuły lub etykiety kolumn.

[CMonthCalCtrl](reference/cmonthcalctrl-class.md)<br/>
Obsługuje prostą kontrolkę interfejsu kalendarza, która umożliwia użytkownikowi wybranie daty.

[CTabCtrl](reference/ctabctrl-class.md)<br/>
Kontrolka z kartami, na których użytkownik może kliknąć, analogicznie do separatorów w notesie.

[CHotKeyCtrl](reference/chotkeyctrl-class.md)<br/>
Umożliwia użytkownikowi tworzenie kombinacji klawisza skrótu, którą użytkownik może nacisnąć, aby szybko wykonać akcję.

[CLinkCtrl](reference/clinkctrl-class.md)<br/>
Renderuje tekst oznaczony tekstem i uruchamia odpowiednie aplikacje, gdy użytkownik kliknie link osadzony.

[CHtmlEditCtrl](reference/chtmleditctrl-class.md)<br/>
Oferuje funkcje kontrolki ActiveX WebBrowser w oknie MFC.

## <a name="related-classes"></a>Powiązane klasy

[Korzystanie CImageList](reference/cimagelist-class.md)<br/>
Oferuje funkcje listy obrazów systemu Windows. Listy obrazów są używane z kontrolkami list i kontrolkami drzewa. Mogą być również używane do przechowywania i archiwizowania zestawu o takich samych mapach bitowych.

[CCtrlView](reference/cctrlview-class.md)<br/>
Klasa bazowa dla wszystkich widoków skojarzonych z kontrolkami systemu Windows. Poniżej opisano widoki oparte na kontrolkach.

[Elementu CEditView](reference/ceditview-class.md)<br/>
Widok, który zawiera kontrolkę edycji standardowej systemu Windows.

[CRichEditView](reference/cricheditview-class.md)<br/>
Widok, który zawiera kontrolkę zaawansowanej edycji systemu Windows.

[CListView](reference/clistview-class.md)<br/>
Widok zawierający formant listy systemu Windows.

[CTreeView](reference/ctreeview-class.md)<br/>
Widok, który zawiera kontrolkę drzewa systemu Windows.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
