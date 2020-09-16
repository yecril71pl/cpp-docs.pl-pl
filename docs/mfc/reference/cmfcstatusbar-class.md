---
title: Klasa CMFCStatusBar
ms.date: 11/19/2018
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
helpviewer_keywords:
- CMFCStatusBar [MFC], CalcFixedLayout
- CMFCStatusBar [MFC], CommandToIndex
- CMFCStatusBar [MFC], Create
- CMFCStatusBar [MFC], CreateEx
- CMFCStatusBar [MFC], DoesAllowDynInsertBefore
- CMFCStatusBar [MFC], EnablePaneDoubleClick
- CMFCStatusBar [MFC], EnablePaneProgressBar
- CMFCStatusBar [MFC], GetCount
- CMFCStatusBar [MFC], GetDrawExtendedArea
- CMFCStatusBar [MFC], GetExtendedArea
- CMFCStatusBar [MFC], GetItemID
- CMFCStatusBar [MFC], GetItemRect
- CMFCStatusBar [MFC], GetPaneInfo
- CMFCStatusBar [MFC], GetPaneProgress
- CMFCStatusBar [MFC], GetPaneStyle
- CMFCStatusBar [MFC], GetPaneText
- CMFCStatusBar [MFC], GetPaneWidth
- CMFCStatusBar [MFC], GetTipText
- CMFCStatusBar [MFC], InvalidatePaneContent
- CMFCStatusBar [MFC], PreCreateWindow
- CMFCStatusBar [MFC], SetDrawExtendedArea
- CMFCStatusBar [MFC], SetIndicators
- CMFCStatusBar [MFC], SetPaneAnimation
- CMFCStatusBar [MFC], SetPaneBackgroundColor
- CMFCStatusBar [MFC], SetPaneIcon
- CMFCStatusBar [MFC], SetPaneInfo
- CMFCStatusBar [MFC], SetPaneProgress
- CMFCStatusBar [MFC], SetPaneStyle
- CMFCStatusBar [MFC], SetPaneText
- CMFCStatusBar [MFC], SetPaneTextColor
- CMFCStatusBar [MFC], SetPaneWidth
- CMFCStatusBar [MFC], SetTipText
- CMFCStatusBar [MFC], OnDrawPane
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
ms.openlocfilehash: 004873ef2696eb9504cdd4df77e700c4a145e886
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686577"
---
# <a name="cmfcstatusbar-class"></a>Klasa CMFCStatusBar

`CMFCStatusBar`Klasa implementuje pasek stanu podobny do `CStatusBar` klasy. Jednak `CMFCStatusBar` Klasa ma funkcje, które nie są oferowane przez `CStatusBar` klasę, takie jak możliwość wyświetlania obrazów, animacji i pasków postępu, a także możliwość reagowania na dwukrotne kliknięcie myszą.

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC \\ atlmfc \\ src \\ MFC** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(Przesłania [CBasePane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||
|[CMFCStatusBar:: Create](#create)|Tworzy pasek sterowania i dołącza go do obiektu [CPane](../../mfc/reference/cpane-class.md) . (Przesłania [CPane:: Create](../../mfc/reference/cpane-class.md#create).)|
|[CMFCStatusBar::CreateEx](#createex)|Tworzy pasek sterowania i dołącza go do obiektu [CPane](../../mfc/reference/cpane-class.md) . (Przesłania [CPane:: CreateEx](../../mfc/reference/cpane-class.md#createex).)|
|[CMFCStatusBar::D oesAllowDynInsertBefore](#doesallowdyninsertbefore)|Określa, czy można dynamicznie wstawiać inne okienka między tym okienkiem i ramką nadrzędną. (Przesłania [CBasePane::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Włącza lub wyłącza obsługę dwukrotnego kliknięcia przycisku myszy na pasku stanu.|
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|Wyświetla pasek postępu w określonym okienku.|
|[CMFCStatusBar:: GetCount](#getcount)|Zwraca liczbę okienek na pasku stanu.|
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCStatusBar:: GetItemID](#getitemid)||
|[CMFCStatusBar::GetItemRect](#getitemrect)||
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||
|[CMFCStatusBar:: getokienks](#getpanestyle)|Zwraca styl okienka. (Przesłania [CBasePane:: Getokienks](../../mfc/reference/cbasepane-class.md#getpanestyle)).|
|[CMFCStatusBar::GetPaneText](#getpanetext)||
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|Zwraca szerokość (w pikselach) określonego okienka na pasku stanu.|
|[CMFCStatusBar::GetTipText](#gettiptext)|Zwraca tekst etykietki narzędzia dla określonego okienka paska stanu.|
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|Unieważnia określone okienko i ponownie rysuje jego zawartość.|
|[CMFCStatusBar::P reCreateWindow](#precreatewindow)|Wywoływane przez platformę przed utworzeniem okna systemu Windows dołączonego do tego `CWnd` obiektu. (Przesłania [CWnd::P recreatewindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||
|[CMFCStatusBar:: setwskaźniks](#setindicators)||
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|Przypisuje animację do określonego okienka.|
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|Ustawia kolor tła dla określonego okienka na pasku stanu.|
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|Ustawia ikonę wskaźnika dla określonego okienka na pasku stanu.|
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|Ustawia bieżący postęp paska postępu dla określonego okienka paska stanu.|
|[CMFCStatusBar:: setokienks](#setpanestyle)|Ustawia styl okienka. (Przesłania [CBasePane:: Setokienks](../../mfc/reference/cbasepane-class.md#setpanestyle)).|
|[CMFCStatusBar::SetPaneText](#setpanetext)||
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|Ustawia kolor tekstu dla określonego okienka na pasku stanu.|
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|Ustawia szerokość w pikselach określonego okienka na pasku stanu.|
|[CMFCStatusBar::SetTipText](#settiptext)|Ustawia tekst etykietki narzędzia dla określonego okienka na pasku stanu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|Wywoływane przez platformę, gdy odrysuje okienko paska stanu.|

## <a name="remarks"></a>Uwagi

Na poniższym diagramie przedstawiono rysunek paska stanu z [przykładowej aplikacji demonstracyjnej na pasku stanu](../../overview/visual-cpp-samples.md) .

![Przykład CMFCStatusBar](../../mfc/reference/media/cmfcstatusbar.png "Przykład CMFCStatusBar")

## <a name="examples"></a>Przykłady

W poniższym przykładzie pokazano zmienne lokalne używane przez aplikację do wywołania różnych metod w `CMFCStatusBar` klasie. Te zmienne są zadeklarowane w StatusBarDemoView. h. Główna ramka jest zadeklarowana w MainFrm. h, dokument jest zadeklarowany w StatusBarDemoDoc. h, a widok jest zadeklarowany w StatusBarDemoView. h. Ten fragment kodu jest częścią [przykładu demonstracyjnego paska stanu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

W poniższym przykładzie pokazano, jak uzyskać odwołanie do `CMFCStatusBar` obiektu, wprowadzając `GetStatusBar` metodę w MainFrm. h, a następnie wywołując tę metodę z `GetStatusBar` metody w StatusBarDemoView. h. Ten fragment kodu jest częścią [przykładu demonstracyjnego paska stanu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

Poniższy przykład ilustruje sposób wywołania różnych metod w `CMFCStatusBar` klasie w StatusBarDemoView. cpp. Stałe są zadeklarowane w MainFrm. h. W przykładzie pokazano, jak ustawić ikonę, ustawić tekst etykietki narzędzia okienka pasek stanu, wyświetlić pasek postępu w określonym okienku, przypisać animację do określonego okienka, ustawić tekst i szerokość okienka pasek stanu i ustawić bieżący wskaźnik postępu na pasku postępu w okienku Pasek stanu. Ten fragment kodu jest częścią [przykładu demonstracyjnego paska stanu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxstatusbar. h

## <a name="cmfcstatusbarcalcfixedlayout"></a><a name="calcfixedlayout"></a> CMFCStatusBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

podczas *bStretch*<br/>
podczas *bHorz*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarcommandtoindex"></a><a name="commandtoindex"></a> CMFCStatusBar::CommandToIndex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

podczas *nIDFind*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarcreate"></a><a name="create"></a> CMFCStatusBar:: Create

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

podczas *pParentWnd*<br/>
podczas *dwStyle*<br/>
podczas *NID*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarcreateex"></a><a name="createex"></a> CMFCStatusBar::CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

podczas *pParentWnd*<br/>
podczas *dwCtrlStyle*<br/>
podczas *dwStyle*<br/>
podczas *NID*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a> CMFCStatusBar::D oesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarenablepanedoubleclick"></a><a name="enablepanedoubleclick"></a> CMFCStatusBar::EnablePaneDoubleClick

Włącza lub wyłącza obsługę dwukrotnego kliknięcia przycisku myszy na pasku stanu.

```cpp
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
podczas W przypadku wartości TRUE należy włączyć przetwarzanie myszą dwukrotnie. W przeciwnym razie Wyłącz przetwarzanie myszą.

### <a name="remarks"></a>Uwagi

Jeśli na pasku stanu włączono opcję Przetwórz podwójne kliknięcia, system Windows wyśle powiadomienie WM_COMMAND wraz z IDENTYFIKATORem zasobu do właściciela paska stanu za każdym razem, gdy użytkownik kliknie dwukrotnie okienko pasek stanu.

## <a name="cmfcstatusbarenablepaneprogressbar"></a><a name="enablepaneprogressbar"></a> CMFCStatusBar::EnablePaneProgressBar

Wyświetla pasek postępu w określonym okienku.

```cpp
void EnablePaneProgressBar(
    int nIndex,
    long nTotal=100,
    BOOL bDisplayText=FALSE,
    COLORREF clrBar=-1,
    COLORREF clrBarDest=-1,
    COLORREF clrProgressText=-1);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
podczas Określa indeks okienka, którego pasek postępu ma zostać włączony.

*nTotal*<br/>
podczas Określa maksymalną wartość paska postępu.

*bDisplayText*<br/>
podczas Określa, czy na pasku postępu ma być wyświetlana bieżąca wartość postępu.

*clrBar*<br/>
podczas Określa kolor tła paska postępu.

*clrBarDest*<br/>
podczas Określa kolor pomocniczy tła paska postępu. Użyj innej wartości niż *clrBar* , aby wypełnić kolorem zmieszanym do gradientu.

*clrProgressText*<br/>
podczas Określa kolor tekstu paska postępu.

### <a name="remarks"></a>Uwagi

Jeśli chcesz wyłączyć wywołanie paska postępu `EnablePaneProgressBar` z opcją *nTotal* ustawioną na wartość-1. Domyślnie *nTotal* jest ustawiony na 100. W związku z tym nie trzeba wykonywać żadnych dodatkowych obliczeń, aby wyświetlić postęp w postaci wartości procentowej.

Należy przekazać różne wartości parametrów *clrBar* i *clrBarDest* , aby kolor tła paska postępu wyświetlał kolor mieszany do gradientu. .

Aby ustawić bieżący postęp, wywołaj metodę [CMFCStatusBar:: SetPaneProgress](#setpaneprogress) .

## <a name="cmfcstatusbargetcount"></a><a name="getcount"></a> CMFCStatusBar:: GetCount

Pobiera liczbę okienek na pasku stanu.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba okienek na pasku stanu.

## <a name="cmfcstatusbargetdrawextendedarea"></a><a name="getdrawextendedarea"></a> CMFCStatusBar::GetDrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetextendedarea"></a><a name="getextendedarea"></a> CMFCStatusBar::GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

podczas *prostokąt*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetitemid"></a><a name="getitemid"></a> CMFCStatusBar:: GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

podczas *nIndex*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetitemrect"></a><a name="getitemrect"></a> CMFCStatusBar::GetItemRect

```cpp
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

podczas *nIndex*<br/>
podczas *lpRect*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetpaneinfo"></a><a name="getpaneinfo"></a> CMFCStatusBar::GetPaneInfo

```cpp
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parametry

podczas *nIndex*<br/>
podczas *NID*<br/>
podczas *nStyle*<br/>
podczas *cxWidth*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetpaneprogress"></a><a name="getpaneprogress"></a> CMFCStatusBar::GetPaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>Parametry

podczas *nIndex*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetpanestyle"></a><a name="getpanestyle"></a> CMFCStatusBar:: getokienks

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

podczas *nIndex*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetpanetext"></a><a name="getpanetext"></a> CMFCStatusBar::GetPaneText

```cpp
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>Parametry

podczas *nIndex*<br/>
podczas *s*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetpanewidth"></a><a name="getpanewidth"></a> CMFCStatusBar::GetPaneWidth

Pobiera szerokość okienka paska stanu.

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
podczas Określa indeks okienka paska stanu.

### <a name="return-value"></a>Wartość zwracana

Szerokość okienka paska stanu, które *nIndex* określa; w przeciwnym razie, zero, jeśli okienko pasek stanu nie istnieje.

## <a name="cmfcstatusbargettiptext"></a><a name="gettiptext"></a> CMFCStatusBar::GetTipText

Pobierz tekst etykietki narzędzia okienka stanu.

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
podczas Określa indeks okienka, dla którego ma zostać pobrany tekst etykietki narzędzia.

### <a name="return-value"></a>Wartość zwracana

Tekst etykietki narzędzia dla okienka stanu, które *nIndex* określa. W przeciwnym razie pusty ciąg, jeśli nie istnieje okienko pasek stanu dla określonego *nIndexu* lub jeśli jego tekst etykietki narzędzia jest pusty.

## <a name="cmfcstatusbarinvalidatepanecontent"></a><a name="invalidatepanecontent"></a> CMFCStatusBar::InvalidatePaneContent

Unieważnienie okienka paska stanu i ponowne narysowanie jego zawartości.

```cpp
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
podczas Określa indeks okienka, którego zawartość ma zostać unieważniona i ponownie narysowana.

### <a name="remarks"></a>Uwagi

Gdy pasek stanu jest unieważniony, jest on oznaczony do przerysowania. System Windows ponownie narysuje, gdy `UpdateWindow` Metoda wyśle do metody komunikat WM_PAINT `OnPaint` .

## <a name="cmfcstatusbarondrawpane"></a><a name="ondrawpane"></a> CMFCStatusBar::OnDrawPane

Ponownie narysuj okienko paska stanu.

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia do rysowania.

*pPane*<br/>
podczas Wskaźnik do `CMFCStatusBarPaneInfo` struktury zawierającej informacje o okienku do odrysowania.

### <a name="remarks"></a>Uwagi

Domyślnie program ponownie `OnDrawPane` rysuje okienko przy użyciu *kontrolera PDC* kontekstu urządzenia zgodnie z stylem i zawartością okienka.

Zastąp tę metodę w `CMFCStatusBar` klasie pochodnej, aby dostosować wygląd okienka.

## <a name="cmfcstatusbarprecreatewindow"></a><a name="precreatewindow"></a> CMFCStatusBar::P reCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parametry

podczas *CS*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarsetdrawextendedarea"></a><a name="setdrawextendedarea"></a> CMFCStatusBar::SetDrawExtendedArea

```cpp
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

podczas *bSet*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarsetindicators"></a><a name="setindicators"></a> CMFCStatusBar:: setwskaźniks

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

podczas *lpIDArray*<br/>
podczas *nIDCount*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarsetpaneanimation"></a><a name="setpaneanimation"></a> CMFCStatusBar::SetPaneAnimation

Przypisuje animację do określonego okienka.

```cpp
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
podczas Określa indeks okienka, do którego chcesz przypisać animację.

*hImageList*<br/>
podczas Określa dojście do listy obrazów, która zawiera ramki animacji.

*nFrameRate*<br/>
podczas Określa wyrażoną w milisekundach szybkość klatek dla animacji.

*bAktualizacja*<br/>
podczas W przypadku wartości TRUE należy natychmiast zaktualizować zawartość okienka. W przeciwnym razie zawartość okienka jest aktualizowana, gdy zostanie unieważniona.

### <a name="remarks"></a>Uwagi

Jeśli chcesz wyłączyć bieżącą animację, wywołaj polecenie `SetPaneAnimation` z `hImageList` USTAWIONĄ wartością null.

## <a name="cmfcstatusbarsetpanebackgroundcolor"></a><a name="setpanebackgroundcolor"></a> CMFCStatusBar::SetPaneBackgroundColor

Ustawia kolor tła okienka paska stanu.

```cpp
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
podczas Określa indeks okienka, dla którego ma zostać ustawiony nowy kolor tła.

*clrBackground*<br/>
podczas Określa nowy kolor tła.

*bAktualizacja*<br/>
podczas W przypadku wartości TRUE należy natychmiast zaktualizować zawartość okienka. W przeciwnym razie nie należy aktualizować zawartości okienka, dopóki okienko nie zostanie unieważnione przez inną metodę.

## <a name="cmfcstatusbarsetpaneicon"></a><a name="setpaneicon"></a> CMFCStatusBar::SetPaneIcon

Ustaw ikonę okienka pasek stanu.

```cpp
void SetPaneIcon(
    int nIndex,
    HICON hIcon,
    BOOL bUpdate=TRUE);

void SetPaneIcon(
    int nIndex,
    HBITMAP hBmp,
    COLORREF clrTransparent=RGB(255, 0, 255),
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
podczas Określa indeks okienka, dla którego ma zostać ustawiony obraz.

*hIcon*<br/>
podczas Określa uchwyt do ikony, która ma być ustawiona jako obraz okienka.

*bAktualizacja*<br/>
podczas Określa, czy zawartość okienka ma być aktualizowana natychmiast.

*hBmp*<br/>
podczas Określa uchwyt mapy bitowej, który ma być ustawiony jako obraz okienka.

*clrTransparent*<br/>
podczas Określa przezroczysty kolor mapy bitowej, która wskazuje *hBmp* .

### <a name="remarks"></a>Uwagi

Aby ustawić obraz okienka, można przekazać HICON lub HBITMAP razem z przezroczystym kolorem. Jeśli nie chcesz wyświetlać obrazu dłużej, przekaż wartość NULL jako uchwyt obrazu.

W przypadku uruchomionej animacji z ustawioną [CMFCStatusBar:: SetPaneAnimation](#setpaneanimation) , animacja zostanie zatrzymana.

## <a name="cmfcstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a> CMFCStatusBar::SetPaneInfo

```cpp
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

podczas *nIndex*<br/>
podczas *NID*<br/>
podczas *nStyle*<br/>
podczas *cxWidth*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarsetpaneprogress"></a><a name="setpaneprogress"></a> CMFCStatusBar::SetPaneProgress

Ustaw wskaźnik bieżącego postępu paska postępu dla określonego okienka.

```cpp
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
podczas Określa indeks okienka, dla którego ma zostać zaktualizowany wskaźnik postępu.

*nCurr*<br/>
podczas Określa bieżącą wartość wskaźnika postępu.

*bAktualizacja*<br/>
podczas Określa, czy okienko ma być aktualizowane od razu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, gdy chcesz zaktualizować wskaźnik postępu dla paska postępu w określonym okienku.

Aby użyć tej funkcji dla danego okienka, należy najpierw wywołać [CMFCStatusBar:: EnablePaneProgressBar](#enablepaneprogressbar) .

## <a name="cmfcstatusbarsetpanestyle"></a><a name="setpanestyle"></a> CMFCStatusBar:: setokienks

```cpp
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

podczas *nIndex*<br/>
podczas *nStyle*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarsetpanetext"></a><a name="setpanetext"></a> CMFCStatusBar::SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parametry

podczas *nIndex*<br/>
podczas *lpszNewText*<br/>
podczas *bAktualizacja*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarsetpanetextcolor"></a><a name="setpanetextcolor"></a> CMFCStatusBar::SetPaneTextColor

Ustawia kolor tekstu w określonym okienku.

```cpp
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
podczas Określa indeks okienka, do którego ma zostać przypisany nowy kolor tekstu.

*clrText*<br/>
podczas Określa kolor tekstu.

*bAktualizacja*<br/>
podczas W przypadku wartości TRUE należy natychmiast zaktualizować zawartość okienka. W przeciwnym razie nie należy aktualizować zawartości okienka, dopóki okienko nie zostanie unieważnione przez inną metodę.

## <a name="cmfcstatusbarsetpanewidth"></a><a name="setpanewidth"></a> CMFCStatusBar::SetPaneWidth

Ustaw szerokość okienka paska stanu.

```cpp
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
podczas Indeks okienka paska stanu, dla którego ma zostać ustawiona nowa szerokość.

*CX*<br/>
podczas Nowa szerokość okienka paska stanu w pikselach.

## <a name="cmfcstatusbarsettiptext"></a><a name="settiptext"></a> CMFCStatusBar::SetTipText

Ustaw tekst etykietki narzędzia w okienku paska stanu.

```cpp
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
podczas Indeks okienka, do którego ma zostać przypisany tekst etykietki narzędzia.

*pszTipText*<br/>
podczas Tekst nowej etykietki narzędzia.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CPane](../../mfc/reference/cpane-class.md)<br/>
[Klasa CStatusBar](../../mfc/reference/cstatusbar-class.md)
