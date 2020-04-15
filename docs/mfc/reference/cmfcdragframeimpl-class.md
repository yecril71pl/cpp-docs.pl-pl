---
title: Klasa CMFCDragFrameImpl
ms.date: 10/18/2018
f1_keywords:
- CMFCDragFrameImpl
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
ms.openlocfilehash: a2f6f558d6b4452ca06429c7e3017b7c575c6676
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367564"
---
# <a name="cmfcdragframeimpl-class"></a>Klasa CMFCDragFrameImpl

Klasa `CMFCDragFrameImpl` rysuje prostokąt przeciągania, który pojawia się, gdy użytkownik przeciąga okienko w trybie standardowej stacji dokującej.
Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>Uwagi

Obiekt tej klasy jest osadzony w każdym [obiekcie CPane Class.](../../mfc/reference/cpane-class.md) W związku z tym każde `CanFloat` okienko, które używa metody wyświetla prostokąt przeciągania, gdy użytkownik przeciąga go.

Grubość prostokąta przeciągania można kontrolować za pomocą [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) i [AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdragframeimpl.h

## <a name="cmfcdragframeimplenddrawdragframe"></a><a name="enddrawdragframe"></a>CMFCDragFrameImpl::EndDrawDragFrame

```
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>Parametry

[w] *bClearInternalRects*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcdragframeimplinit"></a><a name="init"></a>CMFCDragFrameImpl::Init

```
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>Parametry

[w] *pDraggedWnd (właśc.*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcdragframeimplmovedragframe"></a><a name="movedragframe"></a>CMFCDragFrameImpl::MoveDragFrame

```
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>Parametry

[w] *bForceMove (Ruch Sił)*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcdragframeimplplacetabpredocking"></a><a name="placetabpredocking"></a>CMFCDragFrameImpl::PlaceTabPreDocking

```
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>Parametry

[w] *pTabbedBar (Bar)*<br/>

[w] *bFirstTime (Czas powierszy)*<br/>

[w] *pCBarToPlaceOn*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcdragframeimplremovetabpredocking"></a><a name="removetabpredocking"></a>CMFCDragFrameImpl::RemoveTabPreDocking

```
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>Parametry

[w] *pOldTargetBar (Pasek celów)*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcdragframeimplresetstate"></a><a name="resetstate"></a>CMFCDragFrameImpl::ResetState

```
void ResetState();
```

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CPane](../../mfc/reference/cpane-class.md)
