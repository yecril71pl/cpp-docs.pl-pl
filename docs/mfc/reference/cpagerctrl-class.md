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
ms.openlocfilehash: 519a376bdecc488a94eab65973e33d960ca50c8d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503030"
---
# <a name="cpagerctrl-class"></a>Klasa CPagerCtrl

`CPagerCtrl` Klasa otacza formant modułu stronicowania systemu Windows, który może przewinąć do widoku zawartego okna, które nie pasuje do okna zawierającego.

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
|[CPagerCtrl:: Create](#create)|Tworzy formant modułu stronicowania z określonymi stylami i dołącza go do bieżącego `CPagerCtrl` obiektu.|
|[CPagerCtrl::CreateEx](#createex)|Tworzy kontrolkę modułu stronicowania o określonych stylach rozszerzonych i dołącza ją `CPagerCtrl` do bieżącego obiektu.|
|[CPagerCtrl::ForwardMouse](#forwardmouse)|Włącza lub wyłącza przekazywanie komunikatów [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) do okna zawartego w bieżącej kontrolce modułu stronicowania.|
|[CPagerCtrl::GetBkColor](#getbkcolor)|Pobiera kolor tła bieżącej kontrolki modułu stronicowania.|
|[CPagerCtrl::GetBorder](#getborder)|Pobiera rozmiar obramowania bieżącej kontrolki modułu stronicowania.|
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Pobiera rozmiar przycisku bieżącej kontrolki modułu stronicowania.|
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Pobiera stan określonego przycisku w bieżącej kontrolce modułu stronicowania.|
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Pobiera Interfejs [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) dla bieżącej kontrolki modułu stronicowania.|
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Pobiera położenie przewijania bieżącej kontrolki modułu stronicowania.|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Wskazuje, czy określony przycisk bieżącego formantu modułu stronicowania jest w `pressed` stanie.|
|[CPagerCtrl:: IsButtonGrayed](#isbuttongrayed)|Wskazuje, czy określony przycisk bieżącego formantu modułu stronicowania jest w `grayed` stanie.|
|[CPagerCtrl:: IsButtonHot](#isbuttonhot)|Wskazuje, czy określony przycisk bieżącego formantu modułu stronicowania jest w `hot` stanie.|
|[CPagerCtrl:: IsButtonInvisible](#isbuttoninvisible)|Wskazuje, czy określony przycisk bieżącego formantu modułu stronicowania jest w `invisible` stanie.|
|[CPagerCtrl:: IsButtonNormal](#isbuttonnormal)|Wskazuje, czy określony przycisk bieżącego formantu modułu stronicowania jest w `normal` stanie.|
|[CPagerCtrl::RecalcSize](#recalcsize)|Powoduje, że bieżący formant modułu stronicowania ponownie oblicza rozmiar zawartego okna.|
|[CPagerCtrl::SetBkColor](#setbkcolor)|Ustawia kolor tła bieżącej kontrolki modułu stronicowania.|
|[CPagerCtrl::SetBorder](#setborder)|Ustawia rozmiar obramowania bieżącej kontrolki modułu stronicowania.|
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Ustawia rozmiar przycisku bieżącej kontrolki modułu stronicowania.|
|[CPagerCtrl::SetChild](#setchild)|Ustawia okno zawarte dla bieżącej kontrolki modułu stronicowania.|
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Ustawia położenie przewijania bieżącej kontrolki modułu stronicowania.|

## <a name="remarks"></a>Uwagi

Formant modułu stronicowania to okno zawierające inne okno, które jest liniowe i większe niż okno zawierające i umożliwia przewinięcie zawartego okna do widoku. Formant modułu stronicowania wyświetla dwa przyciski przewijania, które są automatycznie znikane, gdy zawarte okno jest przewijane do jego najwcześniejszego zakresu i pojawia się w przeciwnym razie. Można utworzyć formant modułu stronicowania, który przewija poziomo lub pionowo.

Na przykład jeśli aplikacja zawiera pasek narzędzi, który nie jest wystarczająco szeroki, aby pokazać wszystkie jego elementy, można przypisać pasek narzędzi do kontrolki modułu stronicowania, a użytkownicy będą mogli przewijać ten pasek narzędzi w lewo lub w prawo, aby uzyskać dostęp do wszystkich elementów. Program Microsoft Internet Explorer w wersji 4,0 (CommCtrl. dll w wersji 4,71) wprowadza formant modułu stronicowania.

Klasa pochodzi od klasy CWnd. [](../../mfc/reference/cwnd-class.md) `CPagerCtrl` Aby uzyskać więcej informacji i ilustracja kontrolki modułu stronicowania, zobacz [kontrolki pager](/windows/win32/Controls/pager-controls).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

##  <a name="cpagerctrl"></a>CPagerCtrl:: CPagerCtrl

Konstruuje `CPagerCtrl` obiekt.

```
CPagerCtrl();
```

### <a name="remarks"></a>Uwagi

Użyj metody [CPagerCtrl:: Create](#create) lub [CPagerCtrl:: CreateEx](#createex) , aby utworzyć kontrolkę modułu stronicowania i dołączyć `CPagerCtrl` ją do obiektu.

##  <a name="create"></a>CPagerCtrl:: Create

Tworzy formant modułu stronicowania z określonymi stylami i dołącza go do bieżącego `CPagerCtrl` obiektu.

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
|*dwStyle*|podczas Kombinacja bitowa (lub) [stylów okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [stylów kontrolki pager](/windows/win32/Controls/pager-control-styles) , które mają być zastosowane do kontrolki.|
|*cinania*|podczas Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , która zawiera położenie i rozmiar formantu we współrzędnych klienta.|
|*pParentWnd*|podczas Wskaźnik do obiektu [CWnd](../../mfc/reference/cwnd-class.md) , który jest oknem nadrzędnym formantu. Ten parametr nie może mieć wartości NULL.|
|*nID*|podczas Identyfikator kontrolki.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby utworzyć kontrolkę modułu stronicowania, `CPagerCtrl` Zadeklaruj zmienną, a następnie Wywołaj metodę [CPagerCtrl:: Create](#create) lub [CPagerCtrl:: CreateEx](#createex) dla tej zmiennej.

### <a name="example"></a>Przykład

Poniższy przykład tworzy formant modułu stronicowania, a następnie używa metody [CPagerCtrl:: SetChild](#setchild) do kojarzenia bardzo długiej kontrolki Button z kontrolką modułu stronicowania. W przykładzie zostanie użyta metoda [CPagerCtrl:: SetButtonSize](#setbuttonsize) w celu ustawienia wysokości kontrolki modułu stronicowania na 20 pikseli i metody [CPagerCtrl:: SetBorder](#setborder) w celu ustawienia grubości obramowania na 1 piksel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="createex"></a>CPagerCtrl:: CreateEx

Tworzy kontrolkę modułu stronicowania o określonych stylach rozszerzonych i dołącza ją `CPagerCtrl` do bieżącego obiektu.

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
|*dwExStyle*|podczas Bitowa kombinacja rozszerzonych stylów, które mają być zastosowane do kontrolki. Aby uzyskać więcej informacji, zobacz parametr *dwExStyle* funkcji [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) .|
|*dwStyle*|podczas Kombinacja bitowa (lub) [stylów okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [stylów kontrolki pager](/windows/win32/Controls/pager-control-styles) , które mają być zastosowane do kontrolki.|
|*cinania*|podczas Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , która zawiera położenie i rozmiar formantu we współrzędnych klienta.|
|*pParentWnd*|podczas Wskaźnik do obiektu [CWnd](../../mfc/reference/cwnd-class.md) , który jest oknem nadrzędnym formantu. Ten parametr nie może mieć wartości NULL.|
|*nID*|podczas Identyfikator kontrolki.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby utworzyć kontrolkę modułu stronicowania, `CPagerCtrl` Zadeklaruj zmienną, a następnie Wywołaj metodę [CPagerCtrl:: Create](#create) lub [CPagerCtrl:: CreateEx](#createex) dla tej zmiennej.

##  <a name="forwardmouse"></a>CPagerCtrl:: ForwardMouse

Włącza lub wyłącza przekazywanie komunikatów [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) do okna zawartego w bieżącej kontrolce modułu stronicowania.

```
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*bForward*|podczas Wartość TRUE powoduje przekazanie komunikatów myszy lub FAŁSZ, aby nie przekazywać dalej komunikatów myszy.|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_FORWARDMOUSE](/windows/win32/Controls/pgm-forwardmouse) , który jest opisany w Windows SDK.

##  <a name="getborder"></a>CPagerCtrl:: GetBorder

Pobiera rozmiar obramowania bieżącej kontrolki modułu stronicowania.

```
int GetBorder() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący rozmiar obramowania (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBORDER](/windows/win32/Controls/pgm-getborder) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie zastosowano metodę [CPagerCtrl::](#getborder) GetBorders w celu pobrania grubości obramowania kontrolki modułu stronicowania.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

##  <a name="getbkcolor"></a>CPagerCtrl:: GetBkColor

Pobiera kolor tła bieżącej kontrolki modułu stronicowania.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) , która zawiera bieżący kolor tła kontrolki modułu stronicowania.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBKCOLOR](/windows/win32/Controls/pgm-getbkcolor) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto metody [CPagerCtrl:: SetBkColor](#setbkcolor) , aby ustawić kolor tła kontrolki modułu stronicowania na czerwony, i metodę [CPagerCtrl:: GetBkColor](#getbkcolor) , aby potwierdzić, że została wprowadzona zmiana.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="getbuttonsize"></a>CPagerCtrl:: GetButtonSize

Pobiera rozmiar przycisku bieżącej kontrolki modułu stronicowania.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący rozmiar przycisku (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBUTTONSIZE](/windows/win32/Controls/pgm-getbuttonsize) , który jest opisany w Windows SDK.

Jeśli formant modułu stronicowania ma styl PGS_HORZ, rozmiar przycisku określa szerokość przycisków stronicowania, a jeśli formant modułu stronicowania ma styl PGS_VERT, rozmiar przycisku określa wysokość przycisków modułu stronicowania. Aby uzyskać więcej informacji, zobacz [Style kontrolek modułu stronicowania](/windows/win32/Controls/pager-control-styles).

##  <a name="getbuttonstate"></a>CPagerCtrl:: GetButtonState

Pobiera stan określonego przycisku przewijania w bieżącej kontrolce modułu stronicowania.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButton*|podczas Wskazuje przycisk, dla którego jest pobierany stan. Jeśli styl kontrolki modułu stronicowania to PGS_HORZ, określ PGB_TOPORLEFT dla lewego przycisku i PGB_BOTTOMORRIGHT dla przycisku po prawej stronie. Jeśli styl kontrolki modułu stronicowania to PGS_VERT, określ PGB_TOPORLEFT dla górnego przycisku i PGB_BOTTOMORRIGHT dla dolnego przycisku. Aby uzyskać więcej informacji, zobacz [Style kontrolek modułu stronicowania](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

Stan przycisku określony przez parametr *iButton* . Stanem jest PGF_INVISIBLE, PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED lub PGF_HOT. Aby uzyskać więcej informacji, zobacz sekcję zwracana wartość komunikatu [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , który jest opisany w Windows SDK.

##  <a name="getdroptarget"></a>CPagerCtrl:: GetDropTarget

Pobiera Interfejs [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) dla bieżącej kontrolki modułu stronicowania.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IDropTarget` interfejsu dla bieżącej kontrolki modułu stronicowania.

### <a name="remarks"></a>Uwagi

`IDropTarget`jest jednym z interfejsów implementowanych w celu obsługi operacji przeciągania i upuszczania w aplikacji.

Ta metoda wysyła komunikat [PGM_GETDROPTARGET](/windows/win32/Controls/pgm-getdroptarget) , który jest opisany w Windows SDK. Obiekt wywołujący tę metodę jest odpowiedzialny za wywołanie `Release` elementu członkowskiego interfejsu [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) , gdy interfejs nie jest już wymagany.

##  <a name="getscrollpos"></a>CPagerCtrl:: GetScrollPos

Pobiera położenie przewijania bieżącej kontrolki modułu stronicowania.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca pozycja przewijania (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETPOS](/windows/win32/Controls/pgm-getpos) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie zastosowano metodę [CPagerCtrl:: GetScrollPos](#getscrollpos) , aby pobrać bieżącą pozycję przewijania kontrolki modułu stronicowania. Jeśli kontrolka stronicowania nie została jeszcze przesunięta do zera, pozycja z lewej strony, w tym przykładzie, używa metody [CPagerCtrl:: SetScrollPos](#setscrollpos) , aby ustawić pozycję przewijania na zero.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

##  <a name="isbuttondepressed"></a>CPagerCtrl:: IsButtonDepressed

Wskazuje, czy określony przycisk przewijania bieżącej kontrolki modułu stronicowania jest w stanie naciśniętym.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButton*|podczas Wskazuje przycisk, dla którego jest pobierany stan. Jeśli styl kontrolki modułu stronicowania to PGS_HORZ, określ PGB_TOPORLEFT dla lewego przycisku i PGB_BOTTOMORRIGHT dla przycisku po prawej stronie. Jeśli styl kontrolki modułu stronicowania to PGS_VERT, określ PGB_TOPORLEFT dla górnego przycisku i PGB_BOTTOMORRIGHT dla dolnego przycisku. Aby uzyskać więcej informacji, zobacz [Style kontrolek modułu stronicowania](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli określony przycisk jest w stanie naciśniętym; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , który jest opisany w Windows SDK. Następnie sprawdza, czy zwróconym stanem jest PGF_DEPRESSED. Aby uzyskać więcej informacji, zobacz sekcję zwracana wartość komunikatu [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

##  <a name="isbuttongrayed"></a>CPagerCtrl:: IsButtonGrayed

Wskazuje, czy określony przycisk przewijania bieżącego formantu modułu stronicowania jest w stanie szarym.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButton*|podczas Wskazuje przycisk, dla którego jest pobierany stan. Jeśli styl kontrolki modułu stronicowania to PGS_HORZ, określ PGB_TOPORLEFT dla lewego przycisku i PGB_BOTTOMORRIGHT dla przycisku po prawej stronie. Jeśli styl kontrolki modułu stronicowania to PGS_VERT, określ PGB_TOPORLEFT dla górnego przycisku i PGB_BOTTOMORRIGHT dla dolnego przycisku. Aby uzyskać więcej informacji, zobacz [Style kontrolek modułu stronicowania](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli określony przycisk jest w stanie szarym; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , który jest opisany w Windows SDK. Następnie sprawdza, czy zwróconym stanem jest PGF_GRAYED. Aby uzyskać więcej informacji, zobacz sekcję zwracana wartość komunikatu [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

##  <a name="isbuttonhot"></a>CPagerCtrl:: IsButtonHot

Wskazuje, czy określony przycisk przewijania bieżącego formantu modułu stronicowania jest w stanie gorąca.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButton*|podczas Wskazuje przycisk, dla którego jest pobierany stan. Jeśli styl kontrolki modułu stronicowania to PGS_HORZ, określ PGB_TOPORLEFT dla lewego przycisku i PGB_BOTTOMORRIGHT dla przycisku po prawej stronie. Jeśli styl kontrolki modułu stronicowania to PGS_VERT, określ PGB_TOPORLEFT dla górnego przycisku i PGB_BOTTOMORRIGHT dla dolnego przycisku. Aby uzyskać więcej informacji, zobacz [Style kontrolek modułu stronicowania](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli określony przycisk jest w stanie gorąca; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , który jest opisany w Windows SDK. Następnie sprawdza, czy zwróconym stanem jest PGF_HOT. Aby uzyskać więcej informacji, zobacz sekcję zwracana wartość komunikatu [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

##  <a name="isbuttoninvisible"></a>CPagerCtrl:: IsButtonInvisible

Wskazuje, czy określony przycisk przewijania bieżącego formantu modułu stronicowania jest w stanie niewidocznym.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButton*|podczas Wskazuje przycisk, dla którego jest pobierany stan. Jeśli styl kontrolki modułu stronicowania to PGS_HORZ, określ PGB_TOPORLEFT dla lewego przycisku i PGB_BOTTOMORRIGHT dla przycisku po prawej stronie. Jeśli styl kontrolki modułu stronicowania to PGS_VERT, określ PGB_TOPORLEFT dla górnego przycisku i PGB_BOTTOMORRIGHT dla dolnego przycisku. Aby uzyskać więcej informacji, zobacz [Style kontrolek modułu stronicowania](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli określony przycisk jest w stanie niewidocznym; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

System Windows sprawia, że przycisk przewijania w określonym kierunku jest niewidoczny podczas przewijania zawartego okna do jego najpóźniejszego zakresu, ponieważ kliknięcie przycisku Dalej nie pozwala na wyświetlenie większej części zawartego okna.

Ta metoda wysyła komunikat [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , który jest opisany w Windows SDK. Następnie sprawdza, czy zwróconym stanem jest PGF_INVISIBLE. Aby uzyskać więcej informacji, zobacz sekcję zwracana wartość komunikatu [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

### <a name="example"></a>Przykład

W poniższym przykładzie zastosowano metodę [CPagerCtrl:: IsButtonInvisible](#isbuttoninvisible) , aby określić, czy widoczne są przyciski przewijania w lewo i w prawo.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

##  <a name="isbuttonnormal"></a>CPagerCtrl:: IsButtonNormal

Wskazuje, czy określony przycisk przewijania bieżącej kontrolki modułu stronicowania jest w normalnym stanie.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButton*|podczas Wskazuje przycisk, dla którego jest pobierany stan. Jeśli styl kontrolki modułu stronicowania to PGS_HORZ, określ PGB_TOPORLEFT dla lewego przycisku i PGB_BOTTOMORRIGHT dla przycisku po prawej stronie. Jeśli styl kontrolki modułu stronicowania to PGS_VERT, określ PGB_TOPORLEFT dla górnego przycisku i PGB_BOTTOMORRIGHT dla dolnego przycisku. Aby uzyskać więcej informacji, zobacz [Style kontrolek modułu stronicowania](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli określony przycisk jest w normalnym stanie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , który jest opisany w Windows SDK. Następnie sprawdza, czy zwróconym stanem jest PGF_NORMAL. Aby uzyskać więcej informacji, zobacz sekcję zwracana wartość komunikatu [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

##  <a name="recalcsize"></a>CPagerCtrl:: RecalcSize

Powoduje, że bieżący formant modułu stronicowania ponownie oblicza rozmiar zawartego okna.

```
void RecalcSize();
```

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_RECALCSIZE](/windows/win32/Controls/pgm-recalcsize) , który jest opisany w Windows SDK. W związku z tym formant modułu stronicowania wysyła powiadomienie [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) , aby uzyskać przewijalne wymiary zawartego okna.

### <a name="example"></a>Przykład

W poniższym przykładzie zastosowano metodę [CPagerCtrl:: RecalcSize](#recalcsize) , aby zażądać, aby bieżąca kontrolka modułu stronicowania ponownie przeliczyła swój rozmiar.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>Przykład

Poniższy przykład używa [odbicia komunikatu](../../mfc/tn062-message-reflection-for-windows-controls.md) , aby umożliwić kontrolce modułu stronicowania ponowne obliczenie własnego rozmiaru, a nie wymaganie okna dialogowego nadrzędnego formantu do wykonania obliczeń. Przykład dziedziczy `MyPagerCtrl` klasy z [klasy CPagerCtrl](../../mfc/reference/cpagerctrl-class.md), a następnie używa mapy komunikatów do skojarzenia powiadomienia [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) z `OnCalcsize` programem obsługi powiadomień. W tym przykładzie program obsługi powiadomień ustawia szerokość i wysokość kontrolki modułu stronicowania na stałe wartości.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

##  <a name="setbkcolor"></a>  CPagerCtrl::SetBkColor

Ustawia kolor tła bieżącej kontrolki modułu stronicowania.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*clrBk*|podczas Wartość [COLORREF](/windows/win32/gdi/colorref) , która zawiera nowy kolor tła kontrolki modułu stronicowania.|

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) , która zawiera poprzedni kolor tła kontrolki modułu stronicowania.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_SETBKCOLOR](/windows/win32/Controls/pgm-setbkcolor) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto metody [CPagerCtrl:: SetBkColor](#setbkcolor) , aby ustawić kolor tła kontrolki modułu stronicowania na czerwony, i metodę [CPagerCtrl:: GetBkColor](#getbkcolor) , aby potwierdzić, że została wprowadzona zmiana.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="setborder"></a>  CPagerCtrl::SetBorder

Ustawia rozmiar obramowania bieżącej kontrolki modułu stronicowania.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iBorder*|podczas Nowy rozmiar obramowania (w pikselach). Jeśli parametr *iBorder* ma wartość ujemną, rozmiar obramowania jest ustawiony na wartość zero.|

### <a name="return-value"></a>Wartość zwracana

Poprzedni rozmiar obramowania (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_SETBORDER](/windows/win32/Controls/pgm-setborder) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład tworzy formant modułu stronicowania, a następnie używa metody [CPagerCtrl:: SetChild](#setchild) do kojarzenia bardzo długiej kontrolki Button z kontrolką modułu stronicowania. W przykładzie zostanie użyta metoda [CPagerCtrl:: SetButtonSize](#setbuttonsize) w celu ustawienia wysokości kontrolki modułu stronicowania na 20 pikseli i metody [CPagerCtrl:: SetBorder](#setborder) w celu ustawienia grubości obramowania na 1 piksel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setbuttonsize"></a>  CPagerCtrl::SetButtonSize

Ustawia rozmiar przycisku bieżącej kontrolki modułu stronicowania.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iButtonSize*|podczas Nowy rozmiar przycisku (w pikselach).|

### <a name="return-value"></a>Wartość zwracana

Rozmiar poprzedniego przycisku (w pikselach).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_SETBUTTONSIZE](/windows/win32/Controls/pgm-setpos) , który jest opisany w Windows SDK.

Jeśli formant modułu stronicowania ma styl PGS_HORZ, rozmiar przycisku określa szerokość przycisków stronicowania, a jeśli formant modułu stronicowania ma styl PGS_VERT, rozmiar przycisku określa wysokość przycisków modułu stronicowania. Domyślny rozmiar przycisku to trzy czwarte szerokości paska przewijania, a minimalny rozmiar przycisku to 12 pikseli. Aby uzyskać więcej informacji, zobacz [Style kontrolek modułu stronicowania](/windows/win32/Controls/pager-control-styles).

### <a name="example"></a>Przykład

Poniższy przykład tworzy formant modułu stronicowania, a następnie używa metody [CPagerCtrl:: SetChild](#setchild) do kojarzenia bardzo długiej kontrolki Button z kontrolką modułu stronicowania. W przykładzie zostanie użyta metoda [CPagerCtrl:: SetButtonSize](#setbuttonsize) w celu ustawienia wysokości kontrolki modułu stronicowania na 20 pikseli i metody [CPagerCtrl:: SetBorder](#setborder) w celu ustawienia grubości obramowania na 1 piksel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setchild"></a>CPagerCtrl:: SetChild

Ustawia okno zawarte dla bieżącej kontrolki modułu stronicowania.

```
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*hwndChild*|podczas Dojście do okna, które ma być zawarte.|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_SETCHILD](/windows/win32/Controls/pgm-setchild) , który jest opisany w Windows SDK.

Ta metoda nie zmienia elementu nadrzędnego zawartego okna; przypisuje tylko uchwyt okna do kontrolki modułu stronicowania do przewijania. W większości przypadków zawarte okno będzie oknem podrzędnym formantu modułu stronicowania.

### <a name="example"></a>Przykład

Poniższy przykład tworzy formant modułu stronicowania, a następnie używa metody [CPagerCtrl:: SetChild](#setchild) do kojarzenia bardzo długiej kontrolki Button z kontrolką modułu stronicowania. W przykładzie zostanie użyta metoda [CPagerCtrl:: SetButtonSize](#setbuttonsize) w celu ustawienia wysokości kontrolki modułu stronicowania na 20 pikseli i metody [CPagerCtrl:: SetBorder](#setborder) w celu ustawienia grubości obramowania na 1 piksel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setscrollpos"></a>CPagerCtrl:: SetScrollPos

Ustawia położenie przewijania bieżącej kontrolki modułu stronicowania.

```
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iPos*|podczas Nowa pozycja przewijania (w pikselach).|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PGM_SETPOS](/windows/win32/Controls/pgm-setpos) , który jest opisany w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa CPagerCtrl](../../mfc/reference/cpagerctrl-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Kontrolki stronicowania](/windows/win32/Controls/pager-controls)
