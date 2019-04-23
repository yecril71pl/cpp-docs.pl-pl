---
title: CPagerCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CPagerCtrl
- AFXCMN/CPagerCtrl
- AFXCMN/CPagerCtrl::CPagerCtrl
- AFXCMN/CPagerCtrl::Create
- AFXCMN/CPagerCtrl::CreateEx
- AFXCMN/CPagerCtrl::ForwardMouse
- AFXCMN/CPagerCtrl::GetBkColor
- AFXCMN/CPagerCtrl::GetBorder
- AFXCMN/CPagerCtrl::GetButtonSize
- AFXCMN/CPagerCtrl::GetButtonState
- AFXCMN/CPagerCtrl::GetDropTarget
- AFXCMN/CPagerCtrl::GetScrollPos
- AFXCMN/CPagerCtrl::IsButtonDepressed
- AFXCMN/CPagerCtrl::IsButtonGrayed
- AFXCMN/CPagerCtrl::IsButtonHot
- AFXCMN/CPagerCtrl::IsButtonInvisible
- AFXCMN/CPagerCtrl::IsButtonNormal
- AFXCMN/CPagerCtrl::RecalcSize
- AFXCMN/CPagerCtrl::SetBkColor
- AFXCMN/CPagerCtrl::SetBorder
- AFXCMN/CPagerCtrl::SetButtonSize
- AFXCMN/CPagerCtrl::SetChild
- AFXCMN/CPagerCtrl::SetScrollPos
helpviewer_keywords:
- CPagerCtrl [MFC], CPagerCtrl
- CPagerCtrl [MFC], Create
- CPagerCtrl [MFC], CreateEx
- CPagerCtrl [MFC], ForwardMouse
- CPagerCtrl [MFC], GetBkColor
- CPagerCtrl [MFC], GetBorder
- CPagerCtrl [MFC], GetButtonSize
- CPagerCtrl [MFC], GetButtonState
- CPagerCtrl [MFC], GetDropTarget
- CPagerCtrl [MFC], GetScrollPos
- CPagerCtrl [MFC], IsButtonDepressed
- CPagerCtrl [MFC], IsButtonGrayed
- CPagerCtrl [MFC], IsButtonHot
- CPagerCtrl [MFC], IsButtonInvisible
- CPagerCtrl [MFC], IsButtonNormal
- CPagerCtrl [MFC], RecalcSize
- CPagerCtrl [MFC], SetBkColor
- CPagerCtrl [MFC], SetBorder
- CPagerCtrl [MFC], SetButtonSize
- CPagerCtrl [MFC], SetChild
- CPagerCtrl [MFC], SetScrollPos
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
ms.openlocfilehash: 648bc17f0f130b831aa619b90ed13ba6be35b4d4
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417608"
---
# <a name="cpagerctrl-class"></a>CPagerCtrl Class

`CPagerCtrl` Klasy opakowuje formant pagera Windows, który można przewijać w widoku okna, które nie pasuje do okna nadrzędnego.

## <a name="syntax"></a>Składnia

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|Konstruuje `CPagerCtrl` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPagerCtrl::Create](#create)|Tworzy kontrolkę pagera przy użyciu określonego stylów i dołącza go do bieżącego `CPagerCtrl` obiektu.|
|[CPagerCtrl::CreateEx](#createex)|Tworzy kontrolkę pagera przy użyciu określonego style rozszerzone i dołącza go do bieżącego `CPagerCtrl` obiektu.|
|[CPagerCtrl::ForwardMouse](#forwardmouse)|Włącza lub wyłącza przekazywanie [WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove) wiadomości do okna, które są zawarte w bieżącym kontroli pagera.|
|[CPagerCtrl::GetBkColor](#getbkcolor)|Pobiera bieżącą kontroli pagera kolor tła.|
|[CPagerCtrl::GetBorder](#getborder)|Pobiera o bieżącej kontroli pagera wielkości.|
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Pobiera rozmiar przycisku do kontroli bieżącej pager.|
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Pobiera stan określonego przycisku w bieżącej kontroli pagera.|
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Pobiera [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) interfejs dla bieżącej kontroli pagera.|
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Pobiera położenie przewijania bieżącą kontroli pagera.|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Wskazuje, czy określonego przycisku bieżącą kontroli pagera w `pressed` stanu.|
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Wskazuje, czy określonego przycisku bieżącą kontroli pagera w `grayed` stanu.|
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Wskazuje, czy określonego przycisku bieżącą kontroli pagera w `hot` stanu.|
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Wskazuje, czy określonego przycisku bieżącą kontroli pagera w `invisible` stanu.|
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Wskazuje, czy określonego przycisku bieżącą kontroli pagera w `normal` stanu.|
|[CPagerCtrl::RecalcSize](#recalcsize)|Powoduje, że bieżący formant pagera, i ponownie oblicza rozmiar okna zawarte.|
|[CPagerCtrl::SetBkColor](#setbkcolor)|Ustawia kolor tła bieżącą kontroli pagera.|
|[CPagerCtrl::SetBorder](#setborder)|Określa rozmiar obramowania bieżącą kontroli pagera.|
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Określa rozmiar przycisku bieżącą kontroli pagera.|
|[CPagerCtrl::SetChild](#setchild)|Ustawia zawartego okna dla bieżącej kontroli pagera.|
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Ustawia położenie przewijania bieżącą kontroli pagera.|

## <a name="remarks"></a>Uwagi

Formant pagera jest oknem, który zawiera inne okno jest liniowy i większa niż okna nadrzędnego, która umożliwia przewijanie zawartego okna w widoku. Formant pagera są wyświetlane dwa przyciski przewijania, które automatycznie znikają w przypadku zawartego okna jest przewijane w jego zakresie położony, a w przeciwnym razie ponownie. Można utworzyć kontrolkę pagera, który przewija poziomo czy pionowo.

Na przykład jeśli aplikacja ma pasek narzędzi, który nie jest dostatecznie szeroka, aby wyświetlić wszystkie jego elementy, pasek narzędzi można przypisać do kontroli pagera, a użytkownicy będą mogli być przewinięcie w pasku narzędzi po lewej stronie lub w prawo, aby uzyskać dostęp do wszystkich elementów. Microsoft Internet Explorer w wersji 4.0 (wersja commctrl.dll 4.71) wprowadza kontroli pagera.

`CPagerCtrl` Klasa pochodzi od [CWnd](../../mfc/reference/cwnd-class.md) klasy. Więcej informacji oraz ilustrację kontrolkę pagera, zobacz [kontroli pagera](/windows/desktop/Controls/pager-controls).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

##  <a name="cpagerctrl"></a>  CPagerCtrl::CPagerCtrl

Konstruuje `CPagerCtrl` obiektu.

```
CPagerCtrl();
```

### <a name="remarks"></a>Uwagi

Użyj [CPagerCtrl::Create](#create) lub [CPagerCtrl::CreateEx](#createex) metodę, aby utworzyć formant pagera i dołącz je do `CPagerCtrl` obiektu.

##  <a name="create"></a>  CPagerCtrl::Create

Tworzy kontrolkę pagera przy użyciu określonego stylów i dołącza go do bieżącego `CPagerCtrl` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*dwStyle*|[in] Bitowa kombinacja (lub) [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [style kontroli pagera](/windows/desktop/Controls/pager-control-styles) mają być stosowane do formantu.|
|*Rect*|[in] Odwołanie do [Prostokąt](/previous-versions/dd162897\(v=vs.85\)) strukturę, która zawiera położenie i rozmiar formantu w współrzędne klienta.|
|*pParentWnd*|[in] Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne kontrolki. Ten parametr nie może mieć wartości NULL.|
|*nID*|[in] Identyfikator kontrolki.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Aby utworzyć kontrolkę pagera, Zadeklaruj `CPagerCtrl` zmiennej, następnie wywołać [CPagerCtrl::Create](#create) lub [CPagerCtrl::CreateEx](#createex) metody w tej zmiennej.

### <a name="example"></a>Przykład

Poniższy przykład tworzy formant pagera, a następnie używa [CPagerCtrl::SetChild](#setchild) metoda powiązania kontrolki przycisku bardzo długich przy użyciu kontroli pagera. Następnie w przykładzie [CPagerCtrl::SetButtonSize](#setbuttonsize) metodę, aby ustawić wysokość kontroli pagera do 20 pikseli i [CPagerCtrl::SetBorder](#setborder) metodę, aby ustawić grubość obramowania do 1 piksela.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="createex"></a>  CPagerCtrl::CreateEx

Tworzy kontrolkę pagera przy użyciu określonego style rozszerzone i dołącza go do bieżącego `CPagerCtrl` obiektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*dwExStyle*|[in] Bitowa kombinacja rozszerzone style, które mają być stosowane do formantu. Aby uzyskać więcej informacji, zobacz *dwExStyle* parametru [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) funkcji.|
|*dwStyle*|[in] Bitowa kombinacja (lub) [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [style kontroli pagera](/windows/desktop/Controls/pager-control-styles) mają być stosowane do formantu.|
|*Rect*|[in] Odwołanie do [Prostokąt](/previous-versions/dd162897\(v=vs.85\)) strukturę, która zawiera położenie i rozmiar formantu w współrzędne klienta.|
|*pParentWnd*|[in] Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne kontrolki. Ten parametr nie może mieć wartości NULL.|
|*nID*|[in] Identyfikator kontrolki.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Aby utworzyć kontrolkę pagera, Zadeklaruj `CPagerCtrl` zmiennej, następnie wywołać [CPagerCtrl::Create](#create) lub [CPagerCtrl::CreateEx](#createex) metody w tej zmiennej.

##  <a name="forwardmouse"></a>  CPagerCtrl::ForwardMouse

Włącza lub wyłącza przekazywanie [WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove) wiadomości do okna, które są zawarte w bieżącym kontroli pagera.

```
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*bForward*|[in] Wartość true, komunikaty myszy do przodu lub wartość FALSE nie przekazuje komunikaty myszy.|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_FORWARDMOUSE](/windows/desktop/Controls/pgm-forwardmouse) komunikat, który jest opisany w zestawie Windows SDK.

##  <a name="getborder"></a>  CPagerCtrl::GetBorder

Pobiera o bieżącej kontroli pagera wielkości.

```
int GetBorder() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący rozmiar obramowania (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_GETBORDER](/windows/desktop/Controls/pgm-getborder) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [CPagerCtrl::GetBorder](#getborder) metodę, która pobierze grubość obramowania kontrolki pager.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

##  <a name="getbkcolor"></a>  CPagerCtrl::GetBkColor

Pobiera bieżącą kontroli pagera kolor tła.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Wartość zwracana

A [COLORREF](/windows/desktop/gdi/colorref) wartość, która zawiera bieżący kolor tła kontrolki pager.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_GETBKCOLOR](/windows/desktop/Controls/pgm-getbkcolor) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [CPagerCtrl::SetBkColor](#setbkcolor) metodę, aby ustawić kolor tła kontroli pagera czerwony i [CPagerCtrl::GetBkColor](#getbkcolor) metody, aby upewnić się, że zmiana została wprowadzona.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="getbuttonsize"></a>  CPagerCtrl::GetButtonSize

Pobiera rozmiar przycisku do kontroli bieżącej pager.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący rozmiar przycisku (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_GETBUTTONSIZE](/windows/desktop/Controls/pgm-getbuttonsize) komunikat, który jest opisany w zestawie Windows SDK.

Jeśli formant pagera ma styl PGS_HORZ, rozmiar przycisku określa szerokość przyciski pagera, a jeśli formant pagera ma styl PGS_VERT, rozmiar przycisku określa wysokość przyciski pagera. Aby uzyskać więcej informacji, zobacz [style kontroli pagera](/windows/desktop/Controls/pager-control-styles).

##  <a name="getbuttonstate"></a>  CPagerCtrl::GetButtonState

Pobiera stan przycisku przewijania określonego w bieżącym kontroli pagera.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButton*|[in] Określa przycisk, którego stan jest pobierany. Jeśli styl kontroli pagera PGS_HORZ, należy określić PGB_TOPORLEFT przycisku po lewej stronie i PGB_BOTTOMORRIGHT prawy przycisk. Jeśli styl kontroli pagera PGS_VERT, należy określić PGB_TOPORLEFT przycisk u góry i PGB_BOTTOMORRIGHT przycisk u dołu. Aby uzyskać więcej informacji, zobacz [style kontroli pagera](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

Stan przycisku określony przez *iButton* parametru. Stan to PGF_INVISIBLE, PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED albo PGF_HOT. Aby uzyskać więcej informacji, zobacz sekcję zwracają wartość [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) wiadomości.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) komunikat, który jest opisany w zestawie Windows SDK.

##  <a name="getdroptarget"></a>  CPagerCtrl::GetDropTarget

Pobiera [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) interfejs dla bieżącej kontroli pagera.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IDropTarget` interfejs dla bieżącej kontroli pagera.

### <a name="remarks"></a>Uwagi

`IDropTarget` to jeden z interfejsów wdrożenia do obsługi operacji przeciągania i upuszczania w aplikacji.

Ta metoda wysyła [PGM_GETDROPTARGET](/windows/desktop/Controls/pgm-getdroptarget) komunikat, który jest opisany w zestawie Windows SDK. Obiekt wywołujący tę metodę jest odpowiedzialny za wywołanie `Release` członkiem [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) interfejs, gdy interfejs nie jest już potrzebny.

##  <a name="getscrollpos"></a>  CPagerCtrl::GetScrollPos

Pobiera położenie przewijania bieżącą kontroli pagera.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżące położenie przewijania (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_GETPOS](/windows/desktop/Controls/pgm-getpos) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [CPagerCtrl::GetScrollPos](#getscrollpos) metodę, która pobierze bieżące położenie przewijania kontroli pagera. Jeśli formant pagera nie jest już przewijane do zera, skrajnie po lewej stronie pozycji w przykładzie użyto [CPagerCtrl::SetScrollPos](#setscrollpos) metodę, aby ustawić położenie przewijania na zero.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

##  <a name="isbuttondepressed"></a>  CPagerCtrl::IsButtonDepressed

Wskazuje, czy przycisku przewijania określonego bieżącą kontroli pagera jest w stanie po naciśnięciu.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButton*|[in] Określa przycisk, którego stan jest pobierany. Jeśli styl kontroli pagera PGS_HORZ, należy określić PGB_TOPORLEFT przycisku po lewej stronie i PGB_BOTTOMORRIGHT prawy przycisk. Jeśli styl kontroli pagera PGS_VERT, należy określić PGB_TOPORLEFT przycisk u góry i PGB_BOTTOMORRIGHT przycisk u dołu. Aby uzyskać więcej informacji, zobacz [style kontroli pagera](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli określony przycisk znajduje się w stanie po naciśnięciu; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) komunikat, który jest opisany w zestawie Windows SDK. Następnie sprawdza, czy stan, który jest zwracany jest PGF_DEPRESSED. Aby uzyskać więcej informacji, zobacz sekcję zwracają wartość [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) wiadomości.

##  <a name="isbuttongrayed"></a>  CPagerCtrl::IsButtonGrayed

Wskazuje, czy przycisk przewijania określonego bieżącej kontroli pagera znajduje się w stanie wygaszone.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButton*|[in] Określa przycisk, którego stan jest pobierany. Jeśli styl kontroli pagera PGS_HORZ, należy określić PGB_TOPORLEFT przycisku po lewej stronie i PGB_BOTTOMORRIGHT prawy przycisk. Jeśli styl kontroli pagera PGS_VERT, należy określić PGB_TOPORLEFT przycisk u góry i PGB_BOTTOMORRIGHT przycisk u dołu. Aby uzyskać więcej informacji, zobacz [style kontroli pagera](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli określony przycisk znajduje się w stanie wygaszone; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) komunikat, który jest opisany w zestawie Windows SDK. Następnie sprawdza, czy stan, który jest zwracany jest PGF_GRAYED. Aby uzyskać więcej informacji, zobacz sekcję zwracają wartość [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) wiadomości.

##  <a name="isbuttonhot"></a>  CPagerCtrl::IsButtonHot

Wskazuje, czy przycisk przewijania określonego bieżącej kontroli pagera znajduje się w stanie.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButton*|[in] Określa przycisk, którego stan jest pobierany. Jeśli styl kontroli pagera PGS_HORZ, należy określić PGB_TOPORLEFT przycisku po lewej stronie i PGB_BOTTOMORRIGHT prawy przycisk. Jeśli styl kontroli pagera PGS_VERT, należy określić PGB_TOPORLEFT przycisk u góry i PGB_BOTTOMORRIGHT przycisk u dołu. Aby uzyskać więcej informacji, zobacz [style kontroli pagera](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli określony przycisk znajduje się w stanie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) komunikat, który jest opisany w zestawie Windows SDK. Następnie sprawdza, czy stan, który jest zwracany jest PGF_HOT. Aby uzyskać więcej informacji, zobacz sekcję zwracają wartość [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) wiadomości.

##  <a name="isbuttoninvisible"></a>  CPagerCtrl::IsButtonInvisible

Wskazuje, czy przycisku przewijania określonego bieżącą kontroli pagera jest w stanie niewidoczne.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButton*|[in] Określa przycisk, którego stan jest pobierany. Jeśli styl kontroli pagera PGS_HORZ, należy określić PGB_TOPORLEFT przycisku po lewej stronie i PGB_BOTTOMORRIGHT prawy przycisk. Jeśli styl kontroli pagera PGS_VERT, należy określić PGB_TOPORLEFT przycisk u góry i PGB_BOTTOMORRIGHT przycisk u dołu. Aby uzyskać więcej informacji, zobacz [style kontroli pagera](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli określony przycisk znajduje się w stanie niewidoczne; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Windows sprawia, że przycisk przewijania w określonym kierunku niewidoczne po zawartego okna jest przewijane w jego zakresie położony, ponieważ kliknięcie przycisku Dalej nie można przełączyć więcej zawartego okna w widoku.

Ta metoda wysyła [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) komunikat, który jest opisany w zestawie Windows SDK. Następnie sprawdza, czy stan, który jest zwracany jest PGF_INVISIBLE. Aby uzyskać więcej informacji, zobacz sekcję zwracają wartość [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) wiadomości.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [CPagerCtrl::IsButtonInvisible](#isbuttoninvisible) metodę, aby określić, czy formant pagera lewą i przyciski przewijania w prawo są wyświetlane.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

##  <a name="isbuttonnormal"></a>  CPagerCtrl::IsButtonNormal

Wskazuje, czy przycisku przewijania określonego bieżącą kontroli pagera jest w normalnym stanie.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButton*|[in] Określa przycisk, którego stan jest pobierany. Jeśli styl kontroli pagera PGS_HORZ, należy określić PGB_TOPORLEFT przycisku po lewej stronie i PGB_BOTTOMORRIGHT prawy przycisk. Jeśli styl kontroli pagera PGS_VERT, należy określić PGB_TOPORLEFT przycisk u góry i PGB_BOTTOMORRIGHT przycisk u dołu. Aby uzyskać więcej informacji, zobacz [style kontroli pagera](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli określony przycisk znajduje się w normalnym stanie.; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) komunikat, który jest opisany w zestawie Windows SDK. Następnie sprawdza, czy stan, który jest zwracany jest PGF_NORMAL. Aby uzyskać więcej informacji, zobacz sekcję zwracają wartość [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) wiadomości.

##  <a name="recalcsize"></a>  CPagerCtrl::RecalcSize

Powoduje, że bieżący formant pagera, i ponownie oblicza rozmiar okna zawarte.

```
void RecalcSize();
```

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_RECALCSIZE](/windows/desktop/Controls/pgm-recalcsize) komunikat, który jest opisany w zestawie Windows SDK. W związku z tym, kontroli pagera wysyła [PGN_CALCSIZE](/windows/desktop/Controls/pgn-calcsize) powiadomienie, aby uzyskać przewijalne wymiary zawartego okna.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [CPagerCtrl::RecalcSize](#recalcsize) metodę, aby zażądać bieżącej kontroli pagera, aby ponownie obliczyć jej rozmiaru.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [komunikatu odbicia](../../mfc/tn062-message-reflection-for-windows-controls.md) do włączania kontroli pagera ponownego obliczenia rozmiaru zamiast okno nadrzędne kontrolki do wykonywania obliczeń. Przykład pochodzi `MyPagerCtrl` klasy z [klasa CPagerCtrl](../../mfc/reference/cpagerctrl-class.md), następnie używa mapy komunikatów, aby skojarzyć [PGN_CALCSIZE](/windows/desktop/Controls/pgn-calcsize) powiadomienia o `OnCalcsize` obsługi powiadomień. W tym przykładzie obsługi powiadomień Ustawia szerokość i wysokość kontroli pagera wartości stałych.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

##  <a name="setbkcolor"></a>  CPagerCtrl::SetBkColor

Ustawia kolor tła bieżącą kontroli pagera.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*clrBk*|[in] A [COLORREF](/windows/desktop/gdi/colorref) wartość, która zawiera nowy kolor tła kontrolki pager.|

### <a name="return-value"></a>Wartość zwracana

A [COLORREF](/windows/desktop/gdi/colorref) wartość, która zawiera poprzedni kolor tła kontroli pagera.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_SETBKCOLOR](/windows/desktop/Controls/pgm-setbkcolor) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [CPagerCtrl::SetBkColor](#setbkcolor) metodę, aby ustawić kolor tła kontroli pagera czerwony i [CPagerCtrl::GetBkColor](#getbkcolor) metody, aby upewnić się, że zmiana została wprowadzona.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="setborder"></a>  CPagerCtrl::SetBorder

Określa rozmiar obramowania bieżącą kontroli pagera.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iBorder*|[in] Nowy rozmiar obramowania (w pikselach). Jeśli *iBorder* parametr jest liczbą ujemną, rozmiar obramowania jest równa zero.|

### <a name="return-value"></a>Wartość zwracana

Poprzedni rozmiar obramowania (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_SETBORDER](/windows/desktop/Controls/pgm-setborder) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład tworzy formant pagera, a następnie używa [CPagerCtrl::SetChild](#setchild) metoda powiązania kontrolki przycisku bardzo długich przy użyciu kontroli pagera. Następnie w przykładzie [CPagerCtrl::SetButtonSize](#setbuttonsize) metodę, aby ustawić wysokość kontroli pagera do 20 pikseli i [CPagerCtrl::SetBorder](#setborder) metodę, aby ustawić grubość obramowania do 1 piksela.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setbuttonsize"></a>  CPagerCtrl::SetButtonSize

Określa rozmiar przycisku bieżącą kontroli pagera.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButtonSize*|[in] Nowy rozmiar przycisku (w pikselach).|

### <a name="return-value"></a>Wartość zwracana

Poprzedni rozmiar przycisku (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_SETBUTTONSIZE](/windows/desktop/Controls/pgm-setpos) komunikat, który jest opisany w zestawie Windows SDK.

Jeśli formant pagera ma styl PGS_HORZ, rozmiar przycisku określa szerokość przyciski pagera, a jeśli formant pagera ma styl PGS_VERT, rozmiar przycisku określa wysokość przyciski pagera. Domyślny rozmiar przycisku to trzy czwarte szerokości paska przewijania, a rozmiar przycisku minimalnych to 12 pikseli. Aby uzyskać więcej informacji, zobacz [style kontroli pagera](/windows/desktop/Controls/pager-control-styles).

### <a name="example"></a>Przykład

Poniższy przykład tworzy formant pagera, a następnie używa [CPagerCtrl::SetChild](#setchild) metoda powiązania kontrolki przycisku bardzo długich przy użyciu kontroli pagera. Następnie w przykładzie [CPagerCtrl::SetButtonSize](#setbuttonsize) metodę, aby ustawić wysokość kontroli pagera do 20 pikseli i [CPagerCtrl::SetBorder](#setborder) metodę, aby ustawić grubość obramowania do 1 piksela.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setchild"></a>  CPagerCtrl::SetChild

Ustawia zawartego okna dla bieżącej kontroli pagera.

```
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*hwndChild*|[in] Dojście do okna, które mają zostać zawarte.|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_SETCHILD](/windows/desktop/Controls/pgm-setchild) komunikat, który jest opisany w zestawie Windows SDK.

Ta metoda nie powoduje zmiany nadrzędnego zawartego okna; przypisuje tylko uchwyt okna do kontroli pagera przewijania. W większości przypadków zawartego okna będzie kontroli pagera okna podrzędnego.

### <a name="example"></a>Przykład

Poniższy przykład tworzy formant pagera, a następnie używa [CPagerCtrl::SetChild](#setchild) metoda powiązania kontrolki przycisku bardzo długich przy użyciu kontroli pagera. Następnie w przykładzie [CPagerCtrl::SetButtonSize](#setbuttonsize) metodę, aby ustawić wysokość kontroli pagera do 20 pikseli i [CPagerCtrl::SetBorder](#setborder) metodę, aby ustawić grubość obramowania do 1 piksela.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setscrollpos"></a>  CPagerCtrl::SetScrollPos

Ustawia położenie przewijania bieżącą kontroli pagera.

```
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iPos*|[in] Nowe położenie przewijania (w pikselach).|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [PGM_SETPOS](/windows/desktop/Controls/pgm-setpos) komunikat, który jest opisany w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa CPagerCtrl](../../mfc/reference/cpagerctrl-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Formanty pager](/windows/desktop/Controls/pager-controls)
