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
ms.openlocfilehash: 5caf40fc757e2c5c90c06e1698ce4c15d1ed6240
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338062"
---
# <a name="afx-messages"></a>Komunikaty AFX

Te komunikaty są używane w MFC.

## <a name="messages"></a>Komunikaty

Poniższa tabela zawiera listę komunikatów, które są używane w bibliotece MFC:

||||||
|-|-|-|-|-|
|Komunikat|Opis|[in] *wParam*|*lParam* (wszystkie parametry są [in] chyba że określono inaczej).|Wartość zwracana|
|AFX_WM_ACCGETOBJECT|Nie używany.|Nie używany.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_ACCGETSTATE|Używane dla ułatwień dostępu pomocy technicznej. Wyślij wiadomość do `CMFCPopupMenu` lub `CMFCRibbonPanelMenu` można pobrać stanu bieżącego elementu.|Indeks elementu, który może być przycisk menu i separator.|Nie używany.|Stan elementu. Jeśli indeks jest nieprawidłowy, -1 jest 0, jeśli przycisk menu nie ma żadnych specjalnych atrybutów. W przeciwnym razie jest kombinacją następujących flag:<br /><br /> TBBS_DISABLED — element jest wyłączony.<br /><br /> TBBS_CHECKED — element jest wyewidencjonowany.<br /><br /> TBBS_BUTTON — element znajduje się przycisk standardowy<br /><br /> TBBS_PRESSED — przycisk jest wciśnięty<br /><br /> TBBS_INDETERMINATE — stan niezdefiniowane<br /><br /> TBBS_SEPARATOR — zamiast przycisku menu, stanowi element odstęp między innymi elementami menu|
|AFX_WM_CHANGE_ACTIVE_TAB|Struktura wysyła wiadomość do formantu paska sterowania o zmiennym rozmiarze. Przetworzyć ten komunikat, aby otrzymywać powiadomienia z `CMFCTabCtrl` obiekty, gdy użytkownik zmienia aktywnej karty.|Indeks karty.|Nie używany.|Wartość różną od zera.|
|AFX_WM_CHANGE_CURRENT_FOLDER|Struktura wysyła wiadomość do elementu nadrzędnego `CMFCShellListCtrl` po użytkownik zmienił bieżącego folderu.|Nie używany.|Nie używany.|Nie używany.|
|AFX_WM_CHANGEVISUALMANAGER|Struktura wysyła wiadomość do wszystkich okien ramowych, gdy użytkownik zmieni bieżącego Menedżera Visual. W odpowiedzi na tę wiadomość okno ramowe ponownie oblicza jego region i dostosowuje innych parametrów, zgodnie z potrzebami. W aplikacji może przetworzyć komunikatu AFX_WM_CHANGEVISUALMANAGER, jeśli chcesz otrzymywać powiadomienia o tego zdarzenia. Należy wywołać obsługi klasę bazową (`OnChangeVisualManager`) aby upewnić się, że struktura przez wewnętrzny odbywa się przetwarzanie tego zdarzenia.|Nie używany.|Nie używany.|Nie używany.|
|AFX_WM_CHANGING_ACTIVE_TAB|Wysyłane do nadrzędnego `CMFCTabCtrl` obiektu.  Przetworzyć ten komunikat, jeśli chcesz otrzymywać powiadomienia z `CMFCTabCtrl` obiektów po użytkownik resetuje kartę.|Indeks kartę która jest aktywowane.|Nie używany.|Wartość różną od zera.|
|AFX_WM_CHECKEMPTYMINIFRAME|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_CREATETOOLBAR|Wysyłane z `CMFCToolBarsListPropertyPage` po użytkownik tworzy nowy pasek narzędzi podczas procesu dostosowywania. Można przetworzyć ten komunikat, aby utworzyć niestandardowe obiektu klasy pochodnej CMFCToolBar. Jeśli obsłużyć ten komunikat i tworzenie własnych narzędzi, należy pominąć wywołanie domyślny program obsługi.|Nie używany.|Wskaźnik na ciąg, który zawiera nazwę paska narzędzi.|Wskaźnik do nowo utworzonego paska narzędzi. O wartości NULL wskazuje, że tworzenie narzędzi zostało anulowane.|
|AFX_WM_CUSTOMIZEHELP|Wysyłane do głównej ramki okna z arkusza właściwości dostosowywania `CMFCToolbarCustomize Dialog` gdy użytkownik naciśnie **pomocy** przycisku lub klawisz F1.|Określa się stroną aktywną dostosowywania arkusza właściwości.|Wskaźnik do `CMFCToolbarCustomize Dialog` obiektu.|Zero.|
|AFX_WM_CUSTOMIZETOOLBAR|`CMFCToolbarCustomize Dialog` Wysyła tę wiadomość, aby powiadomić nadrzędnej ramki użytkownik tworzy nowy pasek narzędzi.|Wartość TRUE, rozpoczęcie dostosowywania, FAŁSZ. po zakończeniu dostosowywania.|Nie używany.|Zero.|
|AFX_WM_DELETETOOLBAR|Wysyłane do głównej ramki okna, gdy użytkownik jest usunięte z paska narzędzi w tryb dostosowywania.<br /><br /> Przetworzyć ten komunikat, aby podejmować dodatkowe akcje w przypadku, gdy użytkownik usuwa pasek narzędzi w tryb dostosowywania. Należy także wywołać domyślny program obsługi (`OnToolbarDelete`), które powoduje usunięcie paska narzędzi. Domyślny program obsługi zwraca wartość wskazującą, czy jest możliwe usuwanie na pasku narzędzi.|Nie używany.|Wskaźnik do `CMFCToolBar` obiekt do usunięcia.|Wartość różną od zera, jeśli nie można usunąć paska narzędzi & lt; w przeciwnym razie 0.|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton` wysyła wiadomość do ramki głównego okna, aby pobrać kolory dokumentu.|Nie używany.|[out w] Wskaźnik do `CList<COLORREF, COLORREF>` obiektu.|Zero.|
|AFX_WM_GETDRAGBOUNDS|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Wysyłany do głównej ramki okna po użytkownik wyróżnia elementu wstążki.|Indeks wyróżniony element|Wskaźnik do `CMFCBaseRibbonElement`|Nie używany.|
|AFX_WM_ON_AFTER_SHELL_COMMAND|Wysyłane do elementu nadrzędnego `CMFCShellListCtrl` lub `CMFCShellTreeCtrl` kontrolki, gdy użytkownik zakończy się wykonywanie polecenia powłoki.|Identyfikator polecenia wykonywanego przez użytkownika|Nie używany.|Jeśli aplikacja przetwarza tę wiadomość, powinna zwrócić zero.|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|Struktura wysyła tę wiadomość do elementu nadrzędnego wstążki, zanim wyświetli menu podręcznego. Można przetworzyć ten komunikat i zmodyfikować wyskakujących menu w dowolnym momencie.|Nie używany.|Wskaźnik do `CMFCBaseRibbonElement`|Nie używany.|
|AFX_WM_ON_CANCELTABMOVE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|Struktura wysyła wiadomość do głównej ramki, gdy użytkownik zmieni aktywnej kategorii formantu wstążki.|Nie używany.|Wskaźnik do `CMFCRibbonBar` których kategorii został zmieniony.|Nie używany.|
|AFX_WM_ON_CLOSEPOPUPWINDOW|Struktura wysyła tę wiadomość, aby powiadomić właściciela `CMFCDesktopAlertWnd` że okno zostanie zamknięte.|Nie używany.|Wskaźnik do `CMFCDesktopAlertWnd` obiektu.|Nie używany.|
|AFX_WM_ON_DRAGCOMPLETE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_ON_GET_TAB_TOOLTIP|Wysyłane do głównej ramki okna, gdy okno karty zbliża się wyświetlić etykietkę narzędzia dla karty, jeśli włączone są niestandardowe etykietki narzędzi.|Nie używany.|Wskaźnik do `CMFCTabToolTipInfo` struktury.|Nie używany.|
|AFX_WM_ON_HSCROLL|Wysyłane do formantu paska sterowania o zmiennym rozmiarze. Przetworzyć ten komunikat, aby otrzymywać powiadomienia z `CMFCTabCtrl` obiekty, gdy wystąpi zdarzenie przewijania na pasku przewijania w poziomie z kartami elementu widget.|Word niskiego rzędu Określa, że wartość paska przewijania, która wskazuje użytkownika przewijanym żądania.  Aby uzyskać więcej informacji zobacz tabelę w dalszej części tego tematu.|Nie używany.|Wartość różną od zera.|
|AFX_WM_ON_MOVE_TAB|Wysyłane do nadrzędnego okna z kartami, gdy użytkownik przeciągnie kartę do nowej pozycji.|Liczony od zera indeks karty w oryginalnym położeniu.|[out] Liczony od zera indeks kartę w nowej lokalizacji.|Zero.|
|AFX_WM_ON_MOVETABCOMPLETE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_ON_MOVETOTABGROUP|Wysyłane do głównej ramki okna, gdy użytkownik przesuwa okno podrzędne MDI z jednej grupy z kartami na inny.|Dojście do okna z kartami (`CMFCTabCtrl`) z którego okno podrzędne MDI został usunięty.|[out] Dojście do okna z kartami (`CMFCTabCtrl`), do którego włożono okno podrzędne MDI.|Ignorowane.|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Wysyłane do elementu nadrzędnego `CDockablePane` gdy użytkownik kliknie **Zamknij** przycisk na podpis paska sterowania.|Nie używany.|Wskaźnik do okienka dokowalne, na którym użytkownik kliknął element **Zamknij** przycisku.|Wartość TRUE, jeśli nie można zamknąć okienko; w przeciwnym razie wartość FALSE.|
|AFX_WM_ON_RENAME_TAB|Wysyłane do nadrzędnego okna z zakładkami po użytkownik nazwy karty można edytować.|Liczony od zera indeks karty, których nazwy zostały zmienione.|[out] Wskaźnik do ciągu, który zawiera nazwę nowej karty.|Wartość różną od zera, jeśli aplikacja przetwarza tego komunikatu. Struktura blokuje wyświetlanie wywołanie `CMFCBaseTabCtrl::SetTabLabel`.  Jeśli zwracany jest zero, następnie `CMFCBaseTabCtrl::SetTabLabel` jest wywoływane przez platformę.|
|AFX_WM_ON_RIBBON_CUSTOMIZE|Wysyłane do nadrzędnej ramki, gdy użytkownik uruchamia dostosowywania. Przetworzyć ten komunikat, jeśli chcesz wyświetlić okno dialogowe własne dostosowania.|Nie używany.|Wskaźnik do formantu wstążki do dostosowania.|Różna od zera, jeśli aplikacja przetwarza ten komunikat i wyświetla okno dialogowe własne dostosowania. Jeśli aplikacja zwróci wartość zero, struktura spowoduje wyświetlenie okna dialogowego Dostosowywanie wbudowane.|
|AFX_WM_ON_TABGROUPMOUSEMOVE|Tylko do użytku wewnętrznego.|Nie dotyczy.|Nie dotyczy.|Nie dotyczy.|
|AFX_WM_POSTSETPREVIEWFRAME|Wysyłane do głównej ramki powiadomienie, że użytkownik zmienił tryb podglądu wydruku|Wartość TRUE wskazuje, że ustawiono tryb podglądu wydruku. Wartość FALSE wskazuje, że ten tryb podglądu wydruku jest wyłączone.|Nie używany.|Nie używany.|
|AFX_WM_PROPERTY_CHANGED|Wysyłany do właściciela formant siatki właściwości (`CMFCPropertyGridCtrl`) podczas zmiany wartości właściwości wybranej przez użytkownika.|Identyfikator formantu listy właściwości.|Wskaźnik do właściwości (`CMFCPropertyGridProperty`) która się zmieniła.|Nie używany.|
|AFX_WM_RESETCONTEXTMENU|Wysyłany do głównej ramki okna po użytkownik resetuje menu kontekstowe podczas dostosowywania.|Identyfikator zasobu menu kontekstowego.|Wskaźnik do bieżącego menu kontekstowe `CMFCPopupMenu`.|Nie używany.|
|AFX_WM_RESETKEYBOARD|Struktura wysyła tę wiadomość w oknie głównym ramki po użytkownik resetuje wszystkie klawiszy skrótów podczas dostosowywania.|Nie używany.|Nie używany.|Nie używany.|
|AFX_WM_RESETMENU|Struktura wysyła wiadomość do właściciela menu (okno ramowe) po użytkownik resetuje menu ramki aplikacji podczas dostosowywania|Identyfikator zasobu menu|Nie używany.|Nie używany.|
|AFX_WM_RESETPROMPT|Struktura wysyła tę wiadomość, gdy resetuje użytkownika na pasku narzędzi na pasku narzędzi Dostosuj — okno dialogowe. Domyślny program obsługi Wyświetla okno komunikatu z pytaniem, czy użytkownik chce, aby zresetować na pasku narzędzi.|Nie używany.|Nie używany.|Nie używany.|
|AFX_WM_RESETTOOLBAR|Element `CMFCToolBar` obiektu wysyła tę wiadomość, gdy pasek narzędzi jest przywracany do stanu pierwotnego, oznacza to, że ładowanych z zasobów. Przetworzyć ten komunikat, aby ponownie przycisków paska narzędzi, których klasy pochodzą z `CMFCToolbarButton`. Aby uzyskać więcej informacji, zobacz `CMFCToolbarComboBoxButton`.|Identyfikator zasobu paska narzędzi, których stan został przywrócony.|Nie używany.|Zero.|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton` obiekt wysyła wiadomość do jego właściciela, gdy użytkownik kliknie przycisk menu regularne. Przetworzyć ten komunikat za każdym razem, którego używasz `CMFCToolbarMenuButton` do wyświetlenia menu podręcznego, kiedy użytkownik kliknie przycisk.|Identyfikator polecenia przycisk, który wysyła wiadomość.|Współrzędne ekranu znajduje się kursor. Word niskiego rzędu Określa współrzędną x. Word wyższego rzędu Określa współrzędną y.|Nie używany.|
|AFX_WM_TOOLBARMENU|Wysyłane do głównej ramki okna, gdy użytkownik zwolni prawy przycisk myszy, gdy wskaźnik myszy znajduje się w kliencie lub obszaru nieklienckiego w okienku.|Nie używany.|Współrzędne ekranu wskaźnika myszy. Word niskiego rzędu Określa współrzędną x. Word wyższego rzędu Określa współrzędną y.|Zero, jeśli aplikacja przetwarza tego komunikatu. w przeciwnym przypadku wartość różną od zera.|
|AFX_WM_UPDATETOOLTIPS|Wysyłane do wszystkich właścicieli etykietki narzędzia, aby wskazać, że można odtworzyć ich kontrolek typu etykieta.|Typ formantu, który powinien przetworzyć ten komunikat. Zobacz tabelę w dalszej części tego tematu zawiera listę możliwych wartości.|Nie używany.|Nie używany.|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog` wysyła wiadomość do nadrzędnej ramki, gdy użytkownik kliknie **pomocy** przycisk lub przechodzi w tryb pomocy, klikając **pomocy** przycisk paska tytułowego lub klawisz F1.|Nie używany.|Wskaźnik do wystąpienia `CMFCWindowsManagerDialog`.|Nie używany.|

W poniższej tabeli przedstawiono wartości niższe słowo *lParam* parametru metody AFX_WM_HSCROLL:

|||
|-|-|
|Wartość|Znaczenie|
|SB_ENDSCROLL|Użytkownik kończy się przewijania.|
|SB_LEFT|Użytkownik przewija widok lewym górnym rogu.|
|SB_RIGHT|Użytkownik przewija widok prawej dolnej.|
|SB_LINELEFT|Użytkownik przewija widok lewej strony o jedną jednostkę.|
|SB_LINERIGHT|Użytkownik przewija w prawo o jedną jednostkę.|
|SB_PAGELEFT|Użytkownik przewija widok lewej przez szerokość okna.|
|SB_PAGERIGHT|Użytkownik przewija widok w prawo przez szerokość okna.|
|SB_THUMBPOSITION|Użytkownik przeciągnąć pole przewijania (thumb) i przycisk myszy. Word wyższego rzędu wskazuje położenie suwaka na koniec operacji przeciągania.|
|SB_THUMBTRACK|Użytkownik przeciąga suwaka. AFX_WM_ON_HSCROLL wiadomości jest wielokrotnie o tej wartości dopóki użytkownik zwolni przycisk myszy. Word wyższego rzędu wskazuje pozycji, do którego zostało przeciągnięte suwaka.|

> [!NOTE]
>  Słowo wyższego rzędu *lParam* parametr określa bieżące położenie suwaka w przypadku niskiego rzędu wyrazów SB_THUMBPOSITION lub SB_THUMBTRACK; w przeciwnym razie nie jest używany ten wyraz.

W poniższej tabeli wymieniono wartości flag *lParam* parametru AFX_WM_UPDATETOOLTIPS wiadomości:

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

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
