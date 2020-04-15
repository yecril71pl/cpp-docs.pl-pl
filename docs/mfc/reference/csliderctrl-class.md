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
ms.openlocfilehash: 24e1cb18f979d1144f15cf6ffedc6cace5f5361e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318212"
---
# <a name="csliderctrl-class"></a>Klasa CSliderCtrl

Udostępnia funkcje formantu suwaka wspólnego systemu Windows.

## <a name="syntax"></a>Składnia

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|Konstruuje `CSliderCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSliderCtrl::ClearSel](#clearsel)|Czyści bieżące zaznaczenie w formancie suwaka.|
|[CSliderCtrl::ClearTics](#cleartics)|Usuwa bieżące znaczniki osi z kontrolki suwaka.|
|[CSliderCtrl::Tworzenie](#create)|Tworzy kontrolkę suwaka i `CSliderCtrl` dołącza ją do obiektu.|
|[CSliderCtrl::CreateEx](#createex)|Tworzy kontrolkę suwaka z określonymi stylami rozszerzonymi systemu Windows i dołącza ją do `CSliderCtrl` obiektu.|
|[CSliderCtrl::GetBuddy](#getbuddy)|Pobiera dojście do okna buddy formantu suwaka w danej lokalizacji.|
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Pobiera rozmiar kanału formantu suwaka.|
|[CSliderCtrl::GetLineSize](#getlinesize)|Pobiera rozmiar linii formantu suwaka.|
|[CSliderCtrl::GetNumTics](#getnumtics)|Pobiera liczbę znaczników osi w formancie suwaka.|
|[CSliderCtrl::GetPageSize](#getpagesize)|Pobiera rozmiar strony kontrolki suwaka.|
|[CSliderCtrl::GetPos](#getpos)|Pobiera bieżącą pozycję suwaka.|
|[CSliderCtrl::GetRange](#getrange)|Pobiera minimalne i maksymalne pozycje dla suwaka.|
|[CSliderCtrl::GetRangeMax](#getrangemax)|Pobiera maksymalną pozycję suwaka.|
|[CSliderCtrl::GetRangeMin](#getrangemin)|Pobiera minimalną pozycję suwaka.|
|[CSliderCtrl::GetSelection](#getselection)|Pobiera zakres bieżącego zaznaczenia.|
|[CSliderCtrl::GetThumbLength](#getthumblength)|Pobiera długość suwaka w bieżącym formancie paska gąsienic.|
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Pobiera rozmiar kciuka formantu suwaka.|
|[CSliderCtrl::GetTic](#gettic)|Pobiera położenie określonego znacznika osi.|
|[CSliderCtrl::GetTicArray](#getticarray)|Pobiera tablicę pozycji znaczników osi dla formantu suwaka.|
|[CSliderCtrl::GetTicPos](#getticpos)|Pobiera położenie określonego znacznika osi w współrzędnych klienta.|
|[CSliderCtrl::Porady dotyczące właściwości GetTool](#gettooltips)|Pobiera uchwyt do formantu etykietki narzędzia przypisanej do formantu suwaka, jeśli istnieje.|
|[CSliderCtrl::SetBuddy](#setbuddy)|Przypisuje okno jako okno buddy dla kontrolki suwaka.|
|[CSliderCtrl::SetLineSize](#setlinesize)|Ustawia rozmiar linii suwaka.|
|[CSliderCtrl::SetPageSize](#setpagesize)|Ustawia rozmiar strony kontrolki suwaka.|
|[CSliderCtrl::SetPos](#setpos)|Ustawia bieżącą pozycję suwaka.|
|[CSliderCtrl::SetRange](#setrange)|Ustawia minimalne i maksymalne pozycje dla suwaka.|
|[CSliderCtrl::SetRangeMax](#setrangemax)|Ustawia maksymalną pozycję suwaka.|
|[CSliderCtrl::SetRangeMin](#setrangemin)|Ustawia minimalną pozycję suwaka.|
|[CSliderCtrl::SetSelection](#setselection)|Ustawia zakres bieżącego zaznaczenia.|
|[CSliderCtrl::SetThumbLength](#setthumblength)|Ustawia długość suwaka w bieżącym formancie paska gąsienic.|
|[CSliderCtrl::SetTic](#settic)|Ustawia położenie określonego znacznika osi.|
|[CSliderCtrl::SetTicFreq](#setticfreq)|Ustawia częstotliwość znaczników osi na przyrost formantu suwaka.|
|[CSliderCtrl::SetTipSide](#settipside)|Umieszcza formant etykietki narzędzia używany przez kontrolkę paska gąsienic.|
|[CSliderCtrl::SetToolTips](#settooltips)|Przypisuje kontrolkę etykietki narzędzia do formantu suwaka.|

## <a name="remarks"></a>Uwagi

"Kontrolka suwaka" (znana również jako trackbar) to okno zawierające suwak i opcjonalne znaczniki osi. Gdy użytkownik przesuwa suwak, za pomocą myszy lub klawiszy kierunku, formant wysyła komunikaty powiadomień, aby wskazać zmiany.

Kontrolki suwaka są przydatne, gdy użytkownik ma wybrać wartość dyskretną lub zestaw kolejnych wartości w zakresie. Na przykład można użyć suwaka, aby umożliwić użytkownikowi ustawienie częstotliwości powtarzania klawiatury przez przeniesienie suwaka do danego znacznika osi.

Ten formant (i `CSliderCtrl` dlatego klasa) jest dostępny tylko dla programów działających w systemach Windows 95/98 i Windows NT w wersji 3.51 lub nowszych.

Suwak przesuwa się w przyrostach określonych podczas jego tworzenia. Na przykład jeśli określisz, że suwak powinien mieć zakres pięciu, suwak może zajmować tylko sześć pozycji: położenie po lewej stronie suwaka i jedną pozycję dla każdego przyrostu w zakresie. Zazwyczaj każda z tych pozycji jest identyfikowana za pomocą znacznika osi.

Suwak jest tworzęny przy użyciu `Create` konstruktora i funkcji elementu członkowskiego `CSliderCtrl`programu . Po utworzeniu formantu suwaka można użyć `CSliderCtrl` funkcji członkowskich, aby zmienić wiele jego właściwości. Zmiany, które można wprowadzić, obejmują ustawienie minimalnej i maksymalnej pozycji suwaka, rysowanie znaczników osi, ustawianie zakresu zaznaczeń i zmianę położenia suwaka.

Aby uzyskać więcej `CSliderCtrl`informacji na temat używania , zobacz [Formanty](../../mfc/controls-mfc.md) i [Korzystanie z CSliderCtrl](../../mfc/using-csliderctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="csliderctrlclearsel"></a><a name="clearsel"></a>CSliderCtrl::ClearSel

Czyści bieżące zaznaczenie w formancie suwaka.

```
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*bRedraw*<br/>
Przerysuj flagę. Jeśli ten parametr ma wartość PRAWDA, suwak jest ponownie rysowany po wyczyszczeniu zaznaczenia; w przeciwnym razie suwak nie zostanie ponownie narysowany.

## <a name="csliderctrlcleartics"></a><a name="cleartics"></a>CSliderCtrl::ClearTics

Usuwa bieżące znaczniki osi z kontrolki suwaka.

```
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*bRedraw*<br/>
Przerysuj flagę. Jeśli ten parametr ma wartość PRAWDA, suwak jest ponownie rysowany po usunięciu znaczników osi; w przeciwnym razie suwak nie zostanie ponownie narysowany.

## <a name="csliderctrlcreate"></a><a name="create"></a>CSliderCtrl::Tworzenie

Tworzy kontrolkę suwaka i `CSliderCtrl` dołącza ją do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa styl formantu suwaka. Zastosuj dowolną kombinację [stylów sterowania suwakiem,](/windows/win32/Controls/trackbar-control-styles)opisaną w panelu Windows SDK, do formantu.

*Rect*<br/>
Określa rozmiar i położenie formantu suwaka. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [struktura RECT.](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Określa okno nadrzędne formantu suwaka, zwykle `CDialog`. Nie może być null.

*Nid*<br/>
Określa identyfikator formantu suwaka.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruujesz `CSliderCtrl` w dwóch krokach. Najpierw wywołaj konstruktora, `Create`a następnie wywołaj , co tworzy `CSliderCtrl` kontrolka suwaka i dołącza go do obiektu.

W zależności od wartości ustawionych dla *dwStyle,* suwak może mieć orientację pionową lub poziomą. Może mieć znaczniki osi po obu stronach, po obu stronach lub po obu stronach. Może również służyć do określania zakresu kolejnych wartości.

Aby zastosować rozszerzone style okien do suwaka, należy `Create` [wywołać createex](#createex) zamiast .

## <a name="csliderctrlcreateex"></a><a name="createex"></a>CSliderCtrl::CreateEx

Tworzy formant (okno podrzędne) i `CSliderCtrl` kojarzy go z obiektem.

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
Określa styl formantu suwaka. Zastosuj dowolną kombinację [stylów sterowania suwakiem,](/windows/win32/Controls/trackbar-control-styles)opisaną w panelu Windows SDK, do formantu.

*Rect*<br/>
Odwołanie do struktury [RECT](/previous-versions/dd162897\(v=vs.85\)) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest nadrzędnym formantu.

*Nid*<br/>
Identyfikator okna podrzędnego formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [Create,](#create) aby zastosować rozszerzone style systemu Windows, określone przez przedmową styl rozszerzony systemu Windows **WS_EX_**.

## <a name="csliderctrlcsliderctrl"></a><a name="csliderctrl"></a>CSliderCtrl::CSliderCtrl

Konstruuje `CSliderCtrl` obiekt.

```
CSliderCtrl();
```

## <a name="csliderctrlgetbuddy"></a><a name="getbuddy"></a>CSliderCtrl::GetBuddy

Pobiera dojście do okna buddy formantu suwaka w danej lokalizacji.

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>Parametry

*fLokacja*<br/>
Wartość logiczna, która wskazuje, które z dwóch uchwytów okna buddy do pobrania. Może być jedną z następujących wartości:

- Funkcja TRUE pobiera uchwyt do kumpla po lewej stronie suwaka. Jeśli suwak używa stylu TBS_VERT, wiadomość zostanie pobrana kumpel nad suwakiem.

- FALSE Pobiera dojście do kumpla po prawej stronie suwaka. Jeśli suwak używa stylu TBS_VERT, wiadomość spowoduje pobranie znajomego poniżej suwaka.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CWnd,](../../mfc/reference/cwnd-class.md) który jest oknem buddy w lokalizacji określonej przez *fLocation*lub NULL, jeśli w tej lokalizacji nie istnieje żadne okno buddy.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy)komunikatu Win32, zgodnie z opisem w windows SDK. Aby uzyskać opis stylów sterowania suwakiem, zobacz [Style sterowania pasków gładów](/windows/win32/Controls/trackbar-control-styles) w zestaw Windows SDK.

## <a name="csliderctrlgetchannelrect"></a><a name="getchannelrect"></a>CSliderCtrl::GetChannelRect

Pobiera rozmiar i położenie prostokąta ograniczającego dla kanału formantu suwaka.

```
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parametry

*lprc (ł.*<br/>
Wskaźnik do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu, który zawiera rozmiar i położenie prostokąta ograniczającego kanału po powrocie funkcji.

### <a name="remarks"></a>Uwagi

Kanał jest obszarem, nad którym przesuwa się suwak i który zawiera podświetlenie po wybraniu zakresu.

## <a name="csliderctrlgetlinesize"></a><a name="getlinesize"></a>CSliderCtrl::GetLineSize

Pobiera rozmiar linii dla formantu suwaka.

```
int GetLineSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar linii dla suwaka.

### <a name="remarks"></a>Uwagi

Rozmiar wiersza wpływa na to, jak bardzo suwak przesuwa się dla powiadomień TB_LINEUP i TB_LINEDOWN. Domyślnym ustawieniem rozmiaru linii jest 1.

## <a name="csliderctrlgetnumtics"></a><a name="getnumtics"></a>CSliderCtrl::GetNumTics

Pobiera liczbę znaczników osi w formancie suwaka.

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaczników osi w formancie suwaka.

## <a name="csliderctrlgetpagesize"></a><a name="getpagesize"></a>CSliderCtrl::GetPageSize

Pobiera rozmiar strony dla kontrolki suwaka.

```
int GetPageSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar strony dla suwaka.

### <a name="remarks"></a>Uwagi

Rozmiar strony wpływa na to, jak bardzo suwak zostanie przeniesiony dla powiadomień TB_PAGEUP i TB_PAGEDOWN.

## <a name="csliderctrlgetpos"></a><a name="getpos"></a>CSliderCtrl::GetPos

Pobiera bieżącą pozycję suwaka w formancie suwaka.

```
int GetPos() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca pozycja.

## <a name="csliderctrlgetrange"></a><a name="getrange"></a>CSliderCtrl::GetRange

Pobiera maksymalne i minimalne pozycje suwaka w suwaku.

```
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parametry

*nMin (min.*<br/>
Odwołanie do liczby całkowitej, która otrzymuje minimalną pozycję.

*Nmax*<br/>
Odwołanie do liczby całkowitej, która odbiera maksymalną pozycję.

### <a name="remarks"></a>Uwagi

Ta funkcja kopiuje wartości do liczby całkowite, do których odwołują się *nMin* i *nMax*.

## <a name="csliderctrlgetrangemax"></a><a name="getrangemax"></a>CSliderCtrl::GetRangeMax

Pobiera maksymalną pozycję suwaka w formancie suwaka.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna pozycja formantu.

## <a name="csliderctrlgetrangemin"></a><a name="getrangemin"></a>CSliderCtrl::GetRangeMin

Pobiera minimalną pozycję suwaka w formancie suwaka.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Wartość zwracana

Minimalna pozycja formantu.

## <a name="csliderctrlgetselection"></a><a name="getselection"></a>CSliderCtrl::GetSelection

Pobiera pozycje początkowe i końcowe bieżącego zaznaczenia w formancie suwaka.

```
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parametry

*nMin (min.*<br/>
Odwołanie do liczby całkowitej, która odbiera pozycję początkową bieżącego zaznaczenia.

*Nmax*<br/>
Odwołanie do liczby całkowitej, która odbiera pozycję końcową bieżącego zaznaczenia.

## <a name="csliderctrlgetthumblength"></a><a name="getthumblength"></a>CSliderCtrl::GetThumbLength

Pobiera długość suwaka w bieżącym formancie paska gąsienic.

```
int GetThumbLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość suwaka w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [TBM_GETTHUMBLENGTH,](/windows/win32/Controls/tbm-getthumblength) który jest opisany w windows SDK.

## <a name="csliderctrlgetthumbrect"></a><a name="getthumbrect"></a>CSliderCtrl::GetThumbRect

Pobiera rozmiar i położenie prostokąta ograniczającego dla suwaka (kciuka) w formancie suwaka.

```
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parametry

*lprc (ł.*<br/>
Wskaźnik do `CRect` obiektu, który zawiera prostokąt ograniczający dla suwaka po powrocie funkcji.

## <a name="csliderctrlgettic"></a><a name="gettic"></a>CSliderCtrl::GetTic

Pobiera położenie znacznika osi w formancie suwaka.

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>Parametry

*nTic (Niem.*<br/>
Indeks od zera identyfikujący znacznik osi.

### <a name="return-value"></a>Wartość zwracana

Położenie określonego znacznika osi lub - 1 if *nTic* nie określa prawidłowego indeksu.

## <a name="csliderctrlgetticarray"></a><a name="getticarray"></a>CSliderCtrl::GetTicArray

Pobiera adres tablicy zawierającej pozycje znaczników osi dla formantu suwaka.

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres tablicy zawierającej pozycje znaczników osi dla formantu suwaka.

## <a name="csliderctrlgetticpos"></a><a name="getticpos"></a>CSliderCtrl::GetTicPos

Pobiera bieżącą pozycję fizyczną znacznika osi w formancie suwaka.

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>Parametry

*nTic (Niem.*<br/>
Indeks od zera identyfikujący znacznik osi.

### <a name="return-value"></a>Wartość zwracana

Położenie fizyczne, we współrzędnych klienta, określonego znacznika osi lub - 1, jeśli *nTic* nie określa prawidłowego indeksu.

## <a name="csliderctrlgettooltips"></a><a name="gettooltips"></a>CSliderCtrl::Porady dotyczące właściwości GetTool

Pobiera uchwyt do formantu etykietki narzędzia przypisanej do formantu suwaka, jeśli istnieje.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) lub NULL, jeśli etykietki narzędzi nie są używane. Jeśli suwak nie używa stylu TBS_TOOLTIPS, zwracaną wartością jest NULL.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips)komunikatu Win32, zgodnie z opisem w windows SDK. Należy zauważyć, że `CToolTipCtrl` ta funkcja elementu członkowskiego zwraca obiekt zamiast dojścia do formantu.

Aby uzyskać opis stylów sterowania suwakiem, zobacz [Style sterowania pasków gładów](/windows/win32/Controls/trackbar-control-styles) w zestaw Windows SDK.

## <a name="csliderctrlsetbuddy"></a><a name="setbuddy"></a>CSliderCtrl::SetBuddy

Przypisuje okno jako okno buddy dla kontrolki suwaka.

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>Parametry

*pWndBuddy*<br/>
Wskaźnik do `CWnd` obiektu, który zostanie ustawiony jako kumpel formantu suwaka.

*fLokacja*<br/>
Wartość określająca lokalizację, w której ma być wyświetlane okno buddy. Ta wartość może być jedną z następujących wartości:

- PRAWDA Kumpel pojawi się po lewej stronie paska dresu, jeśli kontrolka paska ścieżki używa stylu TBS_HORZ. Jeśli trackbar używa stylu TBS_VERT, kumpel pojawia się nad kontrolkią paska ścieżki.

- FALSE Kumpel pojawi się po prawej stronie paska gąsienic, jeśli kontrolka paska ścieżek używa stylu TBS_HORZ. Jeśli trackbar używa stylu TBS_VERT, kumpel pojawia się poniżej kontrolki paska ścieżki.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CWnd,](../../mfc/reference/cwnd-class.md) który został wcześniej przypisany do suwaka w tej lokalizacji.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy)komunikatu Win32, zgodnie z opisem w windows SDK. Należy zauważyć, że ta funkcja `CWnd` elementu członkowskiego używa wskaźników do obiektów, a nie dojścia okna dla jego zwracanej wartości i parametru.

Aby uzyskać opis stylów sterowania suwakiem, zobacz [Style sterowania pasków gładów](/windows/win32/Controls/trackbar-control-styles) w zestaw Windows SDK.

## <a name="csliderctrlsetlinesize"></a><a name="setlinesize"></a>CSliderCtrl::SetLineSize

Ustawia rozmiar linii dla suwaka.

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize (rozmiar)*<br/>
Nowy rozmiar linii suwaka.

### <a name="return-value"></a>Wartość zwracana

Poprzedni rozmiar wiersza.

### <a name="remarks"></a>Uwagi

Rozmiar wiersza wpływa na to, jak bardzo suwak przesuwa się dla powiadomień TB_LINEUP i TB_LINEDOWN.

## <a name="csliderctrlsetpagesize"></a><a name="setpagesize"></a>CSliderCtrl::SetPageSize

Ustawia rozmiar strony dla suwaka.

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize (rozmiar)*<br/>
Nowy rozmiar strony suwaka.

### <a name="return-value"></a>Wartość zwracana

Poprzedni rozmiar strony.

### <a name="remarks"></a>Uwagi

Rozmiar strony wpływa na to, jak bardzo suwak zostanie przeniesiony dla powiadomień TB_PAGEUP i TB_PAGEDOWN.

## <a name="csliderctrlsetpos"></a><a name="setpos"></a>CSliderCtrl::SetPos

Ustawia bieżącą pozycję suwaka w suwaku.

```
void SetPos(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Określa nową pozycję suwaka.

## <a name="csliderctrlsetrange"></a><a name="setrange"></a>CSliderCtrl::SetRange

Ustawia zakres (pozycje minimalne i maksymalne) dla suwaka w suwaku.

```
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*nMin (min.*<br/>
Minimalna pozycja suwaka.

*Nmax*<br/>
Maksymalna pozycja suwaka.

*bRedraw*<br/>
Flaga ponownego rysowania. Jeśli ten parametr ma wartość PRAWDA, suwak jest ponownie rysowany po ustawieniu zakresu; w przeciwnym razie suwak nie zostanie ponownie narysowany.

## <a name="csliderctrlsetrangemax"></a><a name="setrangemax"></a>CSliderCtrl::SetRangeMax

Ustawia maksymalny zakres suwaka w formancie suwaka.

```
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*Nmax*<br/>
Maksymalna pozycja suwaka.

*bRedraw*<br/>
Flaga ponownego rysowania. Jeśli ten parametr ma wartość PRAWDA, suwak jest ponownie rysowany po ustawieniu zakresu; w przeciwnym razie suwak nie zostanie ponownie narysowany.

## <a name="csliderctrlsetrangemin"></a><a name="setrangemin"></a>CSliderCtrl::SetRangeMin

Ustawia minimalny zakres suwaka w formancie suwaka.

```
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*nMin (min.*<br/>
Minimalna pozycja suwaka.

*bRedraw*<br/>
Flaga ponownego rysowania. Jeśli ten parametr ma wartość PRAWDA, suwak jest ponownie rysowany po ustawieniu zakresu; w przeciwnym razie suwak nie zostanie ponownie narysowany.

## <a name="csliderctrlsetselection"></a><a name="setselection"></a>CSliderCtrl::SetSelection

Ustawia pozycje początkowe i końcowe dla bieżącego zaznaczenia w formancie suwaka.

```
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin (min.*<br/>
Pozycja początkowa suwaka.

*Nmax*<br/>
Pozycja końcowa suwaka.

## <a name="csliderctrlsetthumblength"></a><a name="setthumblength"></a>CSliderCtrl::SetThumbLength

Ustawia długość suwaka w bieżącym formancie paska gąsienic.

```
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*nLength (nLength)*|[w] Długość suwaka w pikselach.|

### <a name="remarks"></a>Uwagi

Ta metoda wymaga, aby kontrolka paska ścieżki została ustawiona [na TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles) stylu.

Ta metoda wysyła [komunikat TBM_SETTHUMBLENGTH,](/windows/win32/Controls/tbm-setthumblength) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_sliderCtrl`zmienną , która jest używana do uzyskania dostępu do bieżącego formantu paska gładka. W przykładzie zdefiniowano `thumbLength`również zmienną , która jest używana do przechowywania domyślnej długości składnika kciuka formantu trackbar. Te zmienne są używane w następnym przykładzie.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia składnik kciuka formantu trackbara na dwukrotnie większą niż domyślna długość.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

## <a name="csliderctrlsettic"></a><a name="settic"></a>CSliderCtrl::SetTic

Ustawia położenie znacznika w formancie suwaka.

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>Parametry

*nTic (Niem.*<br/>
Położenie znacznika osi. Ten parametr musi określać wartość dodatnią.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli znacznik osi jest ustawiony; w przeciwnym razie 0.

## <a name="csliderctrlsetticfreq"></a><a name="setticfreq"></a>CSliderCtrl::SetTicFreq

Ustawia częstotliwość wyświetlania znaczników osi na suwaku.

```
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>Parametry

*nFreq (*<br/>
Częstotliwość znaczników osi.

### <a name="remarks"></a>Uwagi

Na przykład jeśli częstotliwość jest ustawiona na 2, znacznik osi jest wyświetlany dla każdego innego przyrostu w zakresie suwaka. Domyślnym ustawieniem częstotliwości jest 1 (oznacza to, że każdy przyrost w zakresie jest skojarzony ze znacznikiem osi).

Aby użyć tej funkcji, należy utworzyć formant ze stylem TBS_AUTOTICKS. Aby uzyskać więcej informacji, zobacz [CSliderCtrl::Create](#create).

## <a name="csliderctrlsettipside"></a><a name="settipside"></a>CSliderCtrl::SetTipSide

Umieszcza formant etykietki narzędzia używany przez kontrolkę paska gąsienic.

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>Parametry

*nLokacja*<br/>
Wartość reprezentująca lokalizację, w której ma być wyświetlana kontrolka etykietki narzędzia. Aby uzyskać listę możliwych wartości, zobacz komunikat Win32 [TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside), zgodnie z opisem w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wartość reprezentująca poprzednią lokalizację formantu etykietki narzędzia. Zwracana wartość jest równa jednej z możliwych wartości dla *nLocation*.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie TBM_SETTIPSIDE komunikatu Win32, zgodnie z opisem w windows SDK. Suwake, które używają etykietek narzędzi wyświetlania stylu TBS_TOOLTIPS. Aby uzyskać opis stylów sterowania suwakiem, zobacz [Style sterowania pasków gładów](/windows/win32/Controls/trackbar-control-styles) w zestaw Windows SDK.

## <a name="csliderctrlsettooltips"></a><a name="settooltips"></a>CSliderCtrl::SetToolTips

Przypisuje kontrolkę etykietki narzędzia do formantu suwaka.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parametry

*pWdTip*<br/>
Wskaźnik do [obiektu CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) zawierającego etykietki narzędzi do użycia z kontrolką suwaka.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips)komunikatu Win32, zgodnie z opisem w windows SDK. Po utworzeniu suwaka w stylu TBS_TOOLTIPS tworzy domyślną kontrolkę etykietki narzędzia, która pojawia się obok suwaka, wyświetlając bieżącą pozycję suwaka. Aby uzyskać opis stylów sterowania suwakiem, zobacz [Style sterowania pasków gładów](/windows/win32/Controls/trackbar-control-styles) w zestaw Windows SDK.

## <a name="see-also"></a>Zobacz też

[Próbka MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CProgressCtrl](../../mfc/reference/cprogressctrl-class.md)
