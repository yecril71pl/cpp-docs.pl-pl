---
title: Klasa CGlobalUtils
ms.date: 10/18/2018
f1_keywords:
- CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils::AdjustRectToWorkArea
- AFXGLOBALUTILS/CGlobalUtils::CalcExpectedDockedRect
- AFXGLOBALUTILS/CGlobalUtils::CanBeAttached
- AFXGLOBALUTILS/CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd
- AFXGLOBALUTILS/CGlobalUtils::CheckAlignment
- AFXGLOBALUTILS/CGlobalUtils::CyFromString
- AFXGLOBALUTILS/CGlobalUtils::DecimalFromString
- AFXGLOBALUTILS/CGlobalUtils::FlipRect
- AFXGLOBALUTILS/CGlobalUtils::ForceAdjustLayout
- AFXGLOBALUTILS/CGlobalUtils::GetDockingManager
- AFXGLOBALUTILS/CGlobalUtils::GetOppositeAlignment
- AFXGLOBALUTILS/CGlobalUtils::GetPaneAndAlignFromPoint
- AFXGLOBALUTILS/CGlobalUtils::GetWndIcon
- AFXGLOBALUTILS/CGlobalUtils::SetNewParent
- AFXGLOBALUTILS/CGlobalUtils::StringFromCy
- AFXGLOBALUTILS/CGlobalUtils::StringFromDecimal
helpviewer_keywords:
- CGlobalUtils [MFC], AdjustRectToWorkArea
- CGlobalUtils [MFC], CalcExpectedDockedRect
- CGlobalUtils [MFC], CanBeAttached
- CGlobalUtils [MFC], CanPaneBeInFloatingMultiPaneFrameWnd
- CGlobalUtils [MFC], CheckAlignment
- CGlobalUtils [MFC], CyFromString
- CGlobalUtils [MFC], DecimalFromString
- CGlobalUtils [MFC], FlipRect
- CGlobalUtils [MFC], ForceAdjustLayout
- CGlobalUtils [MFC], GetDockingManager
- CGlobalUtils [MFC], GetOppositeAlignment
- CGlobalUtils [MFC], GetPaneAndAlignFromPoint
- CGlobalUtils [MFC], GetWndIcon
- CGlobalUtils [MFC], SetNewParent
- CGlobalUtils [MFC], StringFromCy
- CGlobalUtils [MFC], StringFromDecimal
ms.assetid: 2c5bd1a6-f80c-4e79-a476-b4ceebabfb2f
ms.openlocfilehash: 66c1663774076fcc4b62b766b1781efc8cc33c93
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373720"
---
# <a name="cglobalutils-class"></a>Klasa CGlobalUtils

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CGlobalUtils
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGlobalUtils::AdjustRectToWorkArea](#adjustrecttoworkarea)||
|[CGlobalUtils::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CGlobalUtils::CanBeAttached](#canbeattached)||
|[CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd](#canpanebeinfloatingmultipaneframewnd)||
|[CGlobalUtils::CheckAlignment](#checkalignment)||
|[CGlobalUtils::CyFromString](#cyfromstring)||
|[CGlobalUtils::DecimalFromString](#decimalfromstring)||
|[CGlobalUtils::FlipRect](#fliprect)||
|[CGlobalUtils::ForceAdjustLayout](#forceadjustlayout)||
|[CGlobalUtils::GetDockingManager](#getdockingmanager)||
|[CGlobalUtils::GetOppositeAlignment](#getoppositealignment)||
|[CGlobalUtils::GetPaneAndAlignFromPoint](#getpaneandalignfrompoint)||
|[CGlobalUtils::GetWndIcon](#getwndicon)||
|[CGlobalUtils::SetNewParent](#setnewparent)||
|[CGlobalUtils::StringFromCy](#stringfromcy)||
|[CGlobalUtils::StringFromDecimal](#stringfromdecimal)||

## <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CGlobalUtils](../../mfc/reference/cglobalutils-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxglobalutils.h

## <a name="cglobalutilsadjustrecttoworkarea"></a><a name="adjustrecttoworkarea"></a>CGlobalUtils::AdjustRectToWorkArea

```
void AdjustRectToworkArea(
    CRect& rect,
    CRect* pRectDelta = NULL);
```

### <a name="parameters"></a>Parametry

[w, na zewnątrz] *rect*<br/>
[w] *pRectDelta*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilscalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CGlobalUtils::CalcExpectedDockedRect

```
void CalcExpectedDockedRect(
    CPaneContainerManager& barContainerManager,
    CWnd* pWndTodock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Parametry

[w] *barContainerManager*<br/>

[w] *pWndTodock (Doł.*<br/>

[w] *ptMouse (polski)*<br/>

[na zewnątrz] *reectResult*<br/>

[na zewnątrz] *bNaładka*<br/>

[na zewnątrz] *ppTargetBar (Pasek celetu)*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilscanbeattached"></a><a name="canbeattached"></a>CGlobalUtils::CanBeAttached

```
BOOL CanBeAttached(CWnd* pWnd) const;
```

### <a name="parameters"></a>Parametry

[w] *pWnd (właśc.*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilscanpanebeinfloatingmultipaneframewnd"></a><a name="canpanebeinfloatingmultipaneframewnd"></a>CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd

```
BOOL CanPaneBeInFloatingMultiPaneFrameWnd(CWnd* pWnd) const;
```

### <a name="parameters"></a>Parametry

[w] *pWnd (właśc.*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilscheckalignment"></a><a name="checkalignment"></a>CGlobalUtils::CheckAlignment

```
BOOL CheckAlignment(
    CPoint point,
    CBasePane* pBar,
    int nSensitivity,
    const CDockingManager* pDockManager,
    BOOL bOuterEdge,
    DWORD& dwAlignment,
    DWORD dwEnabledDockBars = CBRS_ALIGN_ANY,
    LPCRECT lpRectBounds = NULL) const;
```

### <a name="parameters"></a>Parametry

[w] *punkt*<br/>

[w] *pBar*<br/>

[w] *nWrażliwość*<br/>

[w] *pDockManager*<br/>

[w] *bOuterEdge (Niem.*<br/>

[na zewnątrz] *dwZładna*<br/>

[w] *dwEnabledDockBars*<br/>

[w] *lpRectBounds (lpRectBounds)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilscyfromstring"></a><a name="cyfromstring"></a>CGlobalUtils::CyFromString

```
BOOL CyFromString(
    CY& cy,
    LPCTSTR psz);
```

### <a name="parameters"></a>Parametry

[na zewnątrz] *cy*<br/>

[w] *psz*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilsdecimalfromstring"></a><a name="decimalfromstring"></a>CGlobalUtils::DecimalFromString

```
BOOL DecimalFromString(
    DECIMAL& decimal,
    LPCTSTR psz);
```

### <a name="parameters"></a>Parametry

[na zewnątrz] *dziesiętne*<br/>

[w] *psz*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilsfliprect"></a><a name="fliprect"></a>CGlobalUtils::FlipRect

```
void FlipRect(
    CRect& rect,
    int nDegrees);
```

### <a name="parameters"></a>Parametry

[w, na zewnątrz] *rect*<br/>
[w] *nNiesztego*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilsforceadjustlayout"></a><a name="forceadjustlayout"></a>CGlobalUtils::ForceAdjustLayout

```
void ForceAdjustLayout(
    CDockingManager* pDockManager,
    BOOL bForce = FALSE,
    BOOL bForceInvisible = FALSE);
```

### <a name="parameters"></a>Parametry

[w, na zewnątrz] *pDockManager*<br/>

[w] *bEchętna*<br/>

[w] *bNiewistynalne*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilsgetdockingmanager"></a><a name="getdockingmanager"></a>CGlobalUtils::GetDockingManager

```
CDockingManager* GetDockingManager(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

[w] *pWnd (właśc.*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilsgetoppositealignment"></a><a name="getoppositealignment"></a>CGlobalUtils::GetOppositeAlignment

```
DWORD GetOppositeAlignment(DWORD dwAlign);
```

### <a name="parameters"></a>Parametry

[w] *dwAlign*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilsgetpaneandalignfrompoint"></a><a name="getpaneandalignfrompoint"></a>CGlobalUtils::GetPaneAndAlignFromPoint

```
BOOL GetPaneAndAlignFromPoint(
    CPaneContainerManager& barContainerManager,
    CPoint pt,
    CDockablePane** ppTargetControlBar,
    DWORD& dwAlignment,
    BOOL& bTabArea,
    BOOL& bCaption);
```

### <a name="parameters"></a>Parametry

[w] *barContainerManager*<br/>

[w] *pt.*<br/>

[na zewnątrz] *p.o.*<br/>

[na zewnątrz] *dwZładna*<br/>

[na zewnątrz] *bObaszary*<br/>

[na zewnątrz] *bCaption (Rozwiązanie)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilsgetwndicon"></a><a name="getwndicon"></a>CGlobalUtils::GetWndIcon

```
HICON GetWndIcon(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

[w] *pWnd (właśc.*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilssetnewparent"></a><a name="setnewparent"></a>CGlobalUtils::SetNewParent

```
void SetNewParent(
    CObList& lstControlBars,
    CWnd* pNewParent,
    BOOL bCheckVisibility = TRUE);
```

### <a name="parameters"></a>Parametry

[w] *lstControlBars (Kierownice)*<br/>

[w] *pNowodawc*<br/>

[w] *bCzycielność*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilsstringfromcy"></a><a name="stringfromcy"></a>CGlobalUtils::StringFromCy

```
BOOL StringFromCy(
    CString& str,
    CY& cy);
```

### <a name="parameters"></a>Parametry

[na zewnątrz] *ul.*<br/>

[w] *cy*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cglobalutilsstringfromdecimal"></a><a name="stringfromdecimal"></a>CGlobalUtils::StringFromDecimal

```
BOOL StringFromDecimal(
    CString& str,
    DECIMAL& decimal);
```

### <a name="parameters"></a>Parametry

[na zewnątrz] *ul.*<br/>

[w] *dziesiętne*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
