---
title: CMFCVisualManagerVS2005 Class
ms.date: 11/04/2016
f1_keywords:
- CMFCVisualManagerVS2005
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetDockingTabsBordersSize
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetMDITabsBordersSize
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetPropertyGridGroupColor
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetTabFrameColors
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawCaptionButton
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawPaneCaption
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawSeparator
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawTab
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawToolBoxFrame
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnEraseTabsArea
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillHighlightedArea
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillMiniFrameCaption
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnUpdateSystemColors
helpviewer_keywords:
- CMFCVisualManagerVS2005 [MFC], GetDockingTabsBordersSize
- CMFCVisualManagerVS2005 [MFC], GetMDITabsBordersSize
- CMFCVisualManagerVS2005 [MFC], GetPropertyGridGroupColor
- CMFCVisualManagerVS2005 [MFC], GetTabFrameColors
- CMFCVisualManagerVS2005 [MFC], HasOverlappedAutoHideButtons
- CMFCVisualManagerVS2005 [MFC], OnDrawAutoHideButtonBorder
- CMFCVisualManagerVS2005 [MFC], OnDrawCaptionButton
- CMFCVisualManagerVS2005 [MFC], OnDrawPaneCaption
- CMFCVisualManagerVS2005 [MFC], OnDrawSeparator
- CMFCVisualManagerVS2005 [MFC], OnDrawTab
- CMFCVisualManagerVS2005 [MFC], OnDrawToolBoxFrame
- CMFCVisualManagerVS2005 [MFC], OnEraseTabsArea
- CMFCVisualManagerVS2005 [MFC], OnFillAutoHideButtonBackground
- CMFCVisualManagerVS2005 [MFC], OnFillHighlightedArea
- CMFCVisualManagerVS2005 [MFC], OnFillMiniFrameCaption
- CMFCVisualManagerVS2005 [MFC], OnUpdateSystemColors
ms.assetid: ea39b9ae-327e-4a51-bce7-dc84c78f005b
ms.openlocfilehash: 4d1ef0c9087e876f3e8f43430b58fc80f3923ba6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773466"
---
# <a name="cmfcvisualmanagervs2005-class"></a>CMFCVisualManagerVS2005 Class

`CMFCVisualManagerVS2005` Nadaje aplikacji wygląd programu Microsoft Visual Studio 2005.

## <a name="syntax"></a>Składnia

```
class CMFCVisualManagerVS2005 : public CMFCVisualManagerOffice2003
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCVisualManagerVS2005::GetDockingTabsBordersSize](#getdockingtabsborderssize)|Struktura wywołuje tę metodę, gdy jej rysuje okienka w którym jest zadokowany i na kartach. (Przesłania [CMFCVisualManager::GetDockingTabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getdockingtabsborderssize).)|
|[CMFCVisualManagerVS2005::GetMDITabsBordersSize](#getmditabsborderssize)|Struktura wywołuje tę metodę, aby określić rozmiar obramowania okna MDITabs, przed jego rysuje okna. (Przesłania [CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize).)|
|[CMFCVisualManagerVS2005::GetPropertyGridGroupColor](#getpropertygridgroupcolor)|(Przesłania [CMFCVisualManagerOffice2003::GetPropertyGridGroupColor](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#getpropertygridgroupcolor).)|
|[CMFCVisualManagerVS2005::GetTabFrameColors](#gettabframecolors)|(Przesłania [CMFCVisualManagerOffice2003::GetTabFrameColors](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#gettabframecolors).)|
|[CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons](#hasoverlappedautohidebuttons)|Zwraca, czy automatyczne ukrywanie przyciski nakładają się w bieżącym menedżerem visual. (Przesłania [CMFCVisualManager::HasOverlappedAutoHideButtons](../../mfc/reference/cmfcvisualmanager-class.md#hasoverlappedautohidebuttons).)|
|[CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder](#ondrawautohidebuttonborder)|(Przesłania [CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawautohidebuttonborder).)|
|[CMFCVisualManagerVS2005::OnDrawCaptionButton](#ondrawcaptionbutton)|(Przesłania `CMFCVisualManagerOfficeXP::OnDrawCaptionButton`).|
|[CMFCVisualManagerVS2005::OnDrawPaneCaption](#ondrawpanecaption)|(Przesłania [CMFCVisualManagerOffice2003::OnDrawPaneCaption](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawpanecaption).)|
|[CMFCVisualManagerVS2005::OnDrawSeparator](#ondrawseparator)|(Przesłania [CMFCVisualManagerOffice2003::OnDrawSeparator](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawseparator).)|
|[CMFCVisualManagerVS2005::OnDrawTab](#ondrawtab)|(Przesłania [CMFCVisualManagerOffice2003::OnDrawTab](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawtab).)|
|[CMFCVisualManagerVS2005::OnDrawToolBoxFrame](#ondrawtoolboxframe)|(Przesłania [CMFCVisualManager::OnDrawToolBoxFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawtoolboxframe).)|
|[CMFCVisualManagerVS2005::OnEraseTabsArea](#onerasetabsarea)|(Przesłania [CMFCVisualManagerOffice2003::OnEraseTabsArea](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onerasetabsarea).)|
|[CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground](#onfillautohidebuttonbackground)|(Przesłania [CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onfillautohidebuttonbackground).)|
|[CMFCVisualManagerVS2005::OnFillHighlightedArea](#onfillhighlightedarea)|(Przesłania [CMFCVisualManagerOffice2003::OnFillHighlightedArea](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onfillhighlightedarea).)|
|[CMFCVisualManagerVS2005::OnFillMiniFrameCaption](#onfillminiframecaption)|(Przesłania `CMFCVisualManagerOfficeXP::OnFillMiniFrameCaption`).|
|[CMFCVisualManagerVS2005::OnUpdateSystemColors](#onupdatesystemcolors)|(Przesłania [CMFCVisualManagerOffice2003::OnUpdateSystemColors](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onupdatesystemcolors).)|

## <a name="remarks"></a>Uwagi

Klasa CMFCVisualManagerVS2005 umożliwia zmienianie wyglądu aplikacji przypominają, Microsoft Visual Studio 2005.

Wszystkie elementy członkowskie tej klasy są funkcje wirtualne, które są uzyskiwane z nadrzędnym tej klasy, [klasa CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak za pomocą Menedżera visual VS 2005. Ten fragment kodu jest częścią [próbka Demo alertu pulpitu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#9](../../mfc/reference/codesnippet/cpp/cmfcvisualmanagervs2005-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

[CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)

[CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)

[CMFCVisualManagerVS2005](../../mfc/reference/cmfcvisualmanagervs2005-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxvisualmanagervs2005.h

##  <a name="getdockingtabsborderssize"></a>  CMFCVisualManagerVS2005::GetDockingTabsBordersSize

```
virtual int GetDockingTabsBordersSize();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getmditabsborderssize"></a>  CMFCVisualManagerVS2005::GetMDITabsBordersSize

```
virtual int GetMDITabsBordersSize();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpropertygridgroupcolor"></a>  CMFCVisualManagerVS2005::GetPropertyGridGroupColor

```
virtual COLORREF GetPropertyGridGroupColor(CMFCPropertyGridCtrl* pPropList);
```

### <a name="parameters"></a>Parametry

[in] *pPropList*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="gettabframecolors"></a>  CMFCVisualManagerVS2005::GetTabFrameColors

```
virtual void GetTabFrameColors(
    const CMFCBaseTabCtrl* pTabWnd,
    COLORREF& clrDark,
    COLORREF& clrBlack,
    COLORREF& clrHighlight,
    COLORREF& clrFace,
    COLORREF& clrDarkShadow,
    COLORREF& clrLight,
    CBrush*& pbrFace,
    CBrush*& pbrBlack);
```

### <a name="parameters"></a>Parametry

[in] *pTabWnd*<br/>
[in] *clrDark*<br/>
[in] *clrBlack*<br/>
[in] *clrHighlight*<br/>
[in] *clrFace*<br/>
[in] *clrDarkShadow*<br/>
[in] *clrLight*<br/>
[in] *pbrFace*<br/>
[in] *pbrBlack*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="hasoverlappedautohidebuttons"></a>  CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons

```
virtual BOOL HasOverlappedAutoHideButtons() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ondrawautohidebuttonborder"></a>  CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder

```
virtual void OnDrawAutoHideButtonBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize,
    CMFCAutoHideButton* pButton);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*<br/>
[in] *rectBounds*<br/>
[in] *rectBorderSize*<br/>
[in] *pButton*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="ondrawcaptionbutton"></a>  CMFCVisualManagerVS2005::OnDrawCaptionButton

```
virtual void OnDrawCaptionButton(
    CDC* pDC,
    CMFCCaptionButton* pButton,
    BOOL bActive,
    BOOL bHorz,
    BOOL bMaximized,
    BOOL bDisabled,
    int nImageID = -1);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*<br/>
[in] *pButton*<br/>
[in] *bWykonywanie aktywnych*<br/>
[in] *bHorz*<br/>
[in] *bMaximized*<br/>
[in] *bWyłączone*<br/>
[in] *nImageID*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="ondrawpanecaption"></a>  CMFCVisualManagerVS2005::OnDrawPaneCaption

```
virtual COLORREF OnDrawPaneCaption(
    CDC* pDC,
    CDockablePane* pBar,
    BOOL bActive,
    CRect rectCaption,
    CRect rectButtons);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*<br/>
[in] *pBar*<br/>
[in] *bWykonywanie aktywnych*<br/>
[in] *rectCaption*<br/>
[in] *rectButtons*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ondrawseparator"></a>  CMFCVisualManagerVS2005::OnDrawSeparator

```
virtual void OnDrawSeparator(
    CDC* pDC,
    CBasePane* pBar,
    CRect rect,
    BOOL bIsHoriz);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*<br/>
[in] *pBar*<br/>
[in] *rect*<br/>
[in] *bIsHoriz*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="ondrawtab"></a>  CMFCVisualManagerVS2005::OnDrawTab

```
virtual void OnDrawTab(
    CDC* pDC,
    CRect rectTab,
    int iTab,
    BOOL bIsActive,
    const CMFCBaseTabCtrl* pTabWnd);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*<br/>
[in] *rectTab*<br/>
[in] *iTab*<br/>
[in] *bIsActive*<br/>
[in] *pTabWnd*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="ondrawtoolboxframe"></a>  CMFCVisualManagerVS2005::OnDrawToolBoxFrame

```
virtual void OnDrawToolBoxFrame(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*<br/>
[in] *rect*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onerasetabsarea"></a>  CMFCVisualManagerVS2005::OnEraseTabsArea

```
virtual void OnEraseTabsArea(
    CDC* pDC,
    CRect rect,
    const CMFCBaseTabCtrl* pTabWnd);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*<br/>
[in] *rect*<br/>
[in] *pTabWnd*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onfillautohidebuttonbackground"></a>  CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground

```
virtual void OnFillAutoHideButtonBackground(
    CDC* pDC,
    CRect rect,
    CMFCAutoHideButton* pButton);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*<br/>
[in] *rect*<br/>
[in] *pButton*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onfillhighlightedarea"></a>  CMFCVisualManagerVS2005::OnFillHighlightedArea

```
virtual void OnFillHighlightedArea(
    CDC* pDC,
    CRect rect,
    CBrush* pBrush,
    CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*<br/>
[in] *rect*<br/>
[in] *pBrush*<br/>
[in] *pButton*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onfillminiframecaption"></a>  CMFCVisualManagerVS2005::OnFillMiniFrameCaption

```
virtual COLORREF OnFillMiniFrameCaption(
    CDC* pDC,
    CRect rectCaption,
    CPaneFrameWnd* pFrameWnd,
    BOOL bActive);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*<br/>
[in] *rectCaption*<br/>
[in] *pFrameWnd*<br/>
[in] *bWykonywanie aktywnych*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="onupdatesystemcolors"></a>  CMFCVisualManagerVS2005::OnUpdateSystemColors

```
virtual void OnUpdateSystemColors();
```

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)<br/>
[Klasa CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)<br/>
[Klasa CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)<br/>
[Klasa CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)
