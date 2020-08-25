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
ms.openlocfilehash: 409760eff6ba6b31413c11fb45ea91a6d07b9485
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832402"
---
# <a name="afx-messages"></a>Komunikaty AFX

Te komunikaty są używane w MFC.

## <a name="messages"></a>Komunikaty

W poniższej tabeli wymieniono komunikaty, które są używane w bibliotece MFC:

|Komunikat|Opis|podczas *wParam*|*lParam* (wszystkie parametry są [in], chyba że określono inaczej).|Wartość zwracana|
|-|-|-|-|-|
|AFX_WM_ACCGETOBJECT|Nie używany.|Nie używany.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_ACCGETSTATE|Służy do obsługi ułatwień dostępu. Wyślij tę wiadomość do `CMFCPopupMenu` lub, `CMFCRibbonPanelMenu` Aby pobrać stan bieżącego elementu.|Indeks elementu, który może być przyciskiem menu lub separatorem.|Nie używany.|Stan elementu. Jeśli indeks jest nieprawidłowy, wartość jest równa 0, jeśli przycisk menu nie ma specjalnych atrybutów. W przeciwnym razie jest to kombinacja następujących flag:<br /><br /> TBBS_DISABLED — element jest wyłączony<br /><br /> TBBS_CHECKED — element jest zaznaczony<br /><br /> TBBS_BUTTON — element to standardowy przycisk<br /><br /> TBBS_PRESSED — przycisk jest wciśnięty<br /><br /> TBBS_INDETERMINATE — niezdefiniowany stan<br /><br /> TBBS_SEPARATOR — a nie przycisk menu, ten element tworzy separację między innymi elementami menu.|
|AFX_WM_CHANGE_ACTIVE_TAB|Struktura wysyła ten komunikat do kontrolki pasek kontroli o zmiennym rozmiarze. Przetwórz ten komunikat, aby otrzymywać powiadomienia z `CMFCTabCtrl` obiektów, gdy użytkownik zmieni aktywną kartę.|Indeks karty.|Nie używany.|Różną od zera.|
|AFX_WM_CHANGE_CURRENT_FOLDER|Struktura wysyła ten komunikat do elementu nadrzędnego, `CMFCShellListCtrl` gdy użytkownik zmienił folder bieżący.|Nie używany.|Nie używany.|Nie używany.|
|AFX_WM_CHANGEVISUALMANAGER|Ta wiadomość jest wysyłana do wszystkich okien ramowych, gdy użytkownik zmieni bieżący program Visual Manager. W odpowiedzi na ten komunikat okno ramki ponownie oblicza jego region i dostosowuje inne parametry zgodnie z wymaganiami. Jeśli musisz otrzymywać powiadomienia o tym zdarzeniu, możesz przetworzyć AFX_WM_CHANGEVISUALMANAGER komunikat w aplikacji. Musisz wywołać procedurę obsługi klasy podstawowej ( `OnChangeVisualManager` ), aby upewnić się, że jest używane wewnętrzne przetwarzanie tego zdarzenia.|Nie używany.|Nie używany.|Nie używany.|
|AFX_WM_CHANGING_ACTIVE_TAB|Wysyłany do obiektu nadrzędnego `CMFCTabCtrl` .  Przetwórz ten komunikat, jeśli chcesz otrzymywać powiadomienia z `CMFCTabCtrl` obiektów, gdy użytkownik resetuje kartę.|Indeks aktywowanej karty.|Nie używany.|Różną od zera.|
|AFX_WM_CHECKEMPTYMINIFRAME|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_CREATETOOLBAR|Wysyłane z, `CMFCToolBarsListPropertyPage` gdy użytkownik tworzy nowy pasek narzędzi podczas procesu dostosowywania. Można przetworzyć ten komunikat, aby utworzyć wystąpienie niestandardowego obiektu pochodnego CMFCToolBar. Jeśli ta wiadomość jest obsługiwana i utworzysz własny pasek narzędzi, Pomiń wywołanie domyślnej procedury obsługi.|Nie używany.|Wskaźnik do ciągu, który zawiera nazwę paska narzędzi.|Wskaźnik do nowo utworzonego paska narzędzi. Wartość NULL wskazuje, że tworzenie paska narzędzi zostało anulowane.|
|AFX_WM_CUSTOMIZEHELP|Wysyłany do okna głównego ramki z arkusza właściwości dostosowywania, `CMFCToolbarCustomize Dialog` gdy użytkownik naciśnie przycisk **Pomoc** lub klawisz F1.|Określa aktywną stronę arkusza właściwości dostosowania.|Wskaźnik do `CMFCToolbarCustomize Dialog` obiektu.|Zero.|
|AFX_WM_CUSTOMIZETOOLBAR|`CMFCToolbarCustomize Dialog`Wysyła ten komunikat, aby powiadomić ramkę nadrzędną, że użytkownik tworzy nowy pasek narzędzi.|PRAWDA po rozpoczęciu dostosowywania, wartość FALSE po zakończeniu dostosowywania.|Nie używany.|Zero.|
|AFX_WM_DELETETOOLBAR|Wysyłany do okna głównego ramki, gdy użytkownik zamierza usunąć pasek narzędzi w trybie dostosowywania.<br /><br /> Przetwórz ten komunikat, aby wykonać dodatkowe akcje, gdy użytkownik usunie pasek narzędzi w trybie dostosowywania. Należy również wywołać domyślną procedurę obsługi ( `OnToolbarDelete` ), która usuwa pasek narzędzi. Domyślna procedura obsługi zwraca wartość wskazującą, czy można usunąć pasek narzędzi.|Nie używany.|Wskaźnik do `CMFCToolBar` obiektu, który ma zostać usunięty.|Niezerowe, jeśli nie można usunąć paska narzędzi; w przeciwnym razie 0.|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton` wysyła ten komunikat do okna głównej ramki w celu pobrania kolorów dokumentu.|Nie używany.|[in. out] Wskaźnik do `CList<COLORREF, COLORREF>` obiektu.|Zero.|
|AFX_WM_GETDRAGBOUNDS|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Wysyłany do okna głównego ramki, gdy użytkownik podświetli element listy wstążki.|Indeks wyróżnionego elementu|Wskaźnik do `CMFCBaseRibbonElement`|Nie używany.|
|AFX_WM_ON_AFTER_SHELL_COMMAND|Wysyłany do elementu nadrzędnego `CMFCShellListCtrl` lub `CMFCShellTreeCtrl` kontrolki, gdy użytkownik zakończy wykonywanie polecenia powłoki.|Identyfikator polecenia wykonywanego przez użytkownika|Nie używany.|Jeśli aplikacja przetwarza ten komunikat, powinien zwrócić wartość zero.|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|Struktura wysyła ten komunikat do elementu nadrzędnego wstążki przed wyświetleniem menu podręcznego. Możesz przetwarzać ten komunikat i modyfikować menu wyskakujące w dowolnym momencie.|Nie używany.|Wskaźnik do `CMFCBaseRibbonElement`|Nie używany.|
|AFX_WM_ON_CANCELTABMOVE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|Struktura wysyła ten komunikat do ramki głównej, gdy użytkownik zmieni aktywną kategorię kontrolki wstążki.|Nie używany.|Wskaźnik do elementu, `CMFCRibbonBar` którego Kategoria została zmieniona.|Nie używany.|
|AFX_WM_ON_CLOSEPOPUPWINDOW|Struktura wyśle ten komunikat, aby powiadomić właściciela o `CMFCDesktopAlertWnd` tym, że okno ma zostać zamknięte.|Nie używany.|Wskaźnik do `CMFCDesktopAlertWnd` obiektu.|Nie używany.|
|AFX_WM_ON_DRAGCOMPLETE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_ON_GET_TAB_TOOLTIP|Wysyłany do okna głównego ramki, gdy okno karty ma wyświetlać etykietkę narzędzia dla karty, jeśli są włączone niestandardowe etykietki narzędzi.|Nie używany.|Wskaźnik do `CMFCTabToolTipInfo` struktury.|Nie używany.|
|AFX_WM_ON_HSCROLL|Wysyłany do kontrolki paska kontroli o zmiennym rozmiarze. Przetwórz ten komunikat, aby otrzymywać powiadomienia z `CMFCTabCtrl` obiektów po wystąpieniu zdarzenia przewijania na pasku przewijania poziomego widżetu z kartami.|Słowo w niskim porządku określa wartość paska przewijania, która wskazuje żądanie przewijania użytkownika.  Więcej informacji znajduje się w tabeli w dalszej części tego tematu.|Nie używany.|Różną od zera.|
|AFX_WM_ON_MOVE_TAB|Wysyłany do elementu nadrzędnego okna z kartami, gdy użytkownik przeciągnie kartę do nowej pozycji.|Indeks (liczony od zera) karty w jego pierwotnym położeniu.|określoną Indeks (liczony od zera) karty w jej nowym położeniu.|Zero.|
|AFX_WM_ON_MOVETABCOMPLETE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_ON_MOVETOTABGROUP|Wysyłany do okna głównego ramki, gdy użytkownik przenosi okno podrzędne MDI z jednej z kart na inną.|Uchwyt okna z kartami ( `CMFCTabCtrl` ), z którego usunięto okno podrzędne MDI.|określoną Uchwyt okna z kartami ( `CMFCTabCtrl` ), do którego wstawiono okno elementu podrzędnego MDI.|Ignorowane.|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Wysyłany do elementu nadrzędnego, `CDockablePane` gdy użytkownik kliknie przycisk **Zamknij** na podpisie paska sterowania.|Nie używany.|Wskaźnik do okienka było dokować, w którym użytkownik kliknął przycisk **Zamknij** .|Ma wartość TRUE, jeśli nie można zamknąć okienka; w przeciwnym razie FALSE.|
|AFX_WM_ON_RENAME_TAB|Wysyłany do nadrzędnego okna z kartami po zmianie nazwy na kartę edytowalną przez użytkownika.|Indeks (liczony od zera) karty o zmienionej nazwie.|określoną Wskaźnik do ciągu, który zawiera nową nazwę karty.|Niezerowe, jeśli aplikacja przetwarza ten komunikat; Platforma spowoduje pominięcie wywołania metody `CMFCBaseTabCtrl::SetTabLabel` .  Jeśli zwracana jest wartość zero, `CMFCBaseTabCtrl::SetTabLabel` to jest wywoływana przez platformę.|
|AFX_WM_ON_RIBBON_CUSTOMIZE|Wysyłany do ramki nadrzędnej po rozpoczęciu dostosowywania przez użytkownika. Przetwórz ten komunikat, jeśli chcesz wyświetlić własne okno dialogowe dostosowywania.|Nie używany.|Wskaźnik do kontrolki wstążki, która ma zostać dostosowana.|Niezerowe, jeśli aplikacja przetwarza ten komunikat i wyświetla własne okno dialogowe dostosowywania. Jeśli aplikacja zwróci zero, środowisko będzie wyświetlać wbudowane okno dialogowe dostosowywania.|
|AFX_WM_ON_TABGROUPMOUSEMOVE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_POSTSETPREVIEWFRAME|Wysyłany w celu powiadomienia głównej ramki, że użytkownik zmienił tryb podglądu wydruku|Wartość TRUE oznacza, że ustawiono tryb podglądu wydruku. Wartość FALSE wskazuje, że tryb podglądu wydruku jest wyłączony.|Nie używany.|Nie używany.|
|AFX_WM_PROPERTY_CHANGED|Wysyłany do właściciela kontrolki siatki właściwości ( `CMFCPropertyGridCtrl` ), gdy użytkownik zmienia wartość wybranej właściwości.|Identyfikator formantu listy właściwości.|Wskaźnik do właściwości ( `CMFCPropertyGridProperty` ), która zmieniła się.|Nie używany.|
|AFX_WM_RESETCONTEXTMENU|Wysyłany do okna głównego ramki, gdy użytkownik resetuje menu kontekstowe podczas dostosowywania.|Identyfikator zasobu menu kontekstowego.|Wskaźnik do bieżącego menu kontekstowego `CMFCPopupMenu` .|Nie używany.|
|AFX_WM_RESETKEYBOARD|Struktura wysyła ten komunikat do okna głównej ramki, gdy użytkownik resetuje wszystkie akceleratory klawiatury podczas dostosowywania.|Nie używany.|Nie używany.|Nie używany.|
|AFX_WM_RESETMENU|Struktura wysyła ten komunikat do menu właściciel (okno ramki), gdy użytkownik resetuje menu ramki aplikacji podczas dostosowywania|Identyfikator zasobu menu.|Nie używany.|Nie używany.|
|AFX_WM_RESETPROMPT|Struktura wysyła ten komunikat, gdy użytkownik resetuje pasek narzędzi z okna dialogowego Dostosuj pasek narzędzi. Domyślna procedura obsługi Wyświetla okno komunikatu z pytaniem, czy użytkownik chce zresetować pasek narzędzi.|Nie używany.|Nie używany.|Nie używany.|
|AFX_WM_RESETTOOLBAR|`CMFCToolBar`Obiekt wysyła ten komunikat, gdy pasek narzędzi zostanie przywrócony do jego oryginalnego stanu, czyli załadowany z zasobów. Przetwórz ten komunikat, aby ponownie wstawić przyciski paska narzędzi, z których pochodzą klasy `CMFCToolbarButton` . Aby uzyskać więcej informacji, zobacz `CMFCToolbarComboBoxButton`.|Identyfikator zasobu paska narzędzi, którego stan został przywrócony.|Nie używany.|Zero.|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton` Obiekt wysyła tę wiadomość do właściciela, gdy użytkownik kliknie przycisk menu zwykłego. Przetwórz ten komunikat za każdym razem, `CMFCToolbarMenuButton` gdy używasz do wyświetlania menu rozwijanego, gdy użytkownik kliknie przycisk.|Identyfikator polecenia przycisku, który wysyła komunikat.|Współrzędne ekranu kursora. W przypadku wyrazów z niskim priorytetem jest określana Współrzędna x. Wyraz o wysokiej kolejności Określa współrzędną y.|Nie używany.|
|AFX_WM_TOOLBARMENU|Wysyłany do okna głównego ramki, gdy użytkownik zwolni prawy przycisk myszy, gdy wskaźnik myszy znajduje się w obszarze klienta lub nieklienckiego okienka.|Nie używany.|Współrzędne ekranu wskaźnika myszy. W przypadku wyrazów z niskim priorytetem jest określana Współrzędna x. Wyraz o wysokiej kolejności Określa współrzędną y.|Zero, jeśli aplikacja przetwarza ten komunikat; w przeciwnym razie wartość różna od zera.|
|AFX_WM_UPDATETOOLTIPS|Wysyłany do wszystkich właścicieli etykietek narzędzi, aby wskazać, że ich kontrolki etykietki narzędzi powinny być ponownie tworzone.|Typ formantu, który powinien przetworzyć tę wiadomość. Listę możliwych wartości można znaleźć w tabeli w dalszej części tego tematu.|Nie używany.|Nie używany.|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog` wysyła ten komunikat do ramki nadrzędnej, gdy użytkownik kliknie przycisk **Pomoc** lub przejdzie do trybu pomocy, klikając przycisk **Pomoc** lub klawisz F1.|Nie używany.|Wskaźnik do wystąpienia `CMFCWindowsManagerDialog` .|Nie używany.|

W poniższej tabeli przedstawiono wartości dla niskiego wyrazu parametru *lParam* metody AFX_WM_HSCROLL:

|Wartość|Znaczenie|
|-|-|
|SB_ENDSCROLL|Użytkownik skończy przewijanie.|
|SB_LEFT|Użytkownik przewija do lewej górnej części.|
|SB_RIGHT|Użytkownik przewija do prawej dolnej krawędzi.|
|SB_LINELEFT|Użytkownik przewija lewo o jedną jednostkę.|
|SB_LINERIGHT|Użytkownik przewija prawo o jedną jednostkę.|
|SB_PAGELEFT|Użytkownik przewija w lewo o szerokość okna.|
|SB_PAGERIGHT|Użytkownik przewija w prawo o szerokość okna.|
|SB_THUMBPOSITION|Użytkownik przełączył pole przewijania (kciuk) i wydano przycisk myszy. Słowo o wysokiej kolejności wskazuje położenie pola przewijania na końcu operacji przeciągania.|
|SB_THUMBTRACK|Użytkownik przeciąga pole przewijania. Wiadomość AFX_WM_ON_HSCROLL jest wysyłana wielokrotnie przy użyciu tej wartości, dopóki użytkownik nie zwolni przycisku myszy. Słowo o wysokim poziomie kolejności wskazuje położenie, do którego pole przewijania zostało przeciągnięte.|

> [!NOTE]
> Słowo *lParam* parametru o wysokim poziomie określa bieżącą pozycję pola przewijania, jeśli wyraz o niskiej kolejności jest SB_THUMBPOSITION lub SB_THUMBTRACK; w przeciwnym razie ten wyraz nie jest używany.

Poniższa tabela zawiera listę wartości flag dla parametru *lParam* komunikatu AFX_WM_UPDATETOOLTIPS:

|Flaga|Wartość|
|-|-|
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

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
