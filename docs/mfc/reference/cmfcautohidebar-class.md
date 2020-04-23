---
title: Klasa CMFCAutoHideBar
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AddAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AllowShowOnPaneMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CalcFixedLayout
- AFXAUTOHIDEBAR/CMFCAutoHideBar::Create
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetFirstAHWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetVisibleCount
- AFXAUTOHIDEBAR/CMFCAutoHideBar::OnShowControlBarMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::RemoveAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetActiveInGroup
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetRecentVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::ShowAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::StretchPane
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UnSetAutoHideMode
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UpdateVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::m_nShowAHWndDelay
helpviewer_keywords:
- CMFCAutoHideBar [MFC], CMFCAutoHideBar
- CMFCAutoHideBar [MFC], AddAutoHideWindow
- CMFCAutoHideBar [MFC], AllowShowOnPaneMenu
- CMFCAutoHideBar [MFC], CalcFixedLayout
- CMFCAutoHideBar [MFC], Create
- CMFCAutoHideBar [MFC], GetFirstAHWindow
- CMFCAutoHideBar [MFC], GetVisibleCount
- CMFCAutoHideBar [MFC], OnShowControlBarMenu
- CMFCAutoHideBar [MFC], RemoveAutoHideWindow
- CMFCAutoHideBar [MFC], SetActiveInGroup
- CMFCAutoHideBar [MFC], SetRecentVisibleState
- CMFCAutoHideBar [MFC], ShowAutoHideWindow
- CMFCAutoHideBar [MFC], StretchPane
- CMFCAutoHideBar [MFC], UnSetAutoHideMode
- CMFCAutoHideBar [MFC], UpdateVisibleState
- CMFCAutoHideBar [MFC], m_nShowAHWndDelay
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
ms.openlocfilehash: 05f77dfba442f1ce4a375c8f225908799ece1788
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751762"
---
# <a name="cmfcautohidebar-class"></a>Klasa CMFCAutoHideBar

Klasa `CMFCAutoHideBar` jest specjalną klasą paska narzędzi, która implementuje funkcję automatycznego ukrywania.

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCAutoHideBar : public CPane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Przesłania `CPane::AllowShowOnPaneMenu`).|
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|(Zastępuje [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCAutoHideBar::Utwórz](#create)|Tworzy pasek sterowania i dołącza go do [CPane](../../mfc/reference/cpane-class.md) obiektu. (Zastępuje [CPane::Create](../../mfc/reference/cpane-class.md#create).)|
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||
|[CMFCAutoHideBar::GetVisibleCount](#getvisiblecount)||
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|Wywoływana przez strukturę, gdy ma zostać wyświetlone specjalne menu okienka. (Zastępuje [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|(Zastępuje [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).)|
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||
|[CMFCAutoHideBar::RozciągnięciePane](#stretchpane)|Rozciąga okienko w pionie lub poziomie. (Zastępuje [CBasePane::StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane).)|
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|Opóźnienie między momentem, gdy użytkownik umieszcza kursor myszy nad [CMFCAutoHideButton klasy](../../mfc/reference/cmfcautohidebutton-class.md) i moment, gdy struktura pokazuje skojarzone okno.|

## <a name="remarks"></a>Uwagi

Gdy użytkownik przełącza okienko dokowania do trybu automatycznego ukrywania, struktura automatycznie tworzy `CMFCAutoHideBar` obiekt. Tworzy również niezbędne [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) i [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) obiektów. Każdy `CAutoHideDockSite` obiekt jest skojarzony `CMFCAutoHideButton`z osobą .

Klasa `CMFCAutoHideBar` implementuje `CAutoHideDockSite` wyświetlanie, gdy mysz użytkownika najeżdża kursorem myszy na . `CMFCAutoHideButton` Gdy pasek narzędzi odbiera komunikat WM_MOUSEMOVE, `CMFCAutoHideBar` uruchamia czasomierz. Po zakończeniu czasomierza wysyła pasek narzędzi powiadomienie o zdarzeniu WM_TIMER. Pasek narzędzi obsługuje to zdarzenie, sprawdzając, czy wskaźnik myszy jest umieszczony nad tym samym przyciskiem automatycznego ukrywania, nad którym został ustawiony podczas rozpoczynania czasomierza. Jeśli tak jest, `CAutoHideDockSite` zostanie wyświetlony dołączony.

Długość opóźnienia czasomierza można kontrolować, `m_nShowAHWndDelay`ustawiając . Wartość domyślna to 400 ms.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonstruować `CMFCAutoHideBar` obiekt i użyć jego `GetDockSiteRow` metody.

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[Cmfcautohidebar](../../mfc/reference/cmfcautohidebar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxautohidebar.h

## <a name="cmfcautohidebaraddautohidewindow"></a><a name="addautohidewindow"></a>CMFCAutoHideBar::AddAutoHideWindow

Dodaje funkcjonalność do `CDockablePane` okna, które umożliwia automatyczne ukrywanie.

```
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

*pAutoHideWnd*<br/>
[w] Okno, które chcesz ukryć.

*dwZładna*<br/>
[w] Wartość określająca wyrównanie przycisku automatycznego ukrywania z oknem aplikacji.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Parametr *dwAlignment wskazuje,* gdzie znajduje się przycisk automatycznego ukrywania w aplikacji. Parametr może być jedną z następujących wartości:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCAutoHideBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCAutoHideBar::CalcFixedLayout

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

## <a name="cmfcautohidebarcmfcautohidebar"></a><a name="cmfcautohidebar"></a>CMFCAutoHideBar::CMFCAutoHideBar

Konstruuje OBIEKT CMFCAutoHideBar.

```
CMFCAutoHideBar();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebarcreate"></a><a name="create"></a>CMFCAutoHideBar::Utwórz

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*lpszClassName (nazwa klasy)*<br/>

*Dwstyle*<br/>

*Rect*<br/>

*pParentWnd*<br/>

*Nid*<br/>

*styl dwControlBarStyle*<br/>

*Pcontext*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebargetfirstahwindow"></a><a name="getfirstahwindow"></a>CMFCAutoHideBar::GetFirstAHWindow

Zwraca wskaźnik do pierwszego okna automatycznego ukrywania w aplikacji.

```
CDockablePane* GetFirstAHWindow();
```

### <a name="return-value"></a>Wartość zwracana

Pierwsze okno automatycznego ukrywania w aplikacji lub NULL, jeśli go nie ma.

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebargetvisiblecount"></a><a name="getvisiblecount"></a>CMFCAutoHideBar::GetVisibleCount

Pobiera liczbę widocznych przycisków automatycznego ukrywania.

```
int GetVisibleCount();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę widocznych przycisków automatycznego ukrywania.

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebarm_nshowahwnddelay"></a><a name="m_nshowahwnddelay"></a>CMFCAutoHideBar::m_nShowAHWndDelay

Opóźnienie między momentem, gdy użytkownik umieszcza kursor myszy nad [CMFCAutoHideButton klasy](../../mfc/reference/cmfcautohidebutton-class.md) i moment, gdy struktura pokazuje skojarzone okno.

```
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik umieszcza kursor myszy `CMFCAutoHideButton`nad , istnieje niewielkie opóźnienie, zanim struktura wyświetla skojarzone okno. Ten parametr określa długość tego opóźnienia w milisekundach.

## <a name="cmfcautohidebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFCAutoHideBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Parametry

[w] *CPoint (punkt CPoint)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebarremoveautohidewindow"></a><a name="removeautohidewindow"></a>CMFCAutoHideBar::RemoveAutoHideWindow

Usuwa i niszczy okno automatycznego ukrywania.

```
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```

### <a name="parameters"></a>Parametry

CDockablePane* *pAutoHideWnd* Automatyczne ukrywanie okna do usunięcia.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebarsetactiveingroup"></a><a name="setactiveingroup"></a>CMFCAutoHideBar::SetActiveInGroup

Oznacza automatyczne ukrywanie paska jako aktywny.

```
virtual void SetActiveInGroup(BOOL bActive);
```

### <a name="parameters"></a>Parametry

[w] BOOL *bAktywny prawda,* aby ustawić aktywny; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Zobacz [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).

## <a name="cmfcautohidebarsetrecentvisiblestate"></a><a name="setrecentvisiblestate"></a>CMFCAutoHideBar::SetRecentVisibleState

```cpp
void SetRecentVisibleState(BOOL bState);
```

### <a name="parameters"></a>Parametry

*bPaństwo*<br/>
[w] Stan do ustawionego.

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebarshowautohidewindow"></a><a name="showautohidewindow"></a>CMFCAutoHideBar::ShowAutoHideWindow

Pokazuje okno automatycznego ukrywania.

```
BOOL ShowAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parametry

*pAutoHideWnd*<br/>
[w] Okno do wyświetlenia.

*bPokaż*<br/>
[w] PRAWDA, aby wyświetlić okno.

*bDelay (własówce)*<br/>
[w] Ten parametr jest ignorowany.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebarstretchpane"></a><a name="stretchpane"></a>CMFCAutoHideBar::RozciągnięciePane

Rozmiar paska automatycznego ukrywania w stanie zwiniętym `CMFCAutoHideButton` powoduje dopasowanie do obiektu.

```
virtual CSize StretchPane(
    int nLength,
    BOOL bVert);
```

### <a name="parameters"></a>Parametry

*nLength (nLength)*<br/>
[w] Wartość jest nieużywane w implementacji podstawowej. W implementacjach pochodnych użyj tej wartości, aby wskazać długość okienka o przesiąkniętym omiń.

*bWert*<br/>
[w] Wartość jest nieużywane w implementacji podstawowej. W implementacjach pochodnych użyj funkcji TRUE do obsługi przypadku, w którym pasek automatycznego ukrywania jest zwinięty pionowo, i FALSE w przypadku, gdy pasek automatycznego ukrywania jest zwinięty poziomo.

### <a name="return-value"></a>Wartość zwracana

Wynikowy rozmiar okienka o rozmiarze.

### <a name="remarks"></a>Uwagi

Klasy pochodne można zastąpić tę metodę, aby dostosować zachowanie.

## <a name="cmfcautohidebarunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFCAutoHideBar::UnSetAutoHideMode

Wyłącza tryb automatycznego ukrywania dla grupy pasków automatycznego ukrywania.

```cpp
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)
```

### <a name="parameters"></a>Parametry

[in] wskaźnik pFirstBarInGroup A do pierwszego paska automatycznego ukrywania w grupie.

### <a name="remarks"></a>Uwagi

## <a name="cmfcautohidebarupdatevisiblestate"></a><a name="updatevisiblestate"></a>CMFCAutoHideBar::UpdateVisibleState

Wywoływana przez strukturę, gdy pasek automatycznego ukrywania musi zostać ponownie narysowany.

```cpp
void UpdateVisibleState();
```

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CPane](../../mfc/reference/cpane-class.md)<br/>
[Klasa CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)<br/>
[Klasa CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)
