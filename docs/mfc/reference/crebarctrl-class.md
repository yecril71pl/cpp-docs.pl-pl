---
title: Klasa CReBarCtrl
ms.date: 11/19/2018
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
helpviewer_keywords:
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
ms.openlocfilehash: 930322f1803eba7709505018c77ecea3f816dd15
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750632"
---
# <a name="crebarctrl-class"></a>Klasa CReBarCtrl

Hermetyzuje funkcjonalność formantu prętów zbrojeniowych, który jest kontenerem dla okna podrzędnego.

## <a name="syntax"></a>Składnia

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|Konstruuje `CReBarCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CReBarCtrl::BeginDrag](#begindrag)|Umieszcza formant prętów zbrojeniowych w tryb przeciągnij i upuść.|
|[CReBarCtrl::Utwórz](#create)|Tworzy formant prętów zbrojeniowych i dołącza go do `CReBarCtrl` obiektu.|
|[CReBarCtrl::CreateEx](#createex)|Tworzy formant prętów zbrojeniowych z określonymi `CReBarCtrl` stylami rozszerzonymi systemu Windows i dołącza go do obiektu.|
|[CReBarCtrl::DeleteBand](#deleteband)|Usuwa zespół z kontrolki prętów zbrojeniowych.|
|[CReBarCtrl::DragMove](#dragmove)|Aktualizuje pozycję przeciągania w formancie prętów zbrojeniowych po wywołaniu do `BeginDrag`.|
|[CReBarCtrl::EndDrag](#enddrag)|Kończy operację przeciągania i upuszczania formantu prętów zbrojeniowych.|
|[CReBarCtrl::GetBandBorders](#getbandborders)|Pobiera granice zespołu.|
|[CReBarCtrl::GetBandCount](#getbandcount)|Pobiera liczbę pasm aktualnie w formancie prętów zbrojeniowych.|
|[CReBarCtrl::GetBandInfo](#getbandinfo)|Pobiera informacje o określonym paśmie w formancie prętów zbrojeniowych.|
|[CReBarCtrl::GetBandMargins](#getbandmargins)|Pobiera marginesy pasma.|
|[CReBarCtrl::GetBarHeight](#getbarheight)|Pobiera wysokość zbrojenia.|
|[CReBarCtrl::GetBarInfo](#getbarinfo)|Pobiera informacje o formancie prętów zbrojeniowych i liście obrazów, których używa.|
|[CReBarCtrl::GetBkColor](#getbkcolor)|Pobiera domyślny kolor tła formantu prętów zbrojeniowych.|
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|Pobiera [strukturę COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) skojarzoną z formantem prętów zbrojeniowych.|
|[CReBarCtrl::GetDropTarget](#getdroptarget)|Pobiera wskaźnik interfejsu formantu prętów zbrojeniowych. `IDropTarget`|
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|Pobiera rozszerzony styl bieżącej kontroli prętów zbrojeniowych.|
|[CReBarCtrl::Lista GetImage](#getimagelist)|Pobiera listę obrazów skojarzoną z kontrolką prętów zbrojeniowych.|
|[CReBarCtrl::GetPalette](#getpalette)|Pobiera bieżącą paletę formantu prętów zbrojeniowych.|
|[CReBarCtrl::GetRect](#getrect)|Pobiera prostokąt ograniczający dla danego pasma w formancie prętów zbrojeniowych.|
|[CReBarCtrl::GetRowCount](#getrowcount)|Pobiera liczbę wierszy pasma w formancie prętów zbrojeniowych.|
|[CReBarCtrl::GetRowHeight](#getrowheight)|Pobiera wysokość określonego wiersza w formancie prętów zbrojeniowych.|
|[CReBarCtrl::GetTextColor](#gettextcolor)|Pobiera domyślny kolor tekstu formantu prętów zbrojeniowych.|
|[CReBarCtrl::Porady dotyczące właściwości GetTool](#gettooltips)|Pobiera uchwyt do dowolnej kontrolki narzędzia skojarzonej z formantem prętów zbrojeniowych.|
|[CReBarCtrl::HitTest](#hittest)|Określa, która część pasma prętów zbrojeniowych znajduje się w danym punkcie na ekranie, jeśli w tym momencie istnieje pasmo prętów zbrojeniowych.|
|[CReBarCtrl::IDToIndex](#idtoindex)|Konwertuje identyfikator zespołu (ID) na indeks pasma w formancie prętów zbrojeniowych.|
|[CReBarCtrl::InsertBand](#insertband)|Wstawia nowy pas do zbrojeń.|
|[CReBarCtrl::MaximizeBand](#maximizeband)|Rozmiar pasma jest do największego rozmiaru.|
|[CReBarCtrl::Minimalizuj opaskę](#minimizeband)|Rozmiar pasma jest do najmniejszego rozmiaru.|
|[CReBarCtrl::MoveBand](#moveband)|Przenosi zespół z jednego indeksu do drugiego.|
|[CReBarCtrl::PushChevron](#pushchevron)|Programowo popycha szewron.|
|[CReBarCtrl::RestoreBand](#restoreband)|Rozmiar paska jest dopasowywać do idealnego rozmiaru.|
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Ustawia charakterystyki istniejącego pasma w formancie prętów zbrojeniowych.|
|[CReBarCtrl::SetBandWidth](#setbandwidth)|Ustawia szerokość określonego zadokowanego pasma w bieżącej formancie prętów zbrojeniowych.|
|[CReBarCtrl::SetBarInfo](#setbarinfo)|Ustawia właściwości zbrojenia.|
|[CReBarCtrl::SetBkColor](#setbkcolor)|Ustawia domyślny kolor tła formantu prętów zbrojeniowych.|
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Ustawia schemat kolorów przycisków na formancie prętów zbrojeniowych.|
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|Ustawia rozszerzone style dla bieżącej kontroli prętów zbrojeniowych.|
|[CReBarCtrl::SetImageList](#setimagelist)|Ustawia listę obrazów formantu prętów zbrojeniowych.|
|[CReBarCtrl::Właściciel zestawu](#setowner)|Ustawia okno właściciela formantu prętów zbrojeniowych.|
|[CReBarCtrl::SetPalette](#setpalette)|Ustawia bieżącą paletę formantu prętów zbrojeniowych.|
|[CReBarCtrl::SetTextColor](#settextcolor)|Ustawia domyślny kolor tekstu formantu prętów zbrojeniowych.|
|[CReBarCtrl::SetToolTips](#settooltips)|Kojarzy kontrolkę narzędzia z kontrolką prętów zbrojeniowych.|
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|Ustawia styl wizualny kontrolki prętów zbrojeniowych.|
|[CReBarCtrl::ShowBand](#showband)|Pokazuje lub ukrywa dany zespół w formancie prętów zbrojeniowych.|
|[CReBarCtrl::SizeToRect](#sizetorect)|Pasuje do formantu prętów zbrojeniowych do określonego prostokąta.|

## <a name="remarks"></a>Uwagi

Aplikacja, w której znajduje się formant prętów zbrojeniowych, przypisuje okno podrzędne zawarte przez formant prętów zbrojeniowych do pasma prętów zbrojeniowych. Okno podrzędne jest zwykle inny wspólny formant.

Elementy sterujące prętów zbrojeniowych zawierają co najmniej jedno pasma. Każdy zespół może zawierać kombinację paska chwytaka, mapy bitowej, etykiety tekstowej i okna podrzędnego. Zespół może zawierać tylko jeden z tych elementów.

Formant prętów zbrojeniowych może wyświetlać okno podrzędne na określonej mapie bitowej tła. Wszystkie pasma sterowania prętów zbrojeniowych można zwymiarować, z wyjątkiem tych, które używają stylu RBBS_FIXEDSIZE. Podczas zmiany położenia lub zmiany rozmiaru pasma sterującego prętów zbrojeniowych formant prętów zbrojeniowych zarządza rozmiarem i położeniem okna podrzędnego przypisanego do tego pasma. Aby zmienić rozmiar lub zmienić kolejność pasm w formancie, kliknij i przeciągnij pasek chwytaka zespołu.

Na poniższej ilustracji przedstawiono kontrolkę prętów zbrojeniowych, która ma trzy pasma:

- Pasmo 0 zawiera płaską, przezroczystą kontrolkę paska narzędzi.

- Pasmo 1 zawiera zarówno przezroczyste standardowe, jak i przezroczyste przyciski rozwijane.

- Band 2 zawiera pudełko kombi i cztery standardowe przyciski.

   ![Przykład menu prętów zbrojeniowych](../../mfc/reference/media/vc4scc1.gif "Przykład menu prętów zbrojeniowych")

## <a name="rebar-control"></a>Sterowanie prętami zbrojeniowym

Obsługa elementów sterujących prętów zbrojeniowych:

- Listy obrazów.

- Obsługa wiadomości.

- Niestandardowa funkcja rysowania.

- Oprócz standardowych stylów okien, oprócz standardowych stylów okiennych. Aby uzyskać listę tych stylów, zobacz [Style sterowania prętami zbrojenia](/windows/win32/Controls/rebar-control-styles) w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [Korzystanie z CReBarCtrl](../../mfc/using-crebarctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="crebarctrlbegindrag"></a><a name="begindrag"></a>CReBarCtrl::BeginDrag

Implementuje zachowanie [RB_BEGINDRAG](/windows/win32/Controls/rb-begindrag)komunikatu Win32, zgodnie z opisem w windows SDK.

```cpp
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parametry

*uBand (opaska)*<br/>
Indeks oparty na wartości zerowej pasma, na który wpłynie operacja przeciągania i upuszczania.

*dwPos (właśc.*<br/>
Wartość DWORD zawierająca początkowe współrzędne myszy. Współrzędna pozioma znajduje się w LOWORD, a współrzędna pionowa jest zawarta w HIWORD. Jeśli przejdziesz (DWORD)-1, zbrojeń użyje położenia myszy przy ostatnim `GetMessage` `PeekMessage`wywołaniu wątku formantu lub .

## <a name="crebarctrlcreate"></a><a name="create"></a>CReBarCtrl::Utwórz

Tworzy formant prętów zbrojeniowych i dołącza go do `CReBarCtrl` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa kombinację stylów sterowania prętami zbrojeniowymi zastosowanych do formantu. Aby uzyskać listę obsługiwanych stylów, zobacz [Style sterowania prętami zbrojenia](/windows/win32/Controls/rebar-control-styles) w zestawie Windows SDK.

*Rect*<br/>
Odwołanie do obiektu [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [RECT](/windows/win32/api/windef/ns-windef-rect) struktury, która jest położenie i rozmiar formantu prętów zbrojeniowych.

*pParentWnd*<br/>
Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu, który jest nadrzędnym oknem zbrojenia. Nie może być null.

*Nid*<br/>
Określa identyfikator formantu prętów zbrojeniowych.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Tworzenie kontrolki prętów zbrojeniowych w dwóch etapach:

1. Wywołanie [CReBarCtrl](#crebarctrl) `CReBarCtrl` do konstruowania obiektu.

1. Wywołanie tej funkcji elementu członkowskiego, która tworzy formant `CReBarCtrl` zbrojenia systemu Windows i dołącza go do obiektu.

Podczas wywoływania `Create`typowe formanty są inicjowane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

## <a name="crebarctrlcreateex"></a><a name="createex"></a>CReBarCtrl::CreateEx

Tworzy formant (okno podrzędne) i `CReBarCtrl` kojarzy go z obiektem.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwexstyle*<br/>
Określa rozszerzony styl tworzonego formantu. Aby uzyskać listę rozszerzonych stylów systemu Windows, zobacz parametr *dwExStyle* dla [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) w zestawie Windows SDK.

*Dwstyle*<br/>
Określa kombinację stylów sterowania prętami zbrojeniowymi zastosowanych do formantu. Aby uzyskać listę obsługiwanych stylów, zobacz [Style sterowania prętami zbrojenia](/windows/win32/Controls/rebar-control-styles) w zestawie Windows SDK.

*Rect*<br/>
Odwołanie do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest nadrzędnym formantu.

*Nid*<br/>
Identyfikator okna podrzędnego formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [Create,](#create) aby zastosować rozszerzone style systemu Windows, określone przez przedmową styl rozszerzony systemu Windows **WS_EX_**.

## <a name="crebarctrlcrebarctrl"></a><a name="crebarctrl"></a>CReBarCtrl::CReBarCtrl

Tworzy obiekt `CReBarCtrl`.

```
CReBarCtrl();
```

### <a name="example"></a>Przykład

  Zobacz przykład [CReBarCtrl::Create](#create).

## <a name="crebarctrldeleteband"></a><a name="deleteband"></a>CReBarCtrl::DeleteBand

Implementuje zachowanie [RB_DELETEBAND](/windows/win32/Controls/rb-deleteband)komunikatu Win32, zgodnie z opisem w windows SDK.

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uBand (opaska)*<br/>
Indeks od zera pasma do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli zespół został usunięty pomyślnie; w przeciwnym razie zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

## <a name="crebarctrldragmove"></a><a name="dragmove"></a>CReBarCtrl::DragMove

Implementuje zachowanie [RB_DRAGMOVE](/windows/win32/Controls/rb-dragmove)komunikatu Win32, zgodnie z opisem w windows SDK.

```cpp
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parametry

*dwPos (właśc.*<br/>
Wartość DWORD zawierająca nowe współrzędne myszy. Współrzędna pozioma znajduje się w LOWORD, a współrzędna pionowa jest zawarta w HIWORD. Jeśli przejdziesz (DWORD)-1, zbrojeń użyje położenia myszy przy ostatnim `GetMessage` `PeekMessage`wywołaniu wątku formantu lub .

## <a name="crebarctrlenddrag"></a><a name="enddrag"></a>CReBarCtrl::EndDrag

Implementuje zachowanie [RB_ENDDRAG](/windows/win32/Controls/rb-enddrag)komunikatu Win32, zgodnie z opisem w windows SDK.

```cpp
void EndDrag();
```

## <a name="crebarctrlgetbandborders"></a><a name="getbandborders"></a>CReBarCtrl::GetBandBorders

Implementuje zachowanie [RB_GETBANDBORDERS](/windows/win32/Controls/rb-getbandborders)komunikatu Win32, zgodnie z opisem w windows SDK.

```cpp
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parametry

*uBand (opaska)*<br/>
Indeks od zera pasma, dla którego zostaną pobrane obramowania.

*Chrl*<br/>
Wskaźnik do struktury [RECT,](/windows/win32/api/windef/ns-windef-rect) która otrzyma obramowania pasma. Jeśli formant prętów zbrojeniowych ma styl RBS_BANDBORDERS, każdy element członkowski tej struktury otrzyma liczbę pikseli po odpowiedniej stronie pasma, które stanowią obramowanie. Jeśli formant prętów zbrojeniowych nie ma stylu RBS_BANDBORDERS, tylko lewy element członkowski tej struktury otrzymuje prawidłowe informacje. Aby uzyskać opis stylów kontroli prętów zbrojeniowych, zobacz [Style sterowania prętami zbrojenia](/windows/win32/Controls/rebar-control-styles) w zestaw Windows SDK.

## <a name="crebarctrlgetbandcount"></a><a name="getbandcount"></a>CReBarCtrl::GetBandCount

Implementuje zachowanie [RB_GETBANDCOUNT](/windows/win32/Controls/rb-getbandcount)komunikatu Win32, zgodnie z opisem w windows SDK.

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba pasm przypisanych do formantu.

## <a name="crebarctrlgetbandinfo"></a><a name="getbandinfo"></a>CReBarCtrl::GetBandInfo

Implementuje zachowanie komunikatu Win32 [RB_GETBANDINFO](/windows/win32/Controls/rb-getbandinfo) zgodnie z opisem w windows SDK.

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>Parametry

*uBand (opaska)*<br/>
Indeks od zera w paśmie, dla którego zostaną pobrane informacje.

*prbbi ( prbbi )*<br/>
Wskaźnik do struktury [REBARBANDINFO,](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) aby otrzymać informacje o paśmie. Należy ustawić `cbSize` element członkowski `sizeof(REBARBANDINFO)` tej struktury `fMask` i ustawić element członkowski do elementów, które mają zostać pobrane przed wysłaniem tej wiadomości.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

## <a name="crebarctrlgetbandmargins"></a><a name="getbandmargins"></a>CReBarCtrl::GetBandMargins

Pobiera marginesy pasma.

```cpp
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>Parametry

*pMargins*<br/>
Wskaźnik do [struktury MARGINESY,](/windows/win32/api/uxtheme/ns-uxtheme-margins)który otrzyma informacje.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego emuluje funkcjonalność [komunikatu RB_GETBANDMARGINS,](/windows/win32/Controls/rb-getbandmargins) zgodnie z opisem w windows SDK.

## <a name="crebarctrlgetbarheight"></a><a name="getbarheight"></a>CReBarCtrl::GetBarHeight

Pobiera wysokość pręta zbrojeniowego.

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość reprezentująca wysokość( w pikselach) formantu.

## <a name="crebarctrlgetbarinfo"></a><a name="getbarinfo"></a>CReBarCtrl::GetBarInfo

Implementuje zachowanie [RB_GETBARINFO](/windows/win32/Controls/rb-getbarinfo)komunikatu Win32, zgodnie z opisem w windows SDK.

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>Parametry

*prbi*<br/>
Wskaźnik do struktury [REBARINFO,](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) który otrzyma informacje o stercie prętów zbrojeniowych. Przed wysłaniem *cbSize* tej wiadomości należy ustawić `sizeof(REBARINFO)` element członkowski rozmiaru tej struktury.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

## <a name="crebarctrlgetbkcolor"></a><a name="getbkcolor"></a>CReBarCtrl::GetBkColor

Implementuje zachowanie [RB_GETBKCOLOR](/windows/win32/Controls/rb-getbkcolor)komunikatu Win32, zgodnie z opisem w windows SDK.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość COLORREF reprezentująca bieżący domyślny kolor tła.

## <a name="crebarctrlgetcolorscheme"></a><a name="getcolorscheme"></a>CReBarCtrl::GetColorScheme

Pobiera [strukturę COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) dla kontroli prętów zbrojeniowych.

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parametry

*szt.*<br/>
Wskaźnik do struktury [COLORSCHEME,](/windows/win32/api/commctrl/ns-commctrl-colorscheme) zgodnie z opisem w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Struktura `COLORSCHEME` zawiera kolor podświetlenia przycisku i kolor cienia przycisku.

## <a name="crebarctrlgetdroptarget"></a><a name="getdroptarget"></a>CReBarCtrl::GetDropTarget

Implementuje zachowanie [RB_GETDROPTARGET](/windows/win32/Controls/rb-getdroptarget)komunikatu Win32, zgodnie z opisem w windows SDK.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu [IDropTarget.](/windows/win32/api/oleidl/nn-oleidl-idroptarget)

## <a name="crebarctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CReBarCtrl::GetExtendedStyle

Pobiera rozszerzone style bieżącej kontroli prętów zbrojeniowych.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Bitowe połączenie (OR) flag, które wskazują style rozszerzone. Możliwe flagi są RBS_EX_SPLITTER i RBS_EX_TRANSPARENT. Aby uzyskać więcej informacji, zobacz *dwMask* parametr [CReBarCtrl::SetExtendedStyle](#setextendedstyle) metody.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [RB_GETEXTENDEDSTYLE,](/windows/win32/Controls/rb-dragmove) który jest opisany w windows SDK.

## <a name="crebarctrlgetimagelist"></a><a name="getimagelist"></a>CReBarCtrl::Lista GetImage

Pobiera `CImageList` obiekt skojarzony z formantem prętów zbrojeniowych.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CImageList.](../../mfc/reference/cimagelist-class.md) Zwraca wartość NULL, jeśli dla formantu nie ustawiono żadnej listy obrazów.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego używa informacji o rozmiarze i masce przechowywanych w strukturze [REBARINFO,](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) zgodnie z opisem w programie Windows SDK.

## <a name="crebarctrlgetpalette"></a><a name="getpalette"></a>CReBarCtrl::GetPalette

Pobiera bieżącą paletę formantu prętów zbrojeniowych.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CPalette](../../mfc/reference/cpalette-class.md) określający bieżącą paletę formantu prętów zbrojeniowych.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że ta `CPalette` funkcja elementu członkowskiego używa obiektu jako jego wartości zwracanej, a nie HPALETTE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

## <a name="crebarctrlgetrect"></a><a name="getrect"></a>CReBarCtrl::GetRect

Implementuje zachowanie [RB_GETRECT](/windows/win32/Controls/rb-getrect)komunikatu Win32, zgodnie z opisem w windows SDK.

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parametry

*uBand (opaska)*<br/>
Indeks od zera pasma w formancie prętów zbrojeniowych.

*Chrl*<br/>
Wskaźnik do struktury [RECT,](/windows/win32/api/windef/ns-windef-rect) która otrzyma granice pasma prętów zbrojeniowych.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

## <a name="crebarctrlgetrowcount"></a><a name="getrowcount"></a>CReBarCtrl::GetRowCount

Implementuje zachowanie [RB_GETROWCOUNT](/windows/win32/Controls/rb-getrowcount)komunikatu Win32, zgodnie z opisem w windows SDK.

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość UINT, która reprezentuje liczbę wierszy pasma w formancie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

## <a name="crebarctrlgetrowheight"></a><a name="getrowheight"></a>CReBarCtrl::GetRowHeight

Implementuje zachowanie [RB_GETROWHEIGHT](/windows/win32/Controls/rb-getrowheight)komunikatu Win32, zgodnie z opisem w windows SDK.

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>Parametry

*uRow (polski)*<br/>
Indeks oparty na wartości zerowej pasma, który będzie miał swoją wysokość pobieraną.

### <a name="return-value"></a>Wartość zwracana

Wartość UINT reprezentująca wysokość wiersza w pikselach.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

## <a name="crebarctrlgettextcolor"></a><a name="gettextcolor"></a>CReBarCtrl::GetTextColor

Implementuje zachowanie [RB_GETTEXTCOLOR](/windows/win32/Controls/rb-gettextcolor)komunikatu Win32, zgodnie z opisem w windows SDK.

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość COLORREF reprezentująca bieżący domyślny kolor tekstu.

## <a name="crebarctrlgettooltips"></a><a name="gettooltips"></a>CReBarCtrl::Porady dotyczące właściwości GetTool

Implementuje zachowanie [RB_GETTOOLTIPS](/windows/win32/Controls/rb-gettooltips)komunikatu Win32, zgodnie z opisem w windows SDK.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CToolTipCtrl.](../../mfc/reference/ctooltipctrl-class.md)

### <a name="remarks"></a>Uwagi

Należy zauważyć, że `GetToolTips` implementacja MFC `CToolTipCtrl`zwraca wskaźnik do , a nie HWND.

## <a name="crebarctrlhittest"></a><a name="hittest"></a>CReBarCtrl::HitTest

Implementuje zachowanie [RB_HITTEST](/windows/win32/Controls/rb-hittest)komunikatu Win32, zgodnie z opisem w windows SDK.

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>Parametry

*prbht ( prbht )*<br/>
Wskaźnik do struktury [RBHITTESTINFO.](/windows/win32/api/commctrl/ns-commctrl-rbhittestinfo) Przed wysłaniem wiadomości `pt` element członkowski tej struktury musi zostać zainicjowany do punktu, który zostanie przetestowany, we współrzędnych klienta.

### <a name="return-value"></a>Wartość zwracana

Indeks od zera pasma w danym punkcie lub -1, jeśli w punkcie nie było pasma prętów zbrojeniowych.

## <a name="crebarctrlidtoindex"></a><a name="idtoindex"></a>CReBarCtrl::IDToIndex

Implementuje zachowanie [RB_IDTOINDEX](/windows/win32/controls/rb-idtoindex)komunikatu Win32, zgodnie z opisem w windows SDK.

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>Parametry

*uBandID (ida)*<br/>
Zdefiniowany przez aplikację identyfikator określonego pasma, `wID` przekazany w części członkowskiej struktury [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) po wstawieniu pasma.

### <a name="return-value"></a>Wartość zwracana

Indeks pasma opartego na wartości zerowej, jeśli zakończy się pomyślnie, lub -1 w przeciwnym razie. Jeśli istnieją zduplikowane indeksy pasm, zwracany jest pierwszy z nich.

## <a name="crebarctrlinsertband"></a><a name="insertband"></a>CReBarCtrl::InsertBand

Implementuje zachowanie [RB_INSERTBAND](/windows/win32/Controls/rb-insertband)komunikatu Win32, zgodnie z opisem w windows SDK.

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parametry

*uIndex*<br/>
Indeks od zera lokalizacji, w której zostanie wstawiony pasmo. Jeśli ustawisz ten parametr na -1, formant doda nowy zespół w ostatniej lokalizacji.

*prbbi ( prbbi )*<br/>
Wskaźnik do struktury [REBARBANDINFO,](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) która definiuje zespół, który ma zostać wstawiony. Należy ustawić *element członkowski rozmiaru* tej `sizeof(REBARBANDINFO)` struktury przed wywołaniem tej funkcji.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

## <a name="crebarctrlmaximizeband"></a><a name="maximizeband"></a>CReBarCtrl::MaximizeBand

Rozmiar pasma jest do największego rozmiaru.

```cpp
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uBand (opaska)*<br/>
Indeks od zera pasma, który ma zostać zmaksymalizowany.

### <a name="remarks"></a>Uwagi

Implementuje zachowanie komunikatu Win32 [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) z `fIdeal` ustawioną na 0, zgodnie z opisem w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

## <a name="crebarctrlminimizeband"></a><a name="minimizeband"></a>CReBarCtrl::Minimalizuj opaskę

Rozmiar pasma jest do najmniejszego rozmiaru.

```cpp
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uBand (opaska)*<br/>
Indeks od zera pasma do zminimalizowania.

### <a name="remarks"></a>Uwagi

Implementuje zachowanie [RB_MINIMIZEBAND](/windows/win32/Controls/rb-minimizeband)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

## <a name="crebarctrlmoveband"></a><a name="moveband"></a>CReBarCtrl::MoveBand

Implementuje zachowanie [RB_MOVEBAND](/windows/win32/Controls/rb-moveband)komunikatu Win32, zgodnie z opisem w windows SDK.

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>Parametry

*uOd*<br/>
Indeks od zera pasma, który ma zostać przeniesiony.

*Uto*<br/>
Indeks zerowy nowej pozycji pasma. Ta wartość parametru nigdy nie może być większa niż liczba pasm minus jeden. Aby uzyskać liczbę pasm, zadzwoń [do GetBandCount](#getbandcount).

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

## <a name="crebarctrlpushchevron"></a><a name="pushchevron"></a>CReBarCtrl::PushChevron

Implementuje zachowanie [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)komunikatu Win32, zgodnie z opisem w windows SDK.

```cpp
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>Parametry

*uBand (opaska)*<br/>
Indeks oparty na wartości zerowej pasma, którego szewron ma zostać wypchnięty.

*lAppValue*<br/>
Aplikacja zdefiniowała wartość 32-bitową. Zobacz *lAppValue* w [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron) w windows SDK.

## <a name="crebarctrlrestoreband"></a><a name="restoreband"></a>CReBarCtrl::RestoreBand

Rozmiar paska jest dopasowywać do idealnego rozmiaru.

```cpp
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>Parametry

*uBand (opaska)*<br/>
Indeks od zera pasma, który ma zostać zmaksymalizowany.

### <a name="remarks"></a>Uwagi

Implementuje zachowanie komunikatu Win32 [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) z `fIdeal` ustawioną na 1, zgodnie z opisem w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

## <a name="crebarctrlsetbandinfo"></a><a name="setbandinfo"></a>CReBarCtrl::SetBandInfo

Implementuje zachowanie [RB_SETBANDINFO](/windows/win32/Controls/rb-setbandinfo)komunikatu Win32, zgodnie z opisem w windows SDK.

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parametry

*uBand (opaska)*<br/>
Indeks od zera w paśmie, aby otrzymać nowe ustawienia.

*prbbi ( prbbi )*<br/>
Wskaźnik do struktury [REBARBANDINFO,](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) która definiuje zespół, który ma zostać wstawiony. Należy ustawić `cbSize` element członkowski `sizeof(REBARBANDINFO)` tej struktury przed wysłaniem tej wiadomości.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

## <a name="crebarctrlsetbandwidth"></a><a name="setbandwidth"></a>CReBarCtrl::SetBandWidth

Ustawia szerokość określonego zadokowanego pasma w bieżącej formancie prętów zbrojeniowych.

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*uBand (opaska)*|[w] Indeks zerowy pasma prętów zbrojeniowych.|
|*cxWidth ( cxWidth )*|[w] Nowa szerokość paska prętów zbrojeniowych w pikselach.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [RB_SETBANDWIDTH,](/windows/win32/Controls/rb-setbandwidth) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_rebar`zmienną , która jest używana do uzyskania dostępu do bieżącego formantu prętów zbrojeniowych. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia każdy pas zbrojenia ma taką samą szerokość.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

## <a name="crebarctrlsetbarinfo"></a><a name="setbarinfo"></a>CReBarCtrl::SetBarInfo

Implementuje zachowanie [RB_SETBARINFO](/windows/win32/Controls/rb-setbarinfo)komunikatu Win32, zgodnie z opisem w sdk systemu Windows.

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>Parametry

*prbi*<br/>
Wskaźnik do struktury [REBARINFO,](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) który zawiera informacje, które mają być ustawione. Należy ustawić `cbSize` element członkowski `sizeof(REBARINFO)` tej struktury przed wysłaniem tej wiadomości

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

## <a name="crebarctrlsetbkcolor"></a><a name="setbkcolor"></a>CReBarCtrl::SetBkColor

Implementuje zachowanie [RB_SETBKCOLOR](/windows/win32/Controls/rb-setbkcolor)komunikatu Win32, zgodnie z opisem w windows SDK.

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*Clr*<br/>
Wartość COLORREF reprezentująca nowy domyślny kolor tła.

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) reprezentująca poprzedni domyślny kolor tła.

### <a name="remarks"></a>Uwagi

Zobacz ten temat, aby uzyskać więcej informacji o tym, kiedy ustawić kolor tła i jak ustawić wartość domyślną.

## <a name="crebarctrlsetcolorscheme"></a><a name="setcolorscheme"></a>CReBarCtrl::SetColorScheme

Ustawia schemat kolorów przycisków na formancie prętów zbrojeniowych.

```cpp
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parametry

*szt.*<br/>
Wskaźnik do struktury [COLORSCHEME,](/windows/win32/api/commctrl/ns-commctrl-colorscheme) zgodnie z opisem w windows SDK.

### <a name="remarks"></a>Uwagi

Struktura `COLORSCHEME` zawiera zarówno kolor podświetlenia przycisku, jak i kolor cienia przycisku.

## <a name="crebarctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CReBarCtrl::SetExtendedStyle

Ustawia rozszerzone style dla bieżącej kontroli prętów zbrojeniowych.

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Dwmask*|[w] Bitowe połączenie (OR) flag, które określają, które flagi w *dwStyleEx* parametru stosuje. Użyj co najmniej jednej z następujących wartości:<br /><br /> RBS_EX_SPLITTER: Domyślnie pokaż rozdzielacz na dole w trybie poziomym i w prawo w trybie pionowym.<br /><br /> RBS_EX_TRANSPARENT: Prześlij dalej wiadomość [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) do okna nadrzędnego.|
|*dwStyleEx (np.*|[w] Bitowa kombinacja (OR) flag określających style do zastosowania. Aby ustawić styl, należy określić tę samą flagę, która jest używana w parametrze *dwMask.* Aby zresetować styl, należy określić zero binarne.|

### <a name="return-value"></a>Wartość zwracana

Poprzedni styl rozszerzony.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [RB_SETEXTENDEDSTYLE,](/windows/win32/Controls/rb-setextendedstyle) który jest opisany w windows SDK.

## <a name="crebarctrlsetimagelist"></a><a name="setimagelist"></a>CReBarCtrl::SetImageList

Przypisuje listę obrazów do kontrolki prętów zbrojeniowych.

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList (Lista pImage)*<br/>
Wskaźnik do [obiektu CImageList](../../mfc/reference/cimagelist-class.md) zawierającego listę obrazów, który ma być przypisany do formantu prętów zbrojeniowych.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

## <a name="crebarctrlsetowner"></a><a name="setowner"></a>CReBarCtrl::Właściciel zestawu

Implementuje zachowanie [RB_SETPARENT](/windows/win32/Controls/rb-setparent)komunikatu Win32, zgodnie z opisem w windows SDK.

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do `CWnd` obiektu, aby ustawić jako właściciel formantu prętów zbrojeniowych.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu, który jest bieżącym właścicielem formantu prętów zbrojeniowych.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że ta funkcja `CWnd` elementu członkowskiego używa wskaźników do obiektów dla bieżącego i wybranego właściciela formantu prętów zbrojeniowych, a nie uchwytów do okien.

> [!NOTE]
> Ta funkcja elementu członkowskiego nie zmienia rzeczywistego elementu nadrzędnego, który został ustawiony podczas tworzenia formantu; raczej wysyła komunikaty powiadomień do określonego okna.

## <a name="crebarctrlsetpalette"></a><a name="setpalette"></a>CReBarCtrl::SetPalette

Implementuje zachowanie [RB_SETPALETTE](/windows/win32/Controls/rb-setpalette)komunikatu Win32, zgodnie z opisem w windows SDK.

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>Parametry

*hPal (właso)*<br/>
HPALETTE, który określa nową paletę, że formant prętów zbrojeniowych będzie używany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CPalette](../../mfc/reference/cpalette-class.md) określający poprzednią paletę formantu prętów zbrojeniowych.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że ta `CPalette` funkcja elementu członkowskiego używa obiektu jako jego wartości zwracanej, a nie HPALETTE.

## <a name="crebarctrlsettextcolor"></a><a name="settextcolor"></a>CReBarCtrl::SetTextColor

Implementuje zachowanie [RB_SETTEXTCOLOR](/windows/win32/Controls/rb-settextcolor)komunikatu Win32, zgodnie z opisem w windows SDK.

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*Clr*<br/>
Wartość COLORREF reprezentująca nowy kolor `CReBarCtrl` tekstu w obiekcie.

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) reprezentująca poprzedni kolor tekstu `CReBarCtrl` skojarzony z obiektem.

### <a name="remarks"></a>Uwagi

Jest on dostarczany do obsługi elastyczności kolorów tekstu w kontroli prętów zbrojeniowych.

## <a name="crebarctrlsettooltips"></a><a name="settooltips"></a>CReBarCtrl::SetToolTips

Kojarzy kontrolkę narzędzia z kontrolką prętów zbrojeniowych.

```cpp
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>Parametry

*pToolTip (etykietka pToolTip)*<br/>
Wskaźnik do [obiektu CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

### <a name="remarks"></a>Uwagi

Musisz zniszczyć `CToolTipCtrl` obiekt, gdy skończysz z nim.

## <a name="crebarctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CReBarCtrl::SetWindowTheme

Ustawia styl wizualny kontrolki prętów zbrojeniowych.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parametry

*pszSubAppName*<br/>
Wskaźnik do ciągu Unicode, który zawiera styl wizualny prętów zbrojeniowych do ustawionego.

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość nie jest używana.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego emuluje funkcjonalność [komunikatu RB_SETWINDOWTHEME,](/windows/win32/Controls/rb-setwindowtheme) zgodnie z opisem w windows SDK.

## <a name="crebarctrlshowband"></a><a name="showband"></a>CReBarCtrl::ShowBand

Implementuje zachowanie [RB_SHOWBAND](/windows/win32/Controls/rb-showband)komunikatu Win32, zgodnie z opisem w windows SDK.

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>Parametry

*uBand (opaska)*<br/>
Indeks od zera pasma w formancie prętów zbrojeniowych.

*fPokaż*<br/>
Wskazuje, czy opaska powinna być wyświetlana czy ukryta. Jeśli ta wartość ma wartość PRAWDA, zostanie wyświetlony pasek. W przeciwnym razie zespół zostanie ukryty.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

## <a name="crebarctrlsizetorect"></a><a name="sizetorect"></a>CReBarCtrl::SizeToRect

Implementuje zachowanie [RB_SIZETORECT](/windows/win32/Controls/rb-sizetorect)komunikatu Win32, zgodnie z opisem w windows SDK.

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu, który określa prostokąt, który ma być dopasowywać formant prętów zbrojeniowych.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że ta `CRect` funkcja elementu członkowskiego używa `RECT` obiektu jako parametru, a nie struktury.

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
