---
title: Klasa CPagerCtrl
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
ms.openlocfilehash: cd27a3acf26abe39831089546df317679f2ecab6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753704"
---
# <a name="cpagerctrl-class"></a>Klasa CPagerCtrl

Klasa `CPagerCtrl` zawija kontrolkę pagera systemu Windows, która może przewijać do widoku zawarte okno, które nie pasuje do okna zawierającego.

## <a name="syntax"></a>Składnia

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|Konstruuje `CPagerCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPagerCtrl::Utwórz](#create)|Tworzy kontrolkę pagera z określonymi stylami i dołącza ją do bieżącego `CPagerCtrl` obiektu.|
|[CPagerCtrl::CreateEx](#createex)|Tworzy kontrolkę pagera z określonymi rozszerzonymi `CPagerCtrl` stylami i dołącza ją do bieżącego obiektu.|
|[CPagerCtrl::ForwardMouse](#forwardmouse)|Włącza lub wyłącza przekazywanie [wiadomości WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) do okna, które jest zawarte w bieżącym formancie pagera.|
|[CPagerCtrl::GetBkColor](#getbkcolor)|Pobiera kolor tła bieżącego kontrolki pagera.|
|[CPagerCtrl::GetBorder](#getborder)|Pobiera rozmiar obramowania bieżącego formantu pagera.|
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Pobiera rozmiar przycisku bieżącego kontrolki pagera.|
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Pobiera stan określonego przycisku w bieżącym formancie pagera.|
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Pobiera interfejs [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) dla bieżącego kontrolki pagera.|
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Pobiera położenie przewijania bieżącego kontrolki pagera.|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Wskazuje, czy określony przycisk bieżącego formantu pagera jest w `pressed` stanie.|
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Wskazuje, czy określony przycisk bieżącego formantu pagera jest w `grayed` stanie.|
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Wskazuje, czy określony przycisk bieżącego formantu pagera jest w `hot` stanie.|
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Wskazuje, czy określony przycisk bieżącego formantu pagera jest w `invisible` stanie.|
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Wskazuje, czy określony przycisk bieżącego formantu pagera jest w `normal` stanie.|
|[CPagerCtrl::RecalcSize](#recalcsize)|Powoduje, że bieżący formant pagera ponownie obliczy rozmiar okna zawartego.|
|[CPagerCtrl::SetBkColor](#setbkcolor)|Ustawia kolor tła bieżącego kontrolki pagera.|
|[CPagerCtrl::SetBorder](#setborder)|Ustawia rozmiar obramowania bieżącego formantu pagera.|
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Ustawia rozmiar przycisku bieżącego kontrolki pagera.|
|[CPagerCtrl::SetChild](#setchild)|Ustawia okno zawarte dla bieżącego kontrolki pagera.|
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Ustawia położenie przewijania bieżącego kontrolki pagera.|

## <a name="remarks"></a>Uwagi

Kontrolka pagera to okno, które zawiera inne okno, które jest liniowe i większe niż okno zawierające i umożliwia przewijanie zawartego okna do widoku. Formant pagera wyświetla dwa przyciski przewijania, które automatycznie znikają, gdy zawarte okno jest przewijane do najdalej i pojawiają się ponownie w inny sposób. Formant pagera, który przewija się w poziomie lub w pionie.

Na przykład jeśli aplikacja ma pasek narzędzi, który nie jest wystarczająco szeroki, aby wyświetlić wszystkie jego elementy, można przypisać pasek narzędzi do formantu pagera i użytkownicy będą mogli przewijać pasek narzędzi w lewo lub w prawo, aby uzyskać dostęp do wszystkich elementów. Microsoft Internet Explorer w wersji 4.0 (commctrl.dll w wersji 4.71) wprowadza kontrolkę pagera.

Klasa `CPagerCtrl` jest pochodną [CWnd](../../mfc/reference/cwnd-class.md) klasy. Aby uzyskać więcej informacji i ilustrację formantu pagera, zobacz [Kontrolki pagera](/windows/win32/Controls/pager-controls).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="cpagerctrlcpagerctrl"></a><a name="cpagerctrl"></a>CPagerCtrl::CPagerCtrl

Konstruuje `CPagerCtrl` obiekt.

```
CPagerCtrl();
```

### <a name="remarks"></a>Uwagi

Użyj [CPagerCtrl::Create](#create) lub [CPagerCtrl::CreateEx](#createex) metody, aby utworzyć kontrolkę pagera i dołączyć go do `CPagerCtrl` obiektu.

## <a name="cpagerctrlcreate"></a><a name="create"></a>CPagerCtrl::Utwórz

Tworzy kontrolkę pagera z określonymi stylami i dołącza ją do bieżącego `CPagerCtrl` obiektu.

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
|*Dwstyle*|[w] Kombinacja bitowa (OR) [stylów okien](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [stylów formantu pagera,](/windows/win32/Controls/pager-control-styles) które mają zostać zastosowane do formantu.|
|*Rect*|[w] Odwołanie do struktury [RECT,](/windows/win32/api/windef/ns-windef-rect) która zawiera położenie i rozmiar formantu we współrzędnych klienta.|
|*pParentWnd*|[w] Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu, który jest nadrzędnym oknem formantu. Ten parametr nie może być null.|
|*Nid*|[w] Identyfikator formantu.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby utworzyć kontrolkę pagera, zadeklaruj zmienną, `CPagerCtrl` następnie wywołaj metodę [CPagerCtrl:::Create](#create) lub [CPagerCtrl::CreateEx](#createex) metody na tej zmiennej.

### <a name="example"></a>Przykład

Poniższy przykład tworzy kontrolkę pagera, a następnie używa [CPagerCtrl::SetChild](#setchild) metody skojarzyć kontrolkę bardzo długi przycisk z kontrolką pagera. W przykładzie użyto metody [CPagerCtrl::SetButtonSize,](#setbuttonsize) aby ustawić wysokość formantu pagera na 20 pikseli, a [CPagerCtrl::SetBorder,](#setborder) aby ustawić grubość obramowania na 1 piksel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlcreateex"></a><a name="createex"></a>CPagerCtrl::CreateEx

Tworzy kontrolkę pagera z określonymi rozszerzonymi `CPagerCtrl` stylami i dołącza ją do bieżącego obiektu.

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
|*Dwexstyle*|[w] Bitowa kombinacja rozszerzonych stylów, które mają być zastosowane do formantu. Aby uzyskać więcej informacji, zobacz parametr *dwExStyle* funkcji [CreateWindowEx.](/windows/win32/api/winuser/nf-winuser-createwindowexw)|
|*Dwstyle*|[w] Kombinacja bitowa (OR) [stylów okien](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [stylów formantu pagera,](/windows/win32/Controls/pager-control-styles) które mają zostać zastosowane do formantu.|
|*Rect*|[w] Odwołanie do struktury [RECT,](/windows/win32/api/windef/ns-windef-rect) która zawiera położenie i rozmiar formantu we współrzędnych klienta.|
|*pParentWnd*|[w] Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu, który jest nadrzędnym oknem formantu. Ten parametr nie może być null.|
|*Nid*|[w] Identyfikator formantu.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby utworzyć kontrolkę pagera, zadeklaruj zmienną, `CPagerCtrl` następnie wywołaj metodę [CPagerCtrl:::Create](#create) lub [CPagerCtrl::CreateEx](#createex) metody na tej zmiennej.

## <a name="cpagerctrlforwardmouse"></a><a name="forwardmouse"></a>CPagerCtrl::ForwardMouse

Włącza lub wyłącza przekazywanie [wiadomości WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) do okna, które jest zawarte w bieżącym formancie pagera.

```cpp
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*bDo tej pory*|[w] PRAWDA do przekazywania wiadomości myszy lub FALSE, aby nie przesyłać dalej wiadomości myszy.|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_FORWARDMOUSE,](/windows/win32/Controls/pgm-forwardmouse) który jest opisany w windows SDK.

## <a name="cpagerctrlgetborder"></a><a name="getborder"></a>CPagerCtrl::GetBorder

Pobiera rozmiar obramowania bieżącego formantu pagera.

```
int GetBorder() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący rozmiar obramowania mierzony w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBORDER,](/windows/win32/Controls/pgm-getborder) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [CPagerCtrl::GetBorder](#getborder) metody do pobierania grubości obramowania formantu pagera.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

## <a name="cpagerctrlgetbkcolor"></a><a name="getbkcolor"></a>CPagerCtrl::GetBkColor

Pobiera kolor tła bieżącego kontrolki pagera.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) zawierająca bieżący kolor tła formantu pagera.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBKCOLOR,](/windows/win32/Controls/pgm-getbkcolor) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [CPagerCtrl::SetBkColor](#setbkcolor) metody, aby ustawić kolor tła pagera formantu na czerwony i [CPagerCtrl::GetBkColor](#getbkcolor) metody, aby potwierdzić, że zmiana została wniesiona.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlgetbuttonsize"></a><a name="getbuttonsize"></a>CPagerCtrl::GetButtonSize

Pobiera rozmiar przycisku bieżącego kontrolki pagera.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący rozmiar przycisku mierzony w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBUTTONSIZE,](/windows/win32/Controls/pgm-getbuttonsize) który jest opisany w windows SDK.

Jeśli kontrolka pagera ma styl PGS_HORZ, rozmiar przycisku określa szerokość przycisków pagera, a jeśli kontrolka pagera ma styl PGS_VERT, rozmiar przycisku określa wysokość przycisków pagera. Aby uzyskać więcej informacji, zobacz [Style sterowania pagerem](/windows/win32/Controls/pager-control-styles).

## <a name="cpagerctrlgetbuttonstate"></a><a name="getbuttonstate"></a>CPagerCtrl::GetButtonState

Pobiera stan określonego przycisku przewijania w bieżącym formancie pagera.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Przycisk iButton*|[w] Wskazuje przycisk, dla którego jest pobierany stan. Jeśli styl sterowania pagerem jest PGS_HORZ, określ PGB_TOPORLEFT lewego przycisku i PGB_BOTTOMORRIGHT dla prawego przycisku. Jeśli styl sterowania pagerem jest PGS_VERT, określ PGB_TOPORLEFT górnego przycisku i PGB_BOTTOMORRIGHT dolnego przycisku. Aby uzyskać więcej informacji, zobacz [Style sterowania pagerem](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

Stan przycisku określony przez parametr *iButton.* Państwo jest albo PGF_INVISIBLE, PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED, albo PGF_HOT. Aby uzyskać więcej informacji, zobacz sekcję Zwracana wartość [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) komunikatu.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) który jest opisany w windows SDK.

## <a name="cpagerctrlgetdroptarget"></a><a name="getdroptarget"></a>CPagerCtrl::GetDropTarget

Pobiera interfejs [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) dla bieżącego kontrolki pagera.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IDropTarget` interfejsu dla bieżącego kontrolki pagera.

### <a name="remarks"></a>Uwagi

`IDropTarget`jest jednym z interfejsów zaimplementować do obsługi operacji przeciągania i upuszczania w aplikacji.

Ta metoda wysyła komunikat [PGM_GETDROPTARGET,](/windows/win32/Controls/pgm-getdroptarget) który jest opisany w windows SDK. Wywołujący tej metody jest odpowiedzialny `Release` za wywołanie członka interfejsu [IDropTarget,](/windows/win32/api/oleidl/nn-oleidl-idroptarget) gdy interfejs nie jest już potrzebny.

## <a name="cpagerctrlgetscrollpos"></a><a name="getscrollpos"></a>CPagerCtrl::GetScrollPos

Pobiera położenie przewijania bieżącego kontrolki pagera.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca pozycja przewijania mierzona w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETPOS,](/windows/win32/Controls/pgm-getpos) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [CPagerCtrl::GetScrollPos](#getscrollpos) metody do pobierania bieżącej pozycji przewijania formantu pagera. Jeśli formant pagera nie jest już przewijany do zera, pozycja po lewej stronie, w przykładzie użyto [metody CPagerCtrl::SetScrollPos,](#setscrollpos) aby ustawić pozycję przewijania na zero.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

## <a name="cpagerctrlisbuttondepressed"></a><a name="isbuttondepressed"></a>CPagerCtrl::IsButtonDepressed

Wskazuje, czy określony przycisk przewijania bieżącego formantu pagera jest w stanie naciśnięcia.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Przycisk iButton*|[w] Wskazuje przycisk, dla którego jest pobierany stan. Jeśli styl sterowania pagerem jest PGS_HORZ, określ PGB_TOPORLEFT lewego przycisku i PGB_BOTTOMORRIGHT dla prawego przycisku. Jeśli styl sterowania pagerem jest PGS_VERT, określ PGB_TOPORLEFT górnego przycisku i PGB_BOTTOMORRIGHT dolnego przycisku. Aby uzyskać więcej informacji, zobacz [Style sterowania pagerem](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli określony przycisk jest w stanie naciśnięcia; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) który jest opisany w windows SDK. Następnie sprawdza, czy stan, który jest zwracany jest PGF_DEPRESSED. Aby uzyskać więcej informacji, zobacz sekcję Zwracana wartość [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) komunikatu.

## <a name="cpagerctrlisbuttongrayed"></a><a name="isbuttongrayed"></a>CPagerCtrl::IsButtonGrayed

Wskazuje, czy określony przycisk przewijania bieżącego formantu pagera jest w stanie wyszarzonym.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Przycisk iButton*|[w] Wskazuje przycisk, dla którego jest pobierany stan. Jeśli styl sterowania pagerem jest PGS_HORZ, określ PGB_TOPORLEFT lewego przycisku i PGB_BOTTOMORRIGHT dla prawego przycisku. Jeśli styl sterowania pagerem jest PGS_VERT, określ PGB_TOPORLEFT górnego przycisku i PGB_BOTTOMORRIGHT dolnego przycisku. Aby uzyskać więcej informacji, zobacz [Style sterowania pagerem](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli określony przycisk jest w stanie wyszarzonym; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) który jest opisany w windows SDK. Następnie sprawdza, czy stan, który jest zwracany jest PGF_GRAYED. Aby uzyskać więcej informacji, zobacz sekcję Zwracana wartość [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) komunikatu.

## <a name="cpagerctrlisbuttonhot"></a><a name="isbuttonhot"></a>CPagerCtrl::IsButtonHot

Wskazuje, czy określony przycisk przewijania bieżącego formantu pagera jest w stanie gorąca.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Przycisk iButton*|[w] Wskazuje przycisk, dla którego jest pobierany stan. Jeśli styl sterowania pagerem jest PGS_HORZ, określ PGB_TOPORLEFT lewego przycisku i PGB_BOTTOMORRIGHT dla prawego przycisku. Jeśli styl sterowania pagerem jest PGS_VERT, określ PGB_TOPORLEFT górnego przycisku i PGB_BOTTOMORRIGHT dolnego przycisku. Aby uzyskać więcej informacji, zobacz [Style sterowania pagerem](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli określony przycisk jest w stanie gorąca; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) który jest opisany w windows SDK. Następnie sprawdza, czy stan, który jest zwracany jest PGF_HOT. Aby uzyskać więcej informacji, zobacz sekcję Zwracana wartość [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) komunikatu.

## <a name="cpagerctrlisbuttoninvisible"></a><a name="isbuttoninvisible"></a>CPagerCtrl::IsButtonInvisible

Wskazuje, czy określony przycisk przewijania bieżącego formantu pagera jest w stanie niewidocznym.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Przycisk iButton*|[w] Wskazuje przycisk, dla którego jest pobierany stan. Jeśli styl sterowania pagerem jest PGS_HORZ, określ PGB_TOPORLEFT lewego przycisku i PGB_BOTTOMORRIGHT dla prawego przycisku. Jeśli styl sterowania pagerem jest PGS_VERT, określ PGB_TOPORLEFT górnego przycisku i PGB_BOTTOMORRIGHT dolnego przycisku. Aby uzyskać więcej informacji, zobacz [Style sterowania pagerem](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli określony przycisk jest w stanie niewidocznym; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

System Windows sprawia, że przycisk przewijania w określonym kierunku jest widoczny, gdy zamknięte okno jest przewijane do najdalej, ponieważ kliknięcie przycisku dalej nie może spowodować wyświetlenia większej liczby zawartych okien.

Ta metoda wysyła komunikat [PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) który jest opisany w windows SDK. Następnie sprawdza, czy stan, który jest zwracany jest PGF_INVISIBLE. Aby uzyskać więcej informacji, zobacz sekcję Zwracana wartość [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) komunikatu.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [CPagerCtrl::IsButtonInvisible](#isbuttoninvisible) metody, aby ustalić, czy pager formantu lewej i prawej przyciski przewijania są widoczne.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

## <a name="cpagerctrlisbuttonnormal"></a><a name="isbuttonnormal"></a>CPagerCtrl::IsButtonNormal

Wskazuje, czy określony przycisk przewijania bieżącego formantu pagera jest w stanie normalnym.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Przycisk iButton*|[w] Wskazuje przycisk, dla którego jest pobierany stan. Jeśli styl sterowania pagerem jest PGS_HORZ, określ PGB_TOPORLEFT lewego przycisku i PGB_BOTTOMORRIGHT dla prawego przycisku. Jeśli styl sterowania pagerem jest PGS_VERT, określ PGB_TOPORLEFT górnego przycisku i PGB_BOTTOMORRIGHT dolnego przycisku. Aby uzyskać więcej informacji, zobacz [Style sterowania pagerem](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli określony przycisk jest w stanie normalnym; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) który jest opisany w windows SDK. Następnie sprawdza, czy stan, który jest zwracany jest PGF_NORMAL. Aby uzyskać więcej informacji, zobacz sekcję Zwracana wartość [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) komunikatu.

## <a name="cpagerctrlrecalcsize"></a><a name="recalcsize"></a>CPagerCtrl::RecalcSize

Powoduje, że bieżący formant pagera ponownie obliczy rozmiar okna zawartego.

```cpp
void RecalcSize();
```

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_RECALCSIZE,](/windows/win32/Controls/pgm-recalcsize) który jest opisany w windows SDK. W związku z tym kontrolka pagera wysyła powiadomienie [PGN_CALCSIZE,](/windows/win32/Controls/pgn-calcsize) aby uzyskać przewijane wymiary okna zawierającego.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [CPagerCtrl::RecalcSize](#recalcsize) metody, aby zażądać bieżącego kontrolki pagera do ponownego obliczenia jego rozmiaru.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [odbicia komunikatu,](../../mfc/tn062-message-reflection-for-windows-controls.md) aby włączyć formant pagera do ponownego obliczania własnego rozmiaru zamiast wymagać nadrzędnego okna dialogowego formantu do wykonania obliczeń. Przykład pochodzi `MyPagerCtrl` klasy z [CPagerCtrl klasy](../../mfc/reference/cpagerctrl-class.md), a następnie używa mapy wiadomości do skojarzenia powiadomienia [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) z programem `OnCalcsize` obsługi powiadomień. W tym przykładzie program obsługi powiadomień ustawia szerokość i wysokość formantu pagera na wartości stałe.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

## <a name="cpagerctrlsetbkcolor"></a><a name="setbkcolor"></a>CPagerCtrl::SetBkColor

Ustawia kolor tła bieżącego kontrolki pagera.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*clrBk ( clrBk )*|[w] Wartość [COLORREF,](/windows/win32/gdi/colorref) która zawiera nowy kolor tła formantu pagera.|

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) zawierająca poprzedni kolor tła formantu pagera.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_SETBKCOLOR,](/windows/win32/Controls/pgm-setbkcolor) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto [CPagerCtrl::SetBkColor](#setbkcolor) metody, aby ustawić kolor tła pagera formantu na czerwony i [CPagerCtrl::GetBkColor](#getbkcolor) metody, aby potwierdzić, że zmiana została wniesiona.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlsetborder"></a><a name="setborder"></a>CPagerCtrl::SetBorder

Ustawia rozmiar obramowania bieżącego formantu pagera.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iBorder*|[w] Nowy rozmiar obramowania, mierzony w pikselach. Jeśli parametr *iBorder* jest ujemny, rozmiar obramowania jest ustawiony na zero.|

### <a name="return-value"></a>Wartość zwracana

Poprzedni rozmiar obramowania, mierzony w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [komunikat PGM_SETBORDER,](/windows/win32/Controls/pgm-setborder) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład tworzy kontrolkę pagera, a następnie używa [CPagerCtrl::SetChild](#setchild) metody skojarzyć kontrolkę bardzo długi przycisk z kontrolką pagera. W przykładzie użyto metody [CPagerCtrl::SetButtonSize,](#setbuttonsize) aby ustawić wysokość formantu pagera na 20 pikseli, a [CPagerCtrl::SetBorder,](#setborder) aby ustawić grubość obramowania na 1 piksel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetbuttonsize"></a><a name="setbuttonsize"></a>CPagerCtrl::SetButtonSize

Ustawia rozmiar przycisku bieżącego kontrolki pagera.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Rozmiar iButtonSize*|[w] Nowy rozmiar przycisku, mierzony w pikselach.|

### <a name="return-value"></a>Wartość zwracana

Poprzedni rozmiar przycisku, mierzony w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_SETBUTTONSIZE,](/windows/win32/Controls/pgm-setpos) który jest opisany w windows SDK.

Jeśli kontrolka pagera ma styl PGS_HORZ, rozmiar przycisku określa szerokość przycisków pagera, a jeśli kontrolka pagera ma styl PGS_VERT, rozmiar przycisku określa wysokość przycisków pagera. Domyślny rozmiar przycisku to trzy czwarte szerokości paska przewijania, a minimalny rozmiar przycisku to 12 pikseli. Aby uzyskać więcej informacji, zobacz [Style sterowania pagerem](/windows/win32/Controls/pager-control-styles).

### <a name="example"></a>Przykład

Poniższy przykład tworzy kontrolkę pagera, a następnie używa [CPagerCtrl::SetChild](#setchild) metody skojarzyć kontrolkę bardzo długi przycisk z kontrolką pagera. W przykładzie użyto metody [CPagerCtrl::SetButtonSize,](#setbuttonsize) aby ustawić wysokość formantu pagera na 20 pikseli, a [CPagerCtrl::SetBorder,](#setborder) aby ustawić grubość obramowania na 1 piksel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetchild"></a><a name="setchild"></a>CPagerCtrl::SetChild

Ustawia okno zawarte dla bieżącego kontrolki pagera.

```cpp
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*hwndDzień*|[w] Uchwyt do okna, które ma być zawarte.|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [komunikat PGM_SETCHILD,](/windows/win32/Controls/pgm-setchild) który jest opisany w windows SDK.

Ta metoda nie zmienia element nadrzędny okna zawarte; przypisuje tylko uchwyt okna do formantu pagera do przewijania. W większości przypadków zawarte okno będzie okno podrzędne formantu pagera.

### <a name="example"></a>Przykład

Poniższy przykład tworzy kontrolkę pagera, a następnie używa [CPagerCtrl::SetChild](#setchild) metody skojarzyć kontrolkę bardzo długi przycisk z kontrolką pagera. W przykładzie użyto metody [CPagerCtrl::SetButtonSize,](#setbuttonsize) aby ustawić wysokość formantu pagera na 20 pikseli, a [CPagerCtrl::SetBorder,](#setborder) aby ustawić grubość obramowania na 1 piksel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetscrollpos"></a><a name="setscrollpos"></a>CPagerCtrl::SetScrollPos

Ustawia położenie przewijania bieżącego kontrolki pagera.

```cpp
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Ipos*|[w] Nowa pozycja przewijania mierzona w pikselach.|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_SETPOS,](/windows/win32/Controls/pgm-setpos) który jest opisany w windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa CPagerCtrl](../../mfc/reference/cpagerctrl-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Kontrolki pagera](/windows/win32/Controls/pager-controls)
