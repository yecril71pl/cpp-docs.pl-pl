---
title: Klasa CSliderCtrl
ms.date: 11/04/2016
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
helpviewer_keywords:
- CSliderCtrl [MFC], CSliderCtrl
- CSliderCtrl [MFC], ClearSel
- CSliderCtrl [MFC], ClearTics
- CSliderCtrl [MFC], Create
- CSliderCtrl [MFC], CreateEx
- CSliderCtrl [MFC], GetBuddy
- CSliderCtrl [MFC], GetChannelRect
- CSliderCtrl [MFC], GetLineSize
- CSliderCtrl [MFC], GetNumTics
- CSliderCtrl [MFC], GetPageSize
- CSliderCtrl [MFC], GetPos
- CSliderCtrl [MFC], GetRange
- CSliderCtrl [MFC], GetRangeMax
- CSliderCtrl [MFC], GetRangeMin
- CSliderCtrl [MFC], GetSelection
- CSliderCtrl [MFC], GetThumbLength
- CSliderCtrl [MFC], GetThumbRect
- CSliderCtrl [MFC], GetTic
- CSliderCtrl [MFC], GetTicArray
- CSliderCtrl [MFC], GetTicPos
- CSliderCtrl [MFC], GetToolTips
- CSliderCtrl [MFC], SetBuddy
- CSliderCtrl [MFC], SetLineSize
- CSliderCtrl [MFC], SetPageSize
- CSliderCtrl [MFC], SetPos
- CSliderCtrl [MFC], SetRange
- CSliderCtrl [MFC], SetRangeMax
- CSliderCtrl [MFC], SetRangeMin
- CSliderCtrl [MFC], SetSelection
- CSliderCtrl [MFC], SetThumbLength
- CSliderCtrl [MFC], SetTic
- CSliderCtrl [MFC], SetTicFreq
- CSliderCtrl [MFC], SetTipSide
- CSliderCtrl [MFC], SetToolTips
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
ms.openlocfilehash: 4db27112daf65b2c3f477527cd7b4351b91d7f18
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776638"
---
# <a name="csliderctrl-class"></a>Klasa CSliderCtrl

Oferuje funkcje formantu typowego suwaka Windows.

## <a name="syntax"></a>Składnia

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|Konstruuje `CSliderCtrl` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSliderCtrl::ClearSel](#clearsel)|Czyści bieżące zaznaczenie w kontrolce suwaka.|
|[CSliderCtrl::ClearTics](#cleartics)|Usuwa bieżący znaczniki w kontrolce suwaka.|
|[CSliderCtrl::Create](#create)|Tworzy formant suwaka i dołącza je do `CSliderCtrl` obiektu.|
|[CSliderCtrl::CreateEx](#createex)|Tworzy formant suwaka w określonym stylu rozszerzonej Windows i dołącza je do `CSliderCtrl` obiektu.|
|[CSliderCtrl::GetBuddy](#getbuddy)|Pobiera uchwyt do okna buddy kontrolki suwaka w danej lokalizacji.|
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Pobiera informacje o rozmiarze kanał kontrolny suwaka.|
|[CSliderCtrl::GetLineSize](#getlinesize)|Pobiera rozmiar wiersza kontrolki suwaka.|
|[CSliderCtrl::GetNumTics](#getnumtics)|Pobiera liczbę znaczników w kontrolce suwaka.|
|[CSliderCtrl::GetPageSize](#getpagesize)|Pobiera rozmiar strony w kontrolce suwaka.|
|[CSliderCtrl::GetPos](#getpos)|Pobiera bieżące położenie suwaka.|
|[CSliderCtrl::GetRange](#getrange)|Pobiera minimalną i maksymalną pozycji suwaka.|
|[CSliderCtrl::GetRangeMax](#getrangemax)|Pobiera maksymalną położenie suwaka.|
|[CSliderCtrl::GetRangeMin](#getrangemin)|Pobiera minimalną położenie suwaka.|
|[CSliderCtrl::GetSelection](#getselection)|Pobiera zakres bieżącego zaznaczenia.|
|[CSliderCtrl::GetThumbLength](#getthumblength)|Pobiera długość suwak w bieżącym TrackBar — formant.|
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Pobiera rozmiar przycisku przewijania suwaka.|
|[CSliderCtrl::GetTic](#gettic)|Pobiera pozycję określonego znacznika.|
|[CSliderCtrl::GetTicArray](#getticarray)|Pobiera tablicę pozycji znacznik osi dla kontrolki suwaka.|
|[CSliderCtrl::GetTicPos](#getticpos)|Pobiera pozycję określonego znacznika w współrzędne klienta.|
|[CSliderCtrl::GetToolTips](#gettooltips)|Pobiera dojścia do kontrolki tooltip przypisany do kontrolki suwaka, jeśli istnieje.|
|[CSliderCtrl::SetBuddy](#setbuddy)|Przypisuje okna jako okno cyklu kontrolki suwaka.|
|[CSliderCtrl::SetLineSize](#setlinesize)|Określa rozmiar wiersza w kontrolce suwaka.|
|[CSliderCtrl::SetPageSize](#setpagesize)|Określa rozmiar strony w kontrolce suwaka.|
|[CSliderCtrl::SetPos](#setpos)|Ustawia bieżące położenie suwaka.|
|[CSliderCtrl::SetRange](#setrange)|Ustawia minimalną i maksymalną pozycji suwaka.|
|[CSliderCtrl::SetRangeMax](#setrangemax)|Ustawia maksymalną położenie suwaka.|
|[CSliderCtrl::SetRangeMin](#setrangemin)|Ustawia minimalną położenie suwaka.|
|[CSliderCtrl::SetSelection](#setselection)|Ustawia zakres bieżącego zaznaczenia.|
|[CSliderCtrl::SetThumbLength](#setthumblength)|Ustawia długość suwak w bieżącym TrackBar — formant.|
|[CSliderCtrl::SetTic](#settic)|Ustawia położenie określonego znacznika.|
|[CSliderCtrl::SetTicFreq](#setticfreq)|Określa częstotliwość znaczników osi, znaczniki za każdy przyrost kontrolki suwaka.|
|[CSliderCtrl::SetTipSide](#settipside)|Położenie formantu etykietki narzędzia używane przez TrackBar — formant.|
|[CSliderCtrl::SetToolTips](#settooltips)|Przypisuje kontrolkę etykiety narzędzia do kontrolki suwaka.|

## <a name="remarks"></a>Uwagi

"Kontrolki suwaka" (trackbar) to okno zawierające suwaka i opcjonalnie znaczniki. Gdy użytkownik przesuwa suwaka, za pomocą myszy lub klucze kierunku, formant wysyła komunikaty powiadomień, aby wskazać zmianę.

Formanty suwaka są przydatne, gdy użytkownik, który ma zaznacz wartość discrete lub zestaw kolejnych wartości w zakresie. Może na przykład użyć kontrolki suwaka, aby umożliwić użytkownikowi na ustawianie częstotliwości powtarzania klawiatury przez przesunięcie suwaka danego znacznika.

Ta kontrolka (i w związku z tym `CSliderCtrl` klasy) jest dostępna tylko dla programów uruchomionych w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.

Przenosi suwak w przyrostach, które można określić podczas jego tworzenia. Na przykład, jeśli określisz, że suwak powinny mieć zakres pięć, suwak mogą tylko zajmować sześć stanowiska: pozycji z lewej strony kontrolki suwaka i jedną pozycję dla każdego przyrostu w zakresie. Zwykle każda z tych pozycji jest identyfikowany przez znacznika.

Tworzenie kontrolki slider przy użyciu konstruktora i `Create` funkcji składowej typu `CSliderCtrl`. Po utworzeniu kontrolki suwaka, można użyć funkcji elementów członkowskich w `CSliderCtrl` zmiany wielu jego właściwości. Zmiany, które można wprowadzić obejmują ustawienia dla suwak w pozycji minimalną i maksymalną, rysowania znaczniki, ustawienie zaznaczony zakres i położenie suwaka.

Aby uzyskać więcej informacji na temat korzystania z `CSliderCtrl`, zobacz [kontrolki](../../mfc/controls-mfc.md) i [korzystanie z CSliderCtrl](../../mfc/using-csliderctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

##  <a name="clearsel"></a>  CSliderCtrl::ClearSel

Czyści bieżące zaznaczenie w kontrolce suwaka.

```
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*bRedraw*<br/>
Ponowne wystawianie flagi. Jeśli ten parametr ma wartość TRUE, suwak jest ponownie rysowany po wyboru jest wyczyszczone; w przeciwnym razie nie jest rysowane suwaka.

##  <a name="cleartics"></a>  CSliderCtrl::ClearTics

Usuwa bieżący znaczniki w kontrolce suwaka.

```
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*bRedraw*<br/>
Ponowne wystawianie flagi. Jeśli ten parametr ma wartość TRUE, suwak jest ponownie rysowany po znaczniki są czyszczone; w przeciwnym razie nie jest rysowane suwaka.

##  <a name="create"></a>  CSliderCtrl::Create

Tworzy formant suwaka i dołącza je do `CSliderCtrl` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl kontrolki slider. Zastosuj dowolną kombinację [style formantu suwaka](/windows/desktop/Controls/trackbar-control-styles), które zostały opisane w zestawie Windows SDK, do formantu.

*rect*<br/>
Określa rozmiar i położenie kontrolki slider. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [Prostokąt](/previous-versions/dd162897\(v=vs.85\)) struktury.

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki suwaka, zwykle `CDialog`. Nie może być równa NULL.

*nID*<br/>
Określa identyfikator kontrolki slider.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli inicjowanie się powiodła. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CSliderCtrl` w dwóch krokach. Po pierwsze wywołanie konstruktora, a następnie wywołaj `Create`, który tworzy formant suwaka i dołącza go do `CSliderCtrl` obiektu.

W zależności od wartości ustawione dla *dwStyle*, formant suwaka może mieć orientacji pionowej lub poziomej. Może mieć znaczniki osi po obu stronach obu stronach lub żadnego z tych celów. Może również służyć do określania zakresu kolejnych wartości.

Aby zastosować rozszerzone Style okna dla kontrolki suwaka, należy wywołać [CreateEx](#createex) zamiast `Create`.

##  <a name="createex"></a>  CSliderCtrl::CreateEx

Tworzy kontrolkę (okno podrzędne) i kojarzy ją z `CSliderCtrl` obiektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyle*<br/>
Określa styl rozszerzony kontrolki tworzona. Aby uzyskać listę rozszerzone style Windows, zobacz *dwExStyle* parametr [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) w zestawie Windows SDK.

*dwStyle*<br/>
Określa styl kontrolki slider. Zastosuj dowolną kombinację [style formantu suwaka](/windows/desktop/Controls/trackbar-control-styles), które zostały opisane w zestawie Windows SDK, do formantu.

*rect*<br/>
Odwołanie do [Prostokąt](/previous-versions/dd162897\(v=vs.85\)) struktury opisujących rozmiar i położenie okna, można utworzyć klienta współrzędne *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym formantu.

*nID*<br/>
Identyfikator formantu okna podrzędnego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [Utwórz](#create) do zastosowania rozszerzone style Windows, określonego przez tekst wstępny rozszerzonego stylu Windows **WS_EX_**.

##  <a name="csliderctrl"></a>  CSliderCtrl::CSliderCtrl

Konstruuje `CSliderCtrl` obiektu.

```
CSliderCtrl();
```

##  <a name="getbuddy"></a>  CSliderCtrl::GetBuddy

Pobiera uchwyt do okna buddy kontrolki suwaka w danej lokalizacji.

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>Parametry

*fLocation*<br/>
Wartość logiczna wskazuje, które dwa buddy okna dojścia do pobrania. Może być jednym z następujących wartości:

- Wartość TRUE umożliwia pobranie dojścia do kolegów z lewej strony suwaka. Jeśli styl TBS_VERT korzysta z kontrolki suwaka, komunikat pobierze buddy powyżej suwaka.

- Wartość FALSE umożliwia pobranie dojścia do kolegów z prawej strony suwaka. Jeśli styl TBS_VERT korzysta z kontrolki suwaka, komunikat pobierze buddy poniżej suwaka.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest oknem buddy w lokalizacji określonej przez *fLocation*, lub wartość NULL, jeśli nie buddy istnieje przedział czasu w tej lokalizacji.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TBM_GETBUDDY](/windows/desktop/Controls/tbm-getbuddy), zgodnie z opisem w zestawie Windows SDK. Aby uzyskać opis style formantu suwaka, zobacz [style kontrolki Trackbar](/windows/desktop/Controls/trackbar-control-styles) w zestawie Windows SDK.

##  <a name="getchannelrect"></a>  CSliderCtrl::GetChannelRect

Pobiera rozmiar i położenie prostokąt otaczający dla kanału kontrolki suwaka.

```
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Wskaźnik do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który zawiera rozmiar i położenie kanału użytkownika prostokąt ograniczający gdy funkcja zwraca.

### <a name="remarks"></a>Uwagi

Kanał jest to obszar, nad przenosi suwaka i zawierającą podświetlenie po wybraniu zakresu.

##  <a name="getlinesize"></a>  CSliderCtrl::GetLineSize

Pobiera rozmiar wiersza dla kontrolki suwaka.

```
int GetLineSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar wiersza dla kontrolki suwaka.

### <a name="remarks"></a>Uwagi

Rozmiar wiersza wpływa na tym, ile suwak przenosi TB_LINEUP i TB_LINEDOWN powiadomienia. Ustawieniem domyślnym dla rozmiaru wiersza to 1.

##  <a name="getnumtics"></a>  CSliderCtrl::GetNumTics

Pobiera liczbę znaczników w kontrolce suwaka.

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaczników w kontrolce suwaka.

##  <a name="getpagesize"></a>  CSliderCtrl::GetPageSize

Pobiera rozmiar strony dla kontrolki suwaka.

```
int GetPageSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar strony dla formantu suwaka.

### <a name="remarks"></a>Uwagi

Wpływa na rozmiar strony, ile suwak przenosi TB_PAGEUP i TB_PAGEDOWN powiadomienia.

##  <a name="getpos"></a>  CSliderCtrl::GetPos

Pobiera bieżące położenie suwaka w kontrolce suwaka.

```
int GetPos() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżące położenie.

##  <a name="getrange"></a>  CSliderCtrl::GetRange

Pobiera maksymalne i minimalne dla pozycji suwaka w kontrolce suwaka.

```
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parametry

*Nmin.*<br/>
Odwołanie do liczba całkowita, która otrzymuje minimalnej pozycji.

*nmaks.*<br/>
Odwołanie do liczba całkowita, która odbiera maksymalna pozycji.

### <a name="remarks"></a>Uwagi

Ta funkcja kopiuje wartości do liczb całkowitych, odwołuje się *nMin* i *nmaks*.

##  <a name="getrangemax"></a>  CSliderCtrl::GetRangeMax

Pobiera maksymalną położenie suwaka w kontrolce suwaka.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna położenie formantu.

##  <a name="getrangemin"></a>  CSliderCtrl::GetRangeMin

Pobiera minimalną położenie suwaka w kontrolce suwaka.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Wartość zwracana

Minimalna położenie formantu.

##  <a name="getselection"></a>  CSliderCtrl::GetSelection

Pobiera początkowy i końcowy pozycji bieżące zaznaczenie w kontrolce suwaka.

```
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parametry

*Nmin.*<br/>
Odwołanie do wartości całkowitej, otrzymuje początkową bieżącego zaznaczenia.

*nmaks.*<br/>
Odwołanie do liczby całkowitej, która odbiera pozycji końcowej bieżącego zaznaczenia.

##  <a name="getthumblength"></a>  CSliderCtrl::GetThumbLength

Pobiera długość suwak w bieżącym TrackBar — formant.

```
int GetThumbLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość suwaka, w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [TBM_GETTHUMBLENGTH](/windows/desktop/Controls/tbm-getthumblength) komunikat, który jest opisany w zestawie Windows SDK.

##  <a name="getthumbrect"></a>  CSliderCtrl::GetThumbRect

Pobiera rozmiar i położenie prostokąt otaczający dla suwak w kontrolce suwaka.

```
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Wskaźnik do `CRect` obiekt, który zawiera prostokąt otaczający potrzeby suwaka, gdy funkcja zwraca.

##  <a name="gettic"></a>  CSliderCtrl::GetTic

Pobiera położenie znaczników głównyc w kontrolce suwaka.

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>Parametry

*nTic*<br/>
Liczony od zera indeks, identyfikowanie znacznika.

### <a name="return-value"></a>Wartość zwracana

Położenie określonego znacznika lub - 1, jeśli *nTic* nie określa prawidłowy indeks.

##  <a name="getticarray"></a>  CSliderCtrl::GetTicArray

Pobiera adres tablicę zawierającą pozycje znaczniki osi dla kontrolki suwaka.

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres tablicę zawierającą stanowisk znacznik osi dla kontrolki suwaka.

##  <a name="getticpos"></a>  CSliderCtrl::GetTicPos

Pobiera bieżącą pozycję fizycznych znacznika w kontrolce suwaka.

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>Parametry

*nTic*<br/>
Liczony od zera indeks, identyfikowanie znacznika.

### <a name="return-value"></a>Wartość zwracana

Fizyczne położenie, we współrzędnych klienta określonego znacznika lub - 1, jeśli *nTic* nie określa prawidłowy indeks.

##  <a name="gettooltips"></a>  CSliderCtrl::GetToolTips

Pobiera dojścia do kontrolki tooltip przypisany do kontrolki suwaka, jeśli istnieje.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) obiekt lub wartość NULL, jeśli etykietki narzędzi nie są używane. Użycie kontrolki suwaka nie styl TBS_TOOLTIPS, wartość zwracana jest wartość NULL.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TBM_GETTOOLTIPS](/windows/desktop/Controls/tbm-gettooltips), zgodnie z opisem w zestawie Windows SDK. Należy zauważyć, że ta funkcja elementu członkowskiego zwraca `CToolTipCtrl` obiektu zamiast dojścia do formantu.

Aby uzyskać opis style formantu suwaka, zobacz [style kontrolki Trackbar](/windows/desktop/Controls/trackbar-control-styles) w zestawie Windows SDK.

##  <a name="setbuddy"></a>  CSliderCtrl::SetBuddy

Przypisuje okna jako okno cyklu kontrolki suwaka.

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>Parametry

*pWndBuddy*<br/>
Wskaźnik do `CWnd` obiekt, który zostanie ustawiony jako buddy formant suwaka.

*fLocation*<br/>
Wartość określająca lokalizację, w której będzie wyświetlać okno buddy. Ta wartość może być jedną z następujących czynności:

- Wartość TRUE, znajomy pojawia się po lewej stronie trackbar gdy trackbar, kontrolka używa stylu TBS_HORZ. Jeśli pasek śledzenia używa stylu TBS_VERT, znajomy pojawia się powyżej TrackBar — formant.

- FALSE buddy pojawia się po prawej stronie trackbar gdy trackbar, kontrolka używa stylu TBS_HORZ. Jeśli pasek śledzenia używa stylu TBS_VERT, znajomy pojawia się poniżej TrackBar — formant.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu, który wcześniej został przypisany do kontrolki suwaka w tej lokalizacji.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TBM_SETBUDDY](/windows/desktop/Controls/tbm-setbuddy), zgodnie z opisem w zestawie Windows SDK. Należy pamiętać, że ta funkcja członkowska używa wskaźników do `CWnd` obiektów, a nie obsługuje okno zarówno jego zwracanej wartości, jak i parametr.

Aby uzyskać opis style formantu suwaka, zobacz [style kontrolki Trackbar](/windows/desktop/Controls/trackbar-control-styles) w zestawie Windows SDK.

##  <a name="setlinesize"></a>  CSliderCtrl::SetLineSize

Ustawia rozmiar linii dla kontrolki suwaka.

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
Nowy rozmiar wiersza kontrolki suwaka.

### <a name="return-value"></a>Wartość zwracana

Poprzedni rozmiar wiersza.

### <a name="remarks"></a>Uwagi

Rozmiar wiersza wpływa na tym, ile suwak przenosi TB_LINEUP i TB_LINEDOWN powiadomienia.

##  <a name="setpagesize"></a>  CSliderCtrl::SetPageSize

Ustawia rozmiar strony dla kontrolki suwaka.

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
Nowy rozmiar strony kontrolki suwaka.

### <a name="return-value"></a>Wartość zwracana

Poprzednie rozmiar strony.

### <a name="remarks"></a>Uwagi

Wpływa na rozmiar strony, ile suwak przenosi TB_PAGEUP i TB_PAGEDOWN powiadomienia.

##  <a name="setpos"></a>  CSliderCtrl::SetPos

Ustawia bieżące położenie suwaka w kontrolce suwaka.

```
void SetPos(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Określa nowe położenie suwaka.

##  <a name="setrange"></a>  CSliderCtrl::SetRange

Ustawia zakres (pozycje minimalne i maksymalne) suwaka w kontrolce suwaka.

```
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*Nmin.*<br/>
Minimalna położenie suwaka.

*nmaks.*<br/>
Maksymalna położenie suwaka.

*bRedraw*<br/>
Flaga ustawiana, ponownego wystawiania. Jeśli ten parametr ma wartość TRUE, suwak jest odświeżana, po ustawieniu zakresu; w przeciwnym razie nie jest rysowane suwaka.

##  <a name="setrangemax"></a>  CSliderCtrl::SetRangeMax

Ustawia maksymalną wielkość zakresu suwaka w kontrolce suwaka.

```
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*nmaks.*<br/>
Maksymalna położenie suwaka.

*bRedraw*<br/>
Flaga ustawiana, ponownego wystawiania. Jeśli ten parametr ma wartość TRUE, suwak jest odświeżana, po ustawieniu zakresu; w przeciwnym razie nie jest rysowane suwaka.

##  <a name="setrangemin"></a>  CSliderCtrl::SetRangeMin

Ustawia zakresu minimalnego suwaka w kontrolce suwaka.

```
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*Nmin.*<br/>
Minimalna położenie suwaka.

*bRedraw*<br/>
Flaga ustawiana, ponownego wystawiania. Jeśli ten parametr ma wartość TRUE, suwak jest odświeżana, po ustawieniu zakresu; w przeciwnym razie nie jest rysowane suwaka.

##  <a name="setselection"></a>  CSliderCtrl::SetSelection

Ustawia położenie datę początkową i końcową dla bieżącego zaznaczenia w kontrolce suwaka.

```
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*Nmin.*<br/>
Pozycja początkowa suwaka.

*nmaks.*<br/>
Pozycja końcowa dla suwaka.

##  <a name="setthumblength"></a>  CSliderCtrl::SetThumbLength

Ustawia długość suwak w bieżącym TrackBar — formant.

```
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*nLength*|[in] Długość suwaka, w pikselach.|

### <a name="remarks"></a>Uwagi

Ta metoda wymaga, że trackbar, kontrolka być równa [TBS_FIXEDLENGTH](/windows/desktop/Controls/trackbar-control-styles) stylu.

Ta metoda wysyła [TBM_SETTHUMBLENGTH](/windows/desktop/Controls/tbm-setthumblength) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

Poniższy kod definiuje zmienną, `m_sliderCtrl`, to znaczy umożliwiają dostęp do bieżącego TrackBar — formant. W przykładzie zdefiniowano też zmiennej, która `thumbLength`, która jest używana do przechowywania domyślna długość TrackBar — formant przycisku przewijania składnika. Te zmienne są używane w następnym przykładzie.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia TrackBar — formant przycisku przewijania składnika dwukrotnie jego domyślna długość.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

##  <a name="settic"></a>  CSliderCtrl::SetTic

Ustawia położenie znaczników głównyc w kontrolce suwaka.

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>Parametry

*nTic*<br/>
Położenie znaczników głównyc. Ten parametr należy określić wartość dodatnią.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli ustawiono wartość znacznika; w przeciwnym razie 0.

##  <a name="setticfreq"></a>  CSliderCtrl::SetTicFreq

Określa częstotliwość, z znaczników, które są widoczne w suwaka.

```
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>Parametry

*nFreq*<br/>
Częstotliwość znaczników.

### <a name="remarks"></a>Uwagi

Na przykład jeśli częstotliwość wynosi 2, co inne przyrostem suwaka zakresu jest wyświetlany znacznika. Ustawienie domyślne, częstotliwość to 1 (co przyrostu w zakresie jest skojarzony ze znakiem znacznika).

Należy utworzyć kontrolkę ze stylem TBS_AUTOTICKS, aby użyć tej funkcji. Aby uzyskać więcej informacji, zobacz [CSliderCtrl::Create](#create).

##  <a name="settipside"></a>  CSliderCtrl::SetTipSide

Położenie formantu etykietki narzędzia używane przez TrackBar — formant.

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>Parametry

*Nlokalizacja*<br/>
Wartość reprezentująca lokalizację, w której do wyświetlania kontrolki tooltip. Aby uzyskać listę możliwych wartości, zobacz komunikat Win32 [TBM_SETTIPSIDE](/windows/desktop/Controls/tbm-settipside), zgodnie z opisem w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wartość, która reprezentuje poprzedniej lokalizacji kontrolki tooltip. Wartość zwracana równa się jedną z możliwych wartości dla *Nlokalizacja*.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 TBM_SETTIPSIDE, zgodnie z opisem w zestawie Windows SDK. Formanty suwaka, które używają stylu TBS_TOOLTIPS wyświetlanie etykietek narzędzi. Aby uzyskać opis style formantu suwaka, zobacz [style kontrolki Trackbar](/windows/desktop/Controls/trackbar-control-styles) w zestawie Windows SDK.

##  <a name="settooltips"></a>  CSliderCtrl::SetToolTips

Przypisuje kontrolkę etykiety narzędzia do kontrolki suwaka.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parametry

*pWndTip*<br/>
Wskaźnik do [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) obiekt zawierający etykietek narzędzi za pomocą suwaka.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TBM_SETTOOLTIPS](/windows/desktop/Controls/tbm-settooltips), zgodnie z opisem w zestawie Windows SDK. Po utworzeniu kontrolki suwaka ze stylem TBS_TOOLTIPS tworzy domyślny formant etykietki narzędzia, która pojawia się obok suwaka, wyświetlanie bieżące położenie suwaka. Aby uzyskać opis style formantu suwaka, zobacz [style kontrolki Trackbar](/windows/desktop/Controls/trackbar-control-styles) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz także

[CMNCTRL2 próbki MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Diagram hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl Class](../../mfc/reference/cprogressctrl-class.md)
