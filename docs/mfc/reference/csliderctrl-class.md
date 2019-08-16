---
title: Klasa korzystanie CSliderCtrl
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
ms.openlocfilehash: 8fffdfc002b25fdcd72dcbbf53e7e6c321f55296
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502519"
---
# <a name="csliderctrl-class"></a>Klasa korzystanie CSliderCtrl

Oferuje funkcje formantu typowego suwaka systemu Windows.

## <a name="syntax"></a>Składnia

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Korzystanie CSliderCtrl:: Korzystanie CSliderCtrl](#csliderctrl)|Konstruuje `CSliderCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Korzystanie CSliderCtrl:: ClearSel](#clearsel)|Czyści bieżące zaznaczenie w kontrolce suwaka.|
|[Korzystanie CSliderCtrl:: ClearTics](#cleartics)|Usuwa bieżące znaczniki z kontrolki suwaka.|
|[Korzystanie CSliderCtrl:: Create](#create)|Tworzy kontrolkę suwaka i dołącza ją do `CSliderCtrl` obiektu.|
|[Korzystanie CSliderCtrl:: CreateEx](#createex)|Tworzy kontrolkę suwaka z określonymi stylami rozszerzonymi systemu Windows i dołącza ją `CSliderCtrl` do obiektu.|
|[CSliderCtrl::GetBuddy](#getbuddy)|Pobiera uchwyt do okna kontrolki suwaka kolega w danej lokalizacji.|
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Pobiera rozmiar kanału kontrolki suwak.|
|[CSliderCtrl::GetLineSize](#getlinesize)|Pobiera rozmiar linii kontrolki suwaka.|
|[CSliderCtrl::GetNumTics](#getnumtics)|Pobiera liczbę znaczników w kontrolce suwaka.|
|[CSliderCtrl::GetPageSize](#getpagesize)|Pobiera rozmiar strony kontrolki suwaka.|
|[Korzystanie CSliderCtrl:: GetPos](#getpos)|Pobiera bieżącą pozycję suwaka.|
|[Korzystanie CSliderCtrl:: GetRange](#getrange)|Pobiera minimalną i maksymalną pozycję suwaka.|
|[Korzystanie CSliderCtrl:: GetRangeMax](#getrangemax)|Pobiera maksymalną pozycję suwaka.|
|[Korzystanie CSliderCtrl:: GetRangeMin](#getrangemin)|Pobiera minimalną pozycję suwaka.|
|[Korzystanie CSliderCtrl:: getselecting](#getselection)|Pobiera zakres bieżącego zaznaczenia.|
|[Korzystanie CSliderCtrl:: GetThumbLength](#getthumblength)|Pobiera długość suwaka w bieżącej kontrolce TrackBar.|
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Pobiera rozmiar przycisku przewijania kontrolki suwaka.|
|[Korzystanie CSliderCtrl:: GetTic](#gettic)|Pobiera pozycję określonego znacznika.|
|[Korzystanie CSliderCtrl:: GetTicArray](#getticarray)|Pobiera tablicę pozycji znaczników znacznika dla kontrolki suwaka.|
|[Korzystanie CSliderCtrl:: GetTicPos](#getticpos)|Pobiera pozycję określonego znacznika we współrzędnych klienta.|
|[Korzystanie CSliderCtrl:: GetToolTips](#gettooltips)|Pobiera uchwyt do kontrolki ToolTip przypisanej do kontrolki suwak (jeśli istnieje).|
|[CSliderCtrl::SetBuddy](#setbuddy)|Przypisuje okno jako okno kolega dla kontrolki suwaka.|
|[CSliderCtrl::SetLineSize](#setlinesize)|Ustawia rozmiar linii kontrolki suwaka.|
|[CSliderCtrl::SetPageSize](#setpagesize)|Ustawia rozmiar strony kontrolki suwaka.|
|[CSliderCtrl::SetPos](#setpos)|Ustawia bieżącą pozycję suwaka.|
|[CSliderCtrl::SetRange](#setrange)|Ustawia minimalną i maksymalną liczbę pozycji suwaka.|
|[CSliderCtrl::SetRangeMax](#setrangemax)|Ustawia maksymalną pozycję suwaka.|
|[CSliderCtrl::SetRangeMin](#setrangemin)|Ustawia minimalną pozycję suwaka.|
|[Korzystanie CSliderCtrl:: setselecting](#setselection)|Ustawia zakres bieżącego zaznaczenia.|
|[Korzystanie CSliderCtrl:: SetThumbLength](#setthumblength)|Ustawia długość suwaka w bieżącej kontrolce TrackBar.|
|[Korzystanie CSliderCtrl:: SetTic](#settic)|Ustawia pozycję określonego znacznika.|
|[CSliderCtrl::SetTicFreq](#setticfreq)|Ustawia częstotliwość znaczników dla kontrolek suwaka.|
|[CSliderCtrl::SetTipSide](#settipside)|Ustawia kontrolkę etykietki narzędzia używaną przez formant TrackBar.|
|[Korzystanie CSliderCtrl:: setetykietki narzędzi](#settooltips)|Przypisuje formant etykietki narzędzia do kontrolki suwaka.|

## <a name="remarks"></a>Uwagi

"Kontrolka suwaka" (znana również jako TrackBar) to okno zawierające suwak i opcjonalne znaczniki. Gdy użytkownik przesuwa suwak przy użyciu myszy lub klawiszy kierunkowych, formant wysyła komunikaty powiadomień, aby wskazać zmianę.

Kontrolki suwaka są przydatne, gdy użytkownik chce wybrać wartość dyskretną lub zestaw kolejnych wartości z zakresu. Na przykład można użyć kontrolki suwaka, aby zezwolić użytkownikowi na ustawienie częstotliwości powtarzania klawiatury przez przesunięcie suwaka do danego znacznika.

Ten formant (i w związku `CSliderCtrl` z tym Klasa) jest dostępny tylko dla programów uruchomionych w systemach Windows 95/98 i Windows NT w wersji 3,51 lub nowszej.

Suwak przesuwa się w przyrostach, które zostały określone podczas tworzenia. Na przykład jeśli określisz, że suwak powinien mieć zakres pięciu, suwak może zajmować tylko sześć pozycji: położenie w lewej części kontrolki suwaka i jedną pozycję dla każdego przyrostu w zakresie. Zazwyczaj każda z tych pozycji jest identyfikowana za pomocą znacznika.

Tworzysz suwak przy użyciu konstruktora i `Create` `CSliderCtrl`funkcji składowej. Po utworzeniu kontrolki suwaka można użyć funkcji składowych w programie `CSliderCtrl` , aby zmienić wiele jej właściwości. Zmiany, które można wprowadzić, obejmują ustawienie minimalnej i maksymalnej liczby pozycji suwaka, rysowania znaczników, ustawienia zakresu zaznaczenia i zmiany położenia suwaka.

Aby uzyskać więcej informacji na `CSliderCtrl`temat korzystania z programu, zobacz [kontrolki](../../mfc/controls-mfc.md) i [Używanie korzystanie CSliderCtrl](../../mfc/using-csliderctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

##  <a name="clearsel"></a>Korzystanie CSliderCtrl:: ClearSel

Czyści bieżące zaznaczenie w kontrolce suwaka.

```
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*bRedraw*<br/>
Ponownie narysuj flagę. Jeśli ten parametr ma wartość TRUE, suwak jest rysowany ponownie po wyczyszczeniu zaznaczenia; w przeciwnym razie suwak nie jest ponownie rysowany.

##  <a name="cleartics"></a>Korzystanie CSliderCtrl:: ClearTics

Usuwa bieżące znaczniki z kontrolki suwaka.

```
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*bRedraw*<br/>
Ponownie narysuj flagę. Jeśli ten parametr ma wartość TRUE, suwak jest rysowany ponownie po wyczyszczeniu znaczników. w przeciwnym razie suwak nie jest ponownie rysowany.

##  <a name="create"></a>Korzystanie CSliderCtrl:: Create

Tworzy kontrolkę suwaka i dołącza ją do `CSliderCtrl` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl kontrolki suwaka. Zastosuj dowolną kombinację [stylów kontrolki suwaka](/windows/win32/Controls/trackbar-control-styles), opisanej w Windows SDK, do kontrolki.

*cinania*<br/>
Określa rozmiar i położenie kontrolki suwaka. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub struktura. [](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki suwaka, zwykle `CDialog`a. Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki suwaka.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli Inicjalizacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`CSliderCtrl` Tworzysz dwa kroki. Najpierw Wywołaj konstruktora, a następnie Wywołaj `Create`, który tworzy kontrolkę suwak i dołącza ją `CSliderCtrl` do obiektu.

W zależności od wartości ustawionych dla *dwStyle*, kontrolka suwaka może mieć orientację pionową lub poziomą. Może mieć znaczniki po obu stronach, obu stron lub żadnej z nich. Można go również użyć do określenia zakresu kolejnych wartości.

Aby zastosować style okna rozszerzonego do kontrolki suwaka [](#createex) , wywołaj `Create`CreateEx zamiast.

##  <a name="createex"></a>Korzystanie CSliderCtrl:: CreateEx

Tworzy kontrolkę (okno podrzędne) i kojarzy ją z `CSliderCtrl` obiektem.

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
Określa rozszerzony styl formantu, który jest tworzony. Aby zapoznać się z listą rozszerzonych stylów systemu Windows, zobacz *dwExStyle* parametru [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) w Windows SDK.

*dwStyle*<br/>
Określa styl kontrolki suwaka. Zastosuj dowolną kombinację [stylów kontrolki suwaka](/windows/win32/Controls/trackbar-control-styles), opisanej w Windows SDK, do kontrolki.

*cinania*<br/>
Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym formantu.

*nID*<br/>
Identyfikator okna podrzędnego kontrolki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [tworzenia](#create) , aby zastosować rozszerzone style systemu Windows, które są określone przez **WS_EX_** styl rozszerzony systemu Windows.

##  <a name="csliderctrl"></a>Korzystanie CSliderCtrl:: Korzystanie CSliderCtrl

Konstruuje `CSliderCtrl` obiekt.

```
CSliderCtrl();
```

##  <a name="getbuddy"></a>Korzystanie CSliderCtrl:: getkolega

Pobiera uchwyt do okna kontrolki suwaka kolega w danej lokalizacji.

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>Parametry

*fLocation*<br/>
Wartość logiczna wskazująca, które dwa uchwyty okna partnera mają być pobierane. Może być jedną z następujących wartości:

- TRUE pobiera uchwyt do partnera z lewej strony suwaka. Jeśli kontrolka suwaka używa stylu TBS_VERT, komunikat spowoduje pobranie partnera powyżej suwaka.

- Wartość FALSE pobiera uchwyt do partnera z prawej strony suwaka. Jeśli kontrolka suwaka używa stylu TBS_VERT, komunikat będzie pobierał partnera poniżej suwaka.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CWnd](../../mfc/reference/cwnd-class.md) , który jest oknem partnera w lokalizacji określonej przez *fLocation*, lub wartość null, jeśli w tej lokalizacji nie istnieje okno partnera.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy), zgodnie z opisem w Windows SDK. Aby uzyskać opis stylów kontrolki suwaka, zobacz [Style formantu TrackBar](/windows/win32/Controls/trackbar-control-styles) w Windows SDK.

##  <a name="getchannelrect"></a>Korzystanie CSliderCtrl:: GetChannelRect

Pobiera rozmiar i położenie prostokąta ograniczenia dla kanału kontrolki suwaka.

```
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Wskaźnik do obiektu [CRect](../../atl-mfc-shared/reference/crect-class.md) , który zawiera rozmiar i położenie prostokąta granicy kanału, gdy funkcja zwraca wartość.

### <a name="remarks"></a>Uwagi

Kanał to obszar, nad którym suwak jest przenoszony i który zawiera wyróżnienie, gdy wybrany jest zakres.

##  <a name="getlinesize"></a>Korzystanie CSliderCtrl:: GetLineSize

Pobiera rozmiar linii dla kontrolki suwaka.

```
int GetLineSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar linii dla kontrolki suwaka.

### <a name="remarks"></a>Uwagi

Rozmiar linii wpływa na to, jak przesuwa się suwak dla powiadomień TB_LINEUP i TB_LINEDOWN. Ustawienie domyślne dla rozmiaru linii to 1.

##  <a name="getnumtics"></a>Korzystanie CSliderCtrl:: GetNumTics

Pobiera liczbę znaczników w kontrolce suwaka.

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaczników w kontrolce suwaka.

##  <a name="getpagesize"></a>Korzystanie CSliderCtrl:: GetPageSize

Pobiera rozmiar strony dla kontrolki suwaka.

```
int GetPageSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar strony kontrolki suwaka.

### <a name="remarks"></a>Uwagi

Rozmiar strony wpływa na to, jak przesuwa się suwak dla powiadomień TB_PAGEUP i TB_PAGEDOWN.

##  <a name="getpos"></a>Korzystanie CSliderCtrl:: GetPos

Pobiera bieżącą pozycję suwaka w kontrolce suwaka.

```
int GetPos() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca pozycja.

##  <a name="getrange"></a>Korzystanie CSliderCtrl:: GetRange

Pobiera maksymalne i minimalne położenia suwaka w kontrolce suwaka.

```
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Odwołanie do liczby całkowitej, która otrzymuje wartość minimalną.

*Nmaks.*<br/>
Odwołanie do liczby całkowitej, która otrzymuje maksymalną pozycję.

### <a name="remarks"></a>Uwagi

Ta funkcja kopiuje wartości do liczb całkowitych przywoływanych przez *Nmin* i *nmaks.* .

##  <a name="getrangemax"></a>Korzystanie CSliderCtrl:: GetRangeMax

Pobiera maksymalną pozycję suwaka w kontrolce suwaka.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna pozycja kontrolki.

##  <a name="getrangemin"></a>Korzystanie CSliderCtrl:: GetRangeMin

Pobiera minimalną pozycję suwaka w kontrolce suwaka.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Wartość zwracana

Minimalna pozycja kontrolki.

##  <a name="getselection"></a>Korzystanie CSliderCtrl:: getselecting

Pobiera początkową i końcową pozycję bieżącego zaznaczenia w kontrolce suwaka.

```
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Odwołanie do liczby całkowitej, która otrzymuje pozycję początkową bieżącego zaznaczenia.

*Nmaks.*<br/>
Odwołanie do liczby całkowitej, która odbiera końcową pozycję bieżącego zaznaczenia.

##  <a name="getthumblength"></a>Korzystanie CSliderCtrl:: GetThumbLength

Pobiera długość suwaka w bieżącej kontrolce TrackBar.

```
int GetThumbLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość suwaka (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [TBM_GETTHUMBLENGTH](/windows/win32/Controls/tbm-getthumblength) , który jest opisany w Windows SDK.

##  <a name="getthumbrect"></a>Korzystanie CSliderCtrl:: GetThumbRect

Pobiera rozmiar i położenie prostokąta ograniczenia dla suwaka (kciuk) w kontrolce suwaka.

```
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Wskaźnik do `CRect` obiektu, który zawiera prostokąt ograniczenia dla suwaka, gdy funkcja zwraca.

##  <a name="gettic"></a>Korzystanie CSliderCtrl:: GetTic

Pobiera pozycję znacznika znaczników w kontrolce suwaka.

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>Parametry

*nTic*<br/>
Indeks (liczony od zera) identyfikujący znacznik.

### <a name="return-value"></a>Wartość zwracana

Pozycja określonego znacznika lub-1, jeśli *nTic* nie określa prawidłowego indeksu.

##  <a name="getticarray"></a>Korzystanie CSliderCtrl:: GetTicArray

Pobiera adres tablicy zawierającej położenia znaczników w kontrolce suwaka.

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres tablicy zawierającej położenia znaczników dla kontrolki suwaka.

##  <a name="getticpos"></a>Korzystanie CSliderCtrl:: GetTicPos

Pobiera bieżącą pozycję fizyczną znacznika znaczników w kontrolce suwaka.

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>Parametry

*nTic*<br/>
Indeks (liczony od zera) identyfikujący znacznik.

### <a name="return-value"></a>Wartość zwracana

Położenie fizyczne, we współrzędnych klienta, określonego znacznika lub-1, jeśli *nTic* nie określa prawidłowego indeksu.

##  <a name="gettooltips"></a>Korzystanie CSliderCtrl:: GetToolTips

Pobiera uchwyt do kontrolki ToolTip przypisanej do kontrolki suwak (jeśli istnieje).

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) lub wartości null, jeśli etykietki narzędzi nie są używane. Jeśli kontrolka suwaka nie używa stylu TBS_TOOLTIPS, zwracana wartość ma wartość NULL.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips), zgodnie z opisem w Windows SDK. Należy zauważyć, że ta funkcja członkowska zwraca `CToolTipCtrl` obiekt zamiast uchwytu do kontrolki.

Aby uzyskać opis stylów kontrolki suwaka, zobacz [Style formantu TrackBar](/windows/win32/Controls/trackbar-control-styles) w Windows SDK.

##  <a name="setbuddy"></a>Korzystanie CSliderCtrl:: setkolega

Przypisuje okno jako okno kolega dla kontrolki suwaka.

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>Parametry

*pWndBuddy*<br/>
Wskaźnik do `CWnd` obiektu, który zostanie ustawiony jako kolega formantu suwaka.

*fLocation*<br/>
Wartość określająca lokalizację, w której ma zostać wyświetlone okno partnera. Może to być jedna z następujących wartości:

- PRAWDA, kolega zostanie wyświetlony po lewej stronie elementu TrackBar, Jeśli kontrolka TrackBar używa stylu TBS_HORZ. Jeśli TrackBar używa stylu TBS_VERT, kolega pojawia się nad kontrolką TrackBar.

- Wartość FALSE, kolega zostanie wyświetlony po prawej stronie elementu TrackBar, Jeśli kontrolka TrackBar używa stylu TBS_HORZ. Jeśli TrackBar używa stylu TBS_VERT, kolega pojawia się poniżej kontrolki TrackBar.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CWnd](../../mfc/reference/cwnd-class.md) , który został wcześniej przypisany do kontrolki suwaka w tej lokalizacji.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy), zgodnie z opisem w Windows SDK. Należy zauważyć, że ta funkcja członkowska `CWnd` używa wskaźników do obiektów, a nie uchwytów okna dla wartości zwracanej i parametru.

Aby uzyskać opis stylów kontrolki suwaka, zobacz [Style formantu TrackBar](/windows/win32/Controls/trackbar-control-styles) w Windows SDK.

##  <a name="setlinesize"></a>Korzystanie CSliderCtrl:: SetLineSize

Ustawia rozmiar linii dla kontrolki suwaka.

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
Nowy rozmiar linii kontrolki suwaka.

### <a name="return-value"></a>Wartość zwracana

Poprzedni rozmiar wiersza.

### <a name="remarks"></a>Uwagi

Rozmiar linii wpływa na to, jak przesuwa się suwak dla powiadomień TB_LINEUP i TB_LINEDOWN.

##  <a name="setpagesize"></a>  CSliderCtrl::SetPageSize

Ustawia rozmiar strony dla kontrolki suwaka.

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
Nowy rozmiar strony kontrolki suwaka.

### <a name="return-value"></a>Wartość zwracana

Poprzedni rozmiar strony.

### <a name="remarks"></a>Uwagi

Rozmiar strony wpływa na to, jak przesuwa się suwak dla powiadomień TB_PAGEUP i TB_PAGEDOWN.

##  <a name="setpos"></a>Korzystanie CSliderCtrl:: SetPos

Ustawia bieżącą pozycję suwaka w kontrolce suwaka.

```
void SetPos(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Określa nową pozycję suwaka.

##  <a name="setrange"></a>Korzystanie CSliderCtrl:: SetRange

Ustawia zakres (minimalne i maksymalne położenie) suwaka w kontrolce suwaka.

```
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Minimalna pozycja suwaka.

*Nmaks.*<br/>
Maksymalna pozycja suwaka.

*bRedraw*<br/>
Flaga ponownego rysowania. Jeśli ten parametr ma wartość TRUE, suwak jest rysowany ponownie po ustawieniu zakresu; w przeciwnym razie suwak nie jest ponownie rysowany.

##  <a name="setrangemax"></a>Korzystanie CSliderCtrl:: SetRangeMax

Ustawia maksymalny zakres suwaka w kontrolce suwaka.

```
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*Nmaks.*<br/>
Maksymalna pozycja suwaka.

*bRedraw*<br/>
Flaga ponownego rysowania. Jeśli ten parametr ma wartość TRUE, suwak jest rysowany ponownie po ustawieniu zakresu; w przeciwnym razie suwak nie jest ponownie rysowany.

##  <a name="setrangemin"></a>Korzystanie CSliderCtrl:: SetRangeMin

Ustawia minimalny zakres dla suwaka w kontrolce suwaka.

```
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Minimalna pozycja suwaka.

*bRedraw*<br/>
Flaga ponownego rysowania. Jeśli ten parametr ma wartość TRUE, suwak jest rysowany ponownie po ustawieniu zakresu; w przeciwnym razie suwak nie jest ponownie rysowany.

##  <a name="setselection"></a>Korzystanie CSliderCtrl:: setselecting

Ustawia początkową i końcową pozycję dla bieżącego zaznaczenia w kontrolce suwaka.

```
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Pozycja początkowa dla suwaka.

*Nmaks.*<br/>
Pozycja końcowa dla suwaka.

##  <a name="setthumblength"></a>Korzystanie CSliderCtrl:: SetThumbLength

Ustawia długość suwaka w bieżącej kontrolce TrackBar.

```
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*nLength*|podczas Długość suwaka (w pikselach).|

### <a name="remarks"></a>Uwagi

Ta metoda wymaga, aby kontrolka TrackBar była ustawiona na styl [TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles) .

Ta metoda wysyła komunikat [TBM_SETTHUMBLENGTH](/windows/win32/Controls/tbm-setthumblength) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną, `m_sliderCtrl`, która jest używana do uzyskiwania dostępu do bieżącej kontrolki TrackBar. W przykładzie zdefiniowano również zmienną, `thumbLength`która jest używana do przechowywania domyślnej długości składnika kciuka kontrolki TrackBar. Te zmienne są używane w następnym przykładzie.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia składnik kciuka kontrolki TrackBar na dwukrotnie jego długość domyślną.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

##  <a name="settic"></a>Korzystanie CSliderCtrl:: SetTic

Ustawia pozycję znacznika w kontrolce suwaka.

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>Parametry

*nTic*<br/>
Pozycja znacznika. Ten parametr musi określać wartość dodatnią.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, Jeśli znacznik jest ustawiony; w przeciwnym razie 0.

##  <a name="setticfreq"></a>Korzystanie CSliderCtrl:: SetTicFreq

Ustawia częstotliwość, z jaką znaczniki są wyświetlane na suwaku.

```
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>Parametry

*nFreq*<br/>
Częstotliwość znaczników.

### <a name="remarks"></a>Uwagi

Na przykład, jeśli częstotliwość jest ustawiona na 2, znacznik jest wyświetlany dla każdego innego przyrostu w zakresie suwaka. Ustawienie domyślne dla częstotliwości to 1 (oznacza to, że każdy przyrost z zakresu jest skojarzony ze znacznikiem).

Aby użyć tej funkcji, należy utworzyć formant z stylem TBS_AUTOTICKS. Aby uzyskać więcej informacji, zobacz [Korzystanie CSliderCtrl:: Create](#create).

##  <a name="settipside"></a>Korzystanie CSliderCtrl:: SetTipSide

Ustawia kontrolkę etykietki narzędzia używaną przez formant TrackBar.

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>Parametry

*Nlokalizacja*<br/>
Wartość reprezentująca lokalizację, w której ma zostać wyświetlona kontrolka ToolTip. Listę możliwych wartości można znaleźć w komunikacie Win32 [TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside), zgodnie z opisem w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wartość, która reprezentuje poprzednią lokalizację kontrolki ToolTip. Wartość zwracana jest równa jednej z możliwych wartości dla *nlokalizacja*.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 TBM_SETTIPSIDE, zgodnie z opisem w Windows SDK. Kontrolki suwaka, które używają etykietek narzędzi w stylu TBS_TOOLTIPS. Aby uzyskać opis stylów kontrolki suwaka, zobacz [Style formantu TrackBar](/windows/win32/Controls/trackbar-control-styles) w Windows SDK.

##  <a name="settooltips"></a>Korzystanie CSliderCtrl:: setetykietki narzędzi

Przypisuje formant etykietki narzędzia do kontrolki suwaka.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parametry

*pWndTip*<br/>
Wskaźnik do obiektu [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) zawierającego etykietki narzędzi do użycia z kontrolką suwaka.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips), zgodnie z opisem w Windows SDK. Gdy kontrolka suwaka jest tworzona przy użyciu stylu TBS_TOOLTIPS, tworzy domyślną kontrolkę etykietki narzędzia, która pojawia się obok suwaka, wyświetlając bieżącą pozycję suwaka. Aby uzyskać opis stylów kontrolki suwaka, zobacz [Style formantu TrackBar](/windows/win32/Controls/trackbar-control-styles) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Przykład CMNCTRL2 MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CProgressCtrl](../../mfc/reference/cprogressctrl-class.md)
