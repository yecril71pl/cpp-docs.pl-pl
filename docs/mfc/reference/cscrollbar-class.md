---
title: Klasa CScrollBar
ms.date: 11/04/2016
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
helpviewer_keywords:
- CScrollBar [MFC], CScrollBar
- CScrollBar [MFC], Create
- CScrollBar [MFC], EnableScrollBar
- CScrollBar [MFC], GetScrollBarInfo
- CScrollBar [MFC], GetScrollInfo
- CScrollBar [MFC], GetScrollLimit
- CScrollBar [MFC], GetScrollPos
- CScrollBar [MFC], GetScrollRange
- CScrollBar [MFC], SetScrollInfo
- CScrollBar [MFC], SetScrollPos
- CScrollBar [MFC], SetScrollRange
- CScrollBar [MFC], ShowScrollBar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
ms.openlocfilehash: 3b8e7dc78ddfa22097c97fb4e97fff92f0984c07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571265"
---
# <a name="cscrollbar-class"></a>Klasa CScrollBar

Oferuje funkcje formantu paska przewijania Windows.

## <a name="syntax"></a>Składnia

```
class CScrollBar : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CScrollBar::CScrollBar](#cscrollbar)|Konstruuje `CScrollBar` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CScrollBar::Create](#create)|Tworzy pasek przewijania Windows i dołącza je do `CScrollBar` obiektu.|
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Włącza lub wyłącza jeden lub oba strzałek przewijania na pasku przewijania.|
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Pobiera informacje o paska przewijania, za pomocą `SCROLLBARINFO` struktury.|
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Pobiera informacje o paska przewijania.|
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Pobiera limit paska przewijania|
|[CScrollBar::GetScrollPos](#getscrollpos)|Pobiera bieżące położenie suwaka.|
|[CScrollBar::GetScrollRange](#getscrollrange)|Pobiera dla paska przewijania danego bieżącej pozycji minimalne i maksymalne paska przewijania.|
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Ustawia informacje o paska przewijania.|
|[CScrollBar::SetScrollPos](#setscrollpos)|Ustawia bieżącej pozycji suwaka.|
|[CScrollBar::SetScrollRange](#setscrollrange)|Ustawia położenie minimalne i maksymalne wartości dla paska przewijania danego.|
|[CScrollBar::ShowScrollBar](#showscrollbar)|Pokazuje lub ukrywa pasek przewijania.|

## <a name="remarks"></a>Uwagi

Utworzysz formantu paska przewijania w dwóch krokach. Po pierwsze wywołanie konstruktora `CScrollBar` do konstruowania `CScrollBar` obiektu, a następnie wywołaj [Utwórz](#create) funkcja elementu członkowskiego, aby utworzyć formantu paska przewijania Windows i dołączyć go do `CScrollBar` obiektu.

Jeśli tworzysz `CScrollBar` obiektu w oknie dialogowym (za pośrednictwem zasobu okna dialogowego), `CScrollBar` automatycznie jest niszczony, kiedy użytkownik zamknie okno dialogowe.

Jeśli tworzysz `CScrollBar` obiekt w tym oknie, konieczne może zniszczyć ją.

Jeśli tworzysz `CScrollBar` obiektów na stosie, zostanie zniszczony automatycznie. Jeśli tworzysz `CScrollBar` obiektów na stosie przy użyciu **nowe** funkcji, należy wywołać **Usuń** obiektu zniszczyć ją, gdy użytkownik kończy Windows paska przewijania.

Jeśli przydzielisz wszystkie pamięci w `CScrollBar` obiektów, Zastąp `CScrollBar` destruktora w celu usunięcia alokacje.

Aby uzyskać powiązane informacje o używaniu `CScrollBar`, zobacz [formantów](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="create"></a>  CScrollBar::Create

Tworzy pasek przewijania Windows i dołącza je do `CScrollBar` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa przewijania styl paska. Zastosuj dowolną kombinację [Style paska przewijania](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) paska przewijania.

*Rect*<br/>
Określa rozmiar paska przewijania i pozycji. Może być `RECT` struktury lub `CRect` obiektu.

*pParentWnd*<br/>
Określa przewijania okno nadrzędne paska, zwykle `CDialog` obiektu. Nie może być równa NULL.

*nID*<br/>
Identyfikator formantu paska przewijania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CScrollBar` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora, który tworzy `CScrollBar` obiektu; następnie wywołać `Create`, który tworzy i inicjuje skojarzone paska przewijania Windows i dołącza go do `CScrollBar` obiektu.

Zastosuj następujące [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) pasek przewijania:

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_GROUP kontrolek grupy

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

##  <a name="cscrollbar"></a>  CScrollBar::CScrollBar

Konstruuje `CScrollBar` obiektu.

```
CScrollBar();
```

### <a name="remarks"></a>Uwagi

Po konstruowanie obiektu, wywołaj `Create` funkcja elementu członkowskiego, aby utworzyć i zainicjować Windows paska przewijania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

##  <a name="enablescrollbar"></a>  CScrollBar::EnableScrollBar

Włącza lub wyłącza jeden lub oba strzałek przewijania na pasku przewijania.

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>Parametry

*nArrowFlags*<br/>
Określa, czy włączać lub wyłączać strzałki przewijania i strzałek, które są włączone lub wyłączone. Ten parametr może być jedną z następujących wartości:

- ESB_ENABLE_BOTH umożliwia zarówno strzałek przewijania na pasku przewijania.

- ESB_DISABLE_LTUP wyłącza pasek przewijania poziomego strzałkę w lewo lub strzałki w górę pionowy pasek przewijania.

- ESB_DISABLE_RTDN wyłącza strzałkę poziomy pasek przewijania w prawo lub strzałkę w dół na pionowy pasek przewijania.

- ESB_DISABLE_BOTH wyłącza zarówno strzałek przewijania na pasku przewijania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli włączone lub wyłączone określonych; strzałki w przeciwnym razie 0, co oznacza, że strzałki znajdują się już w żądany stan lub wystąpił błąd.

### <a name="example"></a>Przykład

  Zobacz przykład [CScrollBar::SetScrollRange](#setscrollrange).

##  <a name="getscrollbarinfo"></a>  CScrollBar::GetScrollBarInfo

Pobiera informacje o który `SCROLLBARINFO` struktury przechowuje informacje paska przewijania.

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>Parametry

*pScrollInfo*<br/>
Wskaźnik do [SCROLLBARINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollbarinfo) struktury.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność [SBM_SCROLLBARINFO](/windows/desktop/Controls/sbm-getscrollbarinfo) komunikat, zgodnie z opisem w zestawie Windows SDK.

##  <a name="getscrollinfo"></a>  CScrollBar::GetScrollInfo

Pobiera informacje o który `SCROLLINFO` struktury przechowuje informacje paska przewijania.

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>Parametry

*lpScrollInfo*<br/>
Wskaźnik do [SCROLLINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollinfo) struktury. Zobacz zestaw SDK Windows, aby uzyskać więcej informacji na temat tej struktury.

*nMask*<br/>
Określa parametry paska przewijania, do pobrania. Typowy SIF_ALL, określa kombinację SIF_PAGE, SIF_POS, SIF_TRACKPOS i SIF_RANGE. Zobacz `SCROLLINFO` więcej informacji na temat wartości nMask.

### <a name="return-value"></a>Wartość zwracana

W przypadku komunikatu pobrania wszelkie wartości, zwracany jest TRUE. W przeciwnym razie ma wartość FAŁSZ.

### <a name="remarks"></a>Uwagi

`GetScrollInfo` Umożliwia aplikacjom używanie pozycji przewijania 32-bitowych.

[SCROLLINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollinfo) struktura zawiera informacje dotyczące paska, w tym minimalne i maksymalne przewijanie położenia, rozmiaru strony i położenie suwaka (thumb) przewijania. Zobacz `SCROLLINFO` struktury tematu w zestawie SDK Windows, aby uzyskać więcej informacji na temat zmiany ustawień domyślnych struktury.

Windows MFC komunikatu programów obsługi, które wskazują na położenie paska przewijania, [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), podaj tylko 16 bitów danych position. `GetScrollInfo` i `SetScrollInfo` zapewniają 32 bity danych position — pasek przewijania. W związku z tym, aplikacja może wywołać `GetScrollInfo` podczas przetwarzania albo `CWnd::OnHScroll` lub `CWnd::OnVScroll` do uzyskania danych położenie paska przewijania 32-bitowych.

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="getscrolllimit"></a>  CScrollBar::GetScrollLimit

Pobiera maksymalną przewijanie pozycja paska przewijania.

```
int GetScrollLimit();
```

### <a name="return-value"></a>Wartość zwracana

Określa maksymalną położenie paska przewijania, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="getscrollpos"></a>  CScrollBar::GetScrollPos

Pobiera bieżące położenie suwaka.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Wartość zwracana

Określa bieżące położenie paska przewijania, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Bieżące położenie jest względna wartość, która jest zależna od bieżącego zakresu przewijania. Na przykład jeśli pole przewijania jest w trakcie pasek przewijania zakres wynosi 100, 200, bieżące położenie jest 150.

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="getscrollrange"></a>  CScrollBar::GetScrollRange

Kopiuje bieżącego położenia minimalne i maksymalne paska przewijania dla paska przewijania danego do lokalizacji określonej przez *lpMinPos* i *lpMaxPos*.

```
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>Parametry

*lpMinPos*<br/>
Wskazuje zmienną całkowitą, który ma otrzymać minimalne pozycji.

*lpMaxPos*<br/>
Wskazuje zmienną całkowitą, który ma otrzymać maksymalna pozycji.

### <a name="remarks"></a>Uwagi

Domyślny zakres dla formantu paska przewijania jest pusty (obie wartości są 0).

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="setscrollinfo"></a>  CScrollBar::SetScrollInfo

Ustawia informacje o `SCROLLINFO` struktury przechowuje informacje paska przewijania.

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*lpScrollInfo*<br/>
Wskaźnik do [SCROLLINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollinfo) struktury.

*bRedraw*<br/>
Określa, czy pasek przewijania powinien być narysowany ponownie, aby odzwierciedlić nowe informacje. Jeśli *bRedraw* ma wartość TRUE, jest odświeżana, pasek przewijania. Jeśli jest to wartość FALSE, nie jest narysowany na ponownie. Pasek przewijania jest odświeżana, domyślnie.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwracana jest wartość TRUE. W przeciwnym razie ma wartość FAŁSZ.

### <a name="remarks"></a>Uwagi

Należy podać wartości wymagane przez `SCROLLINFO` struktury parametrów, w tym wartości flag.

`SCROLLINFO` Struktura zawiera informacje dotyczące paska, w tym minimalne i maksymalne przewijanie położenia, rozmiaru strony i położenie suwaka (thumb) przewijania. Zobacz [SCROLLINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollinfo) struktury tematu w zestawie SDK Windows, aby uzyskać więcej informacji na temat zmiany ustawień domyślnych struktury.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

##  <a name="setscrollpos"></a>  CScrollBar::SetScrollPos

Ustawia określoną przez bieżące położenie suwaka *npos —* i, jeśli zostanie określony, odrysowuje pasek przewijania, aby odzwierciedlić nowe położenie.

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*npos —*<br/>
Określa nowe położenie suwaka. Musi ona należeć do zakresu przewijania.

*bRedraw*<br/>
Określa, czy pasek przewijania powinien być narysowany ponownie, aby odzwierciedlić nowe miejsce. Jeśli *bRedraw* ma wartość TRUE, jest odświeżana, pasek przewijania. Jeśli jest to wartość FALSE, nie jest narysowany na ponownie. Pasek przewijania jest odświeżana, domyślnie.

### <a name="return-value"></a>Wartość zwracana

Określa poprzednie położenie suwaka, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ustaw *bRedraw* FAŁSZ zawsze, gdy pasek przewijania zostaną narysowane ponownie przez kolejne wywołanie do innej funkcji, aby uniknąć paska przewijania, odświeżana, dwa razy w krótkim przedziale czasu.

### <a name="example"></a>Przykład

  Zobacz przykład [CScrollBar::SetScrollRange](#setscrollrange).

##  <a name="setscrollrange"></a>  CScrollBar::SetScrollRange

Ustawia położenie minimalne i maksymalne wartości dla paska przewijania danego.

```
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nMinPos*<br/>
Określa co najmniej położenie przewijania.

*nMaxPos*<br/>
Określa maksymalny położenie przewijania.

*bRedraw*<br/>
Określa, czy pasek przewijania powinien być narysowany ponownie, aby odzwierciedlić zmiany. Jeśli *bRedraw* ma wartość TRUE, jest odświeżana, na pasku przewijania; w przypadku wartości FAŁSZ nie jest rysowane. Jest ponownie rysowany domyślnie.

### <a name="remarks"></a>Uwagi

Ustaw *nMinPos* i *nMaxPos* na 0, aby ukryć paski przewijania standardowych.

Nie wywołuj tę funkcję, aby ukryć pasek przewijania podczas przetwarzania komunikatu powiadomienia paska przewijania.

Jeśli wywołanie `SetScrollRange` następuje bezpośrednio po wywołaniu `SetScrollPos` funkcja elementu członkowskiego zestawu *bRedraw* w `SetScrollPos` na 0, aby uniemożliwić pasek przewijania jest odświeżana, dwa razy.

Różnica między wartościami określony przez *nMinPos* i *nMaxPos* nie może być większa niż 32 767 znaków. Domyślny zakres dla formantu paska przewijania jest pusty (zarówno *nMinPos* i *nMaxPos* 0).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

##  <a name="showscrollbar"></a>  CScrollBar::ShowScrollBar

Pokazuje lub ukrywa pasek przewijania.

```
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Określa, czy pasek przewijania jest wyświetlany, czy ukryty. Jeśli ten parametr ma wartość TRUE, jest wyświetlany na pasku przewijania; w przeciwnym razie jest ukryty.

### <a name="remarks"></a>Uwagi

Aplikacja nie powinna wywołać tę funkcję, aby ukryć pasek przewijania podczas przetwarzania komunikatu powiadomienia paska przewijania.

### <a name="example"></a>Przykład

  Zobacz przykład [CScrollBar::Create](#create).

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CButton](../../mfc/reference/cbutton-class.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Klasa CStatic](../../mfc/reference/cstatic-class.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
