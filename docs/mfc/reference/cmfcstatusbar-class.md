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
ms.openlocfilehash: 8f262d0139b6dffe54e16748ffda4938ba43fc08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366053"
---
# <a name="cmfcstatusbar-class"></a>Klasa CMFCStatusBar

Klasa `CMFCStatusBar` implementuje pasek stanu podobny `CStatusBar` do klasy. Jednak `CMFCStatusBar` klasa ma funkcje nie `CStatusBar` oferowane przez klasę, takie jak możliwość wyświetlania obrazów, animacji i pasków postępu; oraz możliwość reagowania na podwójne kliknięcia myszą.

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(Zastępuje [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||
|[CMFCStatusBar::Utwórz](#create)|Tworzy pasek sterowania i dołącza go do [CPane](../../mfc/reference/cpane-class.md) obiektu. (Zastępuje [CPane::Create](../../mfc/reference/cpane-class.md#create).)|
|[CMFCStatusBar::CreateEx](#createex)|Tworzy pasek sterowania i dołącza go do [CPane](../../mfc/reference/cpane-class.md) obiektu. (Zastępuje [CPane::CreateEx](../../mfc/reference/cpane-class.md#createex).)|
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Określa, czy można dynamicznie wstawiać inne okienko między tym okienkiem a ramką nadrzędną. (Zastępuje [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Włącza lub wyłącza obsługę podwójnych kliknięć myszy na pasku stanu.|
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|Wyświetla pasek postępu w określonym okienku.|
|[CMFCStatusBar::GetCount](#getcount)|Zwraca liczbę okienek na pasku stanu.|
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCStatusBar::GetItemID](#getitemid)||
|[CMFCStatusBar::GetItemRect](#getitemrect)||
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|Zwraca styl okienka. (Zastępuje [CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|
|[CMFCStatusBar::GetPaneText](#getpanetext)||
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|Zwraca szerokość określonego okienka paska stanu w pikselach.|
|[CMFCStatusBar::GetTipText](#gettiptext)|Zwraca tekst etykietki narzędzia dla określonego okienka paska stanu.|
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|Unieważnia określone okienko i ponownie rysuje jego zawartość.|
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|Wywoływane przez strukturę przed utworzeniem okna `CWnd` systemu Windows dołączone do tego obiektu. (Zastępuje [CWnd::PreCreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||
|[CMFCStatusBar::SetIndicators](#setindicators)||
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|Przypisuje animację do określonego okienka.|
|[CMFCStatusBar::SetPaneBackgroundcolor](#setpanebackgroundcolor)|Ustawia kolor tła dla określonego okienka paska stanu.|
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|Ustawia ikonę wskaźnika dla określonego okienka paska stanu.|
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|Ustawia bieżący postęp paska postępu dla określonego okienka paska stanu.|
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|Ustawia styl okienka. (Zastępuje [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|
|[CMFCStatusBar::SetPaneText](#setpanetext)||
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|Ustawia kolor tekstu dla określonego okienka paska stanu.|
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|Ustawia szerokość w pikselach określonego okienka paska stanu.|
|[CMFCStatusBar::SetTipText](#settiptext)|Ustawia tekst etykietki narzędzia dla określonego okienka paska stanu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|Wywoływana przez platformę, gdy ponownie rysuje okienko paska stanu.|

## <a name="remarks"></a>Uwagi

Na poniższym diagramie przedstawiono rysunek paska stanu z przykładowej aplikacji [demo paska stanu.](../../overview/visual-cpp-samples.md)

![Przykład CMFCStatusBar](../../mfc/reference/media/cmfcstatusbar.png "Przykład CMFCStatusBar")

## <a name="example"></a>Przykład

Poniższy przykład pokazuje zmienne lokalne, które aplikacja używa do `CMFCStatusBar` wywoływania różnych metod w klasie. Te zmienne są zadeklarowane w StatusBarDemoView.h. Ramka główna jest zadeklarowana w pliku MainFrm.h, dokument jest zadeklarowany w statusbardemoDoc.h, a widok jest zadeklarowany w StatusBarDemoView.h. Ten fragment kodu jest częścią [przykładu demo paska stanu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, `CMFCStatusBar` jak uzyskać odwołanie `GetStatusBar` do obiektu, wprowadzając metodę w MainFrm.h, a następnie wywołując tę metodę z `GetStatusBar` metody w StatusBarDemoView.h. Ten fragment kodu jest częścią [przykładu demo paska stanu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCStatusBar` wywołać różne metody w klasie w StatusBarDemoView.cpp. Stałe są zadeklarowane w MainFrm.h. W przykładzie pokazano, jak ustawić ikonę, ustawić tekst etykietki narzędzia okienka paska stanu, wyświetlić pasek postępu w określonym okienku, przypisać animację do określonego okienka, ustawić tekst i szerokość okienka paska stanu oraz ustawić bieżący wskaźnik postępu paska postępu dla okienka paska stanu. Ten fragment kodu jest częścią [przykładu demo paska stanu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[Cmfcstatusbar](../../mfc/reference/cmfcstatusbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxstatusbar.h

## <a name="cmfcstatusbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCStatusBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

[w] *bStieczka*<br/>
[w] *bHorz ( bHorz )*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CMFCStatusBar::CommandToIndex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

[w] *nIDZnajduj*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarcreate"></a><a name="create"></a>CMFCStatusBar::Utwórz

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

[w] *pParentWnd*<br/>
[w] *dwStyle (właśc.*<br/>
[w] *nID (nID)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarcreateex"></a><a name="createex"></a>CMFCStatusBar::CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

[w] *pParentWnd*<br/>
[w] *dwCtrlStyle*<br/>
[w] *dwStyle (właśc.*<br/>
[w] *nID (nID)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCStatusBar::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarenablepanedoubleclick"></a><a name="enablepanedoubleclick"></a>CMFCStatusBar::EnablePaneDoubleClick

Włącza lub wyłącza obsługę podwójnych kliknięć myszy na pasku stanu.

```
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] Jeśli true, włącz przetwarzanie myszy kliknij dwukrotnie. W przeciwnym razie wyłącz przetwarzanie myszy dwukrotnie kliknij.

### <a name="remarks"></a>Uwagi

Jeśli pasek stanu jest włączony do przetwarzania podwójnych kliknięć, system Windows wysyła powiadomienie WM_COMMAND wraz z identyfikatorem zasobu do właściciela paska stanu za każdym razem, gdy użytkownik dwukrotnie kliknie okienko paska stanu.

## <a name="cmfcstatusbarenablepaneprogressbar"></a><a name="enablepaneprogressbar"></a>CMFCStatusBar::EnablePaneProgressBar

Wyświetl pasek postępu w określonym okienku.

```
void EnablePaneProgressBar(
    int nIndex,
    long nTotal=100,
    BOOL bDisplayText=FALSE,
    COLORREF clrBar=-1,
    COLORREF clrBarDest=-1,
    COLORREF clrProgressText=-1);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
[w] Określa indeks okienka, którego pasek postępu ma być włączona.

*nPowłask*<br/>
[w] Określa maksymalną wartość paska postępu.

*bWydaj tekst*<br/>
[w] Określa, czy na pasku postępu ma być wyświetlana bieżąca wartość postępu.

*clrBar (clrBar)*<br/>
[w] Określa kolor tła paska postępu.

*clrBarDest (clrBarDest)*<br/>
[w] Określa kolor pomocniczy tła paska postępu. Użyj innej wartości niż *clrBar,* aby wypełnić kolorem wymieszanym z gradientem.

*clrProgressTeker*<br/>
[w] Określa kolor tekstu paska postępu.

### <a name="remarks"></a>Uwagi

Jeśli chcesz wyłączyć wywołanie `EnablePaneProgressBar` paska postępu z *nTotal* ustawiona na -1. Domyślnie *nTotal* jest ustawiony na 100. W związku z tym nie trzeba żadnych dodatkowych obliczeń, aby wyświetlić postęp jako procent.

Należy przekazać różne wartości dla *clrBar* i *clrBarDest* tak, aby kolor tła paska postępu wyświetla kolor zmieszany z gradientem. .

Aby ustawić bieżący postęp, należy wywołać [CMFCStatusBar::SetPaneProgress](#setpaneprogress) metody.

## <a name="cmfcstatusbargetcount"></a><a name="getcount"></a>CMFCStatusBar::GetCount

Pobiera liczbę okienek na pasku stanu.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba okienek na pasku stanu.

## <a name="cmfcstatusbargetdrawextendedarea"></a><a name="getdrawextendedarea"></a>CMFCStatusBar::GetDrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFCStatusBar::GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

[w] *rect*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetitemid"></a><a name="getitemid"></a>CMFCStatusBar::GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[w] *nIndeks*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetitemrect"></a><a name="getitemrect"></a>CMFCStatusBar::GetItemRect

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

[w] *nIndeks*<br/>
[w] *lpRect*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CMFCStatusBar::GetPaneInfo

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parametry

[w] *nIndeks*<br/>
[w] *nID (nID)*<br/>
[w] *styl nStyle*<br/>
[w] *cxWidth ( cxWidth )*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetpaneprogress"></a><a name="getpaneprogress"></a>CMFCStatusBar::GetPaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[w] *nIndeks*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetpanestyle"></a><a name="getpanestyle"></a>CMFCStatusBar::GetPaneStyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[w] *nIndeks*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetpanetext"></a><a name="getpanetext"></a>CMFCStatusBar::GetPaneText

```
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[w] *nIndeks*<br/>
[w] *s*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbargetpanewidth"></a><a name="getpanewidth"></a>CMFCStatusBar::GetPaneWidth

Pobiera szerokość okienka paska stanu.

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
[w] Określa indeks okienka paska stanu.

### <a name="return-value"></a>Wartość zwracana

Szerokość okienka paska stanu, który *określa nIndex;* w przeciwnym razie zero, jeśli okienko paska stanu nie istnieje.

## <a name="cmfcstatusbargettiptext"></a><a name="gettiptext"></a>CMFCStatusBar::GetTipText

Pobierz tekst etykietki narzędzia okienka paska stanu.

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
[w] Określa indeks okienka, dla którego ma być pobierany tekst etykietki narzędzia.

### <a name="return-value"></a>Wartość zwracana

Tekst etykietki narzędzia okienka paska stanu, który określa *nIndex.* W przeciwnym razie pusty ciąg, jeśli okienko paska stanu nie istnieje dla określonego *nIndex* lub jeśli jego tekst etykietki narzędzia jest pusty.

## <a name="cmfcstatusbarinvalidatepanecontent"></a><a name="invalidatepanecontent"></a>CMFCStatusBar::InvalidatePaneContent

Unieważnij okienko paska stanu i przerysuj jego zawartość.

```
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
[w] Określa indeks okienka, którego zawartość ma zostać unieważniona i ponownie narysowana.

### <a name="remarks"></a>Uwagi

Gdy pasek stanu jest unieważniony, jest oznaczony do ponownego rysowania. System Windows ponownie rysuje go, `UpdateWindow` gdy metoda `OnPaint` wysyła komunikat WM_PAINT do metody.

## <a name="cmfcstatusbarondrawpane"></a><a name="ondrawpane"></a>CMFCStatusBar::OnDrawPane

Ponownie wyryj okienko paska stanu.

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia do rysowania.

*pPane (właso)*<br/>
[w] Wskaźnik do `CMFCStatusBarPaneInfo` struktury, który zawiera informacje o okienku do ponownego narysowania.

### <a name="remarks"></a>Uwagi

Domyślnie `OnDrawPane` ponownie rysuje okienko przy użyciu kontekstu urządzenia *pDC* zgodnie ze stylem i zawartością okienka.

Zastąpi tę `CMFCStatusBar`metodę w klasie pochodnej, aby dostosować wygląd okienka.

## <a name="cmfcstatusbarprecreatewindow"></a><a name="precreatewindow"></a>CMFCStatusBar::PreCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parametry

[w] *z o.o.*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarsetdrawextendedarea"></a><a name="setdrawextendedarea"></a>CMFCStatusBar::SetDrawExtendedArea

```
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

[w] *bStaw*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarsetindicators"></a><a name="setindicators"></a>CMFCStatusBar::SetIndicators

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

[w] *lpIDArray (lpIDArray)*<br/>
[w] *nIDCount (liczba NIDCount)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarsetpaneanimation"></a><a name="setpaneanimation"></a>CMFCStatusBar::SetPaneAnimation

Przypisuje animację do określonego okienka.

```
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
[w] Określa indeks okienka, do którego ma zostać przypisana animacja.

*lista hImage*<br/>
[w] Określa dojście do listy obrazów, na których znajdują się klatki animacji.

*nFrameRate (nFrameRate)*<br/>
[w] Określa liczbę klatek na sekundę animacji w milisekundach.

*bUpęb.*<br/>
[w] Jeśli true, należy natychmiast zaktualizować zawartość okienka. W przeciwnym razie zawartość okienka jest aktualizowana po jej unieważnieniu.

### <a name="remarks"></a>Uwagi

Jeśli chcesz wyłączyć bieżącą animację, wywołanie `SetPaneAnimation` z `hImageList` ustawioną wartością NULL.

## <a name="cmfcstatusbarsetpanebackgroundcolor"></a><a name="setpanebackgroundcolor"></a>CMFCStatusBar::SetPaneBackgroundcolor

Ustawia kolor tła okienka paska stanu.

```
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
[w] Określa indeks okienka, dla którego ma być ustawiony nowy kolor tła.

*clrBackground (ziemia powrotna)*<br/>
[w] Określa nowy kolor tła.

*bUpęb.*<br/>
[w] Jeśli true, należy natychmiast zaktualizować zawartość okienka. W przeciwnym razie nie należy aktualizować zawartości okienka, dopóki okienko nie zostanie unieważnione inną metodą.

## <a name="cmfcstatusbarsetpaneicon"></a><a name="setpaneicon"></a>CMFCStatusBar::SetPaneIcon

Ustaw ikonę okienka paska stanu.

```
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

*Nindex*<br/>
[w] Określa indeks okienka, dla którego ma być ustawiony obraz.

*hIcon (własówce)*<br/>
[w] Określa uchwyt do ikony, która ma być ustawiona jako obraz okienka.

*bUpęb.*<br/>
[w] Określa, czy zawartość okienka ma być natychmiast aktualizowana.

*hBmp (wł.)*<br/>
[w] Określa dojście do mapy bitowej, która ma być ustawiona jako obraz okienka.

*clrPrzezroczysty*<br/>
[w] Określa przezroczysty kolor mapy bitowej, który wskazuje *hBmp.*

### <a name="remarks"></a>Uwagi

Aby ustawić obraz okienka, można przekazać hicon lub HBITMAP wraz z przezroczystym kolorem. Jeśli nie chcesz już wyświetlać obrazu, przekaż wartość NULL jako uchwyt obrazu.

Jeśli istnieje jakakolwiek uruchomiona animacja ustawiona [przez CMFCStatusBar::SetPaneAnimation,](#setpaneanimation) animacja zostanie zatrzymana.

## <a name="cmfcstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>CMFCStatusBar::SetPaneInfo

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

[w] *nIndeks*<br/>
[w] *nID (nID)*<br/>
[w] *styl nStyle*<br/>
[w] *cxWidth ( cxWidth )*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarsetpaneprogress"></a><a name="setpaneprogress"></a>CMFCStatusBar::SetPaneProgress

Ustaw bieżący wskaźnik postępu paska postępu dla określonego okienka.

```
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
[w] Określa indeks okienka, dla którego ma być aktualizowany wskaźnik postępu.

*nCurr (niem.*<br/>
[w] Określa bieżącą wartość wskaźnika postępu.

*bUpęb.*<br/>
[w] Określa, czy okienko ma zostać natychmiast zaktualizowane.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, jeśli chcesz zaktualizować wskaźnik postępu dla paska postępu w określonym okienku.

Aby użyć tej funkcji dla danego okienka, należy najpierw wywołać [CMFCStatusBar::EnablePaneProgressBar.](#enablepaneprogressbar)

## <a name="cmfcstatusbarsetpanestyle"></a><a name="setpanestyle"></a>CMFCStatusBar::SetPaneStyle

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

[w] *nIndeks*<br/>
[w] *styl nStyle*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarsetpanetext"></a><a name="setpanetext"></a>CMFCStatusBar::SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parametry

[w] *nIndeks*<br/>
[w] *lpszNewText (Tekst lpszNewText)*<br/>
[w] *bUpęb.*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcstatusbarsetpanetextcolor"></a><a name="setpanetextcolor"></a>CMFCStatusBar::SetPaneTextColor

Ustawia kolor tekstu określonego okienka.

```
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
[w] Określa indeks okienka, do którego chcesz przypisać nowy kolor tekstu.

*clrTekst*<br/>
[w] Określa kolor tekstu.

*bUpęb.*<br/>
[w] Jeśli true, należy natychmiast zaktualizować zawartość okienka. W przeciwnym razie nie należy aktualizować zawartości okienka, dopóki okienko nie zostanie unieważnione inną metodą.

## <a name="cmfcstatusbarsetpanewidth"></a><a name="setpanewidth"></a>CMFCStatusBar::SetPaneWidth

Ustaw szerokość okienka paska stanu.

```
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
[w] Indeks okienka paska stanu, dla którego można ustawić nową szerokość.

*Cx*<br/>
[w] Nowa szerokość okienka paska stanu w pikselach.

## <a name="cmfcstatusbarsettiptext"></a><a name="settiptext"></a>CMFCStatusBar::SetTipText

Ustawianie tekstu etykietki narzędzia okienka paska stanu.

```
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
[w] Indeks okienka, do którego chcesz przypisać tekst etykietki narzędzia.

*pszTipText (tekst pszTip)*<br/>
[w] Nowy tekst etykietki narzędzia.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CPane](../../mfc/reference/cpane-class.md)<br/>
[Klasa CStatusBar](../../mfc/reference/cstatusbar-class.md)
