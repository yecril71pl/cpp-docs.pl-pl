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
ms.openlocfilehash: a95ee024d9df835102eeffc8443ae6225775aff7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375536"
---
# <a name="cdocksite-class"></a>Klasa CDockSite

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

Udostępnia funkcje organizowania okienek, które są pochodną [klasy CPane](../../mfc/reference/cpane-class.md) w zestawy wierszy.

## <a name="syntax"></a>Składnia

```
class CDockSite: public CBasePane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDockSite::AddRow](#addrow)||
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|(Zastępuje [CBasePane::AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout).)|
|[CDockSite::AdjustLayout](#adjustlayout)|(Zastępuje [CBasePane::AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout).)|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(Zastępuje [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CDockSite::CanAcceptPane](#canacceptpane)|(Zastępuje [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane).)|
|[CDockSite::CreateEx](#createex)|(Zastępuje [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|(Zastępuje [CBasePane::DockPane](../../mfc/reference/cbasepane-class.md#dockpane).)|
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Zastępuje [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite::GetDockSiteID](#getdocksiteid)||
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite::IsAccesCompatible](#isaccessibilitycompatible)|(Przesłania `CBasePane::IsAccessibilityCompatible`).|
|[CDockSite::IsDragMode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsrectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::IsResizable](#isresizable)|(Zastępuje [CBasePane::IsResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|
|[CDockWitta::MovePane](#movepane)||
|[CDockSite::OnInsertRow](#oninsertrow)||
|[CDockSite::OnRemoveRow](#onremoverow)||
|[CDockSite::OnResizeRow](#onresizerow)||
|[CDockWitła::OnSetWindowPos](#onsetwindowpos)||
|[CDockSite::OnShowRow](#onshowrow)||
|[CDockSite::OnSizeParent](#onsizeparent)||
|[CDockSite::PaneFromPoint](#panefrompoint)|Zwraca okienko zadokowane w miejscu dokunia w punkcie określonym przez dany parametr.|
|[CDockWitasz::DockPaneLeftOf](#dockpaneleftof)|Dokuje okienko po lewej stronie innego okienka.|
|[CDockWitta::FindPaneByID](#findpanebyid)|Zwraca okienko, które jest identyfikowane przez podany identyfikator.|
|[CDockSite::GetPaneList](#getpanelist)|Zwraca listę okienek, które są zadokowane w miejscu doku.|
|[CDockSite::RectSideFromPoint](#rectsidefrompoint)||
|[CDockSite::RemovePane](#removepane)||
|[CDockWitta::RemoveRow](#removerow)||
|[CDockSite::ReplacePane](#replacepane)||
|[CDockWitta::RepozycjaPanes](#repositionpanes)||
|[CDockSite::ResizeDockSite](#resizedocksite)||
|[CDockSite::ResizeRow](#resizerow)||
|[CDockWitasite::ShowPane](#showpane)|Pokazuje okienko.|
|[CDockWitta::ShowRow](#showrow)||
|[CDockSite::SwapRows](#swaprows)||

## <a name="remarks"></a>Uwagi

Struktura tworzy `CDockSite` obiekty automatycznie po wywołaniu [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Okna witryny stacji dokującej są umieszczone na krawędzi obszaru klienta w oknie ramki głównej.

Zazwyczaj nie trzeba wywoływać usług świadczonych przez lokację dokowania, ponieważ [klasa CFrameWndEx](../../mfc/reference/cframewndex-class.md) obsługuje te usługi.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CDockSite` utworzyć obiekt klasy.

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)\
&nbsp;-[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[CdockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxDockSite.h

## <a name="cdocksiteaddrow"></a><a name="addrow"></a>CDockSite::AddRow

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>Parametry

[w] *poz*<br/>

[w] *nFeksja*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteadjustdockinglayout"></a><a name="adjustdockinglayout"></a>CDockSite::AdjustDockingLayout

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteadjustlayout"></a><a name="adjustlayout"></a>CDockSite::AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>Uwagi

## <a name="cdocksitealigndocksite"></a><a name="aligndocksite"></a>CDockSite::AlignDockSite

```
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>Parametry

[w] *rectToAlignBy*<br/>

[w] *reectResult*<br/>

[w] *bZjęciemnie*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cdocksitecalcfixedlayout"></a><a name="calcfixedlayout"></a>CDockSite::CalcFixedLayout

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

## <a name="cdocksitecanacceptpane"></a><a name="canacceptpane"></a>CDockSite::CanAcceptPane

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parametry

[w] *pBar*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksitecreateex"></a><a name="createex"></a>CDockSite::CreateEx

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

[w] *dwStyleEx (np.*<br/>

[w] *dwStyle (właśc.*<br/>

[w] *rect*<br/>

[w] *pParentWnd*<br/>

[w] *styl dwControlBarStyle*<br/>

[w] *pContext (Tekst)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksitecreaterow"></a><a name="createrow"></a>CDockSite::CreateRow

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>Parametry

[w] *pParentDockBar*<br/>

[w] *nStawa*<br/>

[w] *nRowHeight ( nRowHeight )*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksitedockpane"></a><a name="dockpane"></a>CDockSite::DockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

[w] *pWnd (właśc.*<br/>

[w] *dokMetoda*<br/>

[w] *lpRect*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cdocksitedockpaneleftof"></a><a name="dockpaneleftof"></a>CDockWitasz::DockPaneLeftOf

Dokuje okienko po lewej stronie innego okienka.

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Parametry

*pBarToDock (właskw.*<br/>
[w, na zewnątrz] Wskaźnik do okienka, które ma być zadokowany po lewej stronie *pTargetBar*.

*pTargetBar*<br/>
[w, na zewnątrz] Wskaźnik do okienka docelowego.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okienko jest zadokowane pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cdocksitedoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CDockSite::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksitefindpanebyid"></a><a name="findpanebyid"></a>CDockWitta::FindPaneByID

Zwraca okienko z podanym identyfikatorem.

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[w] Identyfikator polecenia okienka, które należy znaleźć.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okienka o określonym identyfikatorze polecenia lub NULL, jeśli nie zostanie znalezione okienko.

### <a name="remarks"></a>Uwagi

## <a name="cdocksitefindrowindex"></a><a name="findrowindex"></a>CDockSite::FindRowIndex

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parametry

[w] *pRow (pRow)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksitefixupvirtualrects"></a><a name="fixupvirtualrects"></a>CDockSite::FixupVirtualRects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Uwagi

## <a name="cdocksitegetdocksiteid"></a><a name="getdocksiteid"></a>CDockSite::GetDockSiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksitegetdocksiterowslist"></a><a name="getdocksiterowslist"></a>CDockSite::GetDockSiteRowsList

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksitegetpanelist"></a><a name="getpanelist"></a>CDockSite::GetPaneList

Zwraca listę okienek, które są zadokowane w lokacji dokującej.

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie tylko do odczytu do listy okienek aktualnie zadokowanych na pasku dokowania.

## <a name="cdocksiteisaccessibilitycompatible"></a><a name="isaccessibilitycompatible"></a>CDockSite::IsAccesCompatible

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteisdragmode"></a><a name="isdragmode"></a>CDockSite::IsDragMode

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteislastrow"></a><a name="islastrow"></a>CDockSite::IsLastRow

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>Parametry

[w] *pRow (pRow)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteisrectwithindocksite"></a><a name="isrectwithindocksite"></a>CDockSite::IsrectWithinDockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>Parametry

[w] *rect*<br/>

[w] *ptDelta ( ptDelta )*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteisresizable"></a><a name="isresizable"></a>CDockSite::IsResizable

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksitemovepane"></a><a name="movepane"></a>CDockWitta::MovePane

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>Parametry

[w] *pWnd (właśc.*<br/>

[w] *nPłgi*<br/>

[w] *ptOffset (polski)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteoninsertrow"></a><a name="oninsertrow"></a>CDockSite::OnInsertRow

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>Parametry

[w] *poz*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteonremoverow"></a><a name="onremoverow"></a>CDockSite::OnRemoveRow

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>Parametry

[w] *poz*<br/>

[w] *bPokaż*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteonresizerow"></a><a name="onresizerow"></a>CDockSite::OnResizeRow

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>Parametry

[w] *pRowToResize*<br/>

[w] *nStawa*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteonsizeparent"></a><a name="onsizeparent"></a>CDockSite::OnSizeParent

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>Parametry

[w] *naprawaDostępne*<br/>

[w] *nSide*<br/>

[w] *bRozwiń*<br/>

[w] *nStawa*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteonsetwindowpos"></a><a name="onsetwindowpos"></a>CDockWitła::OnSetWindowPos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

[w] *pWndInsertPo*<br/>

[w] *reectWnd*<br/>

[w] *nPłgi*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteonshowrow"></a><a name="onshowrow"></a>CDockSite::OnShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

[w] *poz*<br/>

[w] *bPokaż*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cdocksitepanefrompoint"></a><a name="panefrompoint"></a>CDockSite::PaneFromPoint

Zwraca okienko zadokowane w miejscu dokunia w punkcie określonym przez dany parametr.

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[w] Punkt we współrzędnych ekranu, do pobrania okienka.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okienka znajdującego się w określonym punkcie lub null, jeśli w określonym punkcie nie było okienka.

### <a name="remarks"></a>Uwagi

## <a name="cdocksiterectsidefrompoint"></a><a name="rectsidefrompoint"></a>CDockSite::RectSideFromPoint

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>Parametry

[w] *rect*<br/>

[w] *punkt*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteremovepane"></a><a name="removepane"></a>CDockSite::RemovePane

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Parametry

[w] *pWnd (właśc.*<br/>

[w] *dokMetoda*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteremoverow"></a><a name="removerow"></a>CDockWitta::RemoveRow

```
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parametry

[w] *pRow (pRow)*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cdocksitereplacepane"></a><a name="replacepane"></a>CDockSite::ReplacePane

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>Parametry

[w] *pOldBar (POldBar)*<br/>

[w] *pNowyBar*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksiterepositionpanes"></a><a name="repositionpanes"></a>CDockWitta::RepozycjaPanes

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parametry

[w] *reectNewClientArea*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteresizedocksite"></a><a name="resizedocksite"></a>CDockSite::ResizeDockSite

```
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>Parametry

[w] *nNowyWidth*<br/>

[w] *nNewHeight (Jeślifchowanie)*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteresizerow"></a><a name="resizerow"></a>CDockSite::ResizeRow

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Parametry

[w] *pRow (pRow)*<br/>

[w] *nNowy Rozmiar*<br/>

[w] *bAdjustLayout*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteshowpane"></a><a name="showpane"></a>CDockWitasite::ShowPane

Pokazuje okienko.

```
virtual BOOL ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[w, na zewnątrz] Wskaźnik do okienka, które ma być wyświetlane lub ukryte.

*bPokaż*<br/>
[w] PRAWDA, aby określić, że okienko ma być wyświetlane; FAŁSZ, aby określić, że okienko ma być ukryte.

*bDelay (własówce)*<br/>
[w] PRAWDA, aby określić, że układ okienka powinien być opóźniony, dopóki po wyświetleniu okienka; w przeciwnym razie FALSE.

*bAktywowanie*<br/>
[w] Ten parametr nie jest używany.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okienko zostało pokazane lub ukryte pomyślnie. FAŁSZ, jeśli określone okienko nie należy do tej lokacji dokowania.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pokazać lub ukryć zadokowane okienka. Zwykle nie trzeba wywoływać `CDockSite::ShowPane` bezpośrednio, ponieważ jest wywoływana przez okno ramki nadrzędnej lub przez okienko podstawowe.

## <a name="cdocksiteshowrow"></a><a name="showrow"></a>CDockWitta::ShowRow

```
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>Parametry

[w] *pRow (pRow)*<br/>

[w] *bPokaż*<br/>

[w] *bAdjustLayout*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cdocksiteswaprows"></a><a name="swaprows"></a>CDockSite::SwapRows

```
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>Parametry

[w] *pFirstRow (wład)*<br/>

[w] *pSecondRow*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CBasePane](../../mfc/reference/cbasepane-class.md)
