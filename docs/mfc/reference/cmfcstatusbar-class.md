---
title: CMFCStatusBar Class
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
ms.openlocfilehash: 87f75769e2f400a7721a8c9089d6c5596c31a4e3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775962"
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar Class

`CMFCStatusBar` Klasa implementuje pasek stanu podobny do `CStatusBar` klasy. Jednak `CMFCStatusBar` klasa ma funkcje, które nie są oferowane przez `CStatusBar` klasę, takie jak możliwość wyświetlania obrazów, animacji i pasków postępu, a także zdolność do reagowania na dwukrotne kliknięcie myszy.

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(Przesłania [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||
|[CMFCStatusBar::Create](#create)|Tworzy pasek sterowania i dołącza je do [CPane](../../mfc/reference/cpane-class.md) obiektu. (Przesłania [CPane::Create](../../mfc/reference/cpane-class.md#create).)|
|[CMFCStatusBar::CreateEx](#createex)|Tworzy pasek sterowania i dołącza je do [CPane](../../mfc/reference/cpane-class.md) obiektu. (Przesłania [CPane::CreateEx](../../mfc/reference/cpane-class.md#createex).)|
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Określa, czy innego okienka mogą być dynamicznie między to okienko i dodaje nadrzędnej ramki. (Przesłania [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Włącza lub wyłącza obsługę myszy kliknie dwukrotnie na pasku stanu.|
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|W okienku określony, Wyświetla pasek postępu.|
|[CMFCStatusBar::GetCount](#getcount)|Zwraca liczbę okienek, na pasku stanu.|
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCStatusBar::GetItemID](#getitemid)||
|[CMFCStatusBar::GetItemRect](#getitemrect)||
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|Zwraca wartość stylu okienka. (Przesłania [CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|
|[CMFCStatusBar::GetPaneText](#getpanetext)||
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|Zwraca szerokość w pikselach, określony okienka paska stanu.|
|[CMFCStatusBar::GetTipText](#gettiptext)|Zwraca tekst wskazówki dla określonego okienka paska stanu.|
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|Unieważnia określony okienka i ponownie rysuje zawartość.|
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|Metoda wywoływana przez platformę przed tworzeniem okna Windows dołączona do tego `CWnd` obiektu. (Przesłania [CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||
|[CMFCStatusBar::SetIndicators](#setindicators)||
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|Przypisuje animacji do określonego okienka.|
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|Ustawia kolor tła dla określonego okienka paska stanu.|
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|Ustawia ikona wskaźnika dla określonego okienka paska stanu.|
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|Ustawia bieżący postęp pasek postępu dla określonego okienka paska stanu.|
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|Ustawia styl okienka. (Przesłania [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|
|[CMFCStatusBar::SetPaneText](#setpanetext)||
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|Określa kolor tekstu dla określonego okienka paska stanu.|
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|Określa szerokość w pikselach określonego okienka paska stanu.|
|[CMFCStatusBar::SetTipText](#settiptext)|Ustawia tekst wskazówki dla określonego okienka paska stanu.|

### <a name="protected-methods"></a>Metody chronione

|Name|Opis|
|----------|-----------------|
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|Wywoływane przez platformę, gdy jej odrysowuje okienka paska stanu.|

## <a name="remarks"></a>Uwagi

Na poniższym diagramie przedstawiono na rysunku na pasku stanu z [próbka Demo pasek stanu](../../overview/visual-cpp-samples.md) aplikacji.

![Przykład CMFCStatusBar](../../mfc/reference/media/cmfcstatusbar.png "przykład CMFCStatusBar")

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano zmienne lokalne, których korzysta aplikacja, wywołania różne metody `CMFCStatusBar` klasy. Te zmienne są deklarowane w StatusBarDemoView.h. Głównej ramki jest zadeklarowana w MainFrm.h, dokument jest zadeklarowana w StatusBarDemoDoc.h i widok jest zadeklarowana w StatusBarDemoView.h. Ten fragment kodu jest częścią [próbka Demo pasek stanu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak odwołać się do `CMFCStatusBar` obiektu, wprowadzając `GetStatusBar` metoda w MainFrm.h i następnie wywołanie tej metody z `GetStatusBar` metody w StatusBarDemoView.h. Ten fragment kodu jest częścią [próbka Demo pasek stanu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

## <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób wywołania różnych metod `CMFCStatusBar` klasy w StatusBarDemoView.cpp. Stałe są deklarowane w MainFrm.h. W przykładzie pokazano sposób ustawiania ikony, Ustaw tekst etykietki narzędzia w okienku paska stanu, wyświetlany pasek postępu w okienku określonego, przypisać animacji do okienka określonego, ustawić tekst i szerokość w okienku paska stanu i ustaw wskaźnik postępu bieżącego progr pasek dostępu dla tego okienka paska stanu. Ten fragment kodu jest częścią [próbka Demo pasek stanu](../../overview/visual-cpp-samples.md).

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

**Nagłówek:** afxstatusbar.h

##  <a name="calcfixedlayout"></a>  CMFCStatusBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

[in] *bStretch*<br/>
[in] *bHorz*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="commandtoindex"></a>  CMFCStatusBar::CommandToIndex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

[in] *nIDFind*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="create"></a>  CMFCStatusBar::Create

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

[in] *pParentWnd*<br/>
[in] *dwStyle*<br/>
[in] *nID*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="createex"></a>  CMFCStatusBar::CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

[in] *pParentWnd*<br/>
[in] *dwCtrlStyle*<br/>
[in] *dwStyle*<br/>
[in] *nID*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="doesallowdyninsertbefore"></a>  CMFCStatusBar::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="enablepanedoubleclick"></a>  CMFCStatusBar::EnablePaneDoubleClick

Włącza lub wyłącza obsługę myszy kliknie dwukrotnie na pasku stanu.

```
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] W przypadku opcji TRUE Włącz przetwarzanie dwukrotnego kliknięcia myszą. W przeciwnym razie wyłączyć przetwarzanie dwukrotnego kliknięcia myszą.

### <a name="remarks"></a>Uwagi

Włączenie paska stanu do przetworzenia podwójnego kliknięcia Windows wysyła powiadomienie WM_COMMAND wraz z Identyfikatorem zasobu dla właściciela paska ilekroć dany użytkownik kliknie dwukrotnie w okienku paska stanu stanu.

##  <a name="enablepaneprogressbar"></a>  CMFCStatusBar::EnablePaneProgressBar

W okienku określony, wyświetlany pasek postępu.

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

*nIndex*<br/>
[in] Określa indeks części okienka paska postępu, w których włączyć.

*nTotal*<br/>
[in] Określa maksymalną wartość dla paska postępu.

*bDisplayText*<br/>
[in] Określa, czy bieżąca wartość postępu powinien być wyświetlany pasek postępu.

*clrBar*<br/>
[in] Określa kolor tła paska postępu.

*clrBarDest*<br/>
[in] Określa pomocniczy kolor tła paska postępu. Używana wartość inną niż *clrBar* do wypełnienia przez kolor mieszane do gradientu.

*clrProgressText*<br/>
[in] Określa kolor tekstu pasek postępu.

### <a name="remarks"></a>Uwagi

Jeśli chcesz wyłączyć połączenie paska postępu `EnablePaneProgressBar` z *nLiczba* ustawioną wartość -1. Domyślnie *nLiczba* jest ustawiony na 100. W związku z tym nie trzeba wszelkie dodatkowe obliczenia, aby wyświetlić postęp jako wartość procentowa.

Należy przekazać różne wartości *clrBar* i *clrBarDest* tak, aby kolor tła paska postępu wyświetlany kolor mieszane do gradientu. .

Aby ustawić bieżący postęp, należy wywołać [CMFCStatusBar::SetPaneProgress](#setpaneprogress) metody.

##  <a name="getcount"></a>  CMFCStatusBar::GetCount

Pobiera numer okienka paska stanu.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba okienka paska stanu.

##  <a name="getdrawextendedarea"></a>  CMFCStatusBar::GetDrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getextendedarea"></a>  CMFCStatusBar::GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

[in] *rect*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getitemid"></a>  CMFCStatusBar::GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getitemrect"></a>  CMFCStatusBar::GetItemRect

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>
[in] *lprect —*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="getpaneinfo"></a>  CMFCStatusBar::GetPaneInfo

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>
[in] *nID*<br/>
[in] *nStyle*<br/>
[in] *cxWidth*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="getpaneprogress"></a>  CMFCStatusBar::GetPaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpanestyle"></a>  CMFCStatusBar::GetPaneStyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpanetext"></a>  CMFCStatusBar::GetPaneText

```
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>
[in] *s*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpanewidth"></a>  CMFCStatusBar::GetPaneWidth

Pobiera szerokość okienka paska stanu.

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Określa indeks w okienku paska stanu.

### <a name="return-value"></a>Wartość zwracana

Szerokość okienka paska stanu, *nIndex* określa; w przeciwnym wypadku zero, jeśli nie istnieje w okienku paska stanu.

##  <a name="gettiptext"></a>  CMFCStatusBar::GetTipText

Pobieranie tekstu etykietki narzędzia w okienku paska stanu.

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Określa indeks okienka, dla którego mają zostać pobrane tekst wskazówki.

### <a name="return-value"></a>Wartość zwracana

Tekst etykietki narzędzia w okienku paska stanu, *nIndex* określa. W przeciwnym razie pusty ciąg, jeśli nie istnieje w okienku paska stanu dla określonego *nIndex* lub jego tekst etykietki narzędzia jest pusty.

##  <a name="invalidatepanecontent"></a>  CMFCStatusBar::InvalidatePaneContent

Unieważnienie okienka paska stanu i ponownie narysuj zawartość.

```
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Określa indeks okienka, którego zawartość ma zostać unieważnione i narysowany ponownie.

### <a name="remarks"></a>Uwagi

Gdy zostaje unieważniony na pasku stanu, jest oznaczone do ponownego narysowania. Windows odrysowuje go podczas `UpdateWindow` metoda wysyła komunikat WM_PAINT `OnPaint` metody.

##  <a name="ondrawpane"></a>  CMFCStatusBar::OnDrawPane

Narysuj ponownie w okienku paska stanu.

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia do rysowania.

*pPane*<br/>
[in] Wskaźnik do `CMFCStatusBarPaneInfo` strukturę, która zawiera informacje na temat okienka do narysowania.

### <a name="remarks"></a>Uwagi

Domyślnie `OnDrawPane` odrysowuje okienka przy użyciu kontekstu urządzenia *kontrolera pDC* zgodnie z okienka styl i zawartości.

Należy przesłonić tę metodę w `CMFCStatusBar`-klasy, aby dostosować wygląd okienko.

##  <a name="precreatewindow"></a>  CMFCStatusBar::PreCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parametry

[in] *cs*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="setdrawextendedarea"></a>  CMFCStatusBar::SetDrawExtendedArea

```
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

[in] *bUstawienie*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setindicators"></a>  CMFCStatusBar::SetIndicators

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

[in] *lpIDArray*<br/>
[in] *nIDCount*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="setpaneanimation"></a>  CMFCStatusBar::SetPaneAnimation

Przypisuje animacji do określonego okienka.

```
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Określa indeks okienka, do którego chcesz przypisać do niej animacji.

*hImageList*<br/>
[in] Określa dojścia do listy obrazów, który przechowuje ramek animacji.

*nFrameRate*<br/>
[in] Określa szybkość klatek w milisekundach dla animacji.

*baktualizacji*<br/>
[in] W przypadku opcji TRUE natychmiast zaktualizować zawartość okienka. W przeciwnym razie zawartość okienka jest aktualizowany, gdy zostaje unieważniony.

### <a name="remarks"></a>Uwagi

Jeśli chcesz wyłączyć bieżącej animacji, wywołaj `SetPaneAnimation` z `hImageList` wartość NULL.

##  <a name="setpanebackgroundcolor"></a>  CMFCStatusBar::SetPaneBackgroundColor

Ustawia kolor tła w okienku paska stanu.

```
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Określa indeks okienka, dla której chcesz ustawić nowy kolor tła.

*clrBackground*<br/>
[in] Określa nowy kolor tła.

*baktualizacji*<br/>
[in] W przypadku opcji TRUE natychmiast zaktualizować zawartość okienka. W przeciwnym razie nie są uaktualniane w okienku zawartości do momentu unieważnienia okienka przy użyciu innej metody.

##  <a name="setpaneicon"></a>  CMFCStatusBar::SetPaneIcon

Ustaw ikonę w okienku paska stanu.

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

*nIndex*<br/>
[in] Określa indeks okienka, dla którego ma zostać ustawiony na obrazie.

*hIcon*<br/>
[in] Określa dojścia do ikonę Aby ustawić jako obraz okienka.

*baktualizacji*<br/>
[in] Określa, czy natychmiast zaktualizować zawartość okienka.

*hBmp*<br/>
[in] Określa dojścia do mapy bitowej, można ustawić jako obraz okienka.

*clrTransparent*<br/>
[in] Określa przezroczysty kolor mapy bitowej, *hBmp* wskazuje.

### <a name="remarks"></a>Uwagi

Możesz przekazać HICON lub HBITMAP wraz z przezroczysty kolor, aby ustawić obraz okienka. Jeśli nie chcesz już wyświetlić obraz, należy przekazać wartość NULL jako uchwyt obrazu.

W przypadku dowolnego uruchomiona Animacja, [CMFCStatusBar::SetPaneAnimation](#setpaneanimation) została ustawiona, animacji zostaną zatrzymane.

##  <a name="setpaneinfo"></a>  CMFCStatusBar::SetPaneInfo

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>
[in] *nID*<br/>
[in] *nStyle*<br/>
[in] *cxWidth*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setpaneprogress"></a>  CMFCStatusBar::SetPaneProgress

Ustaw bieżący wskaźnik postępu, pasek postępu dla określonego okienka.

```
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Określa indeks okienka, do których chcesz zaktualizować wskaźnik postępu.

*nCurr*<br/>
[in] Określa bieżącą wartość wskaźnika postępu.

*baktualizacji*<br/>
[in] Określa, czy okienka należy natychmiast zaktualizować.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, gdy ma zostać zaktualizowany wskaźnik postępu, aż pasek postępu, w okienku określony.

Aby użyć tej funkcji dla danego okienka, należy wywołać [CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar) pierwszy.

##  <a name="setpanestyle"></a>  CMFCStatusBar::SetPaneStyle

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>
[in] *nStyle*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setpanetext"></a>  CMFCStatusBar::SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parametry

[in] *nIndex*<br/>
[in] *lpszNewText*<br/>
[in] *baktualizacji*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="setpanetextcolor"></a>  CMFCStatusBar::SetPaneTextColor

Ustawia kolor tekstu w okienku określony.

```
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Określa indeks okienka, do którego chcesz przypisać nowy kolor tekstu.

*clrText*<br/>
[in] Określa kolor tekstu.

*baktualizacji*<br/>
[in] W przypadku opcji TRUE natychmiast zaktualizować zawartość okienka. W przeciwnym razie nie są uaktualniane w okienku zawartości do momentu unieważnienia okienka przy użyciu innej metody.

##  <a name="setpanewidth"></a>  CMFCStatusBar::SetPaneWidth

Ustaw szerokość okienka paska stanu.

```
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Indeks w okienku paska stanu, dla której chcesz ustawić nową szerokość.

*cx*<br/>
[in] Szerokość nowe okienko paska stanu, w pikselach.

##  <a name="settiptext"></a>  CMFCStatusBar::SetTipText

Ustaw tekst etykietki narzędzia w okienku paska stanu.

```
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Indeks okienka, do którego chcesz przypisać tekst etykietki narzędzia.

*pszTipText*<br/>
[in] Nowy tekst etykietki narzędzia.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CPane](../../mfc/reference/cpane-class.md)<br/>
[Klasa CStatusBar](../../mfc/reference/cstatusbar-class.md)
