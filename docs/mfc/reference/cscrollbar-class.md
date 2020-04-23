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
ms.openlocfilehash: 2079e12eccde42fe8c456a7852a029f44ae3cd77
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754405"
---
# <a name="cscrollbar-class"></a>Klasa CScrollBar

Zapewnia funkcjonalność kontrolki paska przewijania systemu Windows.

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
|[CScrollBar::Tworzenie](#create)|Tworzy pasek przewijania systemu Windows `CScrollBar` i dołącza go do obiektu.|
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Włącza lub wyłącza jedną lub obie strzałki paska przewijania.|
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Pobiera informacje o pasku `SCROLLBARINFO` przewijania przy użyciu struktury.|
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Pobiera informacje o pasku przewijania.|
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Pobiera limit paska przewijania|
|[CScrollBar::GetScrollPos](#getscrollpos)|Pobiera bieżącą pozycję pola przewijania.|
|[CScrollBar::GetScrollRange](#getscrollrange)|Pobiera bieżące minimalne i maksymalne pozycje paska przewijania dla danego paska przewijania.|
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Ustawia informacje o pasku przewijania.|
|[CScrollBar::SetScrollPos](#setscrollpos)|Ustawia bieżącą pozycję pola przewijania.|
|[CScrollBar::SetScrollRange](#setscrollrange)|Ustawia minimalne i maksymalne wartości położenia dla danego paska przewijania.|
|[CScrollBar::ShowScrollBar](#showscrollbar)|Pokazuje lub ukrywa pasek przewijania.|

## <a name="remarks"></a>Uwagi

Formant paska przewijania tworzy się w dwóch krokach. Najpierw `CScrollBar` wywołaj konstruktora, aby skonstruować `CScrollBar` obiekt, a następnie wywołaj funkcję [Utwórz](#create) element członkowski, aby utworzyć kontrolka paska przewijania systemu Windows i dołączyć go do `CScrollBar` obiektu.

Jeśli obiekt `CScrollBar` zostanie utworzony w oknie dialogowym (za pośrednictwem zasobu okna dialogowego), `CScrollBar` jest on automatycznie niszczony po zamknięciu okna dialogowego przez użytkownika.

Jeśli utworzysz `CScrollBar` obiekt w oknie, może być również konieczne jego zniszczenie.

Jeśli utworzysz `CScrollBar` obiekt na stosie, zostanie on automatycznie zniszczony. Jeśli `CScrollBar` obiekt zostanie utworzony na stercie przy użyciu **nowej** funkcji, należy wywołać **delete** na obiekcie, aby go zniszczyć, gdy użytkownik zakończy pasek przewijania systemu Windows.

Jeśli przydzielić dowolną `CScrollBar` pamięć w obiekcie, zastąpić `CScrollBar` destruktora do usuwania alokacji.

Aby uzyskać powiązane `CScrollBar`informacje dotyczące używania programu , zobacz [Formanty](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cscrollbarcreate"></a><a name="create"></a>CScrollBar::Tworzenie

Tworzy pasek przewijania systemu Windows `CScrollBar` i dołącza go do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa styl paska przewijania. Zastosuj dowolną kombinację [stylów paska przewijania](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) do paska przewijania.

*Rect*<br/>
Określa rozmiar i położenie paska przewijania. Może to być `RECT` struktura `CRect` lub obiekt.

*pParentWnd*<br/>
Określa okno nadrzędne paska przewijania, zwykle `CDialog` obiekt. Nie może być null.

*Nid*<br/>
Identyfikator sterowania paska przewijania.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CScrollBar` obiektu w dwóch krokach. Najpierw wywołać konstruktora, `CScrollBar` który konstruuje obiekt; następnie `Create`wywołać , który tworzy i inicjuje skojarzony `CScrollBar` pasek przewijania systemu Windows i dołącza go do obiektu.

Zastosuj następujące [style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles) do paska przewijania:

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_GROUP Do grupowanie formantów

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

## <a name="cscrollbarcscrollbar"></a><a name="cscrollbar"></a>CScrollBar::CScrollBar

Konstruuje `CScrollBar` obiekt.

```
CScrollBar();
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu należy `Create` wywołać funkcję elementu członkowskiego, aby utworzyć i zainicjować pasek przewijania systemu Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

## <a name="cscrollbarenablescrollbar"></a><a name="enablescrollbar"></a>CScrollBar::EnableScrollBar

Włącza lub wyłącza jedną lub obie strzałki paska przewijania.

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>Parametry

*nArrowFlags*<br/>
Określa, czy strzałki przewijania są włączone czy wyłączone i które strzałki są włączone czy wyłączone. Ten parametr może być jedną z następujących wartości:

- ESB_ENABLE_BOTH Włącza obie strzałki paska przewijania.

- ESB_DISABLE_LTUP Wyłącza strzałkę w lewo poziomego paska przewijania lub strzałkę w górę pionowego paska przewijania.

- ESB_DISABLE_RTDN Wyłącza strzałkę w prawo poziomego paska przewijania lub strzałkę w dół pionowego paska przewijania.

- ESB_DISABLE_BOTH Wyłącza obie strzałki paska przewijania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli strzałki są włączone lub wyłączone, jak określono; w przeciwnym razie 0, co oznacza, że strzałki są już w żądanym stanie lub wystąpił błąd.

### <a name="example"></a>Przykład

  Zobacz przykład [CScrollBar::SetScrollRange](#setscrollrange).

## <a name="cscrollbargetscrollbarinfo"></a><a name="getscrollbarinfo"></a>CScrollBar::GetScrollBarInfo

Pobiera informacje, które `SCROLLBARINFO` struktura utrzymuje o pasku przewijania.

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>Parametry

*pScrollInfo*<br/>
Wskaźnik do struktury [SCROLLBARINFO.](/windows/win32/api/winuser/ns-winuser-scrollbarinfo)

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego emuluje funkcjonalność [komunikatu SBM_SCROLLBARINFO,](/windows/win32/Controls/sbm-getscrollbarinfo) zgodnie z opisem w windows SDK.

## <a name="cscrollbargetscrollinfo"></a><a name="getscrollinfo"></a>CScrollBar::GetScrollInfo

Pobiera informacje, które `SCROLLINFO` struktura utrzymuje o pasku przewijania.

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>Parametry

*lpScrollInfo*<br/>
Wskaźnik do struktury [SCROLLINFO.](/windows/win32/api/winuser/ns-winuser-scrollinfo) Zobacz SDK systemu Windows, aby uzyskać więcej informacji na temat tej struktury.

*nMask*<br/>
Określa parametry paska przewijania do pobrania. Typowe użycie, SIF_ALL, określa kombinację SIF_PAGE, SIF_POS, SIF_TRACKPOS i SIF_RANGE. Zobacz `SCROLLINFO` więcej informacji na temat wartości nMask.

### <a name="return-value"></a>Wartość zwracana

Jeśli wiadomość została pobrana żadnych wartości, zwrot jest PRAWDA. W przeciwnym razie jest false.

### <a name="remarks"></a>Uwagi

`GetScrollInfo`umożliwia aplikacjom korzystanie z 32-bitowych pozycji przewijania.

Struktura [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) zawiera informacje o pasku przewijania, w tym minimalne i maksymalne pozycje przewijania, rozmiar strony i położenie pola przewijania (kciuk). Zobacz `SCROLLINFO` temat struktury w windows SDK, aby uzyskać więcej informacji na temat zmiany ustawień domyślnych struktury.

Programy obsługi komunikatów systemu Windows MFC, które wskazują położenie paska przewijania, [CWnd::OnHScroll i [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), zapewniają tylko 16 bitów danych położenia. `GetScrollInfo`i `SetScrollInfo` dostarczać 32 bity danych pozycji paska przewijania. W związku z `GetScrollInfo` tym aplikacja `CWnd::OnHScroll` może `CWnd::OnVScroll` wywołać podczas przetwarzania albo lub uzyskać 32-bitowe dane pozycji paska przewijania.

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrolllimit"></a><a name="getscrolllimit"></a>CScrollBar::GetScrollLimit

Pobiera maksymalną pozycję przewijania paska przewijania.

```
int GetScrollLimit();
```

### <a name="return-value"></a>Wartość zwracana

Określa maksymalną pozycję paska przewijania, jeśli zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollpos"></a><a name="getscrollpos"></a>CScrollBar::GetScrollPos

Pobiera bieżącą pozycję pola przewijania.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Wartość zwracana

Określa bieżącą pozycję pola przewijania, jeśli zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Bieżąca pozycja jest wartością względną, która zależy od bieżącego zakresu przewijania. Jeśli na przykład zakres przewijania wynosi od 100 do 200, a pole przewijania znajduje się na środku paska, bieżąca pozycja wynosi 150.

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollrange"></a><a name="getscrollrange"></a>CScrollBar::GetScrollRange

Kopiuje bieżące minimalne i maksymalne pozycje paska przewijania dla danego paska przewijania do lokalizacji określonych przez *lpMinPos* i *lpMaxPos*.

```cpp
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>Parametry

*lpMinPos*<br/>
Wskazuje zmienną całkowitą, która ma otrzymać minimalną pozycję.

*lpMaxPos*<br/>
Wskazuje zmienną całkowitą, która ma otrzymać maksymalną pozycję.

### <a name="remarks"></a>Uwagi

Domyślny zakres formantu paska przewijania jest pusty (obie wartości to 0).

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbarsetscrollinfo"></a><a name="setscrollinfo"></a>CScrollBar::SetScrollInfo

Ustawia informacje, `SCROLLINFO` które struktura utrzymuje o pasku przewijania.

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*lpScrollInfo*<br/>
Wskaźnik do struktury [SCROLLINFO.](/windows/win32/api/winuser/ns-winuser-scrollinfo)

*bRedraw*<br/>
Określa, czy pasek przewijania ma zostać ponownie narysowany w celu odzwierciedlenia nowych informacji. Jeśli *bRedraw* ma wartość TRUE, pasek przewijania zostanie ponownie narysowany. Jeśli jest FALSE, nie jest ponownie rysowane. Pasek przewijania jest domyślnie ponownie rysowany.

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwrot jest TRUE. W przeciwnym razie jest false.

### <a name="remarks"></a>Uwagi

Należy podać wartości wymagane przez `SCROLLINFO` parametry struktury, w tym wartości flagi.

Struktura `SCROLLINFO` zawiera informacje o pasku przewijania, w tym minimalne i maksymalne pozycje przewijania, rozmiar strony i położenie pola przewijania (kciuk). Zobacz temat struktury [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) w usłudze Windows SDK, aby uzyskać więcej informacji na temat zmiany ustawień domyślnych struktury.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

## <a name="cscrollbarsetscrollpos"></a><a name="setscrollpos"></a>CScrollBar::SetScrollPos

Ustawia bieżącą pozycję pola przewijania na określone przez *nPos* i, jeśli jest określony, ponownie rysuje pasek przewijania, aby odzwierciedlić nową pozycję.

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Określa nową pozycję pola przewijania. Musi znajdować się w zakresie przewijania.

*bRedraw*<br/>
Określa, czy pasek przewijania ma zostać ponownie narysowany, aby odzwierciedlić nową pozycję. Jeśli *bRedraw* ma wartość TRUE, pasek przewijania zostanie ponownie narysowany. Jeśli jest FALSE, nie jest ponownie rysowane. Pasek przewijania jest domyślnie ponownie rysowany.

### <a name="return-value"></a>Wartość zwracana

Określa poprzednią pozycję pola przewijania, jeśli zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ustaw *bRedraw* do FALSE, gdy pasek przewijania zostanie ponownie narysowany przez kolejne wywołanie innej funkcji, aby uniknąć ponownego narysowania paska przewijania dwukrotnie w krótkim odstępie czasu.

### <a name="example"></a>Przykład

  Zobacz przykład [CScrollBar::SetScrollRange](#setscrollrange).

## <a name="cscrollbarsetscrollrange"></a><a name="setscrollrange"></a>CScrollBar::SetScrollRange

Ustawia minimalne i maksymalne wartości położenia dla danego paska przewijania.

```cpp
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nMinPos (właso)*<br/>
Określa minimalną pozycję przewijania.

*nMaxPos*<br/>
Określa maksymalną pozycję przewijania.

*bRedraw*<br/>
Określa, czy pasek przewijania ma zostać ponownie narysowany, aby odzwierciedlić zmianę. Jeśli *bRedraw* ma wartość TRUE, pasek przewijania zostanie ponownie narysowany; jeśli FALSE, nie jest przerysowany. Jest on ponownie rysowany domyślnie.

### <a name="remarks"></a>Uwagi

Ustaw *nMinPos* i *nMaxPos* na 0, aby ukryć standardowe paski przewijania.

Nie należy wywoływać tej funkcji, aby ukryć pasek przewijania podczas przetwarzania komunikatu powiadomienia paska przewijania.

Jeśli wywołanie `SetScrollRange` natychmiast następuje `SetScrollPos` wywołanie funkcji elementu członkowskiego, `SetScrollPos` ustaw *bRedraw* w 0, aby zapobiec pasek przewijania jest ponownie rysowane dwa razy.

Różnica między wartościami określonymi przez *nMinPos* i *nMaxPos* nie może być większa niż 32 767. Domyślny zakres formantu paska przewijania jest pusty (zarówno *nMinPos,* jak i *nMaxPos* to 0).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

## <a name="cscrollbarshowscrollbar"></a><a name="showscrollbar"></a>CScrollBar::ShowScrollBar

Pokazuje lub ukrywa pasek przewijania.

```cpp
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>Parametry

*bPokaż*<br/>
Określa, czy pasek przewijania jest wyświetlany, czy ukryty. Jeśli ten parametr ma wartość PRAWDA, wyświetlany jest pasek przewijania; w przeciwnym razie jest ukryty.

### <a name="remarks"></a>Uwagi

Aplikacja nie powinna wywoływać tej funkcji, aby ukryć pasek przewijania podczas przetwarzania komunikatu powiadomienia paska przewijania.

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
