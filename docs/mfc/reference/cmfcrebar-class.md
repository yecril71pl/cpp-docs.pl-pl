---
title: Klasa CMFCReBar
ms.date: 11/04/2016
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
helpviewer_keywords:
- CMFCReBar [MFC], AddBar
- CMFCReBar [MFC], CalcFixedLayout
- CMFCReBar [MFC], CanFloat
- CMFCReBar [MFC], Create
- CMFCReBar [MFC], EnableDocking
- CMFCReBar [MFC], GetReBarBandInfoSize
- CMFCReBar [MFC], GetReBarCtrl
- CMFCReBar [MFC], OnShowControlBarMenu
- CMFCReBar [MFC], OnToolHitTest
- CMFCReBar [MFC], OnUpdateCmdUI
- CMFCReBar [MFC], SetPaneAlignment
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
ms.openlocfilehash: a07f30fb00dd00e7a6315b8935731ccfc7500843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361696"
---
# <a name="cmfcrebar-class"></a>Klasa CMFCReBar

Obiekt `CMFCReBar` jest paskiem sterowania, który zapewnia układ, trwałość i informacje o stanie dla formantów prętów zbrojeniowych.
Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCReBar : public CPane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCReBar::Dodaj pasek](#addbar)|Dodaje opaskę do pręta zbrojeniowego.|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Zastępuje [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCReBar::CanFloat](#canfloat)|(Zastępuje [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CMFCReBar::Tworzenie](#create)|Tworzy formant prętów zbrojeniowych i dołącza go do `CMFCReBar` obiektu.|
|[CMFCReBar::EnableDocking](#enabledocking)|(Zastępuje [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Zapewnia bezpośredni dostęp do podstawowej [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) wspólnej kontroli.|
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Zastępuje [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(Zastępuje [CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Zastępuje [CBasePane::OnUpdateCmdUI](cbasepane-class.md).)|
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Zastępuje [CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|

## <a name="remarks"></a>Uwagi

Obiekt `CMFCReBar` może zawierać wiele okien podrzędnych. Obejmuje to pola edycji, paski narzędzi i pola listy. Rozmiar pręta zbrojeniowego można zmienić programowo lub ręcznie zmienić rozmiar pręta zbrojeniowego, przeciągając pasek chwytaka. Tło obiektu prętów zbrojeniowych można również ustawić na wybraną mapę bitową.

Obiekt prętów zbrojeniowych zachowuje się podobnie do obiektu paska narzędzi. Formant prętów zbrojeniowych może zawierać jeden lub więcej pasm, a każdy zespół może zawierać pasek chwytaka, mapę bitową, etykietę tekstową i okno podrzędne.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCReBar` używać różnych metod w klasie. W przykładzie pokazano, jak utworzyć formant prętów zbrojeniowych i dodać do niej zespół. Pasmo działa jako wewnętrzny pasek narzędzi. Ten fragment kodu jest częścią [próbki testowej prętów zbrojeniowych](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)\
&nbsp;-[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRebar.h

## <a name="cmfcrebaraddbar"></a><a name="addbar"></a>CMFCReBar::Dodaj pasek

Dodaje opaskę do pręta zbrojeniowego.

```
BOOL AddBar(
    CWnd* pBar,
    LPCTSTR pszText = NULL,
    CBitmap* pbmp = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,
    COLORREF clrFore,
    COLORREF clrBack,
    LPCTSTR pszText = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[w, na zewnątrz] Wskaźnik do okna podrzędnego, który ma zostać wstawiony do pręta zbrojeniowego. Obiekt, do którego istnieje odwołanie, musi mieć styl **okna WS_CHILD.**

*pszText (tekst psz)*<br/>
[w] Określa tekst wyświetlany na zbrojeniowym pasku zbrojeniowym. Tekst nie jest częścią okna podrzędnego. Jest on raczej wyświetlany na samym pasku zbrojeniowym.

*pbmp (polski)*<br/>
[w, na zewnątrz] Określa mapę bitową, która ma być wyświetlana w tle prętów zbrojeniowych.

*Dwstyle*<br/>
[w] Zawiera styl, który ma być stosowany do pasma. Aby uzyskać pełną listę stylów pasm, zobacz opis `fStyle` w strukturze [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) w dokumentacji zestawie Windows SDK.

*clrFore (nie ma pozycji)*<br/>
[w] Reprezentuje kolor pierwszego planu prętów zbrojeniowych.

*clrBack (włask*<br/>
[w] Reprezentuje kolor tła pręta zbrojeniowego.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zespół został pomyślnie dodany do pręta zbrojeniowego; w przeciwnym razie FALSE.

## <a name="cmfcrebarcreate"></a><a name="create"></a>CMFCReBar::Tworzenie

Tworzy formant prętów zbrojeniowych i dołącza go do [obiektu CMFCReBar.](../../mfc/reference/cmfcrebar-class.md)

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[w, na zewnątrz] Wskaźnik do okna nadrzędnego tego formantu prętów zbrojeniowych.

*dwCtrlStyle*<br/>
[w] Określa styl formantu prętów zbrojeniowych. Domyślną wartością stylu jest **RBS_BANDBORDERS**, który wyświetla wąskie linie oddzielające przylegające pasma na formancie prętów zbrojeniowych. Aby uzyskać listę prawidłowych stylów, zobacz [Style sterowania prętami zbrojenia](/windows/win32/Controls/rebar-control-styles) w dokumentacji zestawie Windows SDK.

*Dwstyle*<br/>
[w] Styl okna zbrojenia. Aby uzyskać listę prawidłowych stylów, zobacz [Style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Nid*<br/>
[w] Identyfikator okna podrzędnego pręta zbrojeniowego.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli pręt zbrojeniowa została pomyślnie utworzona; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcrebargetrebarctrl"></a><a name="getrebarctrl"></a>CMFCReBar::GetReBarCtrl

Zapewnia bezpośredni `CReBarCtrl` dostęp do podstawowej wspólnej kontroli dla `CMFCReBar` obiektów.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu `CReBarCtrl` źródłowego.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby skorzystać z funkcji wspólnego sterowania prętów systemu Windows podczas dostosowywania prętów zbrojeniowych.

## <a name="cmfcrebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCReBar::CalcFixedLayout

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

## <a name="cmfcrebarcanfloat"></a><a name="canfloat"></a>CMFCReBar::CanFloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcrebarenabledocking"></a><a name="enabledocking"></a>CMFCReBar::EnableDocking

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

[w] *styl dwDockStyle*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcrebargetrebarbandinfosize"></a><a name="getrebarbandinfosize"></a>CMFCReBar::GetReBarBandInfoSize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcrebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFCReBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Parametry

[w] *CPoint (punkt CPoint)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcrebarontoolhittest"></a><a name="ontoolhittest"></a>CMFCReBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parametry

[w] *punkt*<br/>
[w] *pTI*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcrebaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCReBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

[w] *pTarget*<br/>
[w] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcrebarsetpanealignment"></a><a name="setpanealignment"></a>CMFCReBar::SetPaneAlignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

[w] *dwZładna*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CReBarCtrl](../../mfc/reference/crebarctrl-class.md)<br/>
[Klasa CPane](../../mfc/reference/cpane-class.md)
