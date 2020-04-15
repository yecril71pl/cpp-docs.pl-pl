---
title: Komunikaty AFX
ms.date: 11/04/2016
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
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
ms.openlocfilehash: b4ed86c11d3c5b5f1ce38e3146533109f3a6b00d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363598"
---
# <a name="afx-messages"></a>Komunikaty AFX

Te komunikaty są używane w MFC.

## <a name="messages"></a>Komunikaty

W poniższej tabeli wymieniono komunikaty używane w bibliotece MFC:

||||||
|-|-|-|-|-|
|Komunikat|Opis|[w] *wParam*|*lParam* (Wszystkie parametry są [w], chyba że podano inaczej.)|Wartość zwracana|
|AFX_WM_ACCGETOBJECT|Nie używany.|Nie używany.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_ACCGETSTATE|Służy do obsługi ułatwień dostępu. Wyślij tę `CMFCPopupMenu` wiadomość `CMFCRibbonPanelMenu` do lub pobrać stan bieżącego elementu.|Indeks elementu, który może być przyciskiem menu lub separatorem.|Nie używany.|Stan elementu. Jest -1, jeśli indeks jest nieprawidłowy, 0, jeśli przycisk menu nie ma specjalnych atrybutów. W przeciwnym razie jest to kombinacja następujących flag:<br /><br /> TBBS_DISABLED — element jest wyłączony<br /><br /> TBBS_CHECKED — element jest sprawdzany<br /><br /> TBBS_BUTTON — element jest standardowym przyciskiem<br /><br /> TBBS_PRESSED — przycisk jest wciśnięty<br /><br /> TBBS_INDETERMINATE — stan niezdefiniowany<br /><br /> TBBS_SEPARATOR - zamiast przycisku menu, ten element tworzy oddzielenie innych elementów menu|
|AFX_WM_CHANGE_ACTIVE_TAB|Struktura wysyła ten komunikat do formantu paska sterowania o zmiennym rozmiarze. Przetwórz ten komunikat, `CMFCTabCtrl` aby otrzymywać powiadomienia z obiektów, gdy użytkownik zmieni aktywną kartę.|Indeks karty.|Nie używany.|Niezerowa.|
|AFX_WM_CHANGE_CURRENT_FOLDER|Struktura wysyła ten komunikat do `CMFCShellListCtrl` nadrzędnego, gdy użytkownik zmienił bieżący folder.|Nie używany.|Nie używany.|Nie używany.|
|AFX_WM_CHANGEVISUALMANAGER|Struktura wysyła ten komunikat do wszystkich okien ramki, gdy użytkownik zmienia bieżącego Menedżera wizualnego. W odpowiedzi na ten komunikat okno ramki ponownie oblicza jego region i dostosowuje inne parametry w razie potrzeby. Można przetworzyć komunikat AFX_WM_CHANGEVISUALMANAGER w aplikacji, jeśli chcesz otrzymywać powiadomienia o tym zdarzeniu. Należy wywołać program obsługi`OnChangeVisualManager`klasy podstawowej ( ), aby upewnić się, że odbywa się wewnętrzne przetwarzanie tej struktury.|Nie używany.|Nie używany.|Nie używany.|
|AFX_WM_CHANGING_ACTIVE_TAB|Wysłane do obiektu `CMFCTabCtrl` nadrzędnego.  Przetwórz ten komunikat, jeśli `CMFCTabCtrl` chcesz otrzymywać powiadomienia z obiektów, gdy użytkownik resetuje kartę.|Indeks karty, która jest aktywowana.|Nie używany.|Niezerowa.|
|AFX_WM_CHECKEMPTYMINIFRAME|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_CREATETOOLBAR|Wysyłane `CMFCToolBarsListPropertyPage` z gdy użytkownik tworzy nowy pasek narzędzi podczas procesu dostosowywania. Można przetworzyć ten komunikat, aby utworzyć wystąpienie niestandardowego obiektu pochodnego CMFCToolBar. Jeśli obsługujesz ten komunikat i tworzysz własny pasek narzędzi, pomiń wywołanie domyślnego programu obsługi.|Nie używany.|Wskaźnik do ciągu zawierającego nazwę paska narzędzi.|Wskaźnik do nowo utworzonego paska narzędzi. NULL oznacza, że utworzenie paska narzędzi zostało anulowane.|
|AFX_WM_CUSTOMIZEHELP|Wysyłane do okna ramki głównej z `CMFCToolbarCustomize Dialog` arkusza właściwości dostosowywania, gdy użytkownik naciśnie przycisk **Pomocy** lub klawisz F1.|Określa aktywną stronę arkusza właściwości dostosowywania.|Wskaźnik do `CMFCToolbarCustomize Dialog` obiektu.|Zero.|
|AFX_WM_CUSTOMIZETOOLBAR|Wysyła `CMFCToolbarCustomize Dialog` ten komunikat, aby powiadomić ramkę nadrzędną, że użytkownik tworzy nowy pasek narzędzi.|PRAWDA po rozpoczęciu dostosowywania, FAŁSZ po zakończeniu dostosowywania.|Nie używany.|Zero.|
|AFX_WM_DELETETOOLBAR|Wysyłane do okna ramki głównej, gdy użytkownik ma zamiar usunąć pasek narzędzi w trybie dostosowywania.<br /><br /> Przetwórz ten komunikat, aby wykonać dodatkowe akcje, gdy użytkownik usunie pasek narzędzi w trybie dostosowywania. Należy również wywołać domyślny program obsługi (`OnToolbarDelete`), który usuwa pasek narzędzi. Domyślny program obsługi zwraca wartość, która wskazuje, czy możliwe jest usunięcie paska narzędzi.|Nie używany.|Wskaźnik do `CMFCToolBar` obiektu do usunięcia.|Niezerowe, jeśli nie można usunąć paska narzędzi; w przeciwnym razie 0.|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton`wysyła ten komunikat do okna ramki głównej, aby pobrać kolory dokumentu.|Nie używany.|[w, na zewnątrz] Wskaźnik do `CList<COLORREF, COLORREF>` obiektu.|Zero.|
|AFX_WM_GETDRAGBOUNDS|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Wysyłane do okna ramki głównej, gdy użytkownik podświetla element listy wstążki.|Indeks wyróżnionego elementu|Wskaźnik do`CMFCBaseRibbonElement`|Nie używany.|
|AFX_WM_ON_AFTER_SHELL_COMMAND|Wysyłane do podmiotu nadrzędnego `CMFCShellListCtrl` lub `CMFCShellTreeCtrl` formanty, gdy użytkownik kończy wykonywanie polecenia powłoki.|Identyfikator polecenia, które użytkownik wykonał|Nie używany.|Jeśli aplikacja przetwarza ten komunikat, należy zwrócić zero.|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|Struktura wysyła ten komunikat do nadrzędnego wstążki, zanim wyświetli menu podręczne. Tę wiadomość można przetworzyć i zmodyfikować menu podręczne w dowolnym momencie.|Nie używany.|Wskaźnik do`CMFCBaseRibbonElement`|Nie używany.|
|AFX_WM_ON_CANCELTABMOVE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|Struktura wysyła ten komunikat do ramki głównej, gdy użytkownik zmieni kategorię aktywnego sterowania wstążką.|Nie używany.|Wskaźnik do `CMFCRibbonBar` której kategorii została zmieniona.|Nie używany.|
|AFX_WM_ON_CLOSEPOPUPWINDOW|Struktura wysyła ten komunikat, aby `CMFCDesktopAlertWnd` powiadomić właściciela, że okno ma zostać zamknięte.|Nie używany.|Wskaźnik do `CMFCDesktopAlertWnd` obiektu.|Nie używany.|
|AFX_WM_ON_DRAGCOMPLETE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_ON_GET_TAB_TOOLTIP|Wysyłane do okna ramki głównej, gdy okno karty ma być wyświetlane etykietki narzędzia dla karty, jeśli niestandardowe etykietki narzędzi są włączone.|Nie używany.|Wskaźnik do `CMFCTabToolTipInfo` struktury.|Nie używany.|
|AFX_WM_ON_HSCROLL|Wysyłane do kontrolki paska sterowania o zmiennym rozmiarze. Przetwórz ten komunikat, `CMFCTabCtrl` aby otrzymywać powiadomienia z obiektów, gdy wystąpi zdarzenie przewijania na pasku przewijania widżetu z kartami.|Słowo niskiego rzędu określa wartość paska przewijania, która wskazuje żądanie przewijania użytkownika.  Aby uzyskać więcej informacji, zobacz tabelę w dalszej części tego tematu.|Nie używany.|Niezerowa.|
|AFX_WM_ON_MOVE_TAB|Wysyłane do rodzica okna z kartami, gdy użytkownik przeciągnie kartę do nowej pozycji.|Indeks od zera karty w jego oryginalnej pozycji.|[na zewnątrz] Indeks od zera karty w nowej pozycji.|Zero.|
|AFX_WM_ON_MOVETABCOMPLETE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_ON_MOVETOTABGROUP|Wysyłane do okna ramki głównej, gdy użytkownik przenosi okno podrzędne MDI z jednej grupy z kartami do innej.|Uchwyt do okna z`CMFCTabCtrl`kartami ( ), z którego usunięto okno podrzędne MDI.|[na zewnątrz] Uchwyt do okna z`CMFCTabCtrl`kartami ( ), do którego zostało wstawione okno podrzędne MDI.|Ignorowane.|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Wysyłane do rodzica, `CDockablePane` gdy użytkownik kliknie przycisk **Zamknij** na podpisie paska sterowania.|Nie używany.|Wskaźnik do okienka, w którym użytkownik kliknął przycisk **Zamknij.**|PRAWDA, jeśli nie można zamknąć okienka; w przeciwnym razie FALSE.|
|AFX_WM_ON_RENAME_TAB|Wysłane do nadrzędnego okna z kartami po zmianie nazwy karty edytowalnej przez użytkownika.|Indeks od zera karty o zmienionej nazwie.|[na zewnątrz] Wskaźnik do ciągu zawierającego nową nazwę karty.|Nonzero, jeśli aplikacja przetwarza ten komunikat; ramy będą pomijać `CMFCBaseTabCtrl::SetTabLabel`wezwanie do .  Jeśli zero jest `CMFCBaseTabCtrl::SetTabLabel` zwracany, a następnie jest wywoływana przez strukturę.|
|AFX_WM_ON_RIBBON_CUSTOMIZE|Wysyłane do ramki nadrzędnej, gdy użytkownik rozpoczyna dostosowywanie. Przetwórz ten komunikat, jeśli chcesz wyświetlić własne okno dialogowe dostosowywania.|Nie używany.|Wskaźnik do formantu wstążki do dostosowania.|Nonzero, jeśli aplikacja przetwarza ten komunikat i wyświetla własne okno dialogowe dostosowywania. Jeśli aplikacja zwraca zero, struktura wyświetli wbudowane okno dialogowe dostosowywania.|
|AFX_WM_ON_TABGROUPMOUSEMOVE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_POSTSETPREVIEWFRAME|Wysłane w celu powiadomienia ramki głównej o zmianie trybu podglądu wydruku przez użytkownika|Funkcja PRAWDA wskazuje, że ustawiony jest tryb podglądu wydruku. FALSE wskazuje, że tryb podglądu wydruku jest wyłączony.|Nie używany.|Nie używany.|
|AFX_WM_PROPERTY_CHANGED|Wysyłane do właściciela formantu`CMFCPropertyGridCtrl`siatki właściwości ( ), gdy użytkownik zmienia wartość wybranej właściwości.|Identyfikator formantu listy właściwości.|Wskaźnik do właściwości`CMFCPropertyGridProperty`( ), który uległ zmianie.|Nie używany.|
|AFX_WM_RESETCONTEXTMENU|Wysyłane do okna ramki głównej, gdy użytkownik resetuje menu kontekstowe podczas dostosowywania.|Identyfikator zasobu menu kontekstowego.|Wskaźnik do bieżącego menu `CMFCPopupMenu`kontekstowego , .|Nie używany.|
|AFX_WM_RESETKEYBOARD|Struktura wysyła ten komunikat do okna ramki głównej, gdy użytkownik resetuje wszystkie akceleratory klawiatury podczas dostosowywania.|Nie używany.|Nie używany.|Nie używany.|
|AFX_WM_RESETMENU|Struktura wysyła ten komunikat do właściciela menu (okno ramki), gdy użytkownik resetuje menu ramki aplikacji podczas dostosowywania|Identyfikator zasobu menu.|Nie używany.|Nie używany.|
|AFX_WM_RESETPROMPT|Struktura wysyła ten komunikat, gdy użytkownik resetuje pasek narzędzi z paska narzędzi dostosować okno dialogowe. Domyślny program obsługi wyświetla okno komunikatu z pytaniem, czy użytkownik chce zresetować pasek narzędzi.|Nie używany.|Nie używany.|Nie używany.|
|Afx_wm_resettoolbar|Obiekt `CMFCToolBar` wysyła ten komunikat, gdy pasek narzędzi zostanie przywrócony do stanu pierwotnego, czyli załadowany z zasobów. Przetwórz ten komunikat, aby ponownie wstawić `CMFCToolbarButton`przyciski paska narzędzi, których klasy pochodzą od . Aby uzyskać więcej informacji, zobacz `CMFCToolbarComboBoxButton`.|Identyfikator zasobu paska narzędzi, którego stan został przywrócony.|Nie używany.|Zero.|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton`obiekt wysyła ten komunikat do właściciela, gdy użytkownik kliknie przycisk menu zwykłego. Przetwarzaj ten komunikat za `CMFCToolbarMenuButton` każdym razem, gdy używasz do wyświetlania menu podręcznego, gdy użytkownik kliknie przycisk.|Identyfikator polecenia przycisku, który wysyła wiadomość.|Współrzędne ekranu kursora. Słowo niskiego rzędu określa współrzędną x. Słowo wysokiego rzędu określa współrzędną y.|Nie używany.|
|AFX_WM_TOOLBARMENU|Wysyłane do okna ramki głównej, gdy użytkownik zwalnia prawy przycisk myszy, gdy wskaźnik myszy znajduje się w obszarze klienta lub nie-klienta okienka.|Nie używany.|Współrzędne ekranu wskaźnika myszy. Słowo niskiego rzędu określa współrzędną x. Słowo wysokiego rzędu określa współrzędną y.|Zero, jeśli aplikacja przetwarza ten komunikat; w przeciwnym razie, nonzero.|
|AFX_WM_UPDATETOOLTIPS|Wysłane do wszystkich właścicieli etykietki narzędzi, aby wskazać, że ich formanty etykietki narzędzia powinny być odtworzone.|Typ formantu, który powinien przetwarzać ten komunikat. Zobacz tabelę w dalszej części tego tematu, aby uzyskać listę możliwych wartości.|Nie używany.|Nie używany.|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog`wysyła tę wiadomość do ramki nadrzędnej, gdy użytkownik kliknie przycisk **Pomoc** lub wejdzie w tryb pomocy, klikając przycisk Podpis **Pomocy** lub klawisz F1.|Nie używany.|Wskaźnik do wystąpienia `CMFCWindowsManagerDialog`.|Nie używany.|

W poniższej tabeli przedstawiono wartości niskiego wyrazu parametru *lParam* metody AFX_WM_HSCROLL:

|||
|-|-|
|Wartość|Znaczenie|
|SB_ENDSCROLL|Użytkownik kończy przewijanie.|
|SB_LEFT|Użytkownik przewija do lewego górnego rogu.|
|SB_RIGHT|Użytkownik przewija do prawego dolnego.|
|SB_LINELEFT|Użytkownik przewija się w lewo o jedną jednostkę.|
|SB_LINERIGHT|Użytkownik przewija w prawo o jedną jednostkę.|
|SB_PAGELEFT|Użytkownik przewija w lewo o szerokość okna.|
|SB_PAGERIGHT|Użytkownik przewija w prawo o szerokość okna.|
|SB_THUMBPOSITION|Użytkownik przeciągnął pole przewijania (kciuk) i zwolnił przycisk myszy. Wyraz wysokiego rzędu wskazuje położenie pola przewijania na końcu operacji przeciągania.|
|SB_THUMBTRACK|Użytkownik przeciąga pole przewijania. Wiadomość AFX_WM_ON_HSCROLL jest wysyłana wielokrotnie z tą wartością, dopóki użytkownik nie zwolni przycisku myszy. Słowo wysokiego rzędu wskazuje pozycję, do której przeciągnięto pole przewijania.|

> [!NOTE]
> Słowo wysokiego rzędu parametru *lParam* określa bieżącą pozycję pola przewijania, jeśli słowo niskiego rzędu jest SB_THUMBPOSITION lub SB_THUMBTRACK; w przeciwnym razie słowo to nie jest używane.

W poniższej tabeli wymieniono wartości flag dla parametru *lParam* komunikatu AFX_WM_UPDATETOOLTIPS:

|||
|-|-|
|Flaga|Wartość|
|AFX_TOOLTIP_TYPE_DEFAULT|0x0001|
|AFX_TOOLTIP_TYPE_TOOLBAR|0x0002|
|AFX_TOOLTIP_TYPE_TAB|0x0004|
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|
|AFX_TOOLTIP_TYPE_EDIT|0x0020|
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|
|AFX_TOOLTIP_TYPE_TOOLBOX|0x0080|
|AFX_TOOLTIP_TYPE_ALL|0xFFFF|

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
