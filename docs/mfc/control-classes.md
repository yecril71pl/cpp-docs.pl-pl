---
title: Kontrolowanie klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.control
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a159677ffa12961e7f065b2cba2b1287c8ef7a58
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432467"
---
# <a name="control-classes"></a>Klasy formantów

Klasy formantów hermetyzować szerokiej gamy standardowych kontrolek Windows począwszy od statyczny tekst kontrolki do kontrolki drzewa. Ponadto biblioteka MFC zawiera kilka nowych formantów, w tym przycisków z paskami mapy bitowe i kontroli.

Formanty, których nazwy klasy kończyć się "**Ctrl**" wprowadzono nowe Windows 95 i Windows NT w wersji 3.51.

## <a name="static-display-controls"></a>Statyczne formanty wyświetlania

[CStatic](../mfc/reference/cstatic-class.md)<br/>
Okno wyświetlania statyczne. Statyczne formanty są używane do etykiety, pole lub rozdzielić inne kontrolki lub oknie dialogowym. Może również wyświetlić obrazy zamiast tekstu lub pola.

## <a name="text-controls"></a>Kontrolek tekstu

[CEdit](../mfc/reference/cedit-class.md)<br/>
Okno kontrolki edycji tekstu. Edycja kontrolki są używane do akceptowania tekstowe dane wejściowe od użytkownika.

[CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)<br/>
Obsługuje pole edycji do manipulowania adres protokołu internetowego (IP).

[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)<br/>
Formant, w którym użytkownik może wprowadzić i edytować tekst. W przeciwieństwie do kontrolki, zhermetyzowanych w ramach `CEdit`, kontrolki edycji wzbogaconej obsługuje znaków i formatowanie akapitów i obiektów OLE.

## <a name="controls-that-represent-numbers"></a>Formanty, które reprezentują cyfr

[CSliderCtrl](../mfc/reference/csliderctrl-class.md)<br/>
Kontrolka zawierająca suwaka, którego użytkownik przechodzi do wybrania wartością lub zbiorem wartości.

[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)<br/>
Parę przycisków strzałek użytkownik może kliknąć, aby zwiększyć lub zmniejszyć wartość.

[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)<br/>
Wyświetla prostokąt, który stopniowo wypełnione od lewej do prawej, aby wskazać postęp operacji.

[CScrollBar](../mfc/reference/cscrollbar-class.md)<br/>
Okno formantu paska przewijania. Klasa oferuje funkcje paska przewijania, do użytku jako formant w okno dialogowe lub w oknie, za pomocą którego użytkownik może określić położenie w obrębie zakresu.

## <a name="buttons"></a>Przyciski

[CButton](../mfc/reference/cbutton-class.md)<br/>
Okno formantu przycisku. Klasa oferuje interfejs programistyczny dla przycisku, pole wyboru lub przycisku radiowego w lub oknie dialogowym.

[CBitmapButton](../mfc/reference/cbitmapbutton-class.md)<br/>
Przycisk z mapą bitową zamiast podpis tekstowy.

## <a name="lists"></a>Listy

[CListBox](../mfc/reference/clistbox-class.md)<br/>
Okno formantu pola listy. Pole listy przedstawia listę elementów, które użytkownik może wyświetlać i wybierać.

[CDragListBox](../mfc/reference/cdraglistbox-class.md)<br/>
Oferuje funkcje pola listy Windows; Umożliwia użytkownikowi przenoszenie elementów pola listy, takich jak nazwy plików i literałów w obrębie pola listy. Pola list z tej możliwości są przydatne w przypadku listy elementów w kolejności innej niż alfabetycznej, takich jak obejmują nazwy ścieżek lub pliki w projekcie.

[CComboBox](../mfc/reference/ccombobox-class.md)<br/>
Okno kontrolki pola kombi. Pole kombi składa się z formantu edycyjnego i pole listy.

[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)<br/>
Rozszerza formant pola kombi, umożliwiając obsługę list obrazów.

[CCheckListBox](../mfc/reference/cchecklistbox-class.md)<br/>
Wyświetla listę elementów z polami wyboru, które użytkownik może zaznacz lub wyczyść obok każdego elementu.

[CListCtrl](../mfc/reference/clistctrl-class.md)<br/>
Wyświetla zbiór elementów składających się z ikony oraz etykiety, w sposób podobny do prawego okienka Eksploratora plików.

[CTreeCtrl](../mfc/reference/ctreectrl-class.md)<br/>
Wyświetla listę hierarchiczną ikony oraz etykiety ułożone w sposób podobny do okienka po lewej stronie Eksploratora plików.

## <a name="toolbars-and-status-bars"></a>Paski narzędzi i stanu

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Oferuje funkcje formantu typowego paska narzędzi Windows. MFC większości programów użyj [CToolBar](../mfc/reference/ctoolbar-class.md) zamiast tej klasy.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Poziomy okno zwykle są podzielone na okienka, w których aplikacja może wyświetlać informacje o stanie. MFC większości programów użyj [CStatusBar](../mfc/reference/cstatusbar-class.md) zamiast tej klasy.

## <a name="miscellaneous-controls"></a>Różne formanty

[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)<br/>
Wyświetla prosty klipu wideo.

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Niewielkie okno podręczne, które wyświetla pojedynczy wiersz tekstu opisującego cel narzędzia w aplikacji.

[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)<br/>
Obsługuje formant edycji rozszerzonej lub kontrolki interfejsu kalendarza prosty, umożliwiająca użytkownikowi wybrać określoną datę lub godzinę.

[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)<br/>
Wyświetla tytuły i etykiety kolumn.

[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)<br/>
Obsługuje formant interfejs proste kalendarza, który umożliwia użytkownikowi wybranie daty.

[CTabCtrl](../mfc/reference/ctabctrl-class.md)<br/>
Kontrolka, za pomocą karty, na których użytkownik może kliknąć, analogiczne do separatorów w notesie.

[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)<br/>
Umożliwia użytkownikowi utworzenie kombinację klawiszy dostępu, której użytkownik może nacisnąć szybko wykonać akcję.

[CLinkCtrl](../mfc/reference/clinkctrl-class.md)<br/>
Renderowanie tekstu oznaczone w górę i uruchamia odpowiednie aplikacje, gdy użytkownik kliknie łącze osadzonych.

[CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)<br/>
Oferuje funkcje formantu WebBrowser ActiveX w oknie programu MFC.

## <a name="related-classes"></a>Klasy pokrewne

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
Oferuje funkcje Windows listy obrazów. Listy obrazów są używane w kontrolkach listy i kontrolkach drzewa. One może również przechowywanie i archiwizowanie zestaw ten sam rozmiar mapy bitowej.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Klasa bazowa dla wszystkich widoków związane z formantami Windows. Widoki oparte na formanty są opisane poniżej.

[Elementu CEditView](../mfc/reference/ceditview-class.md)<br/>
Widok, który zawiera standardowy Windows formantu edycyjnego.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Widok, który zawiera bogaty Windows formantu edycyjnego.

[CListView](../mfc/reference/clistview-class.md)<br/>
Widok, który zawiera kontrolkę listy Windows.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Widok, który zawiera formant drzewa Windows.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

