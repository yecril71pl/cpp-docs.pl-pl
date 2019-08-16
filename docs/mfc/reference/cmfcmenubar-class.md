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
ms.openlocfilehash: 61a5f83e31b4793ca6467287c99f3b9708659402
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505228"
---
# <a name="cmfcmenubar-class"></a>Klasa CMFCMenuBar

Pasek menu, który implementuje dokowanie.
Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|(Przesłania `CMFCToolBar::AdjustLocations`).|
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|Określa, czy etykiety tekstowe mogą być wyświetlane w obszarze obrazy na przyciskach paska narzędzi. (Przesłania [CMFCToolBar:: AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels).)|
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Przesłania `CPane::AllowShowOnPaneMenu`).|
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|Oblicza rozmiar poziomy paska narzędzi. (Przesłania [CMFCToolBar:: CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout).)|
|[CMFCMenuBar::CalcLayout](#calclayout)|(Przesłania `CMFCToolBar::CalcLayout`).|
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|Oblicza maksymalną wysokość przycisków na pasku narzędzi. (Przesłania [CMFCToolBar:: CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight).)|
|[CMFCMenuBar::CanBeClosed](#canbeclosed)|Określa, czy użytkownik może zamknąć ten pasek narzędzi. (Przesłania [CMFCToolBar:: CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed).)|
|[CMFCMenuBar::CanBeRestored](#canberestored)|Określa, czy system może przywrócić oryginalny stan paska narzędzi po dostosowaniu. (Przesłania [CMFCToolBar:: CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCMenuBar:: Create](#create)|Tworzy formant menu i dołącza go do `CMFCMenuBar` obiektu.|
|[CMFCMenuBar::CreateEx](#createex)|`CMFCMenuBar` Tworzy obiekt z dodatkowymi opcjami stylu.|
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|`CMFCMenuBar` Inicjuje obiekt. Akceptuje parametr HMENU, który działa jako szablon dla wypełnionego `CMFCMenuBar`elementu.|
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|Włącza pole kombi **pomocy** znajdujące się po prawej stronie paska menu.|
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|Określa, czy mają być wyświetlane cienie dla menu podręcznych.|
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|(Przesłania [CPane:: GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize).)|
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|Zwraca szerokość przycisków paska narzędzi. (Przesłania [CMFCToolBar:: GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth).)|
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|Zwraca uchwyt do oryginalnego menu w pliku zasobów.|
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|Zwraca identyfikator zasobu oryginalnego menu w pliku zasobów.|
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|Zwraca wskaźnik do pola kombi **pomocy** .|
|[CMFCMenuBar::GetHMenu](#gethmenu)|Zwraca uchwyt do menu dołączonego do `CMFCMenuBar` obiektu.|
|[CMFCMenuBar::GetMenuFont](#getmenufont)|Zwraca bieżącą czcionkę globalną dla obiektów menu.|
|[CMFCMenuBar:: getmenuitem](#getmenuitem)|Zwraca przycisk paska narzędzi skojarzony z podanym indeksem elementu.|
|[CMFCMenuBar::GetRowHeight](#getrowheight)|Zwraca wysokość przycisków paska narzędzi. (Przesłania [CMFCToolBar:: GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|Wskazuje, czy elementy menu wyłączone są wyróżnione.|
|[CMFCMenuBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Określa, czy pasek narzędzi może wyświetlać przyciski, które mają rozszerzone obramowania. (Przesłania [CMFCToolBar:: IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|Wskazuje, czy elementy wyłączone są wyróżnione.|
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|Wskazuje, czy cienie są rysowane dla menu podręcznych.|
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|Wskazuje, czy ostatnio używane polecenia menu są wyświetlane na pasku menu.|
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|Wskazuje, czy menu podręczne są wyświetlane wszystkie polecenia.|
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|Wskazuje, czy menu wyświetla wszystkie polecenia po krótkim opóźnieniu.|
|[CMFCMenuBar:: LoadState](#loadstate)|Ładuje stan `CMFCMenuBar` obiektu z rejestru.|
|[CMFCMenuBar::OnChangeHot](#onchangehot)|Wywoływane przez platformę, gdy użytkownik wybierze przycisk na pasku narzędzi. (Przesłania [CMFCToolBar:: OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot).)|
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|Wywoływane przez platformę, gdy okno ramki ładuje domyślne menu z pliku zasobów.|
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|(Przesłania `CMFCToolBar::OnSendCommand`).|
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|Wywoływane przez platformę, gdy menu jest w trybie dostosowywania, a użytkownik zmienia tekst elementu menu.|
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(Przesłania `CMFCToolBar::OnToolHitTest`).|
|[CMFCMenuBar::P reTranslateMessage](#pretranslatemessage)|(Przesłania `CMFCToolBar::PreTranslateMessage`).|
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|Wywoływane przez platformę, gdy menu jest w trybie dostosowywania, a użytkownik wybierze opcję **Resetuj** dla paska menu.|
|[CMFCMenuBar:: SaveState](#savestate)|Zapisuje stan `CMFCMenuBar` obiektu w rejestrze.|
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|Ustawia oryginalne menu w pliku zasobów.|
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||
|[CMFCMenuBar:: setmaksymalizujmode](#setmaximizemode)|Wywoływane przez platformę, gdy okno podrzędne MDI zmieni swój tryb wyświetlania. Jeśli okno podrzędne MDI jest nowo zmaksymalizowane lub nie jest już zmaksymalizowane, ta metoda aktualizuje pasek menu.|
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|Ustawia informacje o klasie środowiska uruchomieniowego, które są generowane podczas dynamicznego tworzenia przycisków menu przez użytkownika.|
|[CMFCMenuBar::SetMenuFont](#setmenufont)|Ustawia czcionkę dla wszystkich menu w aplikacji.|
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|Określa, czy na pasku menu są wyświetlane ostatnio używane polecenia menu.|
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|Określa, czy pasek menu zawiera wszystkie polecenia.|

## <a name="remarks"></a>Uwagi

`CMFCMenuBar` Klasa to pasek menu, który implementuje funkcjonalność dokowania. Jest on podobny do paska narzędzi, chociaż nie może być zamknięty — jest zawsze wyświetlany.

`CMFCMenuBar`obsługuje opcję wyświetlania ostatnio używanych obiektów elementu menu. Jeśli ta opcja jest włączona, `CMFCMenuBar` wyświetla tylko podzestaw dostępnych poleceń podczas pierwszego wyświetlania. Następnie ostatnio używane polecenia są wyświetlane razem z oryginalnym podzbiorem poleceń. Ponadto użytkownik może zawsze rozwinąć menu, aby wyświetlić wszystkie dostępne polecenia. W rezultacie każde dostępne polecenie jest skonfigurowane do ciągłego wyświetlania lub do wyświetlania tylko wtedy, gdy zostało ono ostatnio zaznaczone.

Aby użyć `CMFCMenuBar` obiektu, osadź go w głównym obiekcie ramki okna. Podczas przetwarzania `WM_CREATE` komunikatu, wywołaj `CMFCMenuBar::Create` lub `CMFCMenuBar::CreateEx`. Niezależnie od tego, która funkcja tworzenia jest używana, Przekaż wskaźnik do okna głównego ramki. Następnie Włącz Dokowanie przez wywołanie [CFrameWndEx:: EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Dokowanie tego menu przez wywołanie [CFrameWndEx::D ockpane](../../mfc/reference/cframewndex-class.md#dockpane).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia różnych metod w `CMFCMenuBar` klasie. W przykładzie pokazano, jak ustawić styl okienka, włączyć przycisk Dostosuj, włączyć okno Pomoc, włączyć cieniowanie dla menu podręcznych i zaktualizować pasek menu. Ten fragment kodu jest częścią przykładu demonstracyjnego dla programu [IE](../../overview/visual-cpp-samples.md).

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

**Nagłówek:** afxmenubar. h

##  <a name="adjustlocations"></a>CMFCMenuBar::AdjustLocations

Dostosowuje położenie elementów menu na pasku menu.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Uwagi

##  <a name="allowchangetextlabels"></a>CMFCMenuBar::AllowChangeTextLabels

Określa, czy etykiety tekstowe są dozwolone w obszarze obrazów na pasku menu.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli użytkownik może wybrać opcję wyświetlania etykiet tekstowych w obszarze obrazy.

### <a name="remarks"></a>Uwagi

##  <a name="allowshowonpanemenu"></a>CMFCMenuBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="calcfixedlayout"></a>CMFCMenuBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

podczas *bStretch*<br/>

podczas *bHorz*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="calclayout"></a>CMFCMenuBar::CalcLayout

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>Parametry

podczas *dwMode*<br/>

podczas *nLength*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="calcmaxbuttonheight"></a>CMFCMenuBar::CalcMaxButtonHeight

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="canbeclosed"></a>CMFCMenuBar::CanBeClosed

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="canberestored"></a>CMFCMenuBar::CanBeRestored

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="create"></a>CMFCMenuBar:: Create

Tworzy formant menu i dołącza go do obiektu [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) .

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
podczas Wskaźnik do okna nadrzędnego dla nowego `CMFCMenuBar` obiektu.

*dwStyle*<br/>
podczas Styl nowego paska menu.

*nID*<br/>
podczas Identyfikator okna podrzędnego paska menu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Po utworzeniu `CMFCMenuBar` obiektu należy wywołać metodę `Create`. Ta metoda tworzy `CMFCMenuBar` formant i dołącza go `CMFCMenuBar` do obiektu.

Aby uzyskać więcej informacji na temat stylów paska narzędzi, zobacz [CBasePane:: setselector](../../mfc/reference/cbasepane-class.md#setpanestyle).

##  <a name="createex"></a>CMFCMenuBar::CreateEx

Tworzy obiekt [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) o określonych stylach rozszerzonych.

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
podczas Wskaźnik do okna nadrzędnego nowego `CMFCMenuBar` obiektu.

*dwCtrlStyle*<br/>
podczas Dodatkowe style dla nowego paska menu.

*dwStyle*<br/>
podczas Styl główny nowego paska menu.

*rcBorders*<br/>
podczas Parametr określający rozmiary obramowania `CMFCMenuBar` obiektu. `CRect`

*nID*<br/>
podczas Identyfikator okna podrzędnego paska menu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Należy używać tej funkcji zamiast [CMFCMenuBar:: Create](#create) , gdy chcesz określić style oprócz stylu paska narzędzi. Niektóre często używane dodatkowe style to TBSTYLE_TRANSPARENT i CBRS_TOP.

Aby uzyskać listę dodatkowych stylów, zobacz [kontrolki paska narzędzi i style przycisków](/windows/win32/Controls/toolbar-control-and-button-styles), [Style formantów wspólnych](/windows/win32/Controls/common-control-styles)i [wspólne style okien](/windows/win32/winmsg/window-styles).

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia `CreateEx` metody `CMFCMenuBar` klasy. Ten fragment kodu jest częścią przykładu demonstracyjnego dla programu [IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

##  <a name="createfrommenu"></a>CMFCMenuBar::CreateFromMenu

Inicjuje obiekt [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) . Ta metoda modeluje `CMFCMenuBar` obiekt po parametrze HMENU.

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
podczas Uchwyt do zasobu menu. `CreateFromMenu`używa tego zasobu jako szablonu dla `CMFCMenuBar`.

*bDefaultMenu*<br/>
podczas Wartość logiczna wskazująca, czy nowe menu jest menu domyślnym.

*bForceUpdate*<br/>
podczas Wartość logiczna wskazująca, czy ta metoda wymusza aktualizację menu.

### <a name="remarks"></a>Uwagi

Użyj tej metody, jeśli chcesz, aby formant menu miał te same elementy menu co zasób menu. Ta metoda jest wywoływana po wywołaniu elementu [CMFCMenuBar:: Create](#create) lub [CMFCMenuBar:: CreateEx](#createex).

##  <a name="enablehelpcombobox"></a>CMFCMenuBar::EnableHelpCombobox

Włącza pole kombi **pomocy** znajdujące się po prawej stronie paska menu.

```
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
podczas Identyfikator polecenia dla przycisku pola kombi **pomocy** .

*lpszPrompt*<br/>
podczas Ciąg, który zawiera tekst, który zostanie wyświetlony przez strukturę w polu kombi, jeśli jest pusty i nie jest aktywny. Na przykład wpisz tutaj tekst.

*nComboBoxWidth*<br/>
podczas Szerokość przycisku pola kombi w pikselach.

### <a name="remarks"></a>Uwagi

Pole kombi **pomocy** przypomina pole kombi **pomocy** na pasku menu programu Microsoft Word.

Po wywołaniu tej metody z *uiID* ustawionym na 0, ta metoda ukrywa pole kombi. W przeciwnym razie ta metoda Wyświetla pole kombi automatycznie po prawej stronie paska menu. Po wywołaniu tej metody Wywołaj [CMFCMenuBar:: GetHelpCombobox](#gethelpcombobox) , aby uzyskać wskaźnik do wstawionego obiektu [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) .

##  <a name="enablemenushadows"></a>CMFCMenuBar::EnableMenuShadows

Włącza cienie dla menu podręcznych.

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
podczas Parametr logiczny, który wskazuje, czy cienie powinny być włączone dla menu podręcznych.

### <a name="remarks"></a>Uwagi

Algorytm używany przez tę metodę jest skomplikowany i może obniżyć wydajność aplikacji w wolniejszych systemach.

##  <a name="getavailableexpandsize"></a>CMFCMenuBar::GetAvailableExpandSize

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getcolumnwidth"></a>CMFCMenuBar::GetColumnWidth

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getdefaultmenu"></a>CMFCMenuBar::GetDefaultMenu

Pobiera uchwyt do oryginalnego menu. Struktura ładuje oryginalne menu z pliku zasobów.

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do zasobu menu.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja dostosowuje menu, można użyć tej metody do pobrania uchwytu do oryginalnego menu.

##  <a name="getdefaultmenuresid"></a>CMFCMenuBar::GetDefaultMenuResId

Pobiera identyfikator zasobu dla menu domyślnego.

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu menu.

### <a name="remarks"></a>Uwagi

Struktura ładuje domyślne menu dla `CMFCMenuBar` obiektu z pliku zasobów.

##  <a name="getfloatpopupdirection"></a>CMFCMenuBar::GetFloatPopupDirection

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>Parametry

podczas *pButton*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getforcedownarrows"></a>CMFCMenuBar::GetForceDownArrows

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="gethelpcombobox"></a>CMFCMenuBar::GetHelpCombobox

Zwraca wskaźnik do pola kombi **pomocy** .

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pola kombi **pomocy** . Wartość NULL, jeśli pole kombi **pomocy** jest ukryte lub nie jest włączone.

### <a name="remarks"></a>Uwagi

Pole kombi **pomocy** znajduje się po prawej stronie paska menu. Wywołaj metodę [CMFCMenuBar:: EnableHelpCombobox](#enablehelpcombobox) , aby włączyć to pole kombi.

##  <a name="gethmenu"></a>CMFCMenuBar::GetHMenu

Pobiera uchwyt do menu dołączonego do obiektu [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) .

```
HMENU GetHMenu() const;
```

##  <a name="getmenufont"></a>CMFCMenuBar::GetMenuFont

Pobiera bieżącą czcionkę menu.

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*bHorz*<br/>
podczas Parametr logiczny, który określa, czy ma zostać zwrócona czcionka pozioma, czy pionowa. Wartość TRUE oznacza czcionkę poziomą.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do parametru [CFont](../../mfc/reference/cfont-class.md) , który zawiera bieżącą czcionkę paska menu.

### <a name="remarks"></a>Uwagi

Zwracana czcionka jest parametrem globalnym dla aplikacji. Dla wszystkich `CMFCMenuBar` obiektów są utrzymywane dwie czcionki globalne. Te oddzielne czcionki są używane dla pionowych pasków menu.

##  <a name="getmenuitem"></a>CMFCMenuBar:: getmenuitem

Pobiera obiekt [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) na pasku menu opartym na indeksie elementu.

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>Parametry

*iItem*<br/>
podczas Indeks elementu menu, który ma zostać zwrócony.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CMFCToolBarButton` obiektu, który jest zgodny z indeksem określonym przez *iItem*. Wartość NULL, jeśli indeks jest nieprawidłowy.

##  <a name="getrowheight"></a>CMFCMenuBar::GetRowHeight

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getsystembutton"></a>CMFCMenuBar::GetSystemButton

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>Parametry

podczas *uiBtn*<br/>

podczas *bByCommand*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getsystembuttonscount"></a>CMFCMenuBar::GetSystemButtonsCount

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getsystemmenu"></a>CMFCMenuBar::GetSystemMenu

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="highlightdisableditems"></a>CMFCMenuBar::HighlightDisabledItems

Określa, czy struktura wyróżnia wyłączone elementy menu.

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>Parametry

*bHighlight*<br/>
podczas Parametr logiczny, który wskazuje, czy struktura Podświetla elementy menu niedostępne.

### <a name="remarks"></a>Uwagi

Domyślnie struktura nie wyróżnia niedostępnych elementów menu, gdy użytkownik umieści wskaźnik myszy nad nimi.

##  <a name="isbuttonextrasizeavailable"></a>CMFCMenuBar::IsButtonExtraSizeAvailable

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ishighlightdisableditems"></a>CMFCMenuBar::IsHighlightDisabledItems

Wskazuje, czy struktura Podświetla elementy menu niedostępne.

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli elementy menu niedostępne są wyróżnione; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Domyślnie struktura nie wyróżnia niedostępnych elementów menu, gdy użytkownik umieści wskaźnik myszy nad nimi. Aby włączyć tę funkcję, należy użyć metody [CMFCMenuBar:: HighlightDisabledItems](#highlightdisableditems) .

##  <a name="ismenushadows"></a>CMFCMenuBar::IsMenuShadows

Wskazuje, czy struktura rysuje cienie dla menu podręcznych.

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli struktura rysuje cienie menu; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby włączyć lub wyłączyć tę funkcję, należy użyć metody [CMFCMenuBar:: EnableMenuShadows](#enablemenushadows) .

##  <a name="isrecentlyusedmenus"></a>CMFCMenuBar::IsRecentlyUsedMenus

Wskazuje, czy ostatnio używane polecenia menu są wyświetlane na pasku menu.

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli `CMFCMenuBar` obiekt pokazuje ostatnio używane polecenia menu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj funkcji [CMFCMenuBar:: SetRecentlyUsedMenus](#setrecentlyusedmenus) , aby określić, czy pasek menu zawiera ostatnio używane polecenia menu.

##  <a name="isshowallcommands"></a>CMFCMenuBar::IsShowAllCommands

Wskazuje, czy menu wyświetla wszystkie polecenia.

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, `CMFCMenuBar` jeśli są wyświetlane wszystkie polecenia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`CMFCMenuBar` Obiekt można skonfigurować w taki sposób, aby pokazywał wszystkie polecenia lub pokazywał tylko podzestaw poleceń. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [Klasa CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md).

`IsShowAllCommands`informuje o tym, jak ta funkcja jest skonfigurowana dla `CMFCMenuBar` obiektu. Aby kontrolować, które polecenia menu są wyświetlane, użyj metod [CMFCMenuBar:: SetShowAllCommands](#setshowallcommands) i [CMFCMenuBar:: SetRecentlyUsedMenus](#setrecentlyusedmenus).

##  <a name="isshowallcommandsdelay"></a>CMFCMenuBar::IsShowAllCommandsDelay

Wskazuje, czy obiekt [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) wyświetla wszystkie polecenia po krótkim opóźnieniu.

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli pasek menu wyświetla pełne menu po krótkim opóźnieniu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po skonfigurowaniu paska menu w celu wyświetlenia ostatnio używanych elementów pasek menu wyświetla pełne menu na jeden z dwóch sposobów:

- Wyświetl pełne menu po opóźnieniu zaprogramowanym od momentu, gdy użytkownik umieści kursor nad strzałką w dolnej części menu.

- Wyświetl pełne menu, gdy użytkownik kliknie strzałkę w dolnej części menu.

Domyślnie wszystkie `CMFCMenuBar` obiekty używają opcji, aby wyświetlić pełne menu po krótkim opóźnieniu. Tej opcji nie można zmienić programowo w `CMFCMenuBar` klasie. Jednak użytkownik może zmienić zachowanie podczas dostosowywania paska narzędzi przy użyciu okna dialogowego **Dostosowywanie** .

##  <a name="loadstate"></a>CMFCMenuBar:: LoadState

Ładuje stan paska menu z rejestru systemu Windows.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
podczas Ciąg, który zawiera ścieżkę klucza rejestru systemu Windows.

*nIndex*<br/>
podczas Identyfikator kontrolki paska menu.

*uiID*<br/>
podczas Wartość zastrzeżona.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj metody [CMFCMenuBar:: SaveState](#savestate) , aby zapisać stan paska menu w rejestrze. Zapisane informacje obejmują elementy menu, stan dokowania i położenie paska menu.

W większości przypadków aplikacja nie wywołuje `LoadState`. Struktura wywołuje tę metodę po zainicjowaniu obszaru roboczego.

##  <a name="onchangehot"></a>CMFCMenuBar::OnChangeHot

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>Parametry

podczas *iHot*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="ondefaultmenuloaded"></a>CMFCMenuBar::OnDefaultMenuLoaded

Struktura wywołuje tę metodę podczas ładowania zasobu menu z pliku zasobów.

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
podczas Uchwyt dla menu dołączonego do `CMFCMenuBar` obiektu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji nic nie robi. Przesłoń tę funkcję, aby wykonać kod niestandardowy po załadowaniu przez strukturę zasobu menu z pliku zasobów.

##  <a name="onsendcommand"></a>CMFCMenuBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

podczas *pButton*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="onsetdefaultbuttontext"></a>CMFCMenuBar::OnSetDefaultButtonText

Struktura wywołuje tę metodę, gdy użytkownik zmienia tekst elementu na pasku menu.

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

*pButton*<br/>
podczas Wskaźnik do obiektu [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) , który użytkownik chce dostosować.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli struktura stosuje zmiany użytkownika na pasku menu; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej metody zmienia tekst przycisku na tekst udostępniany przez użytkownika.

##  <a name="ontoolhittest"></a>CMFCMenuBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parametry

podczas *punkt*<br/>

podczas *PTI*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="pretranslatemessage"></a>CMFCMenuBar::P reTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

podczas *pMsg*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="restoreoriginalstate"></a>CMFCMenuBar::RestoreOriginalstate

Wywoływane przez platformę, gdy użytkownik wybierze **Reset** z okna dialogowego **Dostosowywanie** .

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, gdy użytkownik wybierze opcję **Zresetuj** z menu Dostosowywanie. Możesz również ręcznie wywołać tę metodę, aby programowo zresetować stan paska menu. Ta metoda ładuje oryginalny stan z pliku zasobów.

Zastąp tę metodę, jeśli chcesz przeprowadzić przetwarzanie, gdy użytkownik wybierze opcję **Reset** .

##  <a name="savestate"></a>CMFCMenuBar:: SaveState

Zapisuje stan obiektu [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) w rejestrze systemu Windows.

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
podczas Ciąg, który zawiera ścieżkę klucza rejestru systemu Windows.

*nIndex*<br/>
podczas Identyfikator kontrolki paska menu.

*uiID*<br/>
podczas Wartość zastrzeżona.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie; w przeciwnym razie FALSE;

### <a name="remarks"></a>Uwagi

Zazwyczaj aplikacja nie wywołuje `SaveState`. Struktura wywołuje tę metodę, gdy obszar roboczy jest serializowany. Aby uzyskać więcej informacji, zobacz [CWinAppEx:: SaveState](../../mfc/reference/cwinappex-class.md#savestate).

Zapisane informacje obejmują elementy menu, stan dokowania i położenie paska menu.

##  <a name="setdefaultmenuresid"></a>CMFCMenuBar::SetDefaultMenuResId

Ustawia menu domyślne dla obiektu [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) na podstawie identyfikatora zasobu.

```
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>Parametry

*uiResId*<br/>
podczas Identyfikator zasobu dla nowego menu domyślnego.

### <a name="remarks"></a>Uwagi

Metoda [CMFCMenuBar:: RestoreOriginalstate](#restoreoriginalstate) przywraca domyślne menu z pliku zasobów.

Użyj metody [CMFCMenuBar:: GetDefaultMenuResId](#getdefaultmenuresid) , aby pobrać domyślne menu bez jego przywracania.

##  <a name="setforcedownarrows"></a>CMFCMenuBar::SetForceDownArrows

```
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>Parametry

podczas *bValue*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setmaximizemode"></a>CMFCMenuBar:: setmaksymalizujmode

Struktura wywołuje tę metodę, gdy obiekt MDI zmieni swój tryb wyświetlania, a pasek menu musi zostać zaktualizowany.

```
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>Parametry

*bMax*<br/>
podczas Wartość logiczna określająca tryb. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

*pWnd*<br/>
podczas Wskaźnik do podrzędnego okna MDI, które zmienia się.

*bRecalcLayout*<br/>
podczas Wartość logiczna określająca, czy układ paska menu należy ponownie obliczyć od razu.

### <a name="remarks"></a>Uwagi

Gdy okno podrzędne MDI jest zmaksymalizowane, pasek menu dołączony do okna głównego ramki MDI wyświetla menu system i przyciski **Minimalizuj**, **Maksymalizuj** i **Zamknij** . Jeśli *Bmax* ma wartość true, a *pWnd* nie ma wartości null, okno podrzędne MDI jest zmaksymalizowane i pasek menu musi zawierać dodatkowe kontrolki. W przeciwnym razie pasek menu powraca do normalnego stanu.

##  <a name="setmenubuttonrtc"></a>CMFCMenuBar::SetMenuButtonRTC

Ustawia informacje o klasie środowiska uruchomieniowego używane przez platformę, gdy użytkownik tworzy przyciski menu.

```
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>Parametry

*pMenuButtonRTC*<br/>
podczas [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) informacje dotyczące klasy pochodzącej od [klasy CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md).

### <a name="remarks"></a>Uwagi

Gdy użytkownik dodaje nowe przyciski do paska menu, struktura tworzy przyciski dynamicznie. Domyślnie tworzy `CMFCMenuButton` obiekty. Zastąp tę metodę, aby zmienić typ obiektów Button tworzonych przez strukturę.

##  <a name="setmenufont"></a>CMFCMenuBar::SetMenuFont

Ustawia czcionkę dla wszystkich pasków menu w aplikacji.

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
podczas Wskaźnik do struktury [LOGFONT](/windows/win32/api/dimm/ns-dimm-__midl___midl_itf_dimm_0000_0000_0003) , który definiuje czcionkę do ustawienia.

*bHorz*<br/>
podczas PRAWDA, jeśli chcesz, aby parametr *lpLogFont* był używany dla czcionki pionowej, wartość false, jeśli ma być używana dla czcionki poziomej.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Dla wszystkich `CMFCMenuBar` obiektów są używane dwie czcionki. Te oddzielne czcionki są używane dla pionowych pasków menu.

Ustawienia czcionki są zmiennymi globalnymi i mają wpływ `CMFCMenuBar` na wszystkie obiekty.

##  <a name="setrecentlyusedmenus"></a>CMFCMenuBar::SetRecentlyUsedMenus

Określa, czy na pasku menu są wyświetlane ostatnio używane polecenia menu.

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parametry

*bOn*<br/>
podczas Wartość logiczna, która kontroluje, czy są wyświetlane ostatnio używane polecenia menu.

##  <a name="setshowallcommands"></a>CMFCMenuBar::SetShowAllCommands

Określa, czy menu wyświetla wszystkie dostępne polecenia.

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>Parametry

*bShowAllCommands*<br/>
podczas Parametr logiczny, który określa, czy menu podręczne pokazuje wszystkie polecenia menu.

### <a name="remarks"></a>Uwagi

Jeśli menu nie wyświetla wszystkich poleceń menu, ukrywa polecenia, które są rzadko używane. Aby uzyskać więcej informacji o wyświetlaniu poleceń menu, zobacz [Klasa CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md).

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
