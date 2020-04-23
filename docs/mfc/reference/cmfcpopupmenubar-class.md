---
title: Klasa CMFCPopupMenuBar
ms.date: 11/04/2016
f1_keywords:
- CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::AdjustSizeImmediate
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::BuildOrigItems
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::CloseDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ExportToMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::FindDestintationToolBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetCurrentMenuImageSize
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetDefaultMenuId
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetLastCommandIndex
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ImportFromMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsDropDownListMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsPaletteMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanel
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanelInRegularMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::LoadFromHash
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::RestoreDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetButtonStyle
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::StartPopupMenuTimer
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::m_bDisableSideBarInXPMode
helpviewer_keywords:
- CMFCPopupMenuBar [MFC], AdjustSizeImmediate
- CMFCPopupMenuBar [MFC], BuildOrigItems
- CMFCPopupMenuBar [MFC], CloseDelayedSubMenu
- CMFCPopupMenuBar [MFC], ExportToMenu
- CMFCPopupMenuBar [MFC], FindDestintationToolBar
- CMFCPopupMenuBar [MFC], GetCurrentMenuImageSize
- CMFCPopupMenuBar [MFC], GetDefaultMenuId
- CMFCPopupMenuBar [MFC], GetLastCommandIndex
- CMFCPopupMenuBar [MFC], GetOffset
- CMFCPopupMenuBar [MFC], ImportFromMenu
- CMFCPopupMenuBar [MFC], IsDropDownListMode
- CMFCPopupMenuBar [MFC], IsPaletteMode
- CMFCPopupMenuBar [MFC], IsRibbonPanel
- CMFCPopupMenuBar [MFC], IsRibbonPanelInRegularMode
- CMFCPopupMenuBar [MFC], LoadFromHash
- CMFCPopupMenuBar [MFC], RestoreDelayedSubMenu
- CMFCPopupMenuBar [MFC], SetButtonStyle
- CMFCPopupMenuBar [MFC], SetOffset
- CMFCPopupMenuBar [MFC], StartPopupMenuTimer
- CMFCPopupMenuBar [MFC], m_bDisableSideBarInXPMode
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
ms.openlocfilehash: c0ba90246d19e8dd07c856eec6a518a8513ee665
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751924"
---
# <a name="cmfcpopupmenubar-class"></a>Klasa CMFCPopupMenuBar

Pasek menu osadzony w wyskakującym menu.

## <a name="syntax"></a>Składnia

```
class CMFCPopupMenuBar : public CMFCToolBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPopupMenuBar::DostosowanoSizeImmediate](#adjustsizeimmediate)|Natychmiast ponownie oblicza układ okienka. (Zastępuje [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).)|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|Ładuje elementy menu podręcznego z określonego zasobu menu.|
|[CMFCPopupMenuBar::ZamknijDelayedSubMenu](#closedelayedsubmenu)|Zamyka przycisk menu opóźnionego okna podręcznego.|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|Tworzy menu z przycisków menu podręcznego.|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|Lokalizuje pasek narzędzi, na którym znajduje się określony punkt.|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|Wskazuje rozmiar obrazów przycisków menu.|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|Zwraca identyfikator domyślnego elementu menu.|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|Pobiera indeks ostatnio wywoływane polecenie menu.|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|Pobiera przesunięcie wiersza paska menu podręcznego.|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|Importuje przyciski menu podręcznego z określonego menu.|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|Wskazuje, czy pasek menu podręcznego znajduje się w trybie listy rozwijanej.|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|Wskazuje, czy pasek menu podręcznego jest w trybie palety.|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|Wskazuje, czy jest to panel wstążki (FALSE domyślnie).|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|Wskazuje, czy jest to panel wstążki w trybie regularnym (FALSE domyślnie).|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|Ładuje zarchiwizowane menu.|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|Przywraca przycisk opóźnionego menu w celu zamknięcia paska menu podręcznego.|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|Ustawia styl przycisku paska narzędzi w danym indeksie. (Zastępuje [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|Ustawia przesunięcie wiersza paska menu podręcznego.|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|Uruchamia czasomierz dla określonego przycisku menu podręcznego z opóźnieniem.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|Określa, czy szary pasek boczny będzie wyświetlany, gdy aplikacja ma wygląd systemu Windows XP.|

## <a name="remarks"></a>Uwagi

Jest `CMFCPopupMenuBar` tworzony w tym samym czasie co [CMFCPopupMenu klasy](../../mfc/reference/cmfcpopupmenu-class.md) i osadzone wewnątrz niego. Obejmuje `CMFCPopupMenuBar` cały obszar klienta `CMFCPopupMenu` obiektu. Obsługuje klawiaturę i mysz. Komunikuje również, że `CMFCPopupMenu` dane wejściowe do i do okna klatki najwyższego poziomu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, `CMFCPopupMenuBar` jak `CMFCPopupMenu` zainicjować obiekt z obiektu. Ten fragment kodu jest częścią [próbki Klienta rysowania](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[Cmfctoolbar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpopupmenubar.h

## <a name="cmfcpopupmenubaradjustsizeimmediate"></a><a name="adjustsizeimmediate"></a>CMFCPopupMenuBar::DostosowanoSizeImmediate

Natychmiast ponownie oblicza układ okienka paska menu podręcznego. (Zastępuje [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>Parametry

*bRecalcLayout*<br/>
[w] PRAWDA, aby automatycznie ponownie obliczyć układ okienka paska menu podręcznego; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubarbuildorigitems"></a><a name="buildorigitems"></a>CMFCPopupMenuBar::BuildOrigItems

Ładuje elementy menu podręcznego z określonego zasobu menu.

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>Parametry

*interfejs użytkownika uiMenuResID*<br/>
[w] Określa identyfikator menu zasobu menu do załadowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli się powiedzie lub FAŁSZ, jeśli nie.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubarclosedelayedsubmenu"></a><a name="closedelayedsubmenu"></a>CMFCPopupMenuBar::ZamknijDelayedSubMenu

Zamyka przycisk menu podręcznego, który został opóźniony.

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubarexporttomenu"></a><a name="exporttomenu"></a>CMFCPopupMenuBar::ExportToMenu

Tworzy menu z przycisków menu podręcznego.

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do nowego menu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubarfinddestintationtoolbar"></a><a name="finddestintationtoolbar"></a>CMFCPopupMenuBar::FindDestintationToolBar

Lokalizuje pasek narzędzi, na którym znajduje się określony punkt.

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
[w] Punkt na ekranie.

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do paska narzędzi, na którym znajduje się punkt, jeśli istnieje, lub NULL, jeśli nie.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubargetcurrentmenuimagesize"></a><a name="getcurrentmenuimagesize"></a>CMFCPopupMenuBar::GetCurrentMenuImageSize

Wskazuje rozmiar obrazów przycisków menu.

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar obrazów przycisków menu na pasku narzędzi.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubargetdefaultmenuid"></a><a name="getdefaultmenuid"></a>CMFCPopupMenuBar::GetDefaultMenuId

Zwraca identyfikator domyślnego elementu menu.

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca identyfikator domyślnego elementu menu na pasku menu podręcznym.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubargetlastcommandindex"></a><a name="getlastcommandindex"></a>CMFCPopupMenuBar::GetLastCommandIndex

Pobiera indeks ostatnio wywoływane polecenie menu.

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca indeks ostatniego polecenia menu, które zostało wywołane.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubargetoffset"></a><a name="getoffset"></a>CMFCPopupMenuBar::GetOffset

Pobiera przesunięcie wiersza paska menu podręcznego.

```
int GetOffset() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca przesunięcie wiersza paska menu podręcznego.

### <a name="remarks"></a>Uwagi

Ta wartość jest ustawiana przy użyciu [polecenia CMFCPopupMenuBar::SetOffset](#setoffset).

## <a name="cmfcpopupmenubarimportfrommenu"></a><a name="importfrommenu"></a>CMFCPopupMenuBar::ImportFromMenu

Importuje przyciski menu podręcznego z określonego menu.

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>Parametry

*Hmenu*<br/>
[w] Menu, z którego mają być importowane przyciski menu podręcznego.

*bShowAllCommands*<br/>
[w] PRAWDA, jeśli wszystkie polecenia w menu mają zostać zaimportowane, lub FALSE, jeśli rzadko używane mogą być ukryte.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli przyciski menu zostały pomyślnie zaimportowane z menu, lub WARTOŚĆ FAŁSZ, jeśli nie.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubarisdropdownlistmode"></a><a name="isdropdownlistmode"></a>CMFCPopupMenuBar::IsDropDownListMode

Wskazuje, czy pasek menu podręcznego znajduje się w trybie listy rozwijanej.

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pasek menu podręcznego jest w trybie listy rozwijanej, lub FALSE, jeśli nie.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubarispalettemode"></a><a name="ispalettemode"></a>CMFCPopupMenuBar::IsPaletteMode

Wskazuje, czy pasek menu podręcznego jest w trybie palety.

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli włączony jest tryb palety, lub wartość FAŁsz, jeśli nie.

### <a name="remarks"></a>Uwagi

Gdy pasek menu jest ustawiony na tryb palety, elementy menu są wyświetlane w wielu kolumnach i ograniczonej liczbie wierszy.

## <a name="cmfcpopupmenubarisribbonpanel"></a><a name="isribbonpanel"></a>CMFCPopupMenuBar::IsRibbonPanel

Wskazuje, czy jest to panel wstążki (FALSE domyślnie).

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślnie zwraca wartość FAŁSZ, wskazując, że nie jest to panel wstążki.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubarisribbonpanelinregularmode"></a><a name="isribbonpanelinregularmode"></a>CMFCPopupMenuBar::IsRibbonPanelInRegularMode

Wskazuje, czy jest to panel wstążki w trybie regularnym (FALSE domyślnie).

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślnie zwraca wartość FAŁSZ, wskazując, że nie jest to panel wstążki w trybie regularnym.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubarloadfromhash"></a><a name="loadfromhash"></a>CMFCPopupMenuBar::LoadFromHash

Ładuje zarchiwizowane menu.

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*Hmenu*<br/>
[w] Uchwyt do zarchiwizowanego menu, aby załadować.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli menu jest pomyślnie załadowane, lub FAŁSZ, jeśli nie.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubarm_bdisablesidebarinxpmode"></a><a name="m_bdisablesidebarinxpmode"></a>CMFCPopupMenuBar::m_bDisableSideBarInXPMode

Parametr logiczny wskazujący, czy aplikacja ma szary pasek boczny, gdy ma wygląd systemu Windows XP.

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>Uwagi

Jeśli ta zmienna elementu członkowskiego jest ustawiona na FAŁSZ, a aplikacja ma wygląd systemu Windows XP, struktura rysuje szary pasek boczny w aplikacji.

Wartością domyślną jest FAŁSZ.

## <a name="cmfcpopupmenubarrestoredelayedsubmenu"></a><a name="restoredelayedsubmenu"></a>CMFCPopupMenuBar::RestoreDelayedSubMenu

Przywraca przycisk opóźnionego menu w celu zamknięcia paska menu podręcznego.

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CMFCPopupMenuBar::SetButtonStyle

Ustawia styl przycisku paska narzędzi w danym indeksie. (Zastępuje [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
[w] Indeks od zera przycisku paska narzędzi, którego styl ma być ustawiony.

*styl nStyle*<br/>
[w] Styl przycisku. Zobacz [Style sterowania paskiem narzędzi,](../../mfc/reference/toolbar-control-styles.md) aby uzyskać listę dostępnych stylów przycisków paska narzędzi.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubarsetoffset"></a><a name="setoffset"></a>CMFCPopupMenuBar::SetOffset

Ustawia przesunięcie wiersza paska menu podręcznego.

```cpp
void SetOffset(int iOffset);
```

### <a name="parameters"></a>Parametry

*Zestaw iOffset*<br/>
[w] Liczba wierszy, które pasek menu podręcznego powinny być przesunięte.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpopupmenubarstartpopupmenutimer"></a><a name="startpopupmenutimer"></a>CMFCPopupMenuBar::StartPopupMenuTimer

Uruchamia czasomierz dla określonego przycisku menu podręcznego z opóźnieniem.

```cpp
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>Parametry

*pMenuButton (Przycisk pMenuButton)*<br/>
[w] Wskaźnik do przycisku menu, dla którego można ustawić czasomierz opóźnienia.

*nDelayFactor*<br/>
[w] Współczynnik opóźnienia, równy co najmniej jednemu, aby pomnożyć przez standardowy czas opóźnienia menu (zazwyczaj od pół sekundy do pięciu sekund).

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)<br/>
[Klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)
