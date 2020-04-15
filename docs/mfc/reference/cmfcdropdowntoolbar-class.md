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
ms.openlocfilehash: 68dd976471b39d7f50c2f0378b2fce99ad3feeca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367605"
---
# <a name="cmfcdropdowntoolbar-class"></a>Klasa CMFCDropDownToolBar

Pasek narzędzi, który pojawia się, gdy użytkownik naciśnie i przytrzymuje przycisk paska narzędzi najwyższego poziomu.

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Przesłania `CPane::AllowShowOnPaneMenu`).|
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Zastępuje [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Zastępuje [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Przesłania `CMFCToolBar::OnSendCommand`).|
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Zastępuje [CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md).|

### <a name="remarks"></a>Uwagi

Obiekt `CMFCDropDownToolBar` łączy wygląd paska narzędzi z zachowaniem menu podręcznego. Gdy użytkownik naciśnie i przytrzymuje przycisk rozwijanego paska narzędzi (zobacz [CMFCDropDownToolButton Class),](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)pojawi się rozwijany pasek narzędzi, a użytkownik może wybrać przycisk z rozwijanego paska narzędzi, przewijając do niego i zwalniając przycisk myszy. Po wybraniu przez użytkownika przycisku na pasku narzędzi rozwijanym przycisk ten jest wyświetlany jako bieżący przycisk na pasku narzędzi najwyższego poziomu.

Nie można dostosować ani zadokować rozwijanego paska narzędzi i nie ma stanu odrywu.

Na poniższej `CMFCDropDownToolBar` ilustracji przedstawiono obiekt:

![Przykład CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "Przykład CMFCDropDownToolbar")

Obiekt jest `CMFCDropDownToolBar` tworzęny w taki sam sposób, jak zwykły pasek narzędzi (zobacz [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)).

Aby wstawić pasek narzędzi listy rozwijanej do nadrzędnego paska narzędzi:

1. Zarezerwuj fikcyjny identyfikator zasobu dla przycisku w zasobie nadrzędnego paska narzędzi.

2. Utwórz `CMFCDropDownToolBarButton` obiekt zawierający pasek narzędzi rozwijany (aby uzyskać więcej informacji, zobacz [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).

3. Zastąp przycisk `CMFCDropDownToolBarButton` manekina obiektem za pomocą [cmfctoolbar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Aby uzyskać więcej informacji na temat przycisków paska narzędzi, zobacz [Instruktaż: Umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md). Na przykład rozwijanego paska narzędzi zobacz przykładowy projekt VisualStudioDemo.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `Create` metody w `CMFCDropDownToolBar` klasie. Ten fragment kodu jest częścią [przykładu demo programu Visual Studio.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[Cmfctoolbar](../../mfc/reference/cmfctoolbar-class.md)

[Cmfcdropdowntoolbar](../../mfc/reference/cmfcdropdowntoolbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCDropDownToolBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcdropdowntoolbarloadbitmap"></a><a name="loadbitmap"></a>CMFCDropDownToolBar::LoadBitmap

Ładuje obrazy paska narzędzi z zasobów aplikacji.

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

*interfejs użytkownika uiResID*<br/>
[w] Identyfikator zasobu mapy bitowej, który odwołuje się do obrazów paska narzędzi gorących.

*identyfikator uiColdResID*<br/>
[w] Identyfikator zasobu mapy bitowej, który odwołuje się do obrazów zimnego paska narzędzi.

*interfejs użytkownika uiMenuResID*<br/>
[w] Identyfikator zasobu mapy bitowej, który odnosi się do zwykłych obrazów menu.

*Zablokowany*<br/>
[w] PRAWDA, aby zablokować pasek narzędzi; w przeciwnym razie FALSE.

*identyfikator uiDisabledResID*<br/>
[w] Identyfikator zasobu mapy bitowej, który odwołuje się do obrazów wyłączonego paska narzędzi.

*identyfikator użytkownika uiMenuDisabledResID*<br/>
[w] Identyfikator zasobu mapy bitowej, który odnosi się do wyłączonych obrazów menu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda powiedzie się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

[CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) metoda wywołuje tę metodę, aby załadować obrazy, które są skojarzone z paskiem narzędzi. Zastąd w tej metodzie należy wykonać niestandardowe ładowanie zasobów obrazu.

Wywołanie `LoadBitmapEx` metody, aby załadować dodatkowe obrazy po utworzeniu paska narzędzi.

## <a name="cmfcdropdowntoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CMFCDropDownToolBar::LoadToolBar

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

[w] *interfejs użytkownika uiResID*<br/>

[w] *identyfikator uiColdResID*<br/>

[w] *interfejs użytkownika uiMenuResID*<br/>

[w] *BOOL (BOOL)*<br/>

[w] *identyfikator uiDisabledResID*<br/>

[w] *identyfikator użytkownika uiMenuDisabledResID*<br/>

[w] *uiHotResID*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcdropdowntoolbaronlbuttonup"></a><a name="onlbuttonup"></a>CMFCDropDownToolBar::OnLButtonUp

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parametry

[w] *nPłgi*<br/>

[w] *punkt*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcdropdowntoolbaronmousemove"></a><a name="onmousemove"></a>CMFCDropDownToolBar::OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parametry

[w] *nPłgi*<br/>

[w] *punkt*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcdropdowntoolbaronsendcommand"></a><a name="onsendcommand"></a>CMFCDropDownToolBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

[w] *pButton (przycisk)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcdropdowntoolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCDropDownToolBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

[w] *pTarget*<br/>

[w] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar::Tworzenie](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Klasa CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[Wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
