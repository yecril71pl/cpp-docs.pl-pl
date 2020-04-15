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
ms.openlocfilehash: c1379d1ef8effea0df564da1b43769bb9a11435d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363928"
---
# <a name="crebar-class"></a>Klasa CReBar

Pasek sterowania, który zawiera informacje o układzie, trwałości i stanie dla formantów prętów zbrojeniowych.

## <a name="syntax"></a>Składnia

```
class CReBar : public CControlBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CReBar::Dodaj pasek](#addbar)|Dodaje opaskę do pręta zbrojeniowego.|
|[CReBar::Tworzenie](#create)|Tworzy formant prętów zbrojeniowych i dołącza go do `CReBar` obiektu.|
|[CReBar::GetReBarCtrl](#getrebarctrl)|Umożliwia bezpośredni dostęp do podstawowej wspólnej kontroli.|

## <a name="remarks"></a>Uwagi

Obiekt prętów zbrojeniowych może zawierać różne okna podrzędne, zazwyczaj inne formanty, w tym pola edycji, paski narzędzi i pola listy. Obiekt prętów zbrojeniowych może wyświetlać swoje okna podrzędne na określonej mapie bitowej. Aplikacja może automatycznie zmienić rozmiar pręta zbrojeniowego lub użytkownik może ręcznie zmienić rozmiar pręta zbrojeniowego, klikając lub przeciągając pasek chwytaka.

![Przykład RebarMenu](../../mfc/reference/media/vc4sc61.gif "Przykład RebarMenu")

## <a name="rebar-control"></a>Sterowanie prętami zbrojeniowym

Obiekt prętów zbrojeniowych zachowuje się podobnie do obiektu paska narzędzi. Pręt zbrojeniowy używa mechanizmu klikania i przeciągania do ponownego rozmiaru jego pasm. Formant prętów zbrojeniowych może zawierać jeden lub więcej pasm, przy czym każdy zespół ma dowolną kombinację paska chwytaka, mapy bitowej, etykiety tekstowej i okna podrzędnego. Jednak pasma nie może zawierać więcej niż jedno okno podrzędne.

`CReBar`używa [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) klasy, aby zapewnić jego implementacji. Można uzyskać dostęp do kontroli prętów zbrojeniowych za pośrednictwem [GetReBarCtrl,](#getrebarctrl) aby skorzystać z opcji dostosowywania formantu. Aby uzyskać więcej informacji na `CReBarCtrl`temat elementów sterujących prętów zbrojeniowych, zobacz . Aby uzyskać więcej informacji na temat używania formantów prętów zbrojeniowych, zobacz [Korzystanie z CReBarCtrl](../../mfc/using-crebarctrl.md).

> [!CAUTION]
> Obiekty sterujące prętami zbrojeniowymi i prętami zbrojeniowymi nie obsługują dokowania pręta sterującego MFC. Jeśli `CRebar::EnableDocking` jest wywoływana, aplikacja będzie potwierdzać.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ccontrolbar](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="crebaraddbar"></a><a name="addbar"></a>CReBar::Dodaj pasek

Wywołanie tej funkcji elementu członkowskiego, aby dodać zespół do pręta zbrojeniowego.

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
Wskaźnik do `CWnd` obiektu, który jest okno podrzędne, które mają być wstawione do pręta zbrojeniowego. Obiekt, do którego istnieje odwołanie, musi mieć WS_CHILD.

*lpszText (tekst)*<br/>
Wskaźnik do ciągu zawierającego tekst, który ma być wyświetlany na pasku zbrojeniowym. NULL domyślnie. Tekst zawarty w *lpszText* nie jest częścią okna podrzędnego; znajduje się na samym zbrojeniowym.

*pbmp (polski)*<br/>
Wskaźnik do `CBitmap` obiektu, który ma być wyświetlany na tle pręta zbrojeniowego. NULL domyślnie.

*Dwstyle*<br/>
A DWORD zawierające styl do zastosowania do pręta zbrojeniowego. Pełna `fStyle` lista stylów pasm można znaleźć w opisie funkcji w strukturze Win32 [REBARBANDINFO.](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)

*clrFore (nie ma pozycji)*<br/>
Wartość COLORREF reprezentująca kolor pierwszego planu prętów zbrojeniowych.

*clrBack (włask*<br/>
Wartość COLORREF reprezentująca kolor tła pręta zbrojeniowego.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

## <a name="crebarcreate"></a><a name="create"></a>CReBar::Tworzenie

Wywołanie tej funkcji elementu członkowskiego, aby utworzyć pręt zbrojeniowy.

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
Styl sterowania prętami zbrojeniowych. Domyślnie RBS_BANDBORDERS, który wyświetla wąskie linie do oddzielenia sąsiednich pasm w formancie prętów zbrojeniowych. Aby uzyskać listę stylów, zobacz [Style sterowania prętami zbrojenia](/windows/win32/Controls/rebar-control-styles) w zestawie Windows SDK.

*Dwstyle*<br/>
Style okien prętów zbrojeniowych.

*Nid*<br/>
Identyfikator okna podrzędnego pręta zbrojeniowego.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CReBar::AddBar](#addbar).

## <a name="crebargetrebarctrl"></a><a name="getrebarctrl"></a>CReBar::GetReBarCtrl

Ta funkcja elementu członkowskiego umożliwia bezpośredni dostęp do podstawowej wspólnej kontroli.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do [obiektu CReBarCtrl.](../../mfc/reference/crebarctrl-class.md)

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego, aby skorzystać z funkcji wspólnego formantu prętów zbrojeniowych systemu Windows w dostosowywaniu prętów zbrojeniowych. Podczas wywoływania `GetReBarCtrl`zwraca obiekt odniesienia `CReBarCtrl` do obiektu, dzięki czemu można użyć jednego zestawu funkcji członkowskich.

Aby uzyskać więcej `CReBarCtrl` informacji na temat używania do dostosowywania prętów zbrojeniowych, zobacz [Korzystanie z CReBarCtrl](../../mfc/using-crebarctrl.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykładowe MFCIE MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
