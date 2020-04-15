---
title: Klasa CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
ms.openlocfilehash: 7a594fdb2d3a35ce905b7790026f7418b7435f3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366028"
---
# <a name="cstatusbarctrl-class"></a>Klasa CStatusBarCtrl

Udostępnia funkcje kontrolki wspólnego paska stanu systemu Windows.

## <a name="syntax"></a>Składnia

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|Konstruuje `CStatusBarCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatusBarCtrl::Utwórz](#create)|Tworzy formant paska stanu i `CStatusBarCtrl` dołącza go do obiektu.|
|[CStatusBarCtrl::CreateEx](#createex)|Tworzy formant paska stanu z określonymi stylami `CStatusBarCtrl` rozszerzonymi systemu Windows i dołącza go do obiektu.|
|[CStatusBarCtrl::DrawItem](#drawitem)|Wywoływane, gdy zmienia się wizualny aspekt formantu paska stanu rysowania właściciela.|
|[CStatusBarCtrl::GetBorders](#getborders)|Pobiera bieżące szerokości obramowania poziomego i pionowego formantu paska stanu.|
|[CStatusBarCtrl::Geticon](#geticon)|Pobiera ikonę części (znanej również jako okienko) w bieżącym formancie paska stanu.|
|[CStatusBarCtrl::GetParts](#getparts)|Pobiera liczbę części w formancie paska stanu.|
|[CStatusBarCtrl::GetRect](#getrect)|Pobiera prostokąt ograniczający części w formancie paska stanu.|
|[CStatusBarCtrl::GetText](#gettext)|Pobiera tekst z danej części formantu paska stanu.|
|[CStatusBarCtrl::GetTextLength](#gettextlength)|Pobieranie długości, w znakach, tekstu z danej części formantu paska stanu.|
|[CStatusBarCtrl::GetTipText](#gettiptext)|Pobiera tekst etykietki narzędzia okienka na pasku stanu.|
|[CStatusBarCtrl::IsSimple](#issimple)|Sprawdza formant okna stanu, aby ustalić, czy jest w trybie prostym.|
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Ustawia kolor tła na pasku stanu.|
|[CStatusBarCtrl::SetIcon](#seticon)|Ustawia ikonę okienka na pasku stanu.|
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Ustawia minimalną wysokość obszaru rysunku formantu paska stanu.|
|[CStatusBarCtrl::SetParts](#setparts)|Ustawia liczbę części w formancie paska stanu i współrzędną prawej krawędzi każdej części.|
|[CStatusBarCtrl::SetSimple](#setsimple)|Określa, czy kontrolka paska stanu wyświetla tekst prosty, `SetParts`czy wszystkie części sterujące ustawione przez poprzednie wywołanie do .|
|[CStatusBarCtrl::SetText](#settext)|Ustawia tekst w danej części formantu paska stanu.|
|[CStatusBarCtrl::SetTipText](#settiptext)|Ustawia tekst etykietki narzędzia dla okienka na pasku stanu.|

## <a name="remarks"></a>Uwagi

"Formant paska stanu" to okno poziome, zwykle wyświetlane w dolnej części okna nadrzędnego, w którym aplikacja może wyświetlać różnego rodzaju informacje o stanie. Formant paska stanu można podzielić na części, aby wyświetlić więcej niż jeden typ informacji.

Ten formant (i `CStatusBarCtrl` dlatego klasa) jest dostępny tylko dla programów działających w systemach Windows 95/98 i Windows NT w wersji 3.51 lub nowszych.

Aby uzyskać więcej `CStatusBarCtrl`informacji na temat używania , zobacz [Formanty](../../mfc/controls-mfc.md) i [Korzystanie z CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="cstatusbarctrlcreate"></a><a name="create"></a>CStatusBarCtrl::Utwórz

Tworzy formant paska stanu i `CStatusBarCtrl` dołącza go do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa styl formantu paska stanu. Zastosuj dowolną kombinację stylów formantu paska stanu wymienionych w [typowych stylach sterowania](/windows/win32/Controls/common-control-styles) w zestaw windows SDK. Ten parametr musi zawierać styl WS_CHILD. Powinien również zawierać styl WS_VISIBLE.

*Rect*<br/>
Określa rozmiar i położenie formantu paska stanu. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [struktura RECT.](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Określa okno nadrzędne formantu paska `CDialog`stanu, zwykle . Nie może być null.

*Nid*<br/>
Określa identyfikator formantu paska stanu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Konstruujesz `CStatusBarCtrl` w dwóch krokach. Najpierw wywołaj konstruktora, `Create`a następnie wywołaj , co tworzy `CStatusBarCtrl` formant paska stanu i dołącza go do obiektu.

Domyślna pozycja okna stanu znajduje się u dołu okna nadrzędnego, ale można określić styl CCS_TOP, aby był wyświetlany w górnej części obszaru klienta okna nadrzędnego. Można określić styl SBARS_SIZEGRIP, aby uwzględnić uchwyt zmiany rozmiaru na prawym końcu okna stanu. Łączenie stylów CCS_TOP i SBARS_SIZEGRIP nie jest zalecane, ponieważ wynikowy uchwyt zmiany rozmiaru nie jest funkcjonalny, nawet jeśli system rysuje go w oknie stanu.

Aby utworzyć pasek stanu z rozszerzonymi stylami okien, zamiast `Create`programu CStatusBarCtrl należy wywołać polecenie [CStatusBarCtrl::CreateEx.](#createex)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

## <a name="cstatusbarctrlcreateex"></a><a name="createex"></a>CStatusBarCtrl::CreateEx

Tworzy formant (okno podrzędne) i `CStatusBarCtrl` kojarzy go z obiektem.

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
Określa styl formantu paska stanu. Zastosuj dowolną kombinację stylów formantu paska stanu wymienionych w [typowych stylach sterowania](/windows/win32/Controls/common-control-styles) w zestaw windows SDK. Ten parametr musi zawierać styl WS_CHILD. Powinien również zawierać styl WS_VISIBLE.

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

## <a name="cstatusbarctrlcstatusbarctrl"></a><a name="cstatusbarctrl"></a>CStatusBarCtrl::CStatusBarCtrl

Konstruuje `CStatusBarCtrl` obiekt.

```
CStatusBarCtrl();
```

## <a name="cstatusbarctrldrawitem"></a><a name="drawitem"></a>CStatusBarCtrl::DrawItem

Wywoływane przez strukturę, gdy zmienia się wizualny aspekt formantu paska stanu rysowania właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Długi wskaźnik do struktury [DRAWITEMSTRUCT,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) który zawiera informacje o typie wymaganego rysunku.

### <a name="remarks"></a>Uwagi

Element `itemAction` członkowski `DRAWITEMSTRUCT` konstrukcji definiuje akcję rysowania, która ma być wykonana.

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpokaj tę funkcję elementu członkowskiego, aby zaimplementować rysunek dla obiektu rysowania `CStatusBarCtrl` właściciela.

Aplikacja powinna przywrócić wszystkie obiekty interfejsu urządzenia graficznego (GDI) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

## <a name="cstatusbarctrlgetborders"></a><a name="getborders"></a>CStatusBarCtrl::GetBorders

Pobiera bieżące szerokości paska stanu obramowania poziomego i pionowego oraz odstępu między prostokątami.

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>Parametry

*pBorders*<br/>
Adres tablicy liczby całkowitej o trzech elementach. Pierwszy element otrzymuje szerokość obramowania poziomego, drugi otrzymuje szerokość obramowania pionowego, a trzeci otrzymuje szerokość obramowania między prostokątami.

*nHorz ( nHorz )*<br/>
Odwołanie do liczby całkowitej, która odbiera szerokość obramowania poziomego.

*nVert (wychw.*<br/>
Odwołanie do liczby całkowitej, która odbiera szerokość obramowania pionowego.

*nSmące*<br/>
Odwołanie do liczby całkowitej, która odbiera szerokość obramowania między prostokątami.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Obramowania te określają odstępy między zewnętrzną krawędzią formantu a prostokątami w formancie zawierającym tekst.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

## <a name="cstatusbarctrlgeticon"></a><a name="geticon"></a>CStatusBarCtrl::Geticon

Pobiera ikonę części (znanej również jako okienko) w bieżącym formancie paska stanu.

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iPart ( iPart)*|[w] Indeks od zera części zawierającej ikonę do pobrania. Jeśli ten parametr wynosi -1, zakłada się, że pasek stanu jest prostym pasem stanu trybu.|

### <a name="return-value"></a>Wartość zwracana

Dojście do ikony, jeśli metoda zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [SB_GETICON,](/windows/win32/Controls/sb-geticon) który jest opisany w windows SDK.

Formant paska stanu składa się z wiersza okienek wyjściowych tekstu, które są również nazywane częściami. Aby uzyskać więcej informacji na temat paska stanu, zobacz [Implementacja paska stanu w MFC](../../mfc/status-bar-implementation-in-mfc.md) i [Ustawianie trybu obiektu CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_statusBar`zmienną , która jest używana do uzyskiwania dostępu do bieżącego formantu paska stanu. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu kopiuje ikonę do dwóch okienek bieżącego formantu paska stanu. We wcześniejszej sekcji przykładu kodu utworzyliśmy kontrolkę paska stanu z trzema okienkami, a następnie dodaliśmy ikonę do pierwszego okienka. W tym przykładzie pobiera ikonę z pierwszego okienka, a następnie dodaje ją do drugiego i trzeciego okienka.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

## <a name="cstatusbarctrlgetparts"></a><a name="getparts"></a>CStatusBarCtrl::GetParts

Pobiera liczbę części w formancie paska stanu.

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>Parametry

*nCzęści*<br/>
Liczba części, dla których mają być pobierane współrzędne. Jeśli ten parametr jest większa niż liczba części w formancie, komunikat pobiera współrzędne tylko dla istniejących części.

*pCzęści*<br/>
Adres tablicy liczby całkowitej o takiej samej liczbie elementów jak liczba części określona przez *nParts*. Każdy element w tablicy odbiera współrzędne klienta prawej krawędzi odpowiedniej części. Jeśli element jest ustawiony na - 1, położenie prawej krawędzi dla tej części rozciąga się do prawej krawędzi paska stanu.

### <a name="return-value"></a>Wartość zwracana

Liczba części w formancie, jeśli zakończy się pomyślnie lub zero w inny sposób.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego pobiera również współrzędne prawej krawędzi danej liczby części.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

## <a name="cstatusbarctrlgetrect"></a><a name="getrect"></a>CStatusBarCtrl::GetRect

Pobiera prostokąt ograniczający części w formancie paska stanu.

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nPane (własówce)*<br/>
Indeks od zera części, której prostokąt ograniczający ma zostać pobrany.

*Lprect*<br/>
Adres struktury [RECT,](/previous-versions/dd162897\(v=vs.85\)) która odbiera prostokąt ograniczający.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

## <a name="cstatusbarctrlgettext"></a><a name="gettext"></a>CStatusBarCtrl::GetText

Pobiera tekst z danej części formantu paska stanu.

```
CString GetText(
    int nPane,
    int* pType = NULL) const;

int GetText(
    LPCTSTR lpszText,
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
Adres buforu, który odbiera tekst. Ten parametr jest ciągiem zakończonym z wartością null.

*nPane (własówce)*<br/>
Indeks od zera części, z której ma być pobierany tekst.

*pTyp*<br/>
Wskaźnik do liczby całkowitej, która odbiera informacje o typie. Typ może być jedną z następujących wartości:

- **0** Tekst jest rysowany obramowaniem, aby wyglądałniż płaszczyzna paska stanu.

- SBT_NOBORDERS Tekst jest rysowany bez obramowań.

- SBT_POPOUT Tekst jest rysowany obramowaniem, aby był wyświetlany wyżej niż płaszczyzna paska stanu.

- SBT_OWNERDRAW Jeśli tekst ma typ rysunku SBT_OWNERDRAW, *pType* odbiera ten komunikat i zwraca wartość 32-bitową skojarzoną z tekstem zamiast długości i typu operacji.

### <a name="return-value"></a>Wartość zwracana

Długość , w znakach, tekstu lub [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierające bieżący tekst.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

## <a name="cstatusbarctrlgettextlength"></a><a name="gettextlength"></a>CStatusBarCtrl::GetTextLength

Pobiera długość, w znakach, tekstu z danej części formantu paska stanu.

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parametry

*nPane (własówce)*<br/>
Indeks od zera części, z której ma być pobierany tekst.

*pTyp*<br/>
Wskaźnik do liczby całkowitej, która odbiera informacje o typie. Typ może być jedną z następujących wartości:

- **0** Tekst jest rysowany obramowaniem, aby wyglądałniż płaszczyzna paska stanu.

- SBT_NOBORDERS Tekst jest rysowany bez obramowań.

- SBT_OWNERDRAW Tekst jest rysowany przez okno nadrzędne.

- SBT_POPOUT Tekst jest rysowany obramowaniem, aby był wyświetlany wyżej niż płaszczyzna paska stanu.

### <a name="return-value"></a>Wartość zwracana

Długość tekstu w znakach.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

## <a name="cstatusbarctrlgettiptext"></a><a name="gettiptext"></a>CStatusBarCtrl::GetTipText

Pobiera tekst etykietki narzędzia okienka na pasku stanu.

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>Parametry

*nPane (własówce)*<br/>
Indeks od zera okienka paska stanu do odbierania tekstu etykietki narzędzia.

### <a name="return-value"></a>Wartość zwracana

Obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający tekst, który ma być używany w etykietce narzędzia.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

## <a name="cstatusbarctrlissimple"></a><a name="issimple"></a>CStatusBarCtrl::IsSimple

Sprawdza formant okna stanu, aby ustalić, czy jest w trybie prostym.

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli kontrolka okna stanu jest w trybie prostym; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [SB_ISSIMPLE](/windows/win32/Controls/sb-issimple)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="cstatusbarctrlsetbkcolor"></a><a name="setbkcolor"></a>CStatusBarCtrl::SetBkColor

Ustawia kolor tła na pasku stanu.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parametry

*Cr*<br/>
WARTOŚĆ COLORREF określająca nowy kolor tła. Określ wartość CLR_DEFAULT, aby pasek stanu używał domyślnego koloru tła.

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) reprezentująca poprzedni domyślny kolor tła.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

## <a name="cstatusbarctrlseticon"></a><a name="seticon"></a>CStatusBarCtrl::SetIcon

Ustawia ikonę okienka na pasku stanu.

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>Parametry

*nPane (własówce)*<br/>
Indeks od zera okienka, w które otrzyma ikonę. Jeśli ten parametr wynosi -1, zakłada się, że pasek stanu jest prostym pasem stanu.

*hIcon (własówce)*<br/>
Uchwyt do ikony, która ma być ustawiona. Jeśli ta wartość ma wartość NULL, ikona zostanie usunięta z części.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [SB_SETICON](/windows/win32/Controls/sb-seticon)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CStatusBarCtrl::SetBkColor](#setbkcolor).

## <a name="cstatusbarctrlsetminheight"></a><a name="setminheight"></a>CStatusBarCtrl::SetMinHeight

Ustawia minimalną wysokość obszaru rysunku formantu paska stanu.

```
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>Parametry

*nMin (min.*<br/>
Minimalna wysokość formantu w pikselach.

### <a name="remarks"></a>Uwagi

Minimalna wysokość jest sumą *nMin* i dwukrotnie większą szerokością w pikselach pionowej granicy formantu paska stanu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

## <a name="cstatusbarctrlsetparts"></a><a name="setparts"></a>CStatusBarCtrl::SetParts

Ustawia liczbę części w formancie paska stanu i współrzędną prawej krawędzi każdej części.

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>Parametry

*nCzęści*<br/>
Liczba części do ustawionego. Liczba części nie może być większa niż 255.

*pWidths*<br/>
Adres tablicy liczby całkowitej o takiej samej liczbie elementów jak części określone przez *nParts*. Każdy element w tablicy określa położenie prawej krawędzi odpowiedniej części we współrzędnych klienta. Jeśli element jest - 1, położenie prawej krawędzi dla tej części rozciąga się do prawej krawędzi formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

## <a name="cstatusbarctrlsetsimple"></a><a name="setsimple"></a>CStatusBarCtrl::SetSimple

Określa, czy kontrolka paska stanu wyświetla tekst prosty, czy wszystkie części sterujące ustawione przez poprzednie wywołanie [SetParts](#setparts).

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłach*<br/>
[w] Flaga typu display. Jeśli ten parametr ma wartość PRAWDA, formant wyświetla prosty tekst; jeśli jest FALSE, wyświetla wiele części.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja zmieni formant paska stanu z nieprecyzyjny do prostego lub odwrotnie, system natychmiast ponownie rysuje formant.

## <a name="cstatusbarctrlsettext"></a><a name="settext"></a>CStatusBarCtrl::SetText

Ustawia tekst w danej części formantu paska stanu.

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
Adres ciągu zakończonego wartością null określającego tekst do skonfigurowania. Jeśli *nType* jest SBT_OWNERDRAW, *lpszText* reprezentuje 32 bity danych.

*nPane (własówce)*<br/>
Indeks od zera części do ustawionego. Jeśli ta wartość wynosi 255, formant paska stanu przyjmuje się, że jest to prosty formant mający tylko jedną część.

*nTyp*<br/>
Typ operacji rysowania. Zobacz [SB_SETTEXT komunikat,](/windows/win32/Controls/sb-settext) aby uzyskać listę możliwych wartości.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Komunikat unieważnia część formantu, który uległ zmianie, powodując, że do wyświetlania nowego tekstu, gdy formant obok odbiera komunikat WM_PAINT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

## <a name="cstatusbarctrlsettiptext"></a><a name="settiptext"></a>CStatusBarCtrl::SetTipText

Ustawia tekst etykietki narzędzia dla okienka na pasku stanu.

```
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parametry

*nPane (własówce)*<br/>
Indeks od zera okienka paska stanu do odbierania tekstu etykietki narzędzia.

*pszTipText (tekst pszTip)*<br/>
Wskaźnik do ciągu zawierającego tekst etykietki narzędzia.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [SB_SETTIPTEXT](/windows/win32/Controls/sb-settiptext)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)
