---
title: CMFCDragFrameImpl Class
ms.date: 10/18/2018
f1_keywords:
- CMFCDragFrameImpl
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
ms.openlocfilehash: 05b4426da6bee0443a407cff583f47bee60262e4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301210"
---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl Class

`CMFCDragFrameImpl` Klasy rysuje przeciągnij prostokąt, który jest wyświetlany, gdy użytkownik przeciągnie okienko w trybie standardowego dokowania.
Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>Uwagi

Obiekt tej klasy jest osadzony w każdym [klasa CPane](../../mfc/reference/cpane-class.md) obiektu. W związku z tym, każde okienko, który używa `CanFloat` metoda Wyświetla przeciągnij prostokąt, gdy użytkownik przeciągnie go.

Grubość przeciągnij prostokąt można kontrolować za pomocą [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) i [AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdragframeimpl.h

##  <a name="enddrawdragframe"></a>  CMFCDragFrameImpl::EndDrawDragFrame

```
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>Parametry

[in] *bClearInternalRects*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="init"></a>  CMFCDragFrameImpl::Init

```
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>Parametry

[in] *pDraggedWnd*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="movedragframe"></a>  CMFCDragFrameImpl::MoveDragFrame

```
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>Parametry

[in] *bForceMove*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="placetabpredocking"></a>  CMFCDragFrameImpl::PlaceTabPreDocking

```
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>Parametry

[in] *pTabbedBar*<br/>

[in] *bFirstTime*<br/>

[in] *pCBarToPlaceOn*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="removetabpredocking"></a>  CMFCDragFrameImpl::RemoveTabPreDocking

```
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>Parametry

[in] *pOldTargetBar*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="resetstate"></a>  CMFCDragFrameImpl::ResetState

```
void ResetState();
```

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CPane](../../mfc/reference/cpane-class.md)
