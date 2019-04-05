---
title: Klasa CMFCMenuBar
ms.date: 10/18/2018
f1_keywords:
- CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar::AdjustLocations
- AFXMENUBAR/CMFCMenuBar::AllowChangeTextLabels
- AFXMENUBAR/CMFCMenuBar::AllowShowOnPaneMenu
- AFXMENUBAR/CMFCMenuBar::CalcFixedLayout
- AFXMENUBAR/CMFCMenuBar::CalcLayout
- AFXMENUBAR/CMFCMenuBar::CalcMaxButtonHeight
- AFXMENUBAR/CMFCMenuBar::CanBeClosed
- AFXMENUBAR/CMFCMenuBar::CanBeRestored
- AFXMENUBAR/CMFCMenuBar::Create
- AFXMENUBAR/CMFCMenuBar::CreateEx
- AFXMENUBAR/CMFCMenuBar::CreateFromMenu
- AFXMENUBAR/CMFCMenuBar::EnableHelpCombobox
- AFXMENUBAR/CMFCMenuBar::EnableMenuShadows
- AFXMENUBAR/CMFCMenuBar::GetAvailableExpandSize
- AFXMENUBAR/CMFCMenuBar::GetColumnWidth
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenu
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::GetFloatPopupDirection
- AFXMENUBAR/CMFCMenuBar::GetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::GetHelpCombobox
- AFXMENUBAR/CMFCMenuBar::GetHMenu
- AFXMENUBAR/CMFCMenuBar::GetMenuFont
- AFXMENUBAR/CMFCMenuBar::GetMenuItem
- AFXMENUBAR/CMFCMenuBar::GetRowHeight
- AFXMENUBAR/CMFCMenuBar::GetSystemButton
- AFXMENUBAR/CMFCMenuBar::GetSystemButtonsCount
- AFXMENUBAR/CMFCMenuBar::GetSystemMenu
- AFXMENUBAR/CMFCMenuBar::HighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsButtonExtraSizeAvailable
- AFXMENUBAR/CMFCMenuBar::IsHighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsMenuShadows
- AFXMENUBAR/CMFCMenuBar::IsRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommands
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommandsDelay
- AFXMENUBAR/CMFCMenuBar::LoadState
- AFXMENUBAR/CMFCMenuBar::OnChangeHot
- AFXMENUBAR/CMFCMenuBar::OnDefaultMenuLoaded
- AFXMENUBAR/CMFCMenuBar::OnSendCommand
- AFXMENUBAR/CMFCMenuBar::OnSetDefaultButtonText
- AFXMENUBAR/CMFCMenuBar::OnToolHitTest
- AFXMENUBAR/CMFCMenuBar::PreTranslateMessage
- AFXMENUBAR/CMFCMenuBar::RestoreOriginalstate
- AFXMENUBAR/CMFCMenuBar::SaveState
- AFXMENUBAR/CMFCMenuBar::SetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::SetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::SetMaximizeMode
- AFXMENUBAR/CMFCMenuBar::SetMenuButtonRTC
- AFXMENUBAR/CMFCMenuBar::SetMenuFont
- AFXMENUBAR/CMFCMenuBar::SetRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::SetShowAllCommands
helpviewer_keywords:
- CMFCMenuBar [MFC], AdjustLocations
- CMFCMenuBar [MFC], AllowChangeTextLabels
- CMFCMenuBar [MFC], AllowShowOnPaneMenu
- CMFCMenuBar [MFC], CalcFixedLayout
- CMFCMenuBar [MFC], CalcLayout
- CMFCMenuBar [MFC], CalcMaxButtonHeight
- CMFCMenuBar [MFC], CanBeClosed
- CMFCMenuBar [MFC], CanBeRestored
- CMFCMenuBar [MFC], Create
- CMFCMenuBar [MFC], CreateEx
- CMFCMenuBar [MFC], CreateFromMenu
- CMFCMenuBar [MFC], EnableHelpCombobox
- CMFCMenuBar [MFC], EnableMenuShadows
- CMFCMenuBar [MFC], GetAvailableExpandSize
- CMFCMenuBar [MFC], GetColumnWidth
- CMFCMenuBar [MFC], GetDefaultMenu
- CMFCMenuBar [MFC], GetDefaultMenuResId
- CMFCMenuBar [MFC], GetFloatPopupDirection
- CMFCMenuBar [MFC], GetForceDownArrows
- CMFCMenuBar [MFC], GetHelpCombobox
- CMFCMenuBar [MFC], GetHMenu
- CMFCMenuBar [MFC], GetMenuFont
- CMFCMenuBar [MFC], GetMenuItem
- CMFCMenuBar [MFC], GetRowHeight
- CMFCMenuBar [MFC], GetSystemButton
- CMFCMenuBar [MFC], GetSystemButtonsCount
- CMFCMenuBar [MFC], GetSystemMenu
- CMFCMenuBar [MFC], HighlightDisabledItems
- CMFCMenuBar [MFC], IsButtonExtraSizeAvailable
- CMFCMenuBar [MFC], IsHighlightDisabledItems
- CMFCMenuBar [MFC], IsMenuShadows
- CMFCMenuBar [MFC], IsRecentlyUsedMenus
- CMFCMenuBar [MFC], IsShowAllCommands
- CMFCMenuBar [MFC], IsShowAllCommandsDelay
- CMFCMenuBar [MFC], LoadState
- CMFCMenuBar [MFC], OnChangeHot
- CMFCMenuBar [MFC], OnDefaultMenuLoaded
- CMFCMenuBar [MFC], OnSendCommand
- CMFCMenuBar [MFC], OnSetDefaultButtonText
- CMFCMenuBar [MFC], OnToolHitTest
- CMFCMenuBar [MFC], PreTranslateMessage
- CMFCMenuBar [MFC], RestoreOriginalstate
- CMFCMenuBar [MFC], SaveState
- CMFCMenuBar [MFC], SetDefaultMenuResId
- CMFCMenuBar [MFC], SetForceDownArrows
- CMFCMenuBar [MFC], SetMaximizeMode
- CMFCMenuBar [MFC], SetMenuButtonRTC
- CMFCMenuBar [MFC], SetMenuFont
- CMFCMenuBar [MFC], SetRecentlyUsedMenus
- CMFCMenuBar [MFC], SetShowAllCommands
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
ms.openlocfilehash: 87844e843057bb295c904b5f1b3d7dd03fa4d797
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58775897"
---
# <a name="cmfcmenubar-class"></a>Klasa CMFCMenuBar

Pasek menu, który implementuje dokowania.
Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|(Przesłania `CMFCToolBar::AdjustLocations`).|
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|Określa, czy etykiety tekstowe może być wyświetlany w obszarze obrazów na przycisków paska narzędzi. (Przesłania [CMFCToolBar::AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels).)|
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Przesłania `CPane::AllowShowOnPaneMenu`).|
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|Oblicza rozmiar poziomy, na pasku narzędzi. (Przesłania [CMFCToolBar::CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout).)|
|[CMFCMenuBar::CalcLayout](#calclayout)|(Przesłania `CMFCToolBar::CalcLayout`).|
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|Oblicza maksymalną wysokość przycisków na pasku narzędzi. (Przesłania [CMFCToolBar::CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight).)|
|[CMFCMenuBar::CanBeClosed](#canbeclosed)|Określa, czy użytkownika można zamknąć paska narzędzi. (Przesłania [CMFCToolBar::CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed).)|
|[CMFCMenuBar::CanBeRestored](#canberestored)|Określa, czy system można przywrócić pasek narzędzi do pierwotnego stanu po dostosowaniu. (Przesłania [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCMenuBar::Create](#create)|Tworzy formant menu i dołącza je do `CMFCMenuBar` obiektu.|
|[CMFCMenuBar::CreateEx](#createex)|Tworzy `CMFCMenuBar` obiektu przy użyciu stylu dodatkowych opcji.|
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|Inicjuje `CMFCMenuBar` obiektu. Akceptuje parametr HMENU, który działa jako szablon służący do wypełniania `CMFCMenuBar`.|
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|Włącza **pomocy** pola kombi, który znajduje się po prawej stronie paska menu.|
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|Określa, czy mają być wyświetlane cieni menu podręcznego.|
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|(Przesłania [CPane::GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize).)|
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|Zwraca szerokość przycisków paska narzędzi. (Przesłania [CMFCToolBar::GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth).)|
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|Zwraca uchwyt do oryginalnego menu w pliku zasobów.|
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|Zwraca identyfikator zasobu menu oryginalnego pliku zasobów.|
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|Zwraca wskaźnik do **pomocy** pola kombi.|
|[CMFCMenuBar::GetHMenu](#gethmenu)|Zwraca uchwyt do menu, który jest dołączony do `CMFCMenuBar` obiektu.|
|[CMFCMenuBar::GetMenuFont](#getmenufont)|Zwraca bieżącą czcionkę globalnych obiektów menu.|
|[CMFCMenuBar::GetMenuItem](#getmenuitem)|Zwraca skojarzony indeks dostarczony element przycisku paska narzędzi.|
|[CMFCMenuBar::GetRowHeight](#getrowheight)|Zwraca wysokość przycisków paska narzędzi. (Przesłania [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|Wskazuje, czy elementy menu wyłączone są wyróżnione.|
|[CMFCMenuBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Określa, czy pasek narzędzi można wyświetlić przyciski, który został rozszerzony obramowania. (Przesłania [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|Wskazuje, czy elementy wyłączone są wyróżnione.|
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|Wskazuje, czy cieni są rysowane w menu podręcznym.|
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|Wskazuje, czy ostatnio używane polecenia są wyświetlane na pasku menu.|
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|Wskazuje, czy wyskakujących menu wyświetlane wszystkie polecenia.|
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|Wskazuje, czy w menu są wyświetlane wszystkie polecenia z niewielkim opóźnieniem.|
|[CMFCMenuBar::LoadState](#loadstate)|Ładuje stan `CMFCMenuBar` obiektu z rejestru.|
|[CMFCMenuBar::OnChangeHot](#onchangehot)|Wywoływane przez platformę, gdy użytkownik wybierze przycisk na pasku narzędzi. (Przesłania [CMFCToolBar::OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot).)|
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|Wywoływane przez platformę, gdy okno ramowe ładuje domyślne menu z pliku zasobów.|
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|(Przesłania `CMFCToolBar::OnSendCommand`).|
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|Wywoływane przez platformę, gdy jest w trybie dostosowywania i użytkownik zmieni tekst elementu menu.|
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(Przesłania `CMFCToolBar::OnToolHitTest`).|
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|(Przesłania `CMFCToolBar::PreTranslateMessage`).|
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|Wywoływane przez platformę, gdy menu jest w trybie dostosowywania, a użytkownik wybierze **resetowania** paska menu.|
|[CMFCMenuBar::SaveState](#savestate)|Zapisuje stan `CMFCMenuBar` obiektu w rejestrze.|
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|Ustawia oryginalnej menu w pliku zasobów.|
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|Wywoływane przez platformę, gdy okno podrzędne MDI zmieni jego trybu wyświetlania. Jeśli okno podrzędne MDI nowo jest zmaksymalizowane, lub już nie jest zmaksymalizowane, ta metoda aktualizuje paska menu.|
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|Ustawia informacji o klasie czasu wykonywania, który jest generowany, gdy użytkownik tworzy dynamicznie przycisków menu.|
|[CMFCMenuBar::SetMenuFont](#setmenufont)|Ustawia czcionkę dla wszystkich menu w aplikacji.|
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|Określa, czy pasek menu zawiera polecenia menu ostatnio używanych.|
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|Określa, czy pasek menu pokazuje wszystkie polecenia.|

## <a name="remarks"></a>Uwagi

`CMFCMenuBar` Klasa znajduje się pasek menu, który implementuje funkcje dokowania. Jest on podobny pasek narzędzi, mimo że nie można zamknąć — zawsze jest wyświetlany.

`CMFCMenuBar` obsługuje możliwość wyświetlania obiektów elementów menu ostatnio używanych. Jeśli ta opcja jest włączona, `CMFCMenuBar` wyświetla tylko podzbiór dostępnych poleceń na pierwszym wyświetlania. Po tej dacie ostatnio używane polecenia są wyświetlane wraz z oryginalnym podzestaw poleceń. Ponadto użytkownik zawsze można rozwinąć menu, aby wyświetlić wszystkie dostępne polecenia. W związku z tym każde polecenie dostępne jest skonfigurowany do wyświetlania stale lub aby wyświetlić tylko wtedy, gdy został ostatnio wybrany.

Aby użyć `CMFCMenuBar` obiektów, osadzenie go w obiekcie ramki głównego okna. Podczas przetwarzania `WM_CREATE` komunikatu, wywołaj `CMFCMenuBar::Create` lub `CMFCMenuBar::CreateEx`. Niezależnie od tego, który tworzy funkcję, należy przekazać wskaźnik do ramki głównego okna. Następnie włącz dokowania, wywołując [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Zadokuj w tym menu, wywołując [CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCMenuBar` klasy. W przykładzie pokazano, jak ustawić styl okienka, włączyć przycisk Dostosuj, włącz okno pomocy, Włącz cieni menu podręczne i aktualizacji na pasku menu. Ten fragment kodu jest częścią [próbka IE Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

`CMFCMenuBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmenubar.h

##  <a name="adjustlocations"></a>  CMFCMenuBar::AdjustLocations

Ustawia położenie elementów menu na pasku menu.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Uwagi

##  <a name="allowchangetextlabels"></a>  CMFCMenuBar::AllowChangeTextLabels

Określa, czy etykiety tekstowe są dozwolone w ramach obrazów na pasku menu.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli użytkownik może wybrać wyświetlić etykiety tekst pod obrazami.

### <a name="remarks"></a>Uwagi

##  <a name="allowshowonpanemenu"></a>  CMFCMenuBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="calcfixedlayout"></a>  CMFCMenuBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

[in] *bStretch*<br/>

[in] *bHorz*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="calclayout"></a>  CMFCMenuBar::CalcLayout

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>Parametry

[in] *dwMode*<br/>

[in] *nLength*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="calcmaxbuttonheight"></a>  CMFCMenuBar::CalcMaxButtonHeight

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="canbeclosed"></a>  CMFCMenuBar::CanBeClosed

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="canberestored"></a>  CMFCMenuBar::CanBeRestored

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="create"></a>  CMFCMenuBar::Create

Tworzy formant menu i dołącza je do [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) obiektu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[in] Wskaźnik do okna nadrzędnego dla nowego `CMFCMenuBar` obiektu.

*dwStyle*<br/>
[in] Styl nowy pasek menu.

*nID*<br/>
[in] Identyfikator okna podrzędnego paska menu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Po konstruowania `CMFCMenuBar` obiektu, należy wywołać `Create`. Ta metoda tworzy `CMFCMenuBar` kontroli i dołącza go do `CMFCMenuBar` obiektu.

Aby uzyskać więcej informacji na temat narzędzi style zobacz [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).

##  <a name="createex"></a>  CMFCMenuBar::CreateEx

Tworzy [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) obiektu z określonym rozszerzone style.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    CRect rcBorders = CRect(1,
    1,
    1,
    1),
    UINT nID =AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[in] Wskaźnik do nadrzędnego okna nowej `CMFCMenuBar` obiektu.

*dwCtrlStyle*<br/>
[in] Dodatkowe style na nowym pasku menu.

*dwStyle*<br/>
[in] Styl głównych nowy pasek menu.

*rcBorders*<br/>
[in] A `CRect` parametr, który określa rozmiary obramowania `CMFCMenuBar` obiektu.

*nID*<br/>
[in] Identyfikator okna podrzędnego paska menu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli metoda się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Należy użyć tej funkcji, zamiast [CMFCMenuBar::Create](#create) kiedy chcesz określić style oprócz styl paska narzędzi. Niektóre najczęściej używane style dodatkowe są TBSTYLE_TRANSPARENT i CBRS_TOP.

W przypadku list dodatkowe style, zobacz [formantu paska narzędzi oraz style przycisku](/windows/desktop/Controls/toolbar-control-and-button-styles), [najczęściej używane style kontrolki](/windows/desktop/Controls/common-control-styles), i [najczęściej używane style okna](/windows/desktop/winmsg/window-styles).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `CreateEx` metody `CMFCMenuBar` klasy. Ten fragment kodu jest częścią [próbka IE Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

##  <a name="createfrommenu"></a>  CMFCMenuBar::CreateFromMenu

Inicjuje [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) obiektu. Ta metoda modeli `CMFCMenuBar` obiektu po parametrze HMENU.

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
[in] Dojście do zasobu menu. `CreateFromMenu` używa tego zasobu jako szablon dla `CMFCMenuBar`.

*bDefaultMenu*<br/>
[in] Wartość logiczna, która wskazuje, czy nowe menu jest domyślne menu.

*bForceUpdate*<br/>
[in] Wartość logiczna, która wskazuje, czy ta metoda wymusza aktualizację menu.

### <a name="remarks"></a>Uwagi

Użyj tej metody, jeśli chcesz, aby formant menu, aby te same elementy menu jako zasób menu. Ta metoda jest wywoływana po wywołaniu metody albo [CMFCMenuBar::Create](#create) lub [CMFCMenuBar::CreateEx](#createex).

##  <a name="enablehelpcombobox"></a>  CMFCMenuBar::EnableHelpCombobox

Włącza **pomocy** pola kombi, który znajduje się po prawej stronie paska menu.

```
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[in] Identyfikator polecenia dla przycisku o **pomocy** pola kombi.

*lpszPrompt*<br/>
[in] Ciąg, który zawiera tekst, który wyświetla platformę w polu kombi, jeśli jest pusta i nie jest aktywny. Na przykład "Wprowadź tutaj tekst".

*nComboBoxWidth*<br/>
[in] Szerokość przycisku pola kombi w pikselach.

### <a name="remarks"></a>Uwagi

**Pomocy** przypomina pola kombi **pomocy** pola kombi na pasku menu programu Microsoft Word.

Wywołanie tej metody za pomocą *uiID* wartość 0, ta metoda powoduje ukrycie pola kombi. W przeciwnym razie ta metoda Wy wyświetla pola kombi automatycznie po prawej stronie na pasku menu. Po wywołaniu tej metody należy wywołać [CMFCMenuBar::GetHelpCombobox](#gethelpcombobox) uzyskać wskaźnik do wstawionego [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) obiektu.

##  <a name="enablemenushadows"></a>  CMFCMenuBar::EnableMenuShadows

Umożliwia cieni menu podręcznego.

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Parametr logiczny, który wskazuje, czy cieni powinien być włączony w menu podręcznym.

### <a name="remarks"></a>Uwagi

Algorytmu, który korzysta z tej metody jest złożona i może obniżyć wydajność aplikacji w systemach wolniej.

##  <a name="getavailableexpandsize"></a>  CMFCMenuBar::GetAvailableExpandSize

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getcolumnwidth"></a>  CMFCMenuBar::GetColumnWidth

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getdefaultmenu"></a>  CMFCMenuBar::GetDefaultMenu

Pobiera uchwyt do oryginalnego menu. Struktura ładuje oryginalnego menu z pliku zasobów.

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do zasobu menu.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja dostosowuje menu, można użyć tej metody można pobrać dojścia do oryginalnego menu.

##  <a name="getdefaultmenuresid"></a>  CMFCMenuBar::GetDefaultMenuResId

Pobiera identyfikator zasobu domyślnego menu.

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu menu.

### <a name="remarks"></a>Uwagi

Struktura ładuje domyślne menu dla `CMFCMenuBar` obiektu z pliku zasobów.

##  <a name="getfloatpopupdirection"></a>  CMFCMenuBar::GetFloatPopupDirection

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>Parametry

[in] *pButton*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getforcedownarrows"></a>  CMFCMenuBar::GetForceDownArrows

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="gethelpcombobox"></a>  CMFCMenuBar::GetHelpCombobox

Zwraca wskaźnik do **pomocy** pola kombi.

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do **pomocy** pola kombi. Wartość NULL, jeśli **pomocy** pola kombi jest ukryta lub nie jest włączona.

### <a name="remarks"></a>Uwagi

**Pomocy** pola kombi znajduje się po prawej stronie paska menu. Wywołaj metodę [CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox) umożliwiające tego pola kombi.

##  <a name="gethmenu"></a>  CMFCMenuBar::GetHMenu

Pobiera uchwyt do menu dołączone do [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) obiektu.

```
HMENU GetHMenu() const;
```

##  <a name="getmenufont"></a>  CMFCMenuBar::GetMenuFont

Pobiera bieżącą czcionkę z menu.

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*bHorz*<br/>
[in] Parametr logiczny, który określa, czy zwracać czcionki poziomej lub pionowej. Wartość TRUE wskazuje czcionki poziomej.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CFont](../../mfc/reference/cfont-class.md) parametr, który zawiera bieżącą czcionkę paska menu.

### <a name="remarks"></a>Uwagi

Czcionka zwracany jest parametrów globalnych aplikacji. Dwie czcionki globalne są utrzymywane dla wszystkich `CMFCMenuBar` obiektów. Te oddzielne czcionki są używane do menu poziome i pionowe paski.

##  <a name="getmenuitem"></a>  CMFCMenuBar::GetMenuItem

Pobiera [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) obiektu na pasku menu, oparte na indeks elementu.

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>Parametry

*Towaru*<br/>
[in] Indeks elementu menu do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CMFCToolBarButton` obiektu, który odpowiada określony przez indeks *towaru*. Wartość NULL, jeśli ten indeks jest nieprawidłowy.

##  <a name="getrowheight"></a>  CMFCMenuBar::GetRowHeight

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getsystembutton"></a>  CMFCMenuBar::GetSystemButton

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>Parametry

[in] *uiBtn*<br/>

[in] *bByCommand*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getsystembuttonscount"></a>  CMFCMenuBar::GetSystemButtonsCount

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getsystemmenu"></a>  CMFCMenuBar::GetSystemMenu

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="highlightdisableditems"></a>  CMFCMenuBar::HighlightDisabledItems

Określa, czy ramach wyróżnia elementy menu wyłączone.

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>Parametry

*bHighlight*<br/>
[in] Parametrów logiczny, który wskazuje, czy ramach wyróżnia elementy menu niedostępny.

### <a name="remarks"></a>Uwagi

Domyślnie struktura nie zaznacz elementy menu dostępne po użytkownik umieszcza wskaźnik myszy nad nimi.

##  <a name="isbuttonextrasizeavailable"></a>  CMFCMenuBar::IsButtonExtraSizeAvailable

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ishighlightdisableditems"></a>  CMFCMenuBar::IsHighlightDisabledItems

Wskazuje, czy ramach wyróżnia elementy menu niedostępny.

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli elementy menu niedostępne są wyróżnione; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Domyślnie struktura nie zaznacz elementy menu dostępne po użytkownik umieszcza wskaźnik myszy nad nimi. Użyj [CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems) metodę, aby włączyć tę funkcję.

##  <a name="ismenushadows"></a>  CMFCMenuBar::IsMenuShadows

Wskazuje, czy struktury rysuje cieni menu podręcznego.

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli w ramach rysuje cieni menu; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Użyj [CMFCMenuBar::EnableMenuShadows](#enablemenushadows) metodę, aby włączyć lub wyłączyć tę funkcję.

##  <a name="isrecentlyusedmenus"></a>  CMFCMenuBar::IsRecentlyUsedMenus

Wskazuje, czy ostatnio używane polecenia są wyświetlane na pasku menu.

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `CMFCMenuBar` obiektu przedstawia ostatnio używane polecenia menu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj funkcji [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus) do kontrolowania tego, czy pasek menu przedstawia ostatnio używane polecenia menu.

##  <a name="isshowallcommands"></a>  CMFCMenuBar::IsShowAllCommands

Wskazuje, czy w menu są wyświetlane wszystkie polecenia.

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `CMFCMenuBar` Wyświetla listę wszystkich poleceń; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Element `CMFCMenuBar` obiektu można skonfigurować, aby pokazać tylko podzbiór poleceń lub Pokaż wszystkie polecenia. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [klasa CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md).

`IsShowAllCommands` temu wiadomo, jak ta funkcja jest skonfigurowana do `CMFCMenuBar` obiektu. Aby kontrolować, jakie polecenia menu są wyświetlane, należy użyć metod [CMFCMenuBar::SetShowAllCommands](#setshowallcommands) i [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus).

##  <a name="isshowallcommandsdelay"></a>  CMFCMenuBar::IsShowAllCommandsDelay

Wskazuje, czy [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) obiektu Wyświetla wszystkie polecenia, po krótkiej chwili.

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli na pasku menu wyświetlane pełne menu, po krótkiej chwili; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Podczas konfigurowania paska menu, do wyświetlania ostatnio używanych elementów na pasku menu wyświetla pełne menu w jeden z dwóch sposobów:

- Wyświetl pełne menu z opóźnieniem zaprogramowanych z po umieszczeniu kursora strzałkę znajdującą się u dołu menu.

- Wyświetl pełne menu, po użytkownik kliknie strzałkę znajdującą się u dołu menu.

Domyślnie wszystkie `CMFCMenuBar` obiektów użyj opcji, aby wyświetlić pełne menu z niewielkim opóźnieniem. Tej opcji nie można zmienić programowo w `CMFCMenuBar` klasy. Jednak użytkownik może zmienić zachowanie podczas dostosowywania paska narzędzi przy użyciu **Dostosuj** okno dialogowe...

##  <a name="loadstate"></a>  CMFCMenuBar::LoadState

Ładuje stan paska menu z rejestru Windows.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Ciąg, który zawiera ścieżkę klucza rejestru Windows.

*nIndex*<br/>
[in] Identyfikator formantu paska menu.

*uiID*<br/>
[in] Zastrzeżonej wartości.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Użyj [CMFCMenuBar::SaveState](#savestate) metodę, aby zapisać stanu na pasku menu w rejestrze. Zapisane informacje obejmują elementy menu, stan dokowania i pozycja paska menu.

W większości przypadków aplikacji, nie wywołuje `LoadState`. Struktura wywołuje tę metodę podczas inicjowania obszaru roboczego.

##  <a name="onchangehot"></a>  CMFCMenuBar::OnChangeHot

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>Parametry

[in] *iHot*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="ondefaultmenuloaded"></a>  CMFCMenuBar::OnDefaultMenuLoaded

Struktura wywołuje tę metodę podczas ładowania zasobu menu z pliku zasobów.

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
[in] Uchwyt menu dołączone do `CMFCMenuBar` obiektu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji, nic nie robi. Należy przesłonić tę funkcję, aby wykonać kod niestandardowy, po ramach ładuje zasobów menu z pliku zasobów.

##  <a name="onsendcommand"></a>  CMFCMenuBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

[in] *pButton*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="onsetdefaultbuttontext"></a>  CMFCMenuBar::OnSetDefaultButtonText

Struktura wywołuje tę metodę, gdy użytkownik zmieni tekst elementu w pasku menu.

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

*pButton*<br/>
[in] Wskaźnik do [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) obiekt, który użytkownik chce, aby dostosować.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ma zastosowanie w ramach użytkownik zmieni się na pasku menu; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej metody zmiany tekstu przycisku tekst, który zawiera użytkownika.

##  <a name="ontoolhittest"></a>  CMFCMenuBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parametry

[in] *punktu*<br/>

[in] *pTI*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="pretranslatemessage"></a>  CMFCMenuBar::PreTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

[in] *pMsg*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="restoreoriginalstate"></a>  CMFCMenuBar::RestoreOriginalstate

Wywoływane przez platformę, gdy użytkownik wybierze **resetowania** z **Dostosuj** okno dialogowe.

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli metoda się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, gdy użytkownik wybierze **resetowania** menu dostosowywania. Możesz również ręcznie wywołać tę metodę, aby programowo Resetowanie stanu paska menu. Ta metoda ładuje pierwotnego stanu z pliku zasobów.

Przesłonić tę metodę, aby wykonać wszelkie przetwarzania, gdy użytkownik wybierze **resetowania** opcji.

##  <a name="savestate"></a>  CMFCMenuBar::SaveState

Zapisuje stan [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) obiektu do rejestru Windows.

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Ciąg, który zawiera ścieżkę klucza rejestru Windows.

*nIndex*<br/>
[in] Identyfikator formantu paska menu.

*uiID*<br/>
[in] Zastrzeżonej wartości.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE;

### <a name="remarks"></a>Uwagi

Zwykle aplikacja nie mogą wywoływać `SaveState`. Struktura wywołuje tę metodę, gdy obszar roboczy jest serializowana. Aby uzyskać więcej informacji, zobacz [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).

Zapisane informacje obejmują elementy menu, stan dokowania i pozycja paska menu.

##  <a name="setdefaultmenuresid"></a>  CMFCMenuBar::SetDefaultMenuResId

Ustawia domyślne menu dla [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) obiektu oparte na identyfikator zasobu.

```
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>Parametry

*uiResId*<br/>
[in] Identyfikator zasobu menu nowy domyślny.

### <a name="remarks"></a>Uwagi

[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate) metoda przywraca domyślne menu z pliku zasobów.

Użyj [CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid) metodę, aby pobrać domyślnego menu bez przywracania jej.

##  <a name="setforcedownarrows"></a>  CMFCMenuBar::SetForceDownArrows

```
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>Parametry

[in] *bDane wartości*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setmaximizemode"></a>  CMFCMenuBar::SetMaximizeMode

Struktura wywołuje tę metodę, gdy MDI przechodzi do trybu wyświetlania i na pasku menu, które muszą zostać zaktualizowane.

```
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>Parametry

*bMax*<br/>
[in] Wartość logiczna, która określa tryb. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

*pWnd*<br/>
[in] Wskaźnik do okno podrzędne MDI, która zmienia się.

*bRecalcLayout*<br/>
[in] Wartość logiczna określająca, czy układ paska menu, powinny zostać ponownie obliczone natychmiast.

### <a name="remarks"></a>Uwagi

Jeśli okno podrzędne MDI jest zmaksymalizowane, pasek menu, dołączone do ramce głównej okna MDI Wyświetla menu systemu i **Minimalizuj**, **Maksymalizuj** i **Zamknij** przycisków. Jeśli *bMax* ma wartość TRUE i *pWnd* nie ma wartości NULL, jest zmaksymalizowane okno podrzędne MDI i na pasku menu należy zastosować dodatkowe kontrolki. W przeciwnym razie na pasku menu powraca do stanu regularne.

##  <a name="setmenubuttonrtc"></a>  CMFCMenuBar::SetMenuButtonRTC

Ustawia informacji o klasie czasu wykonywania, używającej platformę, gdy użytkownik tworzy przyciski menu.

```
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>Parametry

*pMenuButtonRTC*<br/>
[in] [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) informacji dla klasy pochodnej z [klasa CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md).

### <a name="remarks"></a>Uwagi

Gdy użytkownik dodaje nowe przyciski na pasku menu, szablon tworzy przyciski dynamicznie. Domyślnie tworzy `CMFCMenuButton` obiektów. Zastępuje tę metodę, aby zmienić typ obiekty przycisku, utworzone przez platformę.

##  <a name="setmenufont"></a>  CMFCMenuBar::SetMenuFont

Ustawia czcionkę dla wszystkich pasków menu w aplikacji.

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
[in] Wskaźnik do [LOGFONT](/windows/desktop/api/dimm/ns-dimm-__midl___midl_itf_dimm_0000_0000_0003) strukturę, która definiuje czcionki do ustawienia.

*bHorz*<br/>
[in] Wartość TRUE, jeśli chcesz, aby *lpLogFont* parametr służący do czcionki pionowej, wartość FALSE, jeśli chcesz, aby służyć do czcionki poziomej.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Dwie czcionki są używane dla wszystkich `CMFCMenuBar` obiektów. Te oddzielne czcionki są używane do menu poziome i pionowe paski.

Ustawienia czcionki są zmienne globalne i mają wpływ na wszystkie `CMFCMenuBar` obiektów.

##  <a name="setrecentlyusedmenus"></a>  CMFCMenuBar::SetRecentlyUsedMenus

Czy Wyświetla pasek menu ostatnio używane polecenia menu kontrolki.

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parametry

*bOn*<br/>
[in] Wartość logiczna, która kontroluje, czy są wyświetlane polecenia menu ostatnio używanych.

##  <a name="setshowallcommands"></a>  CMFCMenuBar::SetShowAllCommands

Określa, czy menu pokazuje wszystkich dostępnych poleceń.

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>Parametry

*bShowAllCommands*<br/>
[in] Parametr logiczny, który określa, czy menu podręcznym pokazuje wszystkie polecenia menu.

### <a name="remarks"></a>Uwagi

Jeśli menu nie są wyświetlane wszystkie polecenia menu, powoduje ukrycie opcji poleceń, które są rzadko używane. Aby uzyskać więcej informacji na temat wyświetlania poleceń menu zobacz [klasa CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md).

## <a name="see-also"></a>Zobacz także

[Diagram hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
