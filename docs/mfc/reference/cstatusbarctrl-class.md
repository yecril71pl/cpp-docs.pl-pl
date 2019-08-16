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
ms.openlocfilehash: 8c33aa4d77eeeeca69e50dc63982ff4d7e8bd505
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502322"
---
# <a name="cstatusbarctrl-class"></a>Klasa CStatusBarCtrl

Oferuje funkcje kontrolki typowego paska stanu systemu Windows.

## <a name="syntax"></a>Składnia

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatusBarCtrl:: CStatusBarCtrl](#cstatusbarctrl)|Konstruuje `CStatusBarCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatusBarCtrl:: Create](#create)|Tworzy formant paska stanu i dołącza go do `CStatusBarCtrl` obiektu.|
|[CStatusBarCtrl:: CreateEx](#createex)|Tworzy kontrolkę pasek stanu z określonymi stylami rozszerzonymi systemu Windows i dołącza je do `CStatusBarCtrl` obiektu.|
|[CStatusBarCtrl::D rawItem](#drawitem)|Wywołuje się, gdy wizualny aspekt kontrolki paska stanu rysowania przez właściciela jest zmieniany.|
|[CStatusBarCtrl:: GetBorders](#getborders)|Pobiera bieżące szerokości obramowania poziomego i pionowego kontrolki paska stanu.|
|[CStatusBarCtrl:: GetIcon](#geticon)|Pobiera ikonę części (zwanej także okienkiem) w bieżącym formancie paska stanu.|
|[CStatusBarCtrl:: GetParts](#getparts)|Pobiera liczbę części w kontrolce pasek stanu.|
|[CStatusBarCtrl:: getRect](#getrect)|Pobiera prostokąt ograniczenia części w kontrolce pasek stanu.|
|[CStatusBarCtrl:: gettext](#gettext)|Pobiera tekst z danej części kontrolki pasek stanu.|
|[CStatusBarCtrl:: GetTextLength](#gettextlength)|Pobierz Długość (w znakach) tekstu z danej części kontrolki paska stanu.|
|[CStatusBarCtrl:: GetTipText](#gettiptext)|Pobiera tekst etykietki narzędzia dla okienka na pasku stanu.|
|[CStatusBarCtrl:: IsSimple](#issimple)|Sprawdza formant okna stanu, aby określić, czy jest w trybie prostym.|
|[CStatusBarCtrl:: SetBkColor](#setbkcolor)|Ustawia kolor tła na pasku stanu.|
|[CStatusBarCtrl:: SetIcon](#seticon)|Ustawia ikonę okienka na pasku stanu.|
|[CStatusBarCtrl:: SetMinHeight](#setminheight)|Ustawia minimalną wysokość obszaru rysowania kontrolki paska stanu.|
|[CStatusBarCtrl:: SetParts](#setparts)|Ustawia liczbę części w kontrolce pasek stanu i współrzędne prawej krawędzi każdej części.|
|[CStatusBarCtrl:: SetSimple](#setsimple)|Określa, czy kontrolka paska stanu wyświetla prosty tekst, czy też wyświetla wszystkie części sterujące ustawione przez poprzednie `SetParts`wywołanie do.|
|[CStatusBarCtrl:: SetText](#settext)|Ustawia tekst w danej części kontrolki pasek stanu.|
|[CStatusBarCtrl:: SetTipText](#settiptext)|Ustawia tekst etykietki narzędzia dla okienka na pasku stanu.|

## <a name="remarks"></a>Uwagi

"Formant paska stanu" to okno poziome, zwykle wyświetlane w dolnej części okna nadrzędnego, w którym aplikacja może wyświetlać różne rodzaje informacji o stanie. Kontrolka pasek stanu może być podzielona na części, aby wyświetlić więcej niż jeden typ informacji.

Ten formant (i w związku `CStatusBarCtrl` z tym Klasa) jest dostępny tylko dla programów uruchomionych w systemach Windows 95/98 i Windows NT w wersji 3,51 lub nowszej.

Aby uzyskać więcej informacji na `CStatusBarCtrl`temat korzystania z programu, zobacz [kontrolki](../../mfc/controls-mfc.md) i [Używanie CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

##  <a name="create"></a>CStatusBarCtrl:: Create

Tworzy formant paska stanu i dołącza go do `CStatusBarCtrl` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl kontrolki paska stanu. Zastosuj dowolną kombinację stylów kontrolki paska stanu wymienionych w obszarze [Style formantów wspólnych](/windows/win32/Controls/common-control-styles) w Windows SDK. Ten parametr musi zawierać styl WS_CHILD. Powinien również zawierać styl WS_VISIBLE.

*cinania*<br/>
Określa rozmiar i położenie kontrolki paska stanu. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub struktura. [](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki pasek stanu, zazwyczaj a `CDialog`. Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki paska stanu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

`CStatusBarCtrl` Tworzysz dwa kroki. Najpierw Wywołaj konstruktora, a następnie Wywołaj `Create`metodę, która tworzy formant paska stanu i dołącza go `CStatusBarCtrl` do obiektu.

Domyślna pozycja okna stanu znajduje się u dołu okna nadrzędnego, ale można określić styl CCS_TOP, aby był wyświetlany w górnej części obszaru klienckiego okna nadrzędnego. Możesz określić styl SBARS_SIZEGRIP, aby dołączyć uchwyt zmiany wielkości po prawej stronie okna stanu. Nie zaleca się łączenia stylów CCS_TOP i SBARS_SIZEGRIP, ponieważ nie jest on funkcjonalny, mimo że system rysuje go w oknie stanu.

Aby utworzyć pasek stanu z rozszerzonymi stylami okien, należy wywołać [CStatusBarCtrl:: CreateEx](#createex) zamiast `Create`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

##  <a name="createex"></a>CStatusBarCtrl:: CreateEx

Tworzy kontrolkę (okno podrzędne) i kojarzy ją z `CStatusBarCtrl` obiektem.

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
Określa styl kontrolki paska stanu. Zastosuj dowolną kombinację stylów kontrolki paska stanu wymienionych w obszarze [Style formantów wspólnych](/windows/win32/Controls/common-control-styles) w Windows SDK. Ten parametr musi zawierać styl WS_CHILD. Powinien również zawierać styl WS_VISIBLE.

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

##  <a name="cstatusbarctrl"></a>CStatusBarCtrl:: CStatusBarCtrl

Konstruuje `CStatusBarCtrl` obiekt.

```
CStatusBarCtrl();
```

##  <a name="drawitem"></a>CStatusBarCtrl::D rawItem

Wywoływane przez platformę, gdy wizualny aspekt kontrolki paska stanu rysowania przez właściciela jest zmieniany.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Długi wskaźnik do struktury [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) , który zawiera informacje o wymaganym typie rysunku.

### <a name="remarks"></a>Uwagi

`itemAction` Element członkowski`DRAWITEMSTRUCT` struktury definiuje akcję rysowania, która ma zostać wykonana.

Domyślnie ta funkcja członkowska nic nie robi. Przesłoń tę funkcję elementu członkowskiego, aby zaimplementować rysowanie dla `CStatusBarCtrl` obiektu rysowania przez właściciela.

Aplikacja powinna przywrócić wszystkie obiekty interfejsu GDI (Graphics Device Interface) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

##  <a name="getborders"></a>CStatusBarCtrl:: GetBorders

Pobiera bieżące szerokości kontrolki paska stanu w poziomie i w pionie oraz miejsce między prostokątami.

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>Parametry

*pBorders*<br/>
Adres tablicy typu Integer z trzema elementami. Pierwszy element otrzymuje szerokość obramowania poziomego, drugi otrzymuje szerokość obramowania pionowego, a trzecia otrzymuje szerokość obramowania między prostokątami.

*nHorz*<br/>
Odwołanie do liczby całkowitej, która otrzymuje szerokość obramowania poziomego.

*Konweruj*<br/>
Odwołanie do liczby całkowitej, która otrzymuje szerokość obramowania pionowego.

*nSpacing*<br/>
Odwołanie do liczby całkowitej, która otrzymuje szerokość obramowania między prostokątami.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Te obramowania określają odstępy między zewnętrzną krawędzią kontrolki a prostokątami w kontrolce, które zawierają tekst.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

##  <a name="geticon"></a>CStatusBarCtrl:: GetIcon

Pobiera ikonę części (zwanej także okienkiem) w bieżącym formancie paska stanu.

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iPart*|podczas Indeks (liczony od zera) części zawierającej ikonę, która ma zostać pobrana. Jeśli ten parametr ma wartość-1, przyjmuje się, że jest to pasek stanu prosty trybu prostego.|

### <a name="return-value"></a>Wartość zwracana

Dojście do ikony, jeśli metoda się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [SB_GETICON](/windows/win32/Controls/sb-geticon) , który jest opisany w Windows SDK.

Kontrolka pasek stanu składa się z wierszy okienek wyjściowych tekstowych, które są również znane jako części. Aby uzyskać więcej informacji na temat paska stanu, zobacz [implementacja paska stanu w MFC](../../mfc/status-bar-implementation-in-mfc.md) i [Ustawianie trybu obiektu CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną, `m_statusBar`, która jest używana do uzyskiwania dostępu do bieżącej kontrolki paska stanu. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu kopiuje ikonę do dwóch okienek bieżącej kontrolki pasek stanu. W poprzedniej sekcji przykładowego kodu utworzyliśmy kontrolkę pasek stanu z trzema okienkami, a następnie dodaliśmy do pierwszego okienka ikonę. Ten przykład pobiera ikonę z pierwszego okienka, a następnie dodaje ją do drugiego i trzeciego okienka.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

##  <a name="getparts"></a>CStatusBarCtrl:: GetParts

Pobiera liczbę części w kontrolce pasek stanu.

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>Parametry

*nParts*<br/>
Liczba części, dla których mają zostać pobrane współrzędne. Jeśli ten parametr jest większy niż liczba części w kontrolce, komunikat pobiera współrzędne tylko dla istniejących części.

*pParts*<br/>
Adres tablicy liczb całkowitych, która ma taką samą liczbę elementów jak liczba części określona przez *nParts*. Każdy element w tablicy otrzymuje współrzędną klienta prawej krawędzi odpowiedniej części. Jeśli element ma ustawioną wartość-1, pozycja prawej krawędzi tej części rozciąga się do prawej krawędzi paska stanu.

### <a name="return-value"></a>Wartość zwracana

Liczba części w kontrolce, jeśli się powiedzie, lub zero w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska również Pobiera współrzędną prawej krawędzi danej liczby części.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

##  <a name="getrect"></a>CStatusBarCtrl:: getRect

Pobiera prostokąt ograniczenia części w kontrolce pasek stanu.

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Indeks (liczony od zera) części, której prostokąt powiązania ma zostać pobrany.

*lpRect*<br/>
Adres struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , która otrzymuje prostokąt powiązany.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

##  <a name="gettext"></a>CStatusBarCtrl:: gettext

Pobiera tekst z danej części kontrolki pasek stanu.

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

*lpszText*<br/>
Adres buforu, który odbiera tekst. Ten parametr jest ciągiem zakończonym wartością null.

*nPane*<br/>
Indeks (liczony od zera) części, z której ma zostać pobrany tekst.

*pType*<br/>
Wskaźnik na liczbę całkowitą, która odbiera informacje o typie. Typ może być jedną z następujących wartości:

- **0** tekst jest rysowany z obramowaniem wyświetlanym poniżej płaszczyzny paska stanu.

- SBT_NOBORDERS tekst jest rysowany bez obramowania.

- SBT_POPOUT tekst jest rysowany z obramowaniem, aby był wyświetlany powyżej płaszczyzny paska stanu.

- SBT_OWNERDRAW Jeśli tekst ma typ rysunku SBT_OWNERDRAW, *pType* odbiera ten komunikat i zwraca wartość 32-bitową skojarzoną z tekstem, a nie długość i typ operacji.

### <a name="return-value"></a>Wartość zwracana

Długość (w znakach) tekstu lub [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierającego bieżący tekst.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

##  <a name="gettextlength"></a>CStatusBarCtrl:: GetTextLength

Pobiera długość (w znakach) tekstu z danej części kontrolki pasek stanu.

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Indeks (liczony od zera) części, z której ma zostać pobrany tekst.

*pType*<br/>
Wskaźnik na liczbę całkowitą, która odbiera informacje o typie. Typ może być jedną z następujących wartości:

- **0** tekst jest rysowany z obramowaniem wyświetlanym poniżej płaszczyzny paska stanu.

- SBT_NOBORDERS tekst jest rysowany bez obramowania.

- SBT_OWNERDRAW tekst jest rysowany w oknie nadrzędnym.

- SBT_POPOUT tekst jest rysowany z obramowaniem, aby był wyświetlany powyżej płaszczyzny paska stanu.

### <a name="return-value"></a>Wartość zwracana

Długość (w znakach) tekstu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

##  <a name="gettiptext"></a>CStatusBarCtrl:: GetTipText

Pobiera tekst etykietki narzędzia dla okienka na pasku stanu.

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Indeks (liczony od zera) okienka paska stanu do odbierania tekstu etykietki narzędzia.

### <a name="return-value"></a>Wartość zwracana

Obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający tekst, który ma być używany w etykietce narzędzia.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext), zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

##  <a name="issimple"></a>CStatusBarCtrl:: IsSimple

Sprawdza formant okna stanu, aby określić, czy jest w trybie prostym.

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli formant okna stanu jest w trybie prostym; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [SB_ISSIMPLE](/windows/win32/Controls/sb-issimple), zgodnie z opisem w Windows SDK.

##  <a name="setbkcolor"></a>CStatusBarCtrl:: SetBkColor

Ustawia kolor tła na pasku stanu.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parametry

*znaki*<br/>
Wartość COLORREF, która określa nowy kolor tła. Określ wartość CLR_DEFAULT, aby uniemożliwić użycie przez pasek stanu domyślnego koloru tła.

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) , która reprezentuje poprzedni domyślny kolor tła.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor), zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

##  <a name="seticon"></a>CStatusBarCtrl:: SetIcon

Ustawia ikonę okienka na pasku stanu.

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Indeks (liczony od zera) okienka, który będzie otrzymywał ikonę. Jeśli ten parametr ma wartość-1, przyjmuje się, że jest to prosty pasek stanu.

*hIcon*<br/>
Dojście do ikony, która ma zostać ustawiona. Jeśli ta wartość jest RÓWNa NULL, ikona zostanie usunięta z części.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [SB_SETICON](/windows/win32/Controls/sb-seticon), zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CStatusBarCtrl:: SetBkColor](#setbkcolor).

##  <a name="setminheight"></a>CStatusBarCtrl:: SetMinHeight

Ustawia minimalną wysokość obszaru rysowania kontrolki paska stanu.

```
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Minimalna wysokość formantu (w pikselach).

### <a name="remarks"></a>Uwagi

Minimalna wysokość to suma wartości *Nmin* i podwójnej szerokości (w pikselach) pionowej krawędzi kontrolki pasek stanu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

##  <a name="setparts"></a>CStatusBarCtrl:: SetParts

Ustawia liczbę części w kontrolce pasek stanu i współrzędne prawej krawędzi każdej części.

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>Parametry

*nParts*<br/>
Liczba części do ustawienia. Liczba części nie może być większa niż 255.

*pWidths*<br/>
Adres tablicy liczb całkowitych, która ma taką samą liczbę elementów jak części określone przez *nParts*. Każdy element w tablicy określa położenie, we współrzędnych klienta, prawej krawędzi odpowiedniej części. Jeśli element ma wartość-1, pozycja prawej krawędzi tej części rozciąga się z prawą krawędzią kontrolki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

##  <a name="setsimple"></a>CStatusBarCtrl:: SetSimple

Określa, czy kontrolka paska stanu wyświetla prosty tekst, czy też wyświetla wszystkie części sterujące ustawione przez poprzednie [](#setparts)wywołanie do setpart.

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>Parametry

*bSimple*<br/>
podczas Flaga typu wyświetlania. Jeśli ten parametr ma wartość TRUE, formant wyświetla prosty tekst; Jeśli ma wartość FALSE, wyświetla wiele części.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja zmieni formant paska stanu z nieproste na proste lub odwrotnie, system natychmiast ponownie narysuje formant.

##  <a name="settext"></a>CStatusBarCtrl:: SetText

Ustawia tekst w danej części kontrolki pasek stanu.

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Adres ciągu zakończenia o wartości null, określający tekst do ustawienia. Jeśli *npowiadomienia* jest SBT_OWNERDRAW, *lpszText* reprezentuje 32 bitów danych.

*nPane*<br/>
Indeks (liczony od zera) części do ustawienia. Jeśli wartość jest równa 255, przyjmuje się, że kontrolka pasek stanu jest prostą kontrolką tylko z jedną częścią.

*Npowiadomienia*<br/>
Typ operacji rysowania. Zobacz [komunikat SB_SETTEXT](/windows/win32/Controls/sb-settext) , aby uzyskać listę możliwych wartości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Komunikat unieważnia część kontrolki, która zmieniła się, powodując wyświetlenie nowego tekstu, gdy kontrolka odbierze komunikat WM_PAINT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

##  <a name="settiptext"></a>CStatusBarCtrl:: SetTipText

Ustawia tekst etykietki narzędzia dla okienka na pasku stanu.

```
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Indeks (liczony od zera) okienka paska stanu do odbierania tekstu etykietki narzędzia.

*pszTipText*<br/>
Wskaźnik do ciągu zawierającego tekst etykietki narzędzia.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [SB_SETTIPTEXT](/windows/win32/Controls/sb-settiptext), zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)
