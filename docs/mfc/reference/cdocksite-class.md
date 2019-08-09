---
title: Klasa CDockSite
ms.date: 10/18/2018
f1_keywords:
- CDockSite
- AFXDOCKSITE/CDockSite
- AFXDOCKSITE/CDockSite::AddRow
- AFXDOCKSITE/CDockSite::AdjustDockingLayout
- AFXDOCKSITE/CDockSite::AdjustLayout
- AFXDOCKSITE/CDockSite::AlignDockSite
- AFXDOCKSITE/CDockSite::CalcFixedLayout
- AFXDOCKSITE/CDockSite::CanAcceptPane
- AFXDOCKSITE/CDockSite::CreateEx
- AFXDOCKSITE/CDockSite::CreateRow
- AFXDOCKSITE/CDockSite::DockPane
- AFXDOCKSITE/CDockSite::DoesAllowDynInsertBefore
- AFXDOCKSITE/CDockSite::FindRowIndex
- AFXDOCKSITE/CDockSite::FixupVirtualRects
- AFXDOCKSITE/CDockSite::GetDockSiteID
- AFXDOCKSITE/CDockSite::GetDockSiteRowsList
- AFXDOCKSITE/CDockSite::IsAccessibilityCompatible
- AFXDOCKSITE/CDockSite::IsDragMode
- AFXDOCKSITE/CDockSite::IsLastRow
- AFXDOCKSITE/CDockSite::IsRectWithinDockSite
- AFXDOCKSITE/CDockSite::IsResizable
- AFXDOCKSITE/CDockSite::MovePane
- AFXDOCKSITE/CDockSite::OnInsertRow
- AFXDOCKSITE/CDockSite::OnRemoveRow
- AFXDOCKSITE/CDockSite::OnResizeRow
- AFXDOCKSITE/CDockSite::OnSetWindowPos
- AFXDOCKSITE/CDockSite::OnShowRow
- AFXDOCKSITE/CDockSite::OnSizeParent
- AFXDOCKSITE/CDockSite::PaneFromPoint
- AFXDOCKSITE/CDockSite::DockPaneLeftOf
- AFXDOCKSITE/CDockSite::FindPaneByID
- AFXDOCKSITE/CDockSite::GetPaneList
- AFXDOCKSITE/CDockSite::RectSideFromPoint
- AFXDOCKSITE/CDockSite::RemovePane
- AFXDOCKSITE/CDockSite::RemoveRow
- AFXDOCKSITE/CDockSite::ReplacePane
- AFXDOCKSITE/CDockSite::RepositionPanes
- AFXDOCKSITE/CDockSite::ResizeDockSite
- AFXDOCKSITE/CDockSite::ResizeRow
- AFXDOCKSITE/CDockSite::ShowPane
- AFXDOCKSITE/CDockSite::ShowRow
- AFXDOCKSITE/CDockSite::SwapRows
helpviewer_keywords:
- CDockSite [MFC], AddRow
- CDockSite [MFC], AdjustDockingLayout
- CDockSite [MFC], AdjustLayout
- CDockSite [MFC], AlignDockSite
- CDockSite [MFC], CalcFixedLayout
- CDockSite [MFC], CanAcceptPane
- CDockSite [MFC], CreateEx
- CDockSite [MFC], CreateRow
- CDockSite [MFC], DockPane
- CDockSite [MFC], DoesAllowDynInsertBefore
- CDockSite [MFC], FindRowIndex
- CDockSite [MFC], FixupVirtualRects
- CDockSite [MFC], GetDockSiteID
- CDockSite [MFC], GetDockSiteRowsList
- CDockSite [MFC], IsAccessibilityCompatible
- CDockSite [MFC], IsDragMode
- CDockSite [MFC], IsLastRow
- CDockSite [MFC], IsRectWithinDockSite
- CDockSite [MFC], IsResizable
- CDockSite [MFC], MovePane
- CDockSite [MFC], OnInsertRow
- CDockSite [MFC], OnRemoveRow
- CDockSite [MFC], OnResizeRow
- CDockSite [MFC], OnSetWindowPos
- CDockSite [MFC], OnShowRow
- CDockSite [MFC], OnSizeParent
- CDockSite [MFC], PaneFromPoint
- CDockSite [MFC], DockPaneLeftOf
- CDockSite [MFC], FindPaneByID
- CDockSite [MFC], GetPaneList
- CDockSite [MFC], RectSideFromPoint
- CDockSite [MFC], RemovePane
- CDockSite [MFC], RemoveRow
- CDockSite [MFC], ReplacePane
- CDockSite [MFC], RepositionPanes
- CDockSite [MFC], ResizeDockSite
- CDockSite [MFC], ResizeRow
- CDockSite [MFC], ShowPane
- CDockSite [MFC], ShowRow
- CDockSite [MFC], SwapRows
ms.assetid: 0fcfff79-5f50-4281-b2de-a55653bbea40
ms.openlocfilehash: 9c154fe621fb88a6dc96a9835fae95c4b86763de
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866193"
---
# <a name="cdocksite-class"></a>Klasa CDockSite

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

Oferuje funkcje rozmieszczania okienek, które pochodzą z [klasy CPane](../../mfc/reference/cpane-class.md) do zestawów wierszy.

## <a name="syntax"></a>Składnia

```
class CDockSite: public CBasePane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDockSite::AddRow](#addrow)||
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|(Przesłania [CBasePane:: AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout).)|
|[CDockSite::AdjustLayout](#adjustlayout)|(Przesłania [CBasePane:: AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout).)|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(Przesłania [CBasePane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CDockSite::CanAcceptPane](#canacceptpane)|(Przesłania [CBasePane:: CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane).)|
|[CDockSite::CreateEx](#createex)|(Przesłania [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|(Przesłania [CBasePane::D ockpane](../../mfc/reference/cbasepane-class.md#dockpane).)|
|[CDockSite::D oesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Przesłania [CBasePane::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite::GetDockSiteID](#getdocksiteid)||
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|(Przesłania `CBasePane::IsAccessibilityCompatible`).|
|[CDockSite:: isprzeciągnijmode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::IsResizable](#isresizable)|(Przesłania [CBasePane:: IsResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|
|[CDockSite::MovePane](#movepane)||
|[CDockSite::OnInsertRow](#oninsertrow)||
|[CDockSite::OnRemoveRow](#onremoverow)||
|[CDockSite::OnResizeRow](#onresizerow)||
|[CDockSite::OnSetWindowPos](#onsetwindowpos)||
|[CDockSite::OnShowRow](#onshowrow)||
|[CDockSite::OnSizeParent](#onsizeparent)||
|[CDockSite::P aneFromPoint](#panefrompoint)|Zwraca okienko, które jest zadokowane w lokacji Dock w punkcie określonym przez dany parametr.|
|[CDockSite::DockPaneLeftOf](#dockpaneleftof)|Dokowanie okienka z lewej strony w innym okienku.|
|[CDockSite::FindPaneByID](#findpanebyid)|Zwraca okienko identyfikowane przez podany identyfikator.|
|[CDockSite:: getpanelname](#getpanelist)|Zwraca listę okienek, które są zadokowane w lokacji Dock.|
|[CDockSite::RectSideFromPoint](#rectsidefrompoint)||
|[CDockSite::RemovePane](#removepane)||
|[CDockSite::RemoveRow](#removerow)||
|[CDockSite::ReplacePane](#replacepane)||
|[CDockSite::RepositionPanes](#repositionpanes)||
|[CDockSite::ResizeDockSite](#resizedocksite)||
|[CDockSite::ResizeRow](#resizerow)||
|[CDockSite::ShowPane](#showpane)|Wyświetla okienko.|
|[CDockSite::ShowRow](#showrow)||
|[CDockSite::SwapRows](#swaprows)||

## <a name="remarks"></a>Uwagi

Struktura tworzy `CDockSite` obiekty automatycznie po wywołaniu [CFrameWndEx:: EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Okna lokacji dokowania są umieszczane na krawędzi obszaru klienta w oknie ramka główna.

Zazwyczaj nie trzeba wywoływać usług dostarczonych przez lokację Dock, ponieważ [Klasa CFrameWndEx](../../mfc/reference/cframewndex-class.md) obsługuje te usługi.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób tworzenia obiektu `CDockSite` klasy.

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxDockSite. h

##  <a name="addrow"></a>CDockSite::AddRow

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>Parametry

podczas *punkt sprzedaży*<br/>

podczas *nHeight*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="adjustdockinglayout"></a>CDockSite::AdjustDockingLayout

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>Uwagi

##  <a name="adjustlayout"></a>CDockSite::AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>Uwagi

##  <a name="aligndocksite"></a>CDockSite::AlignDockSite

```
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>Parametry

podczas *rectToAlignBy*<br/>

podczas *rectResult*<br/>

podczas *bMoveImmediately*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="calcfixedlayout"></a>CDockSite::CalcFixedLayout

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

##  <a name="canacceptpane"></a>CDockSite::CanAcceptPane

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parametry

podczas *pBar*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="createex"></a>CDockSite::CreateEx

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    DWORD dwControlBarStyle,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

podczas *dwStyleEx*<br/>

podczas *dwStyle*<br/>

podczas *prostokąt*<br/>

podczas *pParentWnd*<br/>

podczas *dwControlBarStyle*<br/>

podczas *pContext*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="createrow"></a>CDockSite::CreateRow

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>Parametry

podczas *pParentDockBar*<br/>

podczas *nOffset*<br/>

podczas *nRowHeight*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="dockpane"></a>CDockSite::D ockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

podczas *pWnd*<br/>

podczas *dockMethod*<br/>

podczas *lpRect*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="dockpaneleftof"></a>  CDockSite::DockPaneLeftOf

Dokowanie okienka z lewej strony w innym okienku.

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Parametry

*pBarToDock*<br/>
[in. out] Wskaźnik do okienka, które ma zostać zadokowane po lewej stronie *pTargetBar*.

*pTargetBar*<br/>
[in. out] Wskaźnik do okienka Target.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli okienko zostało pomyślnie zadokowane; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="doesallowdyninsertbefore"></a>CDockSite::D oesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="findpanebyid"></a>CDockSite::FindPaneByID

Zwraca okienko o podanym IDENTYFIKATORze.

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
podczas Identyfikator polecenia okienka, które ma zostać odnalezione.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okienka z określonym IDENTYFIKATORem polecenia lub wartość NULL, jeśli nie można odnaleźć okienka.

### <a name="remarks"></a>Uwagi

##  <a name="findrowindex"></a>CDockSite::FindRowIndex

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parametry

podczas *PROW*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="fixupvirtualrects"></a>CDockSite::FixupVirtualRects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Uwagi

##  <a name="getdocksiteid"></a>CDockSite::GetDockSiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getdocksiterowslist"></a>CDockSite::GetDockSiteRowsList

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpanelist"></a>CDockSite:: getpanelname

Zwraca listę okienek, które są zadokowane w witrynie Docker.

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie tylko do odczytu do listy okienek, które są obecnie zadokowane na pasku dokowania.

##  <a name="isaccessibilitycompatible"></a>CDockSite::IsAccessibilityCompatible

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isdragmode"></a>CDockSite:: isprzeciągnijmode

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="islastrow"></a>CDockSite::IsLastRow

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>Parametry

podczas *PROW*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isrectwithindocksite"></a>CDockSite::IsRectWithinDockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>Parametry

podczas *prostokąt*<br/>

podczas *ptDelta*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isresizable"></a>CDockSite::IsResizable

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="movepane"></a>CDockSite::MovePane

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>Parametry

podczas *pWnd*<br/>

podczas *nFlags*<br/>

podczas *ptOffset*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="oninsertrow"></a>CDockSite::OnInsertRow

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>Parametry

podczas *punkt sprzedaży*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onremoverow"></a>CDockSite::OnRemoveRow

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>Parametry

podczas *punkt sprzedaży*<br/>

podczas *bByShow*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onresizerow"></a>CDockSite::OnResizeRow

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>Parametry

podczas *pRowToResize*<br/>

podczas *nOffset*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="onsizeparent"></a>CDockSite::OnSizeParent

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>Parametry

podczas *rectAvailable*<br/>

podczas *nSide*<br/>

podczas *bExpand*<br/>

podczas *nOffset*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onsetwindowpos"></a>CDockSite::OnSetWindowPos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

podczas *pWndInsertAfter*<br/>

podczas *rectWnd*<br/>

podczas *nFlags*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="onshowrow"></a>CDockSite::OnShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

podczas *punkt sprzedaży*<br/>

podczas *bShow*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="panefrompoint"></a>CDockSite::P aneFromPoint

Zwraca okienko, które jest zadokowane w lokacji Dock w punkcie określonym przez dany parametr.

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>Parametry

*zmiennoprzecinkow*<br/>
podczas Punkt w współrzędnej ekranu dla okienka do pobrania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okienka znajdującego się w określonym punkcie lub wartości NULL, jeśli w określonym punkcie nie było żadnego okienka.

### <a name="remarks"></a>Uwagi

##  <a name="rectsidefrompoint"></a>CDockSite::RectSideFromPoint

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>Parametry

podczas *prostokąt*<br/>

podczas *punkt*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="removepane"></a>CDockSite::RemovePane

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Parametry

podczas *pWnd*<br/>

podczas *dockMethod*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="removerow"></a>CDockSite::RemoveRow

```
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parametry

podczas *PROW*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="replacepane"></a>CDockSite::ReplacePane

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>Parametry

podczas *pOldBar*<br/>

podczas *pNewBar*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="repositionpanes"></a>CDockSite::RepositionPanes

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parametry

podczas *rectNewClientArea*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="resizedocksite"></a>CDockSite::ResizeDockSite

```
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>Parametry

podczas *nNewWidth*<br/>

podczas *nNewHeight*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="resizerow"></a>CDockSite::ResizeRow

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Parametry

podczas *PROW*<br/>

podczas *nNewSize*<br/>

podczas *bAdjustLayout*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="showpane"></a>CDockSite::ShowPane

Wyświetla okienko.

```
virtual BOOL ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in. out] Wskaźnik do okienka, który ma być wyświetlany lub ukryty.

*bShow*<br/>
podczas Wartość TRUE, aby określić, że okienko ma być wyświetlane; Wartość FALSE, aby określić, że okienko ma być ukryte.

*bDelay*<br/>
podczas Wartość TRUE, aby określić, że układ okienka powinien zostać opóźniony do momentu wyświetlenia okienka; w przeciwnym razie FALSE.

*bActivate*<br/>
podczas Ten parametr nie jest używany.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli okienko zostało pokazane lub ukryte pomyślnie. Wartość FALSE, jeśli określone okienko nie należy do tej witryny dockowej.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pokazać lub ukryć okienka zadokowane. Zwykle nie jest konieczne bezpośrednie wywoływanie `CDockSite::ShowPane` , ponieważ jest on wywoływany przez okno nadrzędnej ramki lub w okienku podstawowym.

##  <a name="showrow"></a>CDockSite::ShowRow

```
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>Parametry

podczas *PROW*<br/>

podczas *bShow*<br/>

podczas *bAdjustLayout*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="swaprows"></a>CDockSite::SwapRows

```
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>Parametry

podczas *pFirstRow*<br/>

podczas *pSecondRow*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CBasePane](../../mfc/reference/cbasepane-class.md)
