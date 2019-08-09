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
ms.openlocfilehash: ccd500547bdcf65e922f7b5e5ca8d30e0423933d
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866185"
---
# <a name="cmfcrebar-class"></a>Klasa CMFCReBar

`CMFCReBar` Obiekt jest paskiem sterowania, który zapewnia informacje o układzie, trwałości i stanie dla formantów paska pomocniczego.
Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.
## <a name="syntax"></a>Składnia

```
class CMFCReBar : public CPane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCReBar::AddBar](#addbar)|Dodaje bandę do paska pomocniczego.|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Przesłania [CBasePane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCReBar:: onfloat](#canfloat)|(Przesłania [CBasePane:: onfloat](../../mfc/reference/cbasepane-class.md#canfloat)).|
|[CMFCReBar:: Create](#create)|Tworzy formant paska pomocniczego i dołącza go do `CMFCReBar` obiektu.|
|[CMFCReBar::EnableDocking](#enabledocking)|(Przesłania [CBasePane:: EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Zapewnia bezpośredni dostęp do podstawowej kontroli [Korzystanie CReBarCtrl](../../mfc/reference/crebarctrl-class.md) .|
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Przesłania [CPane:: OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(Przesłania [CWnd:: OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Przesłania [CBasePane:: OnUpdateCmdUI](cbasepane-class.md).)|
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Przesłania [CBasePane:: SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|

## <a name="remarks"></a>Uwagi

`CMFCReBar` Obiekt może zawierać wiele okien podrzędnych. Obejmuje to pola edycji, paski narzędzi i pola listy. Można programowo zmienić rozmiar paska pomocniczego lub użytkownik może ręcznie zmienić rozmiar paska pomocniczego, przeciągając jego pasek uchwytu. Możesz również ustawić tło obiektu paska pomocniczego na wybraną mapę bitową.

Obiekt paska pomocniczego zachowuje się podobnie do obiektu Toolbar. Kontrolka paska pomocniczego może zawierać co najmniej jedną grupę, a każda z nich może zawierać pasek uchwytu, mapę bitową, etykietę tekstową i okno podrzędne.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia różnych metod w `CMFCReBar` klasie. W przykładzie pokazano, jak utworzyć kontrolkę paska pomocniczego i dodać do niej pasmo. Pasek działa jako wewnętrzny pasek narzędzi. Ten fragment kodu jest częścią [przykładu testu paska pomocniczego](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRebar. h

##  <a name="addbar"></a>CMFCReBar::AddBar

Dodaje bandę do paska pomocniczego.

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
[in. out] Wskaźnik do okna podrzędnego, który ma zostać wstawiony do paska pomocniczego. Obiekt, do którego istnieje odwołanie, musi mieć styl okna **WS_CHILD** .

*pszText*<br/>
podczas Określa tekst, który ma być wyświetlany w paska pomocniczego. Tekst nie jest częścią okna podrzędnego. Zamiast tego jest on wyświetlany na samej paska pomocniczego.

*pbmp*<br/>
[in. out] Określa mapę bitową, która ma być wyświetlana w tle paska pomocniczego.

*dwStyle*<br/>
podczas Zawiera styl, który ma zostać zastosowany do pasma. Aby zapoznać się z pełną listą stylów pasma, zobacz `fStyle` opis struktury [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) w dokumentacji Windows SDK.

*clrFore*<br/>
podczas Przedstawia kolor pierwszego planu paska pomocniczego.

*clrBack*<br/>
podczas Przedstawia kolor tła paska pomocniczego.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pasmo zostało pomyślnie dodane do paska pomocniczego; w przeciwnym razie FALSE.

##  <a name="create"></a>CMFCReBar:: Create

Tworzy formant paska pomocniczego i dołącza go do obiektu [CMFCReBar](../../mfc/reference/cmfcrebar-class.md) .

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[in. out] Wskaźnik do okna nadrzędnego tej kontrolki paska pomocniczego.

*dwCtrlStyle*<br/>
podczas Określa styl dla kontrolki paska pomocniczego. Wartość stylu domyślnego to **RBS_BANDBORDERS**, która wyświetla wąskie linie w celu oddzielenia sąsiednich pasm w kontrolce paska pomocniczego. Aby uzyskać listę prawidłowych stylów, zobacz [Style formantu paska pomocniczego](/windows/desktop/Controls/rebar-control-styles) w dokumentacji Windows SDK.

*dwStyle*<br/>
podczas Styl okna kontrolki paska pomocniczego. Aby uzyskać listę prawidłowych stylów, zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
podczas Identyfikator okna podrzędnego paska pomocniczego.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli paska pomocniczego został utworzony pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="getrebarctrl"></a>CMFCReBar::GetReBarCtrl

Zapewnia bezpośredni dostęp do `CReBarCtrl` zasadniczego wspólnego formantu dla `CMFCReBar` obiektów.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu źródłowego `CReBarCtrl` .

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby skorzystać ze standardowych funkcji kontroli systemu Windows paska pomocniczego podczas dostosowywania paska pomocniczego.

##  <a name="calcfixedlayout"></a>CMFCReBar::CalcFixedLayout

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

##  <a name="canfloat"></a>CMFCReBar:: onfloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="enabledocking"></a>CMFCReBar::EnableDocking

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

podczas *dwDockStyle*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="getrebarbandinfosize"></a>CMFCReBar::GetReBarBandInfoSize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="onshowcontrolbarmenu"></a>CMFCReBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Parametry

podczas *CPoint*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ontoolhittest"></a>CMFCReBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parametry

podczas *punkt*<br/>
podczas *PTI*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="onupdatecmdui"></a>CMFCReBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

podczas *pTarget*<br/>
podczas *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setpanealignment"></a>CMFCReBar::SetPaneAlignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

podczas *dwAlignment*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CReBarCtrl](../../mfc/reference/crebarctrl-class.md)<br/>
[Klasa CPane](../../mfc/reference/cpane-class.md)
