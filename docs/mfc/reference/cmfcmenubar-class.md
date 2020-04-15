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
ms.openlocfilehash: 50dd488d1f59c99b8fee1eb96acf6d0041547df9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369683"
---
# <a name="cmfcmenubar-class"></a>Klasa CMFCMenuBar

Pasek menu, który implementuje dokowanie.
Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|(Przesłania `CMFCToolBar::AdjustLocations`).|
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|Określa, czy etykiety tekstowe mogą być wyświetlane w obrazach na przyciskach paska narzędzi. (Zastępuje [CMFCToolBar::AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels).)|
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Przesłania `CPane::AllowShowOnPaneMenu`).|
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|Oblicza poziomy rozmiar paska narzędzi. (Zastępuje [CMFCToolBar::CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout).)|
|[CMFCMenuBar::CalcLayout](#calclayout)|(Przesłania `CMFCToolBar::CalcLayout`).|
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|Oblicza maksymalną wysokość przycisków na pasku narzędzi. (Zastępuje [CMFCToolBar::CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight).)|
|[CMFCMenuBar::CanBeclosed](#canbeclosed)|Określa, czy użytkownik może zamknąć pasek narzędzi. (Zastępuje [CMFCToolBar::CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed).)|
|[CMFCMenuBar::CanBeRestored](#canberestored)|Określa, czy system może przywrócić pasek narzędzi do stanu pierwotnego po dostosowaniu. (Zastępuje [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCMenuBar::Utwórz](#create)|Tworzy formant menu i dołącza `CMFCMenuBar` go do obiektu.|
|[CMFCMenuBar::CreateEx](#createex)|Tworzy `CMFCMenuBar` obiekt z dodatkowymi opcjami stylu.|
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|Inicjuje `CMFCMenuBar` obiekt. Akceptuje parametr HMENU, który działa jako `CMFCMenuBar`szablon dla wypełnionego .|
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|Włącza pole kombi **Pomocy,** które znajduje się po prawej stronie paska menu.|
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|Określa, czy cienie mają być wyświetlane dla menu podręcznych.|
|[CMFCMenuBar::GetAvailableRozwińRozwińRozwiń](#getavailableexpandsize)|(Zastępuje [CPane::GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize).)|
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|Zwraca szerokość przycisków paska narzędzi. (Zastępuje [CMFCToolBar::GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth).)|
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|Zwraca dojście do oryginalnego menu w pliku zasobów.|
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|Zwraca identyfikator zasobu oryginalnego menu w pliku zasobu.|
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|Zwraca wskaźnik do pola kombi **Pomocy.**|
|[CMFCMenuBar::GetHMenu](#gethmenu)|Zwraca uchwyt do menu dołączonego do `CMFCMenuBar` obiektu.|
|[CMFCMenuBar::GetMenuFont](#getmenufont)|Zwraca bieżącą czcionkę globalną dla obiektów menu.|
|[CMFCMenuBar::GetMenuItem](#getmenuitem)|Zwraca przycisk paska narzędzi skojarzony z podanym indeksem towaru.|
|[CMFCMenuBar::GetRowHeight](#getrowheight)|Zwraca wysokość przycisków paska narzędzi. (Zastępuje [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFCMenuBar::Przycisk Systemu Get](#getsystembutton)||
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|Wskazuje, czy wyłączone elementy menu są wyróżnione.|
|[CMFCMenuBar::IsButtonExtraSizeDostępne](#isbuttonextrasizeavailable)|Określa, czy na pasku narzędzi mogą być wyświetlane przyciski z rozszerzonymi obramowaniami. (Zastępuje [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|Wskazuje, czy wyłączone elementy są wyróżnione.|
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|Wskazuje, czy cienie są rysowane dla menu podręcznych.|
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|Wskazuje, czy ostatnio używane polecenia menu są wyświetlane na pasku menu.|
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|Wskazuje, czy w menu podręcznym są wyświetlane wszystkie polecenia.|
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|Wskazuje, czy w menu są wyświetlane wszystkie polecenia po krótkim opóźnieniu.|
|[CMFCMenuBar::Stan obciążenia](#loadstate)|Ładuje stan `CMFCMenuBar` obiektu z rejestru.|
|[CMFCMenuBar::OnChangeHot](#onchangehot)|Wywoływane przez strukturę, gdy użytkownik wybiera przycisk na pasku narzędzi. (Zastępuje [CMFCToolBar::OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot).)|
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|Wywoływane przez strukturę, gdy okno ramki ładuje domyślne menu z pliku zasobów.|
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|(Przesłania `CMFCToolBar::OnSendCommand`).|
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|Wywoływane przez strukturę, gdy menu jest w trybie dostosowywania i użytkownik zmienia tekst elementu menu.|
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(Przesłania `CMFCToolBar::OnToolHitTest`).|
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|(Przesłania `CMFCToolBar::PreTranslateMessage`).|
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|Wywoływane przez strukturę, gdy menu jest w trybie dostosowywania i użytkownik wybiera **Reset** dla paska menu.|
|[CMFCMenuBar::Stan zapisu](#savestate)|Zapisuje stan obiektu `CMFCMenuBar` w rejestrze.|
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|Ustawia oryginalne menu w pliku zasobów.|
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|Wywoływane przez platformę, gdy okno podrzędne MDI zmienia tryb wyświetlania. Jeśli okno podrzędne MDI jest nowo zmaksymalizowane lub nie jest już zmaksymalizowane, ta metoda aktualizuje pasek menu.|
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|Ustawia informacje o klasie środowiska wykonawczego, które są generowane, gdy użytkownik dynamicznie tworzy przyciski menu.|
|[CMFCMenuBar::SetMenuFont](#setmenufont)|Ustawia czcionkę dla wszystkich menu w aplikacji.|
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|Określa, czy na pasku menu są wyświetlane ostatnio używane polecenia menu.|
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|Określa, czy na pasku menu są wyświetlane wszystkie polecenia.|

## <a name="remarks"></a>Uwagi

Klasa `CMFCMenuBar` jest paskiem menu, który implementuje funkcje dokowania. Przypomina pasek narzędzi, chociaż nie można go zamknąć - jest zawsze wyświetlany.

`CMFCMenuBar`obsługuje opcję wyświetlania ostatnio używanych obiektów elementów menu. Jeśli ta opcja jest `CMFCMenuBar` włączona, wyświetla tylko podzbiór dostępnych poleceń przy pierwszym wyświetlaniu. Następnie wyświetlane są ostatnio używane polecenia wraz z oryginalnym podzbiorem poleceń. Ponadto użytkownik zawsze może rozwinąć menu, aby wyświetlić wszystkie dostępne polecenia. W związku z tym każde dostępne polecenie jest skonfigurowane do ciągłego wyświetlania lub wyświetlania tylko wtedy, gdy zostało niedawno wybrane.

Aby użyć `CMFCMenuBar` obiektu, należy osadzić go w obiekcie ramki okna głównego. Podczas przetwarzania `WM_CREATE` wiadomości, `CMFCMenuBar::Create` `CMFCMenuBar::CreateEx`zadzwoń lub . Niezależnie od tego, której funkcji tworzenia używasz, należy przekazać wskaźnik do okna ramki głównej. Następnie włącz dokowanie, wywołując [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Zadokuj to menu, wywołując [CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCMenuBar` używać różnych metod w klasie. W przykładzie pokazano, jak ustawić styl okienka, włączyć przycisk dostosuj, włączyć pole Pomocy, włączyć cienie dla wyskakujących menu i zaktualizować pasek menu. Ten fragment kodu jest częścią [przykładu IE Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[Cmfctoolbar](../../mfc/reference/cmfctoolbar-class.md)

`CMFCMenuBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmenubar.h

## <a name="cmfcmenubaradjustlocations"></a><a name="adjustlocations"></a>CMFCMenuBar::AdjustLocations

Dostosowuje pozycje elementów menu na pasku menu.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCMenuBar::AllowChangeTextLabels

Określa, czy etykiety tekstowe są dozwolone w obrazach na pasku menu.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli użytkownik może wybrać wyświetlanie etykiet tekstowych pod obrazami.

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCMenuBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCMenuBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

[w] *bStieczka*<br/>

[w] *bHorz ( bHorz )*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarcalclayout"></a><a name="calclayout"></a>CMFCMenuBar::CalcLayout

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>Parametry

[w] *dwMode (tryb)*<br/>

[w] *nLength (nLength)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarcalcmaxbuttonheight"></a><a name="calcmaxbuttonheight"></a>CMFCMenuBar::CalcMaxButtonHeight

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarcanbeclosed"></a><a name="canbeclosed"></a>CMFCMenuBar::CanBeclosed

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarcanberestored"></a><a name="canberestored"></a>CMFCMenuBar::CanBeRestored

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarcreate"></a><a name="create"></a>CMFCMenuBar::Utwórz

Tworzy formant menu i dołącza go do [obiektu CMFCMenuBar.](../../mfc/reference/cmfcmenubar-class.md)

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[w] Wskaźnik do okna nadrzędnego `CMFCMenuBar` dla nowego obiektu.

*Dwstyle*<br/>
[w] Styl nowego paska menu.

*Nid*<br/>
[w] Identyfikator okna podrzędnego paska menu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Po skonstruowaniu `CMFCMenuBar` obiektu należy `Create`wywołać program . Ta metoda `CMFCMenuBar` tworzy formant i `CMFCMenuBar` dołącza go do obiektu.

Aby uzyskać więcej informacji na temat stylów paska narzędzi, zobacz [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).

## <a name="cmfcmenubarcreateex"></a><a name="createex"></a>CMFCMenuBar::CreateEx

Tworzy obiekt [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) z określonymi stylami rozszerzonymi.

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
[w] Wskaźnik do okna nadrzędnego `CMFCMenuBar` nowego obiektu.

*dwCtrlStyle*<br/>
[w] Dodatkowe style dla nowego paska menu.

*Dwstyle*<br/>
[w] Główny styl nowego paska menu.

*rcBorders*<br/>
[w] Parametr `CRect` określający rozmiary obramowań `CMFCMenuBar` obiektu.

*Nid*<br/>
[w] Identyfikator okna podrzędnego paska menu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Tej funkcji należy użyć zamiast [CMFCMenuBar::Create,](#create) jeśli chcesz określić style oprócz stylu paska narzędzi. Niektóre często używane style dodatkowe są TBSTYLE_TRANSPARENT i CBRS_TOP.

Aby uzyskać listę dodatkowych stylów, zobacz [Style formantów i przycisków paska narzędzi,](/windows/win32/Controls/toolbar-control-and-button-styles) [typowe style sterowania](/windows/win32/Controls/common-control-styles)i typowe style [okien](/windows/win32/winmsg/window-styles).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `CreateEx` metody `CMFCMenuBar` klasy. Ten fragment kodu jest częścią [przykładu IE Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

## <a name="cmfcmenubarcreatefrommenu"></a><a name="createfrommenu"></a>CMFCMenuBar::CreateFromMenu

Inicjuje obiekt [CMFCMenuBar.](../../mfc/reference/cmfcmenubar-class.md) Ta metoda `CMFCMenuBar` modeluje obiekt po parametrze HMENU.

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>Parametry

*Hmenu*<br/>
[w] Dojście do zasobu menu. `CreateFromMenu`używa tego zasobu jako `CMFCMenuBar`szablonu dla pliku .

*bDefaultMenu*<br/>
[w] Wartość logiczna wskazująca, czy nowe menu jest menu domyślnym.

*bForceUpdate*<br/>
[w] Wartość logiczna wskazująca, czy ta metoda wymusza aktualizację menu.

### <a name="remarks"></a>Uwagi

Użyj tej metody, jeśli chcesz, aby formant menu miał te same elementy menu co zasób menu. Wywołanie tej metody wywołanie [cmfcmenubar::Tworzenie](#create) lub [CMFCMenuBar::CreateEx](#createex).

## <a name="cmfcmenubarenablehelpcombobox"></a><a name="enablehelpcombobox"></a>CMFCMenuBar::EnableHelpCombobox

Włącza pole kombi **Pomocy,** które znajduje się po prawej stronie paska menu.

```
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>Parametry

*Uiid*<br/>
[w] Identyfikator polecenia dla przycisku pola kombinacja **Pomocy.**

*lpszPrompt*<br/>
[w] Ciąg zawierający tekst wyświetlany przez platformę w polu kombi, jeśli jest pusty i nieaktywny. Na przykład "Wprowadź tekst tutaj".

*nComboBoxWidth*<br/>
[w] Szerokość przycisku pola kombi w pikselach.

### <a name="remarks"></a>Uwagi

Pole kombi **Pomoc** przypomina pole kombi **Pomoc** na pasku menu programu Microsoft Word.

Po wywołaniu tej metody z *uiID* ustawioną na 0 ta metoda ukrywa pole kombi. W przeciwnym razie ta metoda automatycznie wyświetla pole kombi po prawej stronie paska menu. Po wywołaniu tej metody, wywołać [CMFCMenuBar::GetHelpCombobox,](#gethelpcombobox) aby uzyskać wskaźnik do wstawionego [obiektu CMFCToolBarComboBoxButton.](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="cmfcmenubarenablemenushadows"></a><a name="enablemenushadows"></a>CMFCMenuBar::EnableMenuShadows

Włącza cienie do menu podręcznych.

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] Parametr logiczny wskazujący, czy cienie powinny być włączone dla menu podręcznych.

### <a name="remarks"></a>Uwagi

Algorytm, który używa tej metody jest złożony i może zmniejszyć wydajność aplikacji w wolniejszych systemach.

## <a name="cmfcmenubargetavailableexpandsize"></a><a name="getavailableexpandsize"></a>CMFCMenuBar::GetAvailableRozwińRozwińRozwiń

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubargetcolumnwidth"></a><a name="getcolumnwidth"></a>CMFCMenuBar::GetColumnWidth

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubargetdefaultmenu"></a><a name="getdefaultmenu"></a>CMFCMenuBar::GetDefaultMenu

Pobiera dojście do oryginalnego menu. Struktura ładuje oryginalne menu z pliku zasobów.

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do zasobu menu.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja dostosowuje menu, można użyć tej metody, aby pobrać dojście do oryginalnego menu.

## <a name="cmfcmenubargetdefaultmenuresid"></a><a name="getdefaultmenuresid"></a>CMFCMenuBar::GetDefaultMenuResId

Pobiera identyfikator zasobu dla menu domyślnego.

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu menu.

### <a name="remarks"></a>Uwagi

Struktura ładuje domyślne menu `CMFCMenuBar` dla obiektu z pliku zasobów.

## <a name="cmfcmenubargetfloatpopupdirection"></a><a name="getfloatpopupdirection"></a>CMFCMenuBar::GetFloatPopupDirection

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>Parametry

[w] *pButton (przycisk)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubargetforcedownarrows"></a><a name="getforcedownarrows"></a>CMFCMenuBar::GetForceDownArrows

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubargethelpcombobox"></a><a name="gethelpcombobox"></a>CMFCMenuBar::GetHelpCombobox

Zwraca wskaźnik do pola kombi **Pomocy.**

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pola kombi **Pomoc.** NULL, jeśli pole kombi **Pomoc** jest ukryte lub nie włączone.

### <a name="remarks"></a>Uwagi

Pole kombi **Pomoc** znajduje się po prawej stronie paska menu. Wywołanie metody [CMFCMenuBar::EnableHelpCombobox,](#enablehelpcombobox) aby włączyć to pole kombi.

## <a name="cmfcmenubargethmenu"></a><a name="gethmenu"></a>CMFCMenuBar::GetHMenu

Pobiera dojście do menu dołączonego do obiektu [CMFCMenuBar.](../../mfc/reference/cmfcmenubar-class.md)

```
HMENU GetHMenu() const;
```

## <a name="cmfcmenubargetmenufont"></a><a name="getmenufont"></a>CMFCMenuBar::GetMenuFont

Pobiera bieżącą czcionkę menu.

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*Bhorz*<br/>
[w] Parametr logiczny określający, czy czcionka pozioma czy pionowa ma być zwracana. Wartość TRUE wskazuje czcionkę poziomą.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do parametru [CFont](../../mfc/reference/cfont-class.md) zawierający bieżącą czcionkę paska menu.

### <a name="remarks"></a>Uwagi

Zwrócona czcionka jest parametrem globalnym dla aplikacji. Dwie czcionki globalne są `CMFCMenuBar` zachowywane dla wszystkich obiektów. Te oddzielne czcionki są używane dla poziomych i pionowych pasków menu.

## <a name="cmfcmenubargetmenuitem"></a><a name="getmenuitem"></a>CMFCMenuBar::GetMenuItem

Pobiera [OBIEKT CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) na pasku menu na podstawie indeksu elementów.

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>Parametry

*Iitem*<br/>
[w] Indeks elementu menu do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CMFCToolBarButton` obiektu, który pasuje do indeksu określonego przez *iItem*. NULL, jeśli indeks jest nieprawidłowy.

## <a name="cmfcmenubargetrowheight"></a><a name="getrowheight"></a>CMFCMenuBar::GetRowHeight

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubargetsystembutton"></a><a name="getsystembutton"></a>CMFCMenuBar::Przycisk Systemu Get

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>Parametry

[w] *uiBtn*<br/>

[w] *bByCommand*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubargetsystembuttonscount"></a><a name="getsystembuttonscount"></a>CMFCMenuBar::GetSystemButtonsCount

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubargetsystemmenu"></a><a name="getsystemmenu"></a>CMFCMenuBar::GetSystemMenu

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarhighlightdisableditems"></a><a name="highlightdisableditems"></a>CMFCMenuBar::HighlightDisabledItems

Określa, czy struktura wyróżnia wyłączone elementy menu.

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>Parametry

*bWyświetlenie*<br/>
[w] Parametr logiczny wskazujący, czy struktura wyróżnia niedostępne elementy menu.

### <a name="remarks"></a>Uwagi

Domyślnie struktura nie wyróżnia niedostępnych elementów menu, gdy użytkownik umieszcza wskaźnik myszy nad nimi.

## <a name="cmfcmenubarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFCMenuBar::IsButtonExtraSizeDostępne

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarishighlightdisableditems"></a><a name="ishighlightdisableditems"></a>CMFCMenuBar::IsHighlightDisabledItems

Wskazuje, czy struktura wyróżnia niedostępne elementy menu.

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli są wyróżnione niedostępne elementy menu; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Domyślnie struktura nie wyróżnia niedostępnych elementów menu, gdy użytkownik umieszcza wskaźnik myszy nad nimi. Użyj [CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems) metody, aby włączyć tę funkcję.

## <a name="cmfcmenubarismenushadows"></a><a name="ismenushadows"></a>CMFCMenuBar::IsMenuShadows

Wskazuje, czy struktura rysuje cienie dla menu podręcznych.

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli struktura rysuje cienie menu; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj [CMFCMenuBar::EnableMenuShadows](#enablemenushadows) metody, aby włączyć lub wyłączyć tę funkcję.

## <a name="cmfcmenubarisrecentlyusedmenus"></a><a name="isrecentlyusedmenus"></a>CMFCMenuBar::IsRecentlyUsedMenus

Wskazuje, czy ostatnio używane polecenia menu są wyświetlane na pasku menu.

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, `CMFCMenuBar` jeśli obiekt pokazuje ostatnio używane polecenia menu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj funkcji [CMFCMenuBar::SetRecentlyUsedMenus,](#setrecentlyusedmenus) aby kontrolować, czy pasek menu pokazuje ostatnio używane polecenia menu.

## <a name="cmfcmenubarisshowallcommands"></a><a name="isshowallcommands"></a>CMFCMenuBar::IsShowAllCommands

Wskazuje, czy w menu są wyświetlane wszystkie polecenia.

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, `CMFCMenuBar` jeśli wyświetla wszystkie polecenia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Obiekt `CMFCMenuBar` można skonfigurować tak, aby pokazywał wszystkie polecenia lub pokazywał tylko podzbiór poleceń. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [CMFCMenuBar Class](../../mfc/reference/cmfcmenubar-class.md).

`IsShowAllCommands`poinformuje Cię, jak ta funkcja `CMFCMenuBar` jest skonfigurowana dla obiektu. Aby kontrolować, które polecenia menu są wyświetlane, należy użyć metod [CMFCMenuBar::SetShowAllCommands](#setshowallcommands) i [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus).

## <a name="cmfcmenubarisshowallcommandsdelay"></a><a name="isshowallcommandsdelay"></a>CMFCMenuBar::IsShowAllCommandsDelay

Wskazuje, czy obiekt [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) wyświetla wszystkie polecenia po krótkim opóźnieniu.

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli pasek menu wyświetla pełne menu po krótkim opóźnieniu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po skonfigurowaniu paska menu do wyświetlania ostatnio używanych elementów pasek menu wyświetla pełne menu na jeden z dwóch sposobów:

- Wyświetl pełne menu po zaprogramowanym opóźnieniu, od kiedy użytkownik najedzie kursorem na strzałkę u dołu menu.

- Wyświetl pełne menu po kliknięciu przez użytkownika strzałki u dołu menu.

Domyślnie wszystkie `CMFCMenuBar` obiekty używają opcji wyświetlania pełnego menu po krótkim opóźnieniu. Tej opcji nie można zmienić `CMFCMenuBar` programowo w klasie. Użytkownik może jednak zmienić zachowanie podczas dostosowywania paska narzędzi za pomocą okna dialogowego **Dostosowywanie..**

## <a name="cmfcmenubarloadstate"></a><a name="loadstate"></a>CMFCMenuBar::Stan obciążenia

Ładuje stan paska menu z rejestru systemu Windows.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Ciąg zawierający ścieżkę klucza rejestru systemu Windows.

*Nindex*<br/>
[w] Identyfikator formantu paska menu.

*Uiid*<br/>
[w] Wartość zarezerwowana.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj [CMFCMenuBar::SaveState](#savestate) metody, aby zapisać stan paska menu w rejestrze. Zapisane informacje obejmują elementy menu, stan stacji dokującej i położenie paska menu.

W większości przypadków aplikacja `LoadState`nie dzwoni . Struktura wywołuje tę metodę, gdy inicjuje obszar roboczy.

## <a name="cmfcmenubaronchangehot"></a><a name="onchangehot"></a>CMFCMenuBar::OnChangeHot

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>Parametry

[w] *iHot ( iHot )*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarondefaultmenuloaded"></a><a name="ondefaultmenuloaded"></a>CMFCMenuBar::OnDefaultMenuLoaded

Struktura wywołuje tę metodę, gdy ładuje zasób menu z pliku zasobów.

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*Hmenu*<br/>
[w] Uchwyt menu dołączonego do `CMFCMenuBar` obiektu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji nic nie robi. Zastąp tę funkcję, aby wykonać kod niestandardowy po wczytyniu zasób menu z pliku zasobów.

## <a name="cmfcmenubaronsendcommand"></a><a name="onsendcommand"></a>CMFCMenuBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

[w] *pButton (przycisk)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubaronsetdefaultbuttontext"></a><a name="onsetdefaultbuttontext"></a>CMFCMenuBar::OnSetDefaultButtonText

Struktura wywołuje tę metodę, gdy użytkownik zmienia tekst elementu na pasku menu.

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

*pButton (przycisk)*<br/>
[w] Wskaźnik do [obiektu CMFCToolBarButton,](../../mfc/reference/cmfctoolbarbutton-class.md) który użytkownik chce dostosować.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli struktura stosuje zmiany użytkownika na pasku menu; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Domyślna implementacja dla tej metody zmienia tekst przycisku na tekst, który udostępnia użytkownik.

## <a name="cmfcmenubarontoolhittest"></a><a name="ontoolhittest"></a>CMFCMenuBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parametry

[w] *punkt*<br/>

[w] *pTI*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenuBar::PreTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

[w] *pMsg*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarrestoreoriginalstate"></a><a name="restoreoriginalstate"></a>CMFCMenuBar::RestoreOriginalstate

Wywoływane przez strukturę, gdy użytkownik wybiera **Reset** z okna dialogowego **Dostosowywanie.**

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, gdy użytkownik wybierze **Reset** z menu dostosowywania. Można również ręcznie wywołać tę metodę, aby programowo zresetować stan paska menu. Ta metoda ładuje oryginalny stan z pliku zasobu.

Zastąd w tej metodzie należy wykonać dowolną opcję przetwarzania, gdy użytkownik wybierze opcję **Resetuj.**

## <a name="cmfcmenubarsavestate"></a><a name="savestate"></a>CMFCMenuBar::Stan zapisu

Zapisuje stan obiektu [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) w rejestrze systemu Windows.

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Ciąg zawierający ścieżkę klucza rejestru systemu Windows.

*Nindex*<br/>
[w] Identyfikator formantu paska menu.

*Uiid*<br/>
[w] Wartość zarezerwowana.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE;

### <a name="remarks"></a>Uwagi

Zazwyczaj aplikacja nie dzwoni `SaveState`. Struktura wywołuje tę metodę, gdy obszar roboczy jest serializowany. Aby uzyskać więcej informacji, zobacz [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).

Zapisane informacje obejmują elementy menu, stan stacji dokującej i położenie paska menu.

## <a name="cmfcmenubarsetdefaultmenuresid"></a><a name="setdefaultmenuresid"></a>CMFCMenuBar::SetDefaultMenuResId

Ustawia domyślne menu dla obiektu [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) na podstawie identyfikatora zasobu.

```
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>Parametry

*interfejs użytkownika uiResId*<br/>
[w] Identyfikator zasobu dla nowego menu domyślnego.

### <a name="remarks"></a>Uwagi

[Metoda CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate) przywraca domyślne menu z pliku zasobów.

Użyj [CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid) metody, aby pobrać menu domyślne bez przywracania go.

## <a name="cmfcmenubarsetforcedownarrows"></a><a name="setforcedownarrows"></a>CMFCMenuBar::SetForceDownArrows

```
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>Parametry

[w] *bWartość*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubarsetmaximizemode"></a><a name="setmaximizemode"></a>CMFCMenuBar::SetMaximizeMode

Struktura wywołuje tę metodę, gdy MDI zmienia tryb wyświetlania i pasek menu musi zostać zaktualizowany.

```
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>Parametry

*bMax (Niem.*<br/>
[w] Wartość logiczna określająca tryb. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

*Pwnd*<br/>
[w] Wskaźnik do okna podrzędnego MDI, który się zmienia.

*bRecalcLayout*<br/>
[w] Wartość logiczna określająca, czy układ paska menu powinien zostać natychmiast przeliczony ponownie.

### <a name="remarks"></a>Uwagi

Gdy okno podrzędne MDI jest zmaksymalizowane, pasek menu dołączony do okna ramki głównej MDI wyświetla menu systemowe oraz przyciski **Minimalizuj**, **Maksymalizuj** i **Zamknij.** Jeśli *bMax* jest TRUE i *pWnd* nie jest null, okno podrzędne MDI jest zmaksymalizowane i pasek menu musi zawierać dodatkowe formanty. W przeciwnym razie pasek menu powróci do stanu regularnego.

## <a name="cmfcmenubarsetmenubuttonrtc"></a><a name="setmenubuttonrtc"></a>CMFCMenuBar::SetMenuButtonRTC

Ustawia informacje o klasie środowiska wykonawczego, które jest używana przez platformę podczas tworzenia przez użytkownika przycisków menu.

```
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>Parametry

*pMenuButtonRTC*<br/>
[w] Informacje [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) dla klasy pochodzące z [CMFCMenuButton Class](../../mfc/reference/cmfcmenubutton-class.md).

### <a name="remarks"></a>Uwagi

Gdy użytkownik dodaje nowe przyciski do paska menu, struktura tworzy przyciski dynamicznie. Domyślnie tworzy `CMFCMenuButton` obiekty. Zastąp tę metodę, aby zmienić typ obiektów przycisków, które tworzy struktura.

## <a name="cmfcmenubarsetmenufont"></a><a name="setmenufont"></a>CMFCMenuBar::SetMenuFont

Ustawia czcionkę dla wszystkich pasków menu w aplikacji.

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
[w] Wskaźnik do struktury [LOGFONT,](/windows/win32/api/dimm/ns-dimm-logfonta) który definiuje czcionkę do ustawienia.

*Bhorz*<br/>
[w] PRAWDA, jeśli chcesz, aby parametr *lpLogFont* był używany dla czcionki pionowej, FALSE, jeśli chcesz, aby był używany dla czcionki poziomej.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Dwie czcionki są `CMFCMenuBar` używane dla wszystkich obiektów. Te oddzielne czcionki są używane dla poziomych i pionowych pasków menu.

Ustawienia czcionek są zmiennymi `CMFCMenuBar` globalnymi i mają wpływ na wszystkie obiekty.

## <a name="cmfcmenubarsetrecentlyusedmenus"></a><a name="setrecentlyusedmenus"></a>CMFCMenuBar::SetRecentlyUsedMenus

Określa, czy na pasku menu są wyświetlane ostatnio używane polecenia menu.

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parametry

*Bon*<br/>
[w] Wartość logiczna, która określa, czy wyświetlane są ostatnio używane polecenia menu.

## <a name="cmfcmenubarsetshowallcommands"></a><a name="setshowallcommands"></a>CMFCMenuBar::SetShowAllCommands

Określa, czy w menu są wyświetlane wszystkie dostępne polecenia.

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>Parametry

*bShowAllCommands*<br/>
[w] Parametr logiczny określający, czy w menu podręcznym są wyświetlane wszystkie polecenia menu.

### <a name="remarks"></a>Uwagi

Jeśli w menu nie są wyświetlane wszystkie polecenia menu, ukrywa ono rzadko używane polecenia. Aby uzyskać więcej informacji na temat wyświetlania poleceń menu, zobacz [CMFCMenuBar Class](../../mfc/reference/cmfcmenubar-class.md).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
