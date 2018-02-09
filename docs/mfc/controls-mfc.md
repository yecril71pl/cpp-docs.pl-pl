---
title: Formanty (MFC) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b18979ec502ea645cf8cdac39ca9ea75cb229e61
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="controls-mfc"></a>Formanty (MFC)
Formanty są obiektami, które użytkownicy mogą wykorzystywać do wprowadzania lub manipulować danymi. Występują najczęściej w oknach dialogowych lub na paskach narzędzi. Ten temat rodziny obejmuje trzy główne rodzaje kontrolki:  
  
-   Formanty standardowe systemu Windows, w tym formanty rysowane przez właściciela  
  
-   Kontrolki ActiveX  
  
-   Inne klasy formantów dostarczonych przez Microsoft Foundation Class biblioteki (MFC)  
  
## <a name="windows-common-controls"></a>Formanty standardowe systemu Windows  
 System operacyjny Windows zawsze udostępnił liczba formanty standardowe systemu Windows. Te obiekty sterowania są programowalny i Edytor okien dialogowych programu Visual C++ obsługuje dodanie ich do użytkownika okien dialogowych. Biblioteka Microsoft Foundation Class (MFC) dostarcza klas, które zapewniają każdego z tych elementów, jak pokazano w tabeli [formanty standardowe systemu Windows i klas MFC](#_core_windows_common_controls_and_mfc_classes). (Niektóre elementy w tabeli mają powiązanych tematach opisano je w dodatkowe. Dla formantów, których brakuje tematów zobacz dokumentację dla klasy MFC.)  
  
 Klasa [CWnd](../mfc/reference/cwnd-class.md) jest klasą bazową wszystkie klasy okien, w tym wszystkie klasy formantu. 
  
## <a name="activex-controls"></a>Kontrolki ActiveX  
 Kontrolki ActiveX, wcześniej znana jako formantów OLE, można w oknach dialogowych w aplikacjach dla systemu Windows lub na stronach HTML w sieci World Wide Web. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md).  
  
## <a name="other-mfc-control-classes"></a>Inne klasy formantów MFC  
 Oprócz klas, które zapewniają wszystkie formanty standardowe systemu Windows i że programowanie formantów ActiveX (lub za pomocą formantów ActiveX dostarczanych przez innych użytkowników) MFC dostarcza następujące klasy formantu własnych:  
  
-   [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)  
  
-   [CCheckListBox](../mfc/reference/cchecklistbox-class.md)  
  
-   [CDragListBox](../mfc/reference/cdraglistbox-class.md)  
  
##  <a name="_core_finding_information_about_windows_common_controls"></a>Znajdowanie informacji o formanty standardowe systemu Windows  
 W poniższej tabeli krótko opisano poszczególne formanty standardowe systemu Windows, łącznie z klasy otoki formantu MFC.  
  
### <a name="_core_windows_common_controls_and_mfc_classes"></a>Formanty standardowe systemu Windows i klas MFC  
  
|Formant|Klasy MFC|Opis|Nowość w systemie Windows 95|  
|-------------|---------------|-----------------|------------------------|  
|[Animacja](../mfc/using-canimatectrl.md)|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Wyświetla kolejnych klatek AVI klipu wideo|Tak|  
|button|[CButton](../mfc/reference/cbutton-class.md)|Przyciski, które powodują akcji; również używane do pola wyboru, przyciski radiowe i pola grupy|Nie|  
|pole kombi|[CComboBox](../mfc/reference/ccombobox-class.md)|Kombinacja pole edycji i pola listy|Nie|  
|[selektora daty i godziny](../mfc/using-cdatetimectrl.md)|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|Zezwala użytkownikowi na wybranie wartości określonej daty lub czasu|Tak|  
|pole edycji|[CEdit](../mfc/reference/cedit-class.md)|Pola do wprowadzania tekstu|Nie|  
|[pole kombi rozszerzone](../mfc/using-ccomboboxex.md)|[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)|Kontrolka pola kombi umożliwia wyświetlanie obrazów|Tak|  
|[header](../mfc/using-cheaderctrl.md)|[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)|Przycisk, który pojawi się powyżej kolumny tekstu; Określa szerokość wyświetlanego tekstu|Tak|  
|[klawisze skrótu](../mfc/using-chotkeyctrl.md)|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Okno, który umożliwia użytkownikowi utworzenie "klawisza dostępu" szybko wykonania akcji|Tak|  
|[listy obrazów](../mfc/using-cimagelist.md)|[CImageList](../mfc/reference/cimagelist-class.md)|Kolekcją obrazów, które umożliwiają zarządzanie dużymi zbiorami ikony lub mapy bitowe (listy obrazów nie jest naprawdę formantu; obsługuje list używane przez inne formanty)|Tak|  
|[list](../mfc/using-clistctrl.md)|[CListCtrl](../mfc/reference/clistctrl-class.md)|Okno, który wyświetla listę wartości tekstowych z ikonami|Tak|  
|pola listy|[CListBox](../mfc/reference/clistbox-class.md)|Pole zawierające listę ciągów|Nie|  
|[kalendarza miesięcznego](../mfc/using-cmonthcalctrl.md)|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|Formant, który wyświetla informacje o dacie|Tak|  
|[postęp](../mfc/using-cprogressctrl.md)|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Okno, która wskazuje postępu długotrwałej operacji|Tak|  
|[paska pomocniczego](../mfc/using-crebarctrl.md)|[Crebarctrl —](../mfc/reference/crebarctrl-class.md)|Pasek narzędzi, zawierające więcej podrzędnych windows w postaci formantów|Tak|  
|[edycji wzbogaconej](../mfc/using-cricheditctrl.md)|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|Okna, w którym użytkownik może edytować z formatowanie znaków i akapitów (zobacz [klasy powiązane z formantów edycji wzbogaconej](../mfc/classes-related-to-rich-edit-controls.md))|Tak|  
|pasek przewijania|[CScrollBar](../mfc/reference/cscrollbar-class.md)|Pasek przewijania używany jako formant wewnątrz okno dialogowe (nie w oknie)|Nie|  
|[slider](../mfc/using-csliderctrl.md)|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|Znaczniki okna zawierającego formantu suwaka o opcjonalne|Tak|  
|[przycisk pokrętła](../mfc/using-cspinbuttonctrl.md)|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Para użytkownika przycisków strzałek można kliknąć przyrost lub zmniejszanie wartości|Tak|  
|tekst statyczne|[CStatic](../mfc/reference/cstatic-class.md)|Tekst dla innych formantów etykiet|Nie|  
|[pasek stanu](../mfc/using-cstatusbarctrl.md)|[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)|Okno do wyświetlania informacji o stanie, podobny do klasy MFC`CStatusBar`|Tak|  
|[tab](../mfc/using-ctabctrl.md)|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Analogiczne do separatorów w notesie; używane w "okna dialogowe kart" lub arkusze właściwości|Tak|  
|[pasek narzędzi](../mfc/using-ctoolbarctrl.md)|[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)|Przyciski okna z generowania polecenia, podobny do klasy MFC`CToolBar`|Tak|  
|[Etykietka narzędzia](../mfc/using-ctooltipctrl.md)|[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)|Niewielkie okno podręczne, opisujący cel przycisku paska narzędzi lub innego narzędzia|Tak|  
|[drzewa](../mfc/using-ctreectrl.md)|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Okna hierarchicznych listy elementów|Tak|  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   Poszczególnych kontrolek: Zobacz tabelę [formanty standardowe systemu Windows i klas MFC](#_core_windows_common_controls_and_mfc_classes) tego tematu zawiera linki do wszystkich kontrolek  
  
-   [Tworzenie i używanie formantów](../mfc/making-and-using-controls.md)  
  
-   [Używanie edytora okien dialogowych do dodawania formantów](../mfc/using-the-dialog-editor-to-add-controls.md)  
  
-   [Ręczne dodawanie formantów do okna dialogowego](../mfc/adding-controls-by-hand.md)  
  
-   [Wyprowadzanie klasy formantów z klasy formantów MFC](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [Używanie formantów wspólnych jako okien podrzędnych](../mfc/using-a-common-control-as-a-child-window.md)  
  
-   [Powiadomienia od formantów wspólnych](../mfc/receiving-notification-from-common-controls.md)  
  
-   [Dodaj formanty standardowe okno dialogowe](../mfc/using-common-controls-in-a-dialog-box.md).  
  
-   [Pochodzi formantu z formantu standardowego systemu Windows](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [Dostęp do formantów okno dialogowe zabezpieczenie typów](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)  
  
-   [Komunikaty powiadomień od formantów wspólnych](../mfc/receiving-notification-from-common-controls.md)  
  
-   [Przykłady](../mfc/common-control-sample-list.md)  
  
 Informacji o formanty standardowe systemu Windows w zestawie SDK systemu Windows, temacie [formanty standardowe](http://msdn.microsoft.com/library/windows/desktop/bb775493).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)   
 [Edytor okien dialogowych](../windows/dialog-editor.md)

