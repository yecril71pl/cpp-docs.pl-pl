---
title: Klasa CMFCDropDownToolBar
ms.date: 11/19/2018
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
ms.openlocfilehash: 704d48cc546943d818ae8b898060fe0f7e203c53
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303556"
---
# <a name="cmfcdropdowntoolbar-class"></a>Klasa CMFCDropDownToolBar

Pasek narzędzi, który pojawia się po naciśnięciu i przytrzymaniu przycisku paska narzędzi najwyższego poziomu.

   Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.
## <a name="syntax"></a>Składnia

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Przesłania `CPane::AllowShowOnPaneMenu`).|
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Przesłania [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Przesłania [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Przesłania `CMFCToolBar::OnSendCommand`).|
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Przesłania [CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md).|

### <a name="remarks"></a>Uwagi

Element `CMFCDropDownToolBar` obiektu łączy wygląd paska narzędzi z zachowaniem menu podręcznego. Po naciśnięciu i przytrzymaniu przycisku paska narzędzi z listy rozwijanej (zobacz [klasa CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), zostanie wyświetlony pasek narzędzi listy rozwijanej i użytkownik może wybrać przycisk na pasku narzędzi listy rozwijanej, przewijania do niego i zwolnieniem przycisku myszy przycisk. Po użytkownik wybierze przycisk na pasku narzędzi listy rozwijanej, ten przycisk jest wyświetlana jako bieżący przycisk na pasku narzędzi najwyższego poziomu.

Rozwijany pasek narzędzi nie może zostać dostosowany lub zadokowane, a nie ma stanu odrywania.

Poniższa ilustracja przedstawia `CMFCDropDownToolBar` obiektu:

![Przykład CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "przykład CMFCDropDownToolbar")

Możesz utworzyć `CMFCDropDownToolBar` obiektu taki sam sposób utworzyć zwykłej paska narzędzi (zobacz [klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)).

Aby wstawić rozwijany pasek narzędzi do narzędzi nadrzędnego:

1. Zarezerwuj identyfikator zasobu fikcyjnego przycisku w nadrzędnej zasób paska narzędzi.

2. Tworzenie `CMFCDropDownToolBarButton` obiekt, który zawiera rozwijany pasek narzędzi (Aby uzyskać więcej informacji, zobacz [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).

3. Zamień zastępczy button z `CMFCDropDownToolBarButton` obiektu za pomocą [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Aby uzyskać więcej informacji na temat przycisków paska narzędzi, zobacz [instruktażu: Umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md). Aby uzyskać przykład rozwijany pasek narzędzi zobacz przykładowy projekt VisualStudioDemo.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `Create` method in Class metoda `CMFCDropDownToolBar` klasy. Ten fragment kodu jest częścią [Visual Studio przykład](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdropdowntoolbar.h

##  <a name="allowshowonpanemenu"></a>  CMFCDropDownToolBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="loadbitmap"></a>  CMFCDropDownToolBar::LoadBitmap

Wczytuje obrazy paska narzędzi z zasobów aplikacji.

```
virtual BOOL LoadBitmap(
    UINT uiResID,
    UINT uiColdResID=0,
    UINT uiMenuResID=0,
    BOOL bLocked=FALSE,
    UINT uiDisabledResID=0,
    UINT uiMenuDisabledResID=0);
```

### <a name="parameters"></a>Parametry

*uiResID*<br/>
[in] Identyfikator zasobu mapy bitowej, która odwołuje się do gorąca paska narzędzi obrazów.

*uiColdResID*<br/>
[in] Identyfikator zasobu mapy bitowej, która odwołuje się do zimnej paska narzędzi obrazów.

*uiMenuResID*<br/>
[in] Identyfikator zasobu mapy bitowej, która odwołuje się do obrazów regularne menu.

*bLocked*<br/>
[in] Wartość TRUE, aby zablokować narzędzi; w przeciwnym razie wartość FALSE.

*uiDisabledResID*<br/>
[in] Identyfikator zasobu mapy bitowej, która odwołuje się do wyłączonego paska narzędzi obrazów.

*uiMenuDisabledResID*<br/>
[in] Identyfikator zasobu mapy bitowej, która odwołuje się do obrazów menu wyłączone.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli metoda się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

[CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) metoda wywołuje tę metodę, aby załadować obrazy, które są skojarzone z paska narzędzi. Zastępuje tę metodę do wykonywania niestandardowych ładowanie zasobów obrazu.

Wywołaj `LoadBitmapEx` metodę, aby załadować dodatkowe obrazy, po utworzeniu paska narzędzi.

##  <a name="loadtoolbar"></a>  CMFCDropDownToolBar::LoadToolBar

```
virtual BOOL LoadToolBar(
    UINT uiResID,
    UINT uiColdResID = 0,
    UINT uiMenuResID = 0,
    BOOL = FALSE,
    UINT uiDisabledResID = 0,
    UINT uiMenuDisabledResID = 0,
    UINT uiHotResID = 0);
```

### <a name="parameters"></a>Parametry

[in] *uiResID*<br/>

[in] *uiColdResID*<br/>

[in] *uiMenuResID*<br/>

[in] *BOOL*<br/>

[in] *uiDisabledResID*<br/>

[in] *uiMenuDisabledResID*<br/>

[in] *uiHotResID*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="onlbuttonup"></a>  CMFCDropDownToolBar::OnLButtonUp

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parametry

[in] *nFlags*<br/>

[in] *punktu*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onmousemove"></a>  CMFCDropDownToolBar::OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parametry

[in] *nFlags*<br/>

[in] *punktu*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onsendcommand"></a>  CMFCDropDownToolBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

[in] *pButton*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="onupdatecmdui"></a>  CMFCDropDownToolBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

[in] *pTarget*<br/>

[in] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Klasa CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[Przewodnik: Umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
