---
title: Klasa CReBar
ms.date: 11/19/2018
f1_keywords:
- CReBar
- AFXEXT/CReBar
- AFXEXT/CReBar::AddBar
- AFXEXT/CReBar::Create
- AFXEXT/CReBar::GetReBarCtrl
helpviewer_keywords:
- CReBar [MFC], AddBar
- CReBar [MFC], Create
- CReBar [MFC], GetReBarCtrl
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
ms.openlocfilehash: 434232e8f99bf914b00379db53d4b4a37d24fe36
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502795"
---
# <a name="crebar-class"></a>Klasa CReBar

Pasek sterowania, który zawiera układ, trwałość i informacje o stanie dla formantów paska pomocniczego.

## <a name="syntax"></a>Składnia

```
class CReBar : public CControlBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CReBar:: AddBar](#addbar)|Dodaje bandę do paska pomocniczego.|
|[CReBar:: Create](#create)|Tworzy formant paska pomocniczego i dołącza go do `CReBar` obiektu.|
|[CReBar::GetReBarCtrl](#getrebarctrl)|Zezwala na bezpośredni dostęp do podstawowej kontroli wspólnej.|

## <a name="remarks"></a>Uwagi

Obiekt paska pomocniczego może zawierać różne okna podrzędne, zwykle inne kontrolki, takie jak pola edycji, paski narzędzi i pola listy. Obiekt paska pomocniczego może wyświetlać jego okna podrzędne przez określoną mapę bitową. Aplikacja może automatycznie zmienić rozmiar paska pomocniczego lub można ręcznie zmienić rozmiar paska pomocniczego, klikając lub przeciągając pasek uchwytu.

![Przykład RebarMenu](../../mfc/reference/media/vc4sc61.gif "Przykład RebarMenu")

## <a name="rebar-control"></a>Paska pomocniczego — formant

Obiekt paska pomocniczego zachowuje się podobnie do obiektu Toolbar. Paska pomocniczego używa mechanizmu klikania i przeciągania, aby zmienić rozmiar jego pasm. Kontrolka paska pomocniczego może zawierać co najmniej jedną grupę, a każdy z nich ma dowolną kombinację paska uchwytu, mapy bitowej, etykiety tekstowej i okna podrzędnego. Jednak pasma nie mogą zawierać więcej niż jednego okna podrzędnego.

`CReBar`używa klasy [Korzystanie CReBarCtrl](../../mfc/reference/crebarctrl-class.md) w celu zapewnienia jej implementacji. Aby skorzystać z opcji dostosowania kontrolki, można uzyskać dostęp do formantu paska pomocniczego za pomocą [GetReBarCtrl](#getrebarctrl) . Aby uzyskać więcej informacji na temat kontrolek `CReBarCtrl`paska pomocniczego, zobacz. Aby uzyskać więcej informacji na temat używania formantów paska pomocniczego, zobacz [using korzystanie CReBarCtrl](../../mfc/using-crebarctrl.md).

> [!CAUTION]
>  Obiekty sterowania paska pomocniczego i paska pomocniczego nie obsługują dokowania paska sterowania MFC. Jeśli `CRebar::EnableDocking` jest wywoływana, aplikacja zostanie zatwierdzona.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext. h

##  <a name="addbar"></a>CReBar:: AddBar

Wywołaj tę funkcję elementu członkowskiego, aby dodać pasmo do paska pomocniczego.

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
Wskaźnik do `CWnd` obiektu, który jest oknem podrzędnym, który ma zostać wstawiony do paska pomocniczego. Obiekt, do którego istnieje odwołanie, musi mieć WS_CHILD.

*lpszText*<br/>
Wskaźnik do ciągu zawierającego tekst, który ma być wyświetlany w paska pomocniczego. Domyślnie wartość NULL. Tekst zawarty w *lpszText* nie jest częścią okna podrzędnego; jest on paska pomocniczego.

*pbmp*<br/>
Wskaźnik do `CBitmap` obiektu, który ma być wyświetlany w tle paska pomocniczego. Domyślnie wartość NULL.

*dwStyle*<br/>
Element DWORD zawierający styl, który ma zostać zastosowany do paska pomocniczego. Zobacz opis funkcji w strukturze Win32 REBARBANDINFO, aby uzyskać pełną listę stylów pasma. [](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) `fStyle`

*clrFore*<br/>
Wartość COLORREF, która reprezentuje kolor pierwszego planu paska pomocniczego.

*clrBack*<br/>
Wartość COLORREF, która reprezentuje kolor tła paska pomocniczego.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

##  <a name="create"></a>CReBar:: Create

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć paska pomocniczego.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do `CWnd` obiektu, którego okno systemu Windows jest elementem nadrzędnym paska stanu. Zwykle okno ramki.

*dwCtrlStyle*<br/>
Styl formantu paska pomocniczego. Domyślnie RBS_BANDBORDERS, który wyświetla wąskie linie do oddzielania sąsiadujących pasm w kontrolce paska pomocniczego. Zobacz [Style formantów paska pomocniczego](/windows/win32/Controls/rebar-control-styles) w Windows SDK, aby wyświetlić listę stylów.

*dwStyle*<br/>
Style okna paska pomocniczego.

*nID*<br/>
Identyfikator okna podrzędnego paska pomocniczego.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CReBar:: AddBar](#addbar).

##  <a name="getrebarctrl"></a>CReBar:: GetReBarCtrl

Ta funkcja członkowska umożliwia bezpośredni dostęp do zasadniczej kontroli wspólnej.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu [Korzystanie CReBarCtrl](../../mfc/reference/crebarctrl-class.md) .

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby skorzystać z funkcji wspólnego formantu paska pomocniczego systemu Windows w dostosowaniu paska pomocniczego. Po wywołaniu `GetReBarCtrl`funkcja zwraca obiekt Reference `CReBarCtrl` do obiektu, aby można było użyć dowolnego zestawu funkcji Członkowskich.

Aby uzyskać więcej informacji na `CReBarCtrl` temat dostosowywania paska pomocniczego, zobacz [using korzystanie CReBarCtrl](../../mfc/using-crebarctrl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>Zobacz także

[Przykład MFCIE MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
