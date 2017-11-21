---
title: Kontrolowanie klas | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.control
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c1bba69597425c10119af1f2c7d29afd870d8c48
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="control-classes"></a>Klasy formantów
Klasy formantów Hermetyzowanie różnych od statyczny tekst kontrolki do drzewa formantów standardowych formantów systemu Windows. Ponadto MFC zawiera niektóre nowe formanty przycisków z paskami mapy bitowe i kontroli w tym.  
  
 Formanty, których nazwy klasy kończyć się "**Ctrl**" wprowadzono w systemie Windows 95 i Windows NT w wersji 3.51.  
  
## <a name="static-display-controls"></a>Statyczne formanty wyświetlania  
 [CStatic](../mfc/reference/cstatic-class.md)  
 Static — Wyświetl okno. Statyczne formanty są używane do etykiety, pole lub różnych innych kontrolek w lub oknie dialogowym. Może również wyświetlić obrazy zamiast tekstu lub okno.  
  
## <a name="text-controls"></a>Kontrolki tekstu  
 [CEdit](../mfc/reference/cedit-class.md)  
 Okno kontrolki edycji tekstu. Edytuj formanty są używane do akceptowania tekstową danych wejściowych od użytkownika.  
  
 [CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)  
 Obsługuje pole edycji do manipulowania adres protokołu internetowego (IP).  
  
 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)  
 Formant, w którym użytkownik może wprowadzić i edytować tekst. W przeciwieństwie do formantu z `CEdit`, kontrolki zaawansowanej edycji obsługuje znaków i akapitu formatowanie i obiektów OLE.  
  
## <a name="controls-that-represent-numbers"></a>Formanty, które reprezentują cyfry  
 [Csliderctrl —](../mfc/reference/csliderctrl-class.md)  
 Formant zawierający suwaka, użytkownik przechodzi do wybierz wartość lub zbiór wartości.  
  
 [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)  
 Para przycisków strzałek użytkownik może kliknąć, aby zwiększyć lub zmniejszyć wartość.  
  
 [Cprogressctrl —](../mfc/reference/cprogressctrl-class.md)  
 Wyświetla prostokąt stopniowo jest wypełniony od lewej do prawej strony, aby wskazać postęp operacji.  
  
 [CScrollBar](../mfc/reference/cscrollbar-class.md)  
 Okno formantu paska przewijania. Ta klasa dostarcza funkcje paska przewijania, do użycia jako formant w dialogowego lub okna, za pomocą którego użytkownik może określić pozycji w zakresie.  
  
## <a name="buttons"></a>Przyciski  
 [CButton](../mfc/reference/cbutton-class.md)  
 Okno formantu przycisku. Ta klasa dostarcza interfejs programistyczny dla przycisku polecenia, pole wyboru lub przycisku radiowego w lub oknie dialogowym.  
  
 [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)  
 Przycisk z mapą bitową zamiast podpis tekstowy.  
  
## <a name="lists"></a>Listy  
 [Clistbox —](../mfc/reference/clistbox-class.md)  
 Okno formantu pola listy. Pole listy wyświetla listę elementów, które użytkownik może wyświetlać i wybierać.  
  
 [CDragListBox](../mfc/reference/cdraglistbox-class.md)  
 Udostępnia funkcje systemu Windows pole listy; Umożliwia użytkownikowi Przenieś elementy pola listy, takich jak nazwy plików i ciągu literałów, w polu listy. Pola listy z tej funkcji są przydatne do listy elementów w kolejności innej niż alfabetyczne, takich jak obejmują nazwy ścieżek lub pliki w projekcie.  
  
 [Ccombobox —](../mfc/reference/ccombobox-class.md)  
 Okno kontrolki pola kombi. Pole kombi składa się z formantu edycyjnego i pola listy.  
  
 [CComboBoxEx](../mfc/reference/ccomboboxex-class.md)  
 Rozszerza pole kombi kontrolki pola, zapewniając obsługę listy obrazów.  
  
 [CCheckListBox](../mfc/reference/cchecklistbox-class.md)  
 Wyświetla listę elementów z pola wyboru, które użytkownik może zaznacz lub usuń zaznaczenie, obok każdego elementu.  
  
 [CListCtrl](../mfc/reference/clistctrl-class.md)  
 Wyświetla kolekcję elementów, każdy zawiera ikonę i etykietę, w sposób podobny do prawego okienka Eksploratora plików.  
  
 [CTreeCtrl](../mfc/reference/ctreectrl-class.md)  
 Wyświetla listę hierarchiczną ikony i etykiety ułożone w sposób podobny do okienka po lewej stronie Eksploratora plików.  
  
## <a name="toolbars-and-status-bars"></a>Paski narzędzi i paski stanu  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 Udostępnia funkcje formantu typowych narzędzi systemu Windows. Większość MFC programy użyj [ctoolbar —](../mfc/reference/ctoolbar-class.md) zamiast tej klasy.  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 Poziomy okno zwykle podzielone okienka, w których aplikacja może wyświetlać informacje o stanie. Większość MFC programy użyj [cstatusbar —](../mfc/reference/cstatusbar-class.md) zamiast tej klasy.  
  
## <a name="miscellaneous-controls"></a>Inne formanty.  
 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)  
 Wyświetla simple klipu wideo.  
  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 Małe okno podręczne wyświetlające pojedynczy wiersz tekst opisujący cel narzędzia w aplikacji.  
  
 [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)  
 Obsługuje rozszerzonych edycji lub formant interfejsu prostego kalendarza, który umożliwia użytkownikowi wybierz określoną datę lub godzinę.  
  
 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)  
 Wyświetla tytuły lub etykiety kolumn.  
  
 [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)  
 Obsługuje prosty kalendarza formant interfejsu, który umożliwia użytkownikowi wybranie daty.  
  
 [CTabCtrl](../mfc/reference/ctabctrl-class.md)  
 Formant karty, na których użytkownik może kliknąć, analogiczne do separatorów w notesie.  
  
 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)  
 Umożliwia użytkownikowi utworzenie kombinację klawiszy dostępu, które użytkownik może nacisnąć szybko wykonać akcję.  
  
 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)  
 Renderuje oznaczony tekst i uruchamia odpowiednie aplikacje, gdy użytkownik kliknie łącze osadzonych.  
  
 [CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)  
 Udostępnia funkcje formantu WebBrowser ActiveX w oknie MFC.  
  
## <a name="related-classes"></a>Klasy pokrewne  
 [Cimagelist —](../mfc/reference/cimagelist-class.md)  
 Udostępnia funkcję listy obrazów systemu Windows. Listy obrazów są używane przez formanty listy i drzewa. One mogą służyć do przechowywania i archiwum zestaw o tej samej wielkości map bitowych.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 Klasa podstawowa dla wszystkich widoków skojarzonych z formantów systemu Windows. Widoki oparte na formanty są opisane poniżej.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Formant edycji widoku, który zawiera standardowe systemu Windows.  
  
 [Cricheditview —](../mfc/reference/cricheditview-class.md)  
 Formant edycji widok zawierający sformatowanego systemu Windows.  
  
 [Clistview —](../mfc/reference/clistview-class.md)  
 Widok, który zawiera formant listy systemu Windows.  
  
 [CTreeView —](../mfc/reference/ctreeview-class.md)  
 Widok, który zawiera kontrolki drzewa systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

