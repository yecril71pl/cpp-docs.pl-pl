---
title: Komunikaty AFX | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SB_LINELEFT
- SB_THUMBTRACK
- AFX_TOOLTIP_TYPE_EDIT
- AFX_WM_ON_HSCROLL
- SB_PAGERIGHT
- AFX_WM_RESETPROMPT
- AFX_WM_CHANGE_RIBBON_CATEGORY
- AFX_TOOLTIP_TYPE_MINIFRAME
- AFX_WM_CUSTOMIZETOOLBAR
- AFX_WM_CHANGE_ACTIVE_TAB
- AFX_WM_ACCGETOBJECT
- AFX_WM_TOOLBARMENU
- AFX_TOOLTIP_TYPE_DOCKBAR
- AFX_WM_CUSTOMIZEHELP
- AFX_WM_ON_GET_TAB_TOOLTIP
- AFX_WM_ON_RIBBON_CUSTOMIZE
- AFX_WM_ON_DRAGCOMPLETE
- AFX_WM_RESETTOOLBAR
- AFX_WM_ON_MOVETOTABGROUP
- AFX_WM_CHECKEMPTYMINIFRAME
- AFX_WM_GETDOCUMENTCOLORS
- SB_RIGHT
- AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU
- AFX_WM_ACCGETSTATE
- SB_PAGELEFT
- SB_ENDSCROLL
- AFX_WM_ON_CANCELTABMOVE
- AFX_TOOLTIP_TYPE_TAB
- AFX_WM_WINDOW_HELP
- AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM
- AFX_WM_SHOWREGULARMENU
- AFX_TOOLTIP_TYPE_TOOLBAR
- AFX_WM_CHANGE_CURRENT_FOLDER
- AFX_WM_UPDATETOOLTIPS
- AFX_WM_ON_MOVE_TAB
- AFX_WM_CHANGING_ACTIVE_TAB
- AFX_WM_RESETMENU
- AFX_WM_GETDRAGBOUNDS
- AFX_WM_RESETCONTEXTMENU
- AFX_TOOLTIP_TYPE_BUTTON
- AFX_WM_ON_CLOSEPOPUPWINDOW
- AFX_TOOLTIP_TYPE_TOOLBOX
- AFX_WM_CHANGEVISUALMANAGER
- SB_LINERIGHT
- AFX_WM_ON_RENAME_TAB
- AFX_TOOLTIP_TYPE_DEFAULT
- AFX_WM_ON_TABGROUPMOUSEMOVE
- SB_LEFT
- AFX_WM_DELETETOOLBAR
- AFX_WM_PROPERTY_CHANGED
- AFX_TOOLTIP_TYPE_ALL
- AFX_WM_ACCHITTEST
- AFX_WM_ON_AFTER_SHELL_COMMAND
- AFX_WM_ON_PRESS_CLOSE_BUTTON
- AFX_WM_RESETKEYBOARD
- AFX_WM_ON_MOVETABCOMPLETE
- AFX_WM_CREATETOOLBAR
- SB_THUMBPOSITION
- AFX_WM_POSTSETPREVIEWFRAME
dev_langs:
- C++
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 41f300f285fb4eaf1a6154a21cbbabc0253fc730
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="afx-messages"></a>Komunikaty AFX
Komunikaty te są używane w MFC.  
  
## <a name="messages"></a>Komunikaty  
 Poniższa tabela zawiera listę komunikatów, które są używane w bibliotece MFC:  
  
||||||  
|-|-|-|-|-|  
|Komunikat|Opis|[in]`wParam`|`lParam`(Wszystkie parametry są [in] chyba że określono inaczej).|Wartość zwracana|  
|AFX_WM_ACCGETOBJECT|Nie używany.|Nie używany.|Nie dotyczy.|Nie dotyczy.|  
|AFX_WM_ACCGETSTATE|Używany dla ułatwień dostępu pomocy technicznej. Ten komunikat, aby wysłać `CMFCPopupMenu` lub `CMFCRibbonPanelMenu` można pobrać stanu bieżącego elementu.|Indeks elementu, który może być przycisk menu i separatora.|Nie używany.|Stan elementu. Jeśli indeks jest nieprawidłowy, -1 jest równa 0, jeśli przycisku menu nie ma żadnych specjalnych atrybutów. W przeciwnym razie jest kombinacją następujące flagi:<br /><br /> TBBS_DISABLED — element jest wyłączony.<br /><br /> TBBS_CHECKED — element jest zaznaczony.<br /><br /> TBBS_BUTTON — element jest standardowe przycisku polecenia<br /><br /> TBBS_PRESSED — przycisk jest naciśnięty.<br /><br /> TBBS_INDETERMINATE — Niezdefiniowany stanu<br /><br /> TBBS_SEPARATOR — zamiast przycisku menu stanowi element odstęp między innymi elementami menu|  
|AFX_WM_CHANGE_ACTIVE_TAB|Platformę wysyła wiadomość do formantu paska formantu o zmiennym rozmiarze. Przetwarzać tego komunikatu, aby otrzymywać powiadomienia z `CMFCTabCtrl` obiektów, gdy użytkownik zmienia aktywnej karty.|Indeks karty.|Nie używany.|Różna od zera.|  
|AFX_WM_CHANGE_CURRENT_FOLDER|Platformę wysyła wiadomość do nadrzędnego `CMFCShellListCtrl` gdy użytkownik zmienił bieżącego folderu.|Nie używany.|Nie używany.|Nie używany.|  
|AFX_WM_CHANGEVISUALMANAGER|Platformę wysyła wiadomość do wszystkich okien ramowych, gdy użytkownik zmieni bieżący Menedżer Visual. W odpowiedzi na tę wiadomość okno ramowe ponownie oblicza regionu i dostosowuje innych parametrów, zgodnie z potrzebami. W aplikacji może przetworzyć komunikatu AFX_WM_CHANGEVISUALMANAGER, jeśli chcesz otrzymywać powiadomienia o tego zdarzenia. Należy wywołać obsługi klasy podstawowej (`OnChangeVisualManager`) aby upewnić się, że platformę obiektu wewnętrznego odbywa się przetwarzanie tego zdarzenia.|Nie używany.|Nie używany.|Nie używany.|  
|AFX_WM_CHANGING_ACTIVE_TAB|Wysyłane do nadrzędnego `CMFCTabCtrl` obiektu.  Przetwarzać tego komunikatu, jeśli chcesz otrzymywać powiadomienia z `CMFCTabCtrl` obiekty użytkownika zresetowaniu karty.|Indeks kartę, która jest aktywowane.|Nie używany.|Różna od zera.|  
|AFX_WM_CHECKEMPTYMINIFRAME|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|  
|AFX_WM_CREATETOOLBAR|Wysyłane z `CMFCToolBarsListPropertyPage` gdy użytkownik tworzy nowy pasek narzędzi podczas procesu dostosowywania. Mogą przetwarzać tego komunikatu, można utworzyć wystąpienia niestandardowego obiektu pochodnego CMFCToolBar. Jeśli obsłużyć ten komunikat i tworzyć własne paski narzędzi, pomiń wywołanie domyślny program obsługi.|Nie używany.|Wskaźnik do ciągu zawierającego nazwę paska narzędzi.|Wskaźnik do nowo utworzonego paska narzędzi. Wartości NULL wskazuje, czy Anulowano Tworzenie narzędzi.|  
|AFX_WM_CUSTOMIZEHELP|Wysyłane do głównego okna ramowego z arkusza właściwości dostosowywania `CMFCToolbarCustomize Dialog` gdy użytkownik naciśnie **pomocy** przycisku lub klawisza F1.|Określa stronę aktywnego arkusza właściwości dostosowywania.|Wskaźnik do `CMFCToolbarCustomize Dialog` obiektu.|Zero.|  
|AFX_WM_CUSTOMIZETOOLBAR|`CMFCToolbarCustomize Dialog` Wysyła tę wiadomość, aby powiadomić ramka nadrzędny użytkownik tworzy nowy pasek narzędzi.|`TRUE`Po uruchomieniu dostosowania `FALSE` po zakończeniu dostosowywania.|Nie używany.|Zero.|  
|AFX_WM_DELETETOOLBAR|Wysyłany do głównego okna ramowego, gdy użytkownik należy usunąć w trybie Dostosowywanie paska narzędzi.<br /><br /> Przetwarzać tego komunikatu, aby podejmować dodatkowe akcje, gdy użytkownik usuwa w trybie Dostosowywanie paska narzędzi. Należy także wywołać domyślny program obsługi (`OnToolbarDelete`), które powoduje usunięcie paska narzędzi. Domyślny program obsługi zwraca wartość wskazującą, czy jest możliwe usuwanie na pasku narzędzi.|Nie używany.|Wskaźnik do `CMFCToolBar` obiektu do usunięcia.|Różna od zera, jeśli nie można usunąć pasek narzędzi; w przeciwnym razie 0.|  
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton`wysyła wiadomość do głównego okna ramowego można pobrać kolorów dokumentu.|Nie używany.|[w, out] Wskaźnik do `CList<COLORREF, COLORREF>` obiektu.|Zero.|  
|AFX_WM_GETDRAGBOUNDS|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|  
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Wysyłany do głównego okna ramowego, gdy użytkownik wyróżnia elementu wstążki.|Indeks wyróżniony element|Wskaźnik do`CMFCBaseRibbonElement`|Nie używany.|  
|AFX_WM_ON_AFTER_SHELL_COMMAND|Wysyłane do elementu nadrzędnego `CMFCShellListCtrl` lub `CMFCShellTreeCtrl` steruje po zakończeniu wykonywania polecenia powłoki użytkownika.|Identyfikator polecenia, które są wykonywane przez użytkownika|Nie używany.|Jeśli aplikacja przetwarza ten komunikat, powinien on zwrócić wartość zero.|  
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|Platformę wysyła wiadomość do nadrzędnego wstążki, przed wyświetleniem menu podręczne. Mogą przetwarzać tego komunikatu i zmodyfikować menu podręcznego w dowolnym momencie.|Nie używany.|Wskaźnik do`CMFCBaseRibbonElement`|Nie używany.|  
|AFX_WM_ON_CANCELTABMOVE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.||  
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|Platformę wysyła wiadomość do ramki głównej, gdy użytkownik zmieni aktywnej kategorii kontroli wstążki.|Nie używany.|Wskaźnik do `CMFCRibbonBar` których kategorii została zmieniona.|Nie używany.|  
|AFX_WM_ON_CLOSEPOPUPWINDOW|Platformę wysyła ten komunikat, aby poinformować o tym właściciela `CMFCDesktopAlertWnd` że okno zostanie zamknięte.|Nie używany.|Wskaźnik do `CMFCDesktopAlertWnd` obiektu.|Nie używany.|  
|AFX_WM_ON_DRAGCOMPLETE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|  
|AFX_WM_ON_GET_TAB_TOOLTIP|Wysyłane do głównego okna ramowego, gdy okno karty ma wyświetlić etykietkę narzędzia dla karty, jeśli włączono niestandardowych etykietek narzędzi.|Nie używany.|Wskaźnik do `CMFCTabToolTipInfo` struktury.|Nie używany.|  
|AFX_WM_ON_HSCROLL|Wysyłane do formantu paska formantu o zmiennym rozmiarze. Przetwarzać tego komunikatu, aby otrzymywać powiadomienia z `CMFCTabCtrl` obiektów po wystąpieniu zdarzenia przewijania na pasku przewijania w poziomie z kartami elementu widget.|Word znaczącymi bitami określa wartość paska przewijania, która wskazuje użytkownika na przewijanie żądania.  Aby uzyskać więcej informacji zobacz tabelę w dalszej części tego tematu.|Nie używany.|Różna od zera.|  
|AFX_WM_ON_MOVE_TAB|Wysyłany do nadrzędnego okna z kartami, gdy użytkownik przeciąga kartę do nowej pozycji.|Liczony od zera indeks karty w oryginalnego położenia.|[out] Liczony od zera indeks kartę w nowej lokalizacji.|Zero.|  
|AFX_WM_ON_MOVETABCOMPLETE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|  
|AFX_WM_ON_MOVETOTABGROUP|Wysyłany do głównego okna ramowego, gdy użytkownik przesuwa okno podrzędne MDI z jednej grupy z kartami na inny.|Dojście do okna z kartami (`CMFCTabCtrl`) z której usunięto okna podrzędnego MDI.|[out] Dojście do okna z kartami (`CMFCTabCtrl`) do którego został wstawiony okna podrzędnego MDI.|Ignorowane.|  
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Wysyłane do elementu nadrzędnego `CDockablePane` gdy użytkownik kliknie **Zamknij** przycisk na podpis pasek sterowania.|Nie używany.|Wskaźnik do okienka zadokowane, na którym użytkownik kliknął **Zamknij** przycisku.|`TRUE`Jeśli nie można zamknąć okienko; w przeciwnym razie wartość FALSE.|  
|AFX_WM_ON_RENAME_TAB|Wysyłane do nadrzędnego okna z kartami po kartę można edytować nazwy użytkownika.|Liczony od zera indeks karcie zmienioną nazwę.|[out] Wskaźnik do ciąg, który zawiera nową nazwę karty.|Różna od zera, jeśli aplikacja przetwarza tego komunikatu. platformę blokuje wyświetlanie wywołanie `CMFCBaseTabCtrl::SetTabLabel`.  Jeśli zero jest zwracany, następnie `CMFCBaseTabCtrl::SetTabLabel` jest wywoływana przez platformę.|  
|AFX_WM_ON_RIBBON_CUSTOMIZE|Wysyłany do ramka nadrzędny, gdy użytkownik uruchamia dostosowania. Przetwarzać tego komunikatu, jeśli chcesz wyświetlić okno dialogowe własne dostosowania.|Nie używany.|Wskaźnik do sterowania wstążki do dostosowania.|Różna od zera, jeśli aplikacja przetwarza ten komunikat i wyświetla okno dialogowe własne dostosowania. Jeśli aplikacja zwraca zero, platformę wyświetlane okno dialogowe wbudowanych dostosowania.|  
|AFX_WM_ON_TABGROUPMOUSEMOVE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|  
|AFX_WM_POSTSETPREVIEWFRAME|Wysyłane do ramki głównej powiadomienia, że użytkownik zmienił tryb podglądu wydruku|`TRUE`Wskazuje, że ustawiono tryb podglądu wydruku. `FALSE`Wskazuje, że ten tryb podglądu wydruku jest wyłączony.|Nie używany.|Nie używany.|  
|AFX_WM_PROPERTY_CHANGED|Wysyłany do właściciela właściwości kontrolki siatki (`CMFCPropertyGridCtrl`) podczas zmiany wartości właściwości wybranego użytkownika.|Identyfikator formantu listy właściwości.|Wskaźnik do właściwości (`CMFCPropertyGridProperty`) zmianie.|Nie używany.|  
|AFX_WM_RESETCONTEXTMENU|Wysyłany do głównego okna ramowego, gdy użytkownik resetuje menu kontekstowe podczas dostosowywania.|Identyfikator zasobu menu kontekstowego.|Wskaźnik do bieżącego menu kontekstowego, `CMFCPopupMenu`.|Nie używany.|  
|AFX_WM_RESETKEYBOARD|Platformę wysyła wiadomość do głównego okna ramowego, gdy użytkownik resetuje wszystkie klawiaturowymi podczas dostosowywania.|Nie używany.|Nie używany.|Nie używany.|  
|AFX_WM_RESETMENU|Platformę wysyła wiadomość do właściciela menu (okno ramowe) gdy użytkownik resetuje menu ramki aplikacji podczas dostosowywania|Identyfikator zasobu menu.|Nie używany.|Nie używany.|  
|AFX_WM_RESETPROMPT|Platformę wysyła tę wiadomość, gdy okno dialogowe Dostosowywanie resetuje użytkownika na pasku narzędzi z paska narzędzi. Domyślny program obsługi wyświetla komunikat z pytaniem, czy użytkownik chce zresetować na pasku narzędzi.|Nie używany.|Nie używany.|Nie używany.|  
|AFX_WM_RESETTOOLBAR|A `CMFCToolBar` obiekt wysyła tę wiadomość, gdy pasek narzędzi zostanie przywrócony do stanu pierwotnego, oznacza to, ładowanych z zasobów. Przetwarzać tego komunikatu, aby ponownie przycisków paska narzędzi, których klasy pochodne `CMFCToolbarButton`. Aby uzyskać więcej informacji, zobacz `CMFCToolbarComboBoxButton`.|Identyfikator zasobu paska narzędzi, których stan został przywrócony.|Nie używany.|Zero.|  
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton`obiekt wysyła wiadomość do jego właściciela, gdy użytkownik kliknie przycisk menu regularne. Przetwarzać tego komunikatu, zawsze należy używać `CMFCToolbarMenuButton` mają być wyświetlane menu podręczne, gdy użytkownik kliknie przycisk.|Identyfikator polecenia przycisku, który wysyła wiadomość.|Współrzędne ekranu kursora. Word znaczącymi bitami Określa współrzędną x. Word znaczących Określa współrzędną y.|Nie używany.|  
|AFX_WM_TOOLBARMENU|Wysyłany do głównego okna ramowego, gdy użytkownik zwolni prawy przycisk myszy, gdy wskaźnik myszy znajduje się w kliencie lub obszaru nieklienckiego okienka.|Nie używany.|Współrzędne ekranu wskaźnik myszy. Word znaczącymi bitami Określa współrzędną x. Word znaczących Określa współrzędną y.|Zero, jeśli aplikacja przetwarza tego komunikatu. w przeciwnym razie wartość różna od zera.|  
|AFX_WM_UPDATETOOLTIPS|Wysłane do wszystkich właścicieli etykietka narzędzia, aby wskazać, że ich kontrolek typu etykieta powinien być tworzony ponownie.|Typ formantu, który powinien przetwarzać tego komunikatu. Znajdują się w tabeli w dalszej części tego tematu, aby uzyskać listę możliwych wartości.|Nie używany.|Nie używany.|  
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog`wysyła wiadomość do ramka nadrzędny, gdy użytkownik kliknie **pomocy** przycisk lub przejdzie do trybu pomocy, klikając **pomocy** przycisku Podpis lub klawisz F1.|Nie używany.|Wskaźnik do wystąpienia `CMFCWindowsManagerDialog`.|Nie używany.|  
  
 W poniższej tabeli przedstawiono wartości niższe słowo `lParam` parametru metody AFX_WM_HSCROLL:  
  
|||  
|-|-|  
|Wartość|Znaczenie|  
|SB_ENDSCROLL|Użytkownik kończy przewijania.|  
|SB_LEFT|Użytkownik przewija widok lewego górnego.|  
|SB_RIGHT|Użytkownik przewija widok prawym dolnym.|  
|SB_LINELEFT|Użytkownik przewija lewej przez jedną jednostkę.|  
|SB_LINERIGHT|Użytkownik przewija przez jedną jednostkę.|  
|SB_PAGELEFT|Użytkownik przewija lewej przez szerokość okna.|  
|SB_PAGERIGHT|Użytkownik przewija widok w prawo o szerokość okna.|  
|SB_THUMBPOSITION|Użytkownik ma przeciągnąć pola przewijania (przenośny) i wydane przycisk myszy. Word znaczącymi bitami wskazuje pozycję pola przewijania na koniec operacji przeciągania.|  
|SB_THUMBTRACK|Użytkownik przeciąga pole przewijania. AFX_WM_ON_HSCROLL wiadomości jest często z tej wartości dopóki użytkownik zwolni przycisk myszy. Wyraz znaczącymi bitami oznacza sytuację, do którego został przeciągnięty pole przewijania.|  
  
> [!NOTE]
>  Wyrazu znaczącymi bitami `lParam` parametr określa bieżącą pozycję pola przewijania w przypadku programu word znaczącymi bitami SB_THUMBPOSITION lub SB_THUMBTRACK; w przeciwnym razie nie jest używany ten wyraz.  
  
 W poniższej tabeli wymieniono wartości flag `lParam` parametru komunikatu AFX_WM_UPDATETOOLTIPS:  
  
|||  
|-|-|  
|Flaga|Wartość|  
|AFX_TOOLTIP_TYPE_DEFAULT|0X0001|  
|AFX_TOOLTIP_TYPE_TOOLBAR|0X0002|  
|AFX_TOOLTIP_TYPE_TAB|0X0004|  
|AFX_TOOLTIP_TYPE_MINIFRAME|0X0008|  
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|  
|AFX_TOOLTIP_TYPE_EDIT|0x0020|  
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|  
|AFX_TOOLTIP_TYPE_TOOLBOX|0x0080|  
|AFX_TOOLTIP_TYPE_ALL|0xFFFF|  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
