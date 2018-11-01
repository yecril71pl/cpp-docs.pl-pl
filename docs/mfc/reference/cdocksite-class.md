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
ms.openlocfilehash: 08acf9e47a26d4cbc5bcb96cbff086b19768e972
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486310"
---
# <a name="cdocksite-class"></a>Klasa CDockSite

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

Oferuje funkcję rozmieszczania okienek, które są uzyskiwane z [klasa CPane](../../mfc/reference/cpane-class.md) do zestawów wierszy.

## <a name="syntax"></a>Składnia

```
class CDockSite: public CBasePane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDockSite::AddRow](#addrow)||
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|(Przesłania [CBasePane::AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout).)|
|[CDockSite::AdjustLayout](#adjustlayout)|(Przesłania [CBasePane::AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout).)|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(Przesłania [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CDockSite::CanAcceptPane](#canacceptpane)|(Przesłania [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane).)|
|[CDockSite::CreateEx](#createex)|(Przesłania [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|(Przesłania [CBasePane::DockPane](../../mfc/reference/cbasepane-class.md#dockpane).)|
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Przesłania [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite::GetDockSiteID](#getdocksiteid)||
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|(Przesłania `CBasePane::IsAccessibilityCompatible`).|
|[CDockSite::IsDragMode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::IsResizable](#isresizable)|(Przesłania [CBasePane::IsResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|
|[CDockSite::MovePane](#movepane)||
|[CDockSite::OnInsertRow](#oninsertrow)||
|[CDockSite::OnRemoveRow](#onremoverow)||
|[CDockSite::OnResizeRow](#onresizerow)||
|[CDockSite::OnSetWindowPos](#onsetwindowpos)||
|[CDockSite::OnShowRow](#onshowrow)||
|[CDockSite::OnSizeParent](#onsizeparent)||
|[CDockSite::PaneFromPoint](#panefrompoint)|Zwraca okienko, w którym jest zadokowany w witrynie Zadokuj w punkcie określonym przez danego parametru.|
|[CDockSite::DockPaneLeftOf](#dockpaneleftof)|Stacje dokujące okienko po lewej stronie okienka innego.|
|[CDockSite::FindPaneByID](#findpanebyid)|Zwraca okienko w którym jest identyfikowane za pomocą podanym identyfikatorze.|
|[CDockSite::GetPaneList](#getpanelist)|Zwraca listę okienek, które są zadokowane w witrynie dokowania.|
|[CDockSite::RectSideFromPoint](#rectsidefrompoint)||
|[CDockSite::RemovePane](#removepane)||
|[CDockSite::RemoveRow](#removerow)||
|[CDockSite::ReplacePane](#replacepane)||
|[CDockSite::RepositionPanes](#repositionpanes)||
|[CDockSite::ResizeDockSite](#resizedocksite)||
|[CDockSite::ResizeRow](#resizerow)||
|[CDockSite::ShowPane](#showpane)|Pokazuje okienka.|
|[CDockSite::ShowRow](#showrow)||
|[CDockSite::SwapRows](#swaprows)||

## <a name="remarks"></a>Uwagi

Szablon tworzy `CDockSite` obiekty automatycznie po wywołaniu [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Zadokuj witryny windows są umieszczone na krawędzi obszaru klienckiego okna ramki głównej.

Zazwyczaj nie trzeba wywołać usługi świadczone przez witryny dokowania, ponieważ [klasa CFrameWndEx](../../mfc/reference/cframewndex-class.md) obsługi tych usług.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób tworzenia obiektu `CDockSite` klasy.

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md) [CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxDockSite.h

##  <a name="addrow"></a>  CDockSite::AddRow

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>Parametry

[in] *punktu sprzedaży*<br/>

[in] *nHeight*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="adjustdockinglayout"></a>  CDockSite::AdjustDockingLayout

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>Uwagi

##  <a name="adjustlayout"></a>  CDockSite::AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>Uwagi

##  <a name="aligndocksite"></a>  CDockSite::AlignDockSite

```
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>Parametry

[in] *rectToAlignBy*<br/>

[in] *rectResult*<br/>

[in] *bMoveImmediately*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="calcfixedlayout"></a>  CDockSite::CalcFixedLayout

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

##  <a name="canacceptpane"></a>  CDockSite::CanAcceptPane

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parametry

[in] *pBar*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="createex"></a>  CDockSite::CreateEx

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

[in] *dwStyleEx*<br/>

[in] *dwStyle*<br/>

[in] *rect*<br/>

[in] *pParentWnd*<br/>

[in] *dwControlBarStyle*<br/>

[in] *pContext*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="createrow"></a>  CDockSite::CreateRow

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>Parametry

[in] *pParentDockBar*<br/>

[in] *nOffset*<br/>

[in] *nRowHeight*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="dockpane"></a>  CDockSite::DockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

[in] *pWnd*<br/>

[in] *dockMethod*<br/>

[in] *lprect —*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="dockpaneleftof"></a>  CDockSite::DockPaneLeftOf

Stacje dokujące okienko po lewej stronie okienka innego.

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Parametry

*pBarToDock*<br/>
[out w] Wskaźnik do okienka, aby być zadokowane po lewej stronie *pTargetBar*.

*pTargetBar*<br/>
[out w] Wskaźnik do okienka docelowego.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli panel jest zadokowany pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="doesallowdyninsertbefore"></a>  CDockSite::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="findpanebyid"></a>  CDockSite::FindPaneByID

Zwraca okienko o podanym identyfikatorze.

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
[in] Identyfikator polecenia okienka ma zostać odnaleziona.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okienka z polecenie o określonym identyfikatorze lub o wartości NULL, jeśli nie zostanie znaleziony okienka.

### <a name="remarks"></a>Uwagi

##  <a name="findrowindex"></a>  CDockSite::FindRowIndex

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parametry

[in] *pRow*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="fixupvirtualrects"></a>  CDockSite::FixupVirtualRects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Uwagi

##  <a name="getdocksiteid"></a>  CDockSite::GetDockSiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getdocksiterowslist"></a>  CDockSite::GetDockSiteRowsList

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpanelist"></a>  CDockSite::GetPaneList

Zwraca listę okienek, które są zadokowane w witrynie dokowania.

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołania tylko do odczytu do listy okienka obecnie zadokowane, na pasku dokowania.

##  <a name="isaccessibilitycompatible"></a>  CDockSite::IsAccessibilityCompatible

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isdragmode"></a>  CDockSite::IsDragMode

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="islastrow"></a>  CDockSite::IsLastRow

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>Parametry

[in] *pRow*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isrectwithindocksite"></a>  CDockSite::IsRectWithinDockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>Parametry

[in] *rect*<br/>

[in] *ptDelta*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isresizable"></a>  CDockSite::IsResizable

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="movepane"></a>  CDockSite::MovePane

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>Parametry

[in] *pWnd*<br/>

[in] *nFlags*<br/>

[in] *ptOffset*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="oninsertrow"></a>  CDockSite::OnInsertRow

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>Parametry

[in] *punktu sprzedaży*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onremoverow"></a>  CDockSite::OnRemoveRow

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>Parametry

[in] *punktu sprzedaży*<br/>

[in] *bByShow*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onresizerow"></a>  CDockSite::OnResizeRow

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>Parametry

[in] *pRowToResize*<br/>

[in] *nOffset*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="onsizeparent"></a>  CDockSite::OnSizeParent

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>Parametry

[in] *rectAvailable*<br/>

[in] *nSide*<br/>

[in] *bExpand*<br/>

[in] *nOffset*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onsetwindowpos"></a>  CDockSite::OnSetWindowPos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

[in] *pWndInsertAfter*<br/>

[in] *rectWnd*<br/>

[in] *nFlags*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="onshowrow"></a>  CDockSite::OnShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

[in] *punktu sprzedaży*<br/>

[in] *bShow*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="panefrompoint"></a>  CDockSite::PaneFromPoint

Zwraca okienko, w którym jest zadokowany w witrynie Zadokuj w punkcie określonym przez danego parametru.

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>Parametry

*(czas pacyficzny)*<br/>
[in] Punkt, w układzie współrzędnych ekranu, dla tego okienka do pobrania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okienka znajdujący się w określonym lub wartość NULL, jeśli okienko nie była obecna w określonym momencie.

### <a name="remarks"></a>Uwagi

##  <a name="rectsidefrompoint"></a>  CDockSite::RectSideFromPoint

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>Parametry

[in] *rect*<br/>

[in] *punktu*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="removepane"></a>  CDockSite::RemovePane

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Parametry

[in] *pWnd*<br/>

[in] *dockMethod*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="removerow"></a>  CDockSite::RemoveRow

```
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parametry

[in] *pRow*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="replacepane"></a>  CDockSite::ReplacePane

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>Parametry

[in] *pOldBar*<br/>

[in] *pNewBar*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="repositionpanes"></a>  CDockSite::RepositionPanes

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parametry

[in] *rectNewClientArea*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="resizedocksite"></a>  CDockSite::ResizeDockSite

```
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>Parametry

[in] *nNewWidth*<br/>

[in] *nNewHeight*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="resizerow"></a>  CDockSite::ResizeRow

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Parametry

[in] *pRow*<br/>

[in] *nNewSize*<br/>

[in] *bAdjustLayout*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="showpane"></a>  CDockSite::ShowPane

Pokazuje okienka.

```
virtual BOOL ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[out w] Wskaźnik do okienka, które mają być wyświetlane lub ukryte.

*bShow*<br/>
[in] Wartość TRUE, aby określić, że okienka ma być wyświetlana; Wartość FALSE, aby określić, to okienko zostanie ukryte.

*bDelay*<br/>
[in] Wartość TRUE, aby określić, że układ okienka powinno zostać opóźnione do po okienku są wyświetlane; w przeciwnym razie wartość FALSE.

*bActivate*<br/>
[in] Ten parametr nie jest używany.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli okienko zostało pokazane lub ukryte pomyślnie. Wartość FALSE, jeśli określony okienko nie należy do tej witryny dokowania.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pokazać lub ukryć zadokowanego okienka. Zwykle nie trzeba wywoływać `CDockSite::ShowPane` bezpośrednio, ponieważ jest ona wywoływana przez nadrzędnej ramki okna lub okienku podstawowej.

##  <a name="showrow"></a>  CDockSite::ShowRow

```
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>Parametry

[in] *pRow*<br/>

[in] *bShow*<br/>

[in] *bAdjustLayout*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="swaprows"></a>  CDockSite::SwapRows

```
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>Parametry

[in] *pFirstRow*<br/>

[in] *pSecondRow*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CBasePane](../../mfc/reference/cbasepane-class.md)
