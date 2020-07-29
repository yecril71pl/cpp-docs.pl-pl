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
ms.openlocfilehash: 1ab25ad26357abe9091d273637f3ae9f77457342
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230483"
---
# <a name="cscrollbar-class"></a>Klasa CScrollBar

Oferuje funkcje kontrolki paska przewijania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CScrollBar : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CScrollBar::CScrollBar](#cscrollbar)|Konstruuje `CScrollBar` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CScrollBar:: Create](#create)|Tworzy pasek przewijania systemu Windows i dołącza go do `CScrollBar` obiektu.|
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Włącza lub wyłącza jedną strzałkę paska przewijania.|
|[CScrollBar:: GetScrollBarInfo](#getscrollbarinfo)|Pobiera informacje o pasku przewijania przy użyciu `SCROLLBARINFO` struktury.|
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Pobiera informacje o pasku przewijania.|
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Pobiera limit paska przewijania|
|[CScrollBar::GetScrollPos](#getscrollpos)|Pobiera bieżącą pozycję pola przewijania.|
|[CScrollBar::GetScrollRange](#getscrollrange)|Pobiera bieżące minimalne i maksymalne położenie paska przewijania dla danego paska przewijania.|
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Ustawia informacje o pasku przewijania.|
|[CScrollBar::SetScrollPos](#setscrollpos)|Ustawia bieżącą pozycję pola przewijania.|
|[CScrollBar::SetScrollRange](#setscrollrange)|Ustawia wartości minimalne i maksymalne pozycji dla danego paska przewijania.|
|[CScrollBar:: ShowScrollBar](#showscrollbar)|Pokazuje lub ukrywa pasek przewijania.|

## <a name="remarks"></a>Uwagi

Kontrolkę paska przewijania można utworzyć w dwóch krokach. Najpierw Wywołaj konstruktora `CScrollBar` w celu skonstruowania `CScrollBar` obiektu, a następnie wywołaj funkcję [tworzenia](#create) elementu członkowskiego, aby utworzyć kontrolkę paska przewijania systemu Windows i dołączyć ją do `CScrollBar` obiektu.

Jeśli utworzysz `CScrollBar` obiekt w oknie dialogowym (za pomocą zasobu okna dialogowego), `CScrollBar` zostanie on automatycznie zniszczony, gdy użytkownik zamknie okno dialogowe.

Jeśli utworzysz `CScrollBar` obiekt w oknie, może być również konieczne jego zniszczenie.

Jeśli utworzysz `CScrollBar` obiekt na stosie, zostanie on zniszczony automatycznie. Jeśli obiekt jest tworzony `CScrollBar` na stercie przy użyciu **`new`** funkcji, należy wywołać **`delete`** obiekt, aby zniszczyć go, gdy użytkownik zakończy pasek przewijania systemu Windows.

W przypadku przydzielenia pamięci w `CScrollBar` obiekcie Zastąp `CScrollBar` destruktor, aby usunąć alokacje.

Aby uzyskać informacje dotyczące korzystania z usługi `CScrollBar` , zobacz [Controls](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="cscrollbarcreate"></a><a name="create"></a>CScrollBar:: Create

Tworzy pasek przewijania systemu Windows i dołącza go do `CScrollBar` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl paska przewijania. Zastosuj dowolną kombinację [stylów paska przewijania](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) na pasku przewijania.

*cinania*<br/>
Określa rozmiar i położenie paska przewijania. Może być `RECT` strukturą lub `CRect` obiektem.

*pParentWnd*<br/>
Określa okno nadrzędne paska przewijania, zazwyczaj `CDialog` obiekt. Nie może mieć wartości NULL.

*nID*<br/>
Identyfikator kontrolki paska przewijania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Obiekt jest konstruowany `CScrollBar` w dwóch krokach. Najpierw Wywołaj konstruktora, który konstruuje `CScrollBar` obiekt, a następnie Wywołaj `Create` , który tworzy i inicjuje skojarzony pasek przewijania systemu Windows i dołącza go do `CScrollBar` obiektu.

Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do paska przewijania:

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_GROUP do grup formantów

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

## <a name="cscrollbarcscrollbar"></a><a name="cscrollbar"></a>CScrollBar::CScrollBar

Konstruuje `CScrollBar` obiekt.

```
CScrollBar();
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu Wywołaj `Create` funkcję członkowską, aby utworzyć i zainicjować pasek przewijania systemu Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

## <a name="cscrollbarenablescrollbar"></a><a name="enablescrollbar"></a>CScrollBar::EnableScrollBar

Włącza lub wyłącza jedną strzałkę paska przewijania.

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>Parametry

*nArrowFlags*<br/>
Określa, czy strzałki przewijania są włączone, czy wyłączone, a które strzałki są włączone lub wyłączone. Ten parametr może mieć jedną z następujących wartości:

- ESB_ENABLE_BOTH włącza obie strzałki paska przewijania.

- ESB_DISABLE_LTUP wyłącza strzałkę w lewo w poziomym pasku przewijania lub strzałkę w górę pionowego paska przewijania.

- ESB_DISABLE_RTDN wyłącza strzałkę w prawo w poziomym pasku przewijania lub strzałkę w dół pionowego paska przewijania.

- ESB_DISABLE_BOTH wyłącza obie strzałki paska przewijania.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli strzałki są włączone lub wyłączone w określony sposób; w przeciwnym razie, co oznacza, że strzałki znajdują się już w żądanym stanie lub wystąpił błąd.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CScrollBar:: SetScrollRange](#setscrollrange).

## <a name="cscrollbargetscrollbarinfo"></a><a name="getscrollbarinfo"></a>CScrollBar:: GetScrollBarInfo

Pobiera informacje `SCROLLBARINFO` przechowywane przez strukturę na pasku przewijania.

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>Parametry

*pScrollInfo*<br/>
Wskaźnik do struktury [SCROLLBARINFO](/windows/win32/api/winuser/ns-winuser-scrollbarinfo) .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność komunikatu [SBM_SCROLLBARINFO](/windows/win32/Controls/sbm-getscrollbarinfo) , zgodnie z opisem w Windows SDK.

## <a name="cscrollbargetscrollinfo"></a><a name="getscrollinfo"></a>CScrollBar::GetScrollInfo

Pobiera informacje `SCROLLINFO` przechowywane przez strukturę na pasku przewijania.

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>Parametry

*lpScrollInfo*<br/>
Wskaźnik do struktury [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) . Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

*nMask*<br/>
Określa parametry paska przewijania do pobrania. Typowy sposób użycia, SIF_ALL, określa kombinację SIF_PAGE, SIF_POS, SIF_TRACKPOS i SIF_RANGE. Zobacz `SCROLLINFO` , aby uzyskać więcej informacji na temat wartości nMask.

### <a name="return-value"></a>Wartość zwracana

Jeśli komunikat pobrał wartości, zwracana jest wartość TRUE. W przeciwnym razie ma wartość FALSE.

### <a name="remarks"></a>Uwagi

`GetScrollInfo`umożliwia aplikacjom używanie 32-bitowych pozycji przewijania.

Struktura [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) zawiera informacje o pasku przewijania, w tym o minimalnych i maksymalnych położeniach przewijania, rozmiarze strony i pozycji pola przewijania (kciuk). Zobacz `SCROLLINFO` temat struktura w Windows SDK, aby uzyskać więcej informacji na temat zmiany ustawień domyślnych struktury.

Procedury obsługi komunikatów systemu Windows MFC wskazujące położenie paska przewijania, [CWnd:: OnHScroll i [CWnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), zapewniają tylko 16 bitów danych pozycji. `GetScrollInfo`i `SetScrollInfo` podaj 32 bitów danych pozycji paska przewijania. W ten sposób aplikacja może wywołać `GetScrollInfo` podczas przetwarzania `CWnd::OnHScroll` lub, `CWnd::OnVScroll` Aby uzyskać 32-bitowe dane pozycji paska przewijania.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrolllimit"></a><a name="getscrolllimit"></a>CScrollBar::GetScrollLimit

Pobiera maksymalną pozycję przewijania paska przewijania.

```
int GetScrollLimit();
```

### <a name="return-value"></a>Wartość zwracana

Określa maksymalną pozycję paska przewijania, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollpos"></a><a name="getscrollpos"></a>CScrollBar::GetScrollPos

Pobiera bieżącą pozycję pola przewijania.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Wartość zwracana

Określa bieżącą pozycję pola przewijania, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Bieżąca pozycja jest wartością względną, która zależy od bieżącego zakresu przewijania. Na przykład, jeśli zakres przewijania wynosi od 100 do 200, a pole przewijania znajduje się w środku paska, bieżąca pozycja to 150.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollrange"></a><a name="getscrollrange"></a>CScrollBar::GetScrollRange

Kopiuje bieżące minimalne i maksymalne położenie paska przewijania dla danego paska przewijania do lokalizacji określonych przez *lpMinPos* i *lpMaxPos*.

```cpp
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>Parametry

*lpMinPos*<br/>
Wskazuje zmienną całkowitą, która ma otrzymać pozycję minimalną.

*lpMaxPos*<br/>
Wskazuje zmienną całkowitą, która ma otrzymać maksymalną pozycję.

### <a name="remarks"></a>Uwagi

Domyślny zakres dla kontrolki paska przewijania jest pusty (obie wartości są równe 0).

### <a name="example"></a>Przykład

  Zobacz przykład dla [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbarsetscrollinfo"></a><a name="setscrollinfo"></a>CScrollBar::SetScrollInfo

Ustawia informacje `SCROLLINFO` przechowywane przez strukturę na pasku przewijania.

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*lpScrollInfo*<br/>
Wskaźnik do struktury [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) .

*bRedraw*<br/>
Określa, czy pasek przewijania ma być rysowany ponownie w celu odzwierciedlenia nowych informacji. Jeśli *bRedraw* ma wartość true, pasek przewijania jest rysowany ponownie. Jeśli wartość jest równa FALSE, nie jest ponownie narysowana. Pasek przewijania jest domyślnie rysowany ponownie.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca wartość TRUE. W przeciwnym razie ma wartość FALSE.

### <a name="remarks"></a>Uwagi

Należy podać wartości wymagane przez `SCROLLINFO` parametry struktury, w tym wartości flag.

`SCROLLINFO`Struktura zawiera informacje o pasku przewijania, w tym o minimalnych i maksymalnych położeniach przewijania, rozmiarze strony i pozycji pola przewijania (kciuk). Zobacz temat struktura [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) w Windows SDK, aby uzyskać więcej informacji na temat zmiany wartości domyślnych struktury.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

## <a name="cscrollbarsetscrollpos"></a><a name="setscrollpos"></a>CScrollBar::SetScrollPos

Ustawia bieżące położenie pola przewijania do określonego przez *nPos* i, jeśli jest określony, ponownie rysuje pasek przewijania w celu odzwierciedlenia nowego położenia.

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Określa nową pozycję pola przewijania. Musi ona należeć do zakresu przewijania.

*bRedraw*<br/>
Określa, czy pasek przewijania ma być rysowany ponownie w celu odzwierciedlenia nowego położenia. Jeśli *bRedraw* ma wartość true, pasek przewijania jest rysowany ponownie. Jeśli wartość jest równa FALSE, nie jest ponownie narysowana. Pasek przewijania jest domyślnie rysowany ponownie.

### <a name="return-value"></a>Wartość zwracana

Określa poprzednią pozycję pola przewijania, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ustaw *bRedraw* na false za każdym razem, gdy pasek przewijania zostanie ponownie narysowany przez kolejne wywołanie do innej funkcji, aby uniknąć ponownego rysowania paska przewijania w krótkim odstępie czasu.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CScrollBar:: SetScrollRange](#setscrollrange).

## <a name="cscrollbarsetscrollrange"></a><a name="setscrollrange"></a>CScrollBar::SetScrollRange

Ustawia wartości minimalne i maksymalne pozycji dla danego paska przewijania.

```cpp
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nMinPos*<br/>
Określa minimalną pozycję przewijania.

*nMaxPos*<br/>
Określa maksymalną pozycję przewijania.

*bRedraw*<br/>
Określa, czy pasek przewijania ma być rysowany ponownie w celu odzwierciedlenia zmiany. Jeśli *bRedraw* ma wartość true, pasek przewijania jest ponownie rysowany; Jeśli wartość jest równa FALSE, nie jest ponownie narysowana. Jest on ponownie rysowany domyślnie.

### <a name="remarks"></a>Uwagi

Ustaw *nMinPos* i *nMaxPos* na 0, aby ukryć standardowe paski przewijania.

Nie wywołuj tej funkcji, aby ukryć pasek przewijania podczas przetwarzania komunikatu powiadomienia paska przewijania.

Jeśli wywołanie w celu `SetScrollRange` natychmiast następuje po wywołaniu `SetScrollPos` funkcji członkowskiej, ustaw *bRedraw* w wartości `SetScrollPos` 0, aby zapobiec dwukrotnemu narysowaniu paska przewijania.

Różnica między wartościami określonymi przez *nMinPos* i *nMaxPos* nie może być większa niż 32 767. Domyślny zakres dla kontrolki paska przewijania jest pusty (zarówno *nMinPos* , jak i *nMaxPos* są równe 0).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

## <a name="cscrollbarshowscrollbar"></a><a name="showscrollbar"></a>CScrollBar:: ShowScrollBar

Pokazuje lub ukrywa pasek przewijania.

```cpp
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Określa, czy pasek przewijania jest wyświetlany, czy ukryty. Jeśli ten parametr ma wartość TRUE, wyświetlany jest pasek przewijania; w przeciwnym razie jest ukryta.

### <a name="remarks"></a>Uwagi

Aplikacja nie powinna wywoływać tej funkcji, aby ukryć pasek przewijania podczas przetwarzania komunikatu powiadomienia paska przewijania.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CScrollBar:: Create](#create).

## <a name="see-also"></a>Zobacz także

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CButton](../../mfc/reference/cbutton-class.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Klasa CStatic](../../mfc/reference/cstatic-class.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
