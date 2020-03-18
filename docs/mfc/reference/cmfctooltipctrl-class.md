---
title: Klasa CMFCToolTipCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetIconSize
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetParams
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawBorder
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawLabel
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnFillBackground
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetFixedWidth
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetHotRibbonButton
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetLocation
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetParams
helpviewer_keywords:
- CMFCToolTipCtrl [MFC], GetIconSize
- CMFCToolTipCtrl [MFC], GetParams
- CMFCToolTipCtrl [MFC], OnDrawBorder
- CMFCToolTipCtrl [MFC], OnDrawDescription
- CMFCToolTipCtrl [MFC], OnDrawIcon
- CMFCToolTipCtrl [MFC], OnDrawLabel
- CMFCToolTipCtrl [MFC], OnDrawSeparator
- CMFCToolTipCtrl [MFC], OnFillBackground
- CMFCToolTipCtrl [MFC], SetDescription
- CMFCToolTipCtrl [MFC], SetFixedWidth
- CMFCToolTipCtrl [MFC], SetHotRibbonButton
- CMFCToolTipCtrl [MFC], SetLocation
- CMFCToolTipCtrl [MFC], SetParams
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
ms.openlocfilehash: aecd03371f0dfd4b4af5886bea6c6202c40b5236
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445560"
---
# <a name="cmfctooltipctrl-class"></a>Klasa CMFCToolTipCtrl

Implementacja rozszerzonej etykietki narzędzia oparta na [klasie CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md). Etykietka narzędzia oparta na klasie `CMFCToolTipCtrl` może wyświetlać ikonę, etykietę i opis. Możesz dostosować jego wygląd wizualny przy użyciu wypełnienia gradientowego, niestandardowego tekstu i koloru obramowania, tekstu pogrubionego, zaokrąglonych rogów lub stylu dymka.

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** w instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|Konstruktor domyślny.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|Zwraca rozmiar ikony w etykietce narzędzia.|
|[CMFCToolTipCtrl:: getparams](#getparams)|Zwraca ustawienia wyświetlania etykietki narzędzia.|
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|Rysuje obramowanie etykietki narzędzia.|
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|Wyświetla ikonę w etykietce narzędzia.|
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|Rysuje etykietę etykietki narzędzia lub oblicza rozmiar etykiety.|
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|Rysuje separator między etykietą a opisem w etykietce narzędzia.|
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|Wypełnia tło etykietki narzędzia.|
|[CMFCToolTipCtrl:: SetDescription](#setdescription)|Ustawia opis wyświetlany przez etykietkę narzędzia.|
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl:: SetLocation](#setlocation)||
|[CMFCToolTipCtrl:: setparams](#setparams)|Określa wygląd etykietki narzędzia przy użyciu obiektu `CMFCToolTipInfo`.|

## <a name="remarks"></a>Uwagi

Użyj obiektów klasy `CMFCToolTipCtrl`, `CMFCToolTipInfo`i [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) , aby zaimplementować niestandardowe etykietki narzędzi w aplikacji.

Na przykład, aby użyć etykietek narzędzi w stylu dymkowym, wykonaj następujące kroki:

1. Użyj metody [klasy CWinAppEx](../../mfc/reference/cwinappex-class.md) , aby zainicjować Menedżera etykietek narzędzi w aplikacji.

2. Utwórz strukturę `CMFCToolTipInfo`, aby określić żądany styl wizualizacji:

```
CMFCToolTipInfo params;
params.m_bBoldLabel = FALSE;
params.m_bDrawDescription = FALSE;
params.m_bDrawIcon = FALSE;
params.m_bRoundedCorners = TRUE;
params.m_bDrawSeparator = FALSE;
if (m_bCustomColors)
{
    params.m_clrFill = RGB (255, 255, 255);
    params.m_clrFillGradient = RGB (228, 228, 240);
    params.m_clrText = RGB (61, 83, 80);
    params.m_clrBorder = RGB (144, 149, 168);

}
```

3. Użyj metody [CTooltipManager:: SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) , aby ustawić styl wizualny dla wszystkich etykietek narzędzi w aplikacji za pomocą stylów zdefiniowanych w obiekcie `CMFCToolTipInfo`:

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);
```

Możesz również utworzyć nową klasę z `CMFCToolTipCtrl`, aby kontrolować zachowanie i renderowanie etykietki narzędzi. Aby określić nową klasę formantu tooltip, użyj metody `CTooltipManager::SetTooltipParams`:

```
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```

Aby przywrócić domyślną klasę kontrolki etykietki narzędzia i zresetować wygląd etykietki narzędzia do stanu domyślnego, należy określić wartość NULL w klasie uruchomieniowej i parametry etykietki narzędzia `SetTooltipParams`:

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    NULL,
    NULL);
```

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania obiektu `CMFCToolTipCtrl`, ustawiania opisu wyświetlanego w etykietce narzędzia i ustawiania szerokości kontrolki ToolTip.

[!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxToolTipCtrl. h

##  <a name="cmfctooltipctrl"></a>CMFCToolTipCtrl::CMFCToolTipCtrl

```
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>Parametry

podczas *pParams*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="geticonsize"></a>CMFCToolTipCtrl::GetIconSize

Zwraca rozmiar ikony w etykietce narzędzia.

```
virtual CSize GetIconSize();
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar ikony w pikselach.

##  <a name="getparams"></a>CMFCToolTipCtrl:: getparams

Zwraca ustawienia wyświetlania etykietki narzędzia.

```
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca etykietka narzędzia wyświetla ustawienia, które są przechowywane w obiekcie [klasy CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) .

##  <a name="ondrawborder"></a>CMFCToolTipCtrl::OnDrawBorder

Rysuje obramowanie etykietki narzędzia.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*cinania*<br/>
podczas Prostokąt ograniczający etykietki narzędzia.

*clrLine*<br/>
podczas Kolor obramowania.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby dostosować wygląd obramowania etykietki narzędzia.

##  <a name="ondrawdescription"></a>CMFCToolTipCtrl::OnDrawDescription

```
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parametry

podczas *kontroler PDC*<br/>
podczas *prostokąt*<br/>
podczas *bCalcOnly*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ondrawicon"></a>CMFCToolTipCtrl::OnDrawIcon

Wyświetla ikonę w etykietce narzędzia.

```
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*rectImage*<br/>
podczas Współrzędne ikony.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, Jeśli ikona została narysowana. W przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby wyświetlić niestandardową ikonę. Należy również zastąpić [CMFCToolTipCtrl:: GetIconSize](#geticonsize) , aby umożliwić etykietce narzędzia prawidłowe obliczenie układu tekstu i opisu.

##  <a name="ondrawlabel"></a>CMFCToolTipCtrl::OnDrawLabel

Rysuje etykietę etykietki narzędzia lub oblicza rozmiar etykiety.

```
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*cinania*<br/>
podczas Prostokąt ograniczający obszaru etykiety.

*bCalcOnly*<br/>
podczas Jeśli wartość jest równa TRUE, etykieta nie zostanie narysowana.

### <a name="return-value"></a>Wartość zwracana

Rozmiar etykiety (w pikselach).

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, jeśli chcesz dostosować wygląd etykiety etykietki narzędzia.

##  <a name="ondrawseparator"></a>CMFCToolTipCtrl::OnDrawSeparator

Rysuje separator między etykietą a opisem w etykietce narzędzia.

```
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*x1*<br/>
podczas Współrzędna pozioma lewego końca separatora.

*x2*<br/>
podczas Współrzędne poziome z prawej strony separatora.

*T*<br/>
podczas Współrzędne pionowe separatora.

### <a name="remarks"></a>Uwagi

Domyślna implementacja rysuje linię z punktu (x1, y) do punktu (X2, y).

Zastąp tę metodę w klasie pochodnej, aby dostosować wygląd separatora.

##  <a name="onfillbackground"></a>CMFCToolTipCtrl::OnFillBackground

Wypełnia tło etykietki narzędzia.

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*cinania*<br/>
podczas Określa prostokąt ograniczenia obszaru do wypełnienia.

*clrText*<br/>
podczas Kolor pierwszego planu etykietki narzędzia.

*clrLine*<br/>
podczas Kolor obramowań i linia ogranicznika między etykietą a opisem.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wypełnia prostokąt, który jest określony przez obiekt *Rect* z kolorem lub wzorem określonym przez ostatnie wywołanie [CMFCToolTipCtrl:: setparams](#setparams).

Zastąp tę metodę w klasie pochodnej, jeśli chcesz dostosować wygląd etykietki narzędzia.

##  <a name="setdescription"></a>CMFCToolTipCtrl:: SetDescription

Ustawia opis wyświetlany przez etykietkę narzędzia.

```
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>Parametry

*strDesrciption*<br/>
podczas Tekst opisu.

### <a name="remarks"></a>Uwagi

Tekst opisu jest wyświetlany w etykietce narzędzia pod separatorem.

##  <a name="setfixedwidth"></a>CMFCToolTipCtrl::SetFixedWidth

```
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>Parametry

podczas *nWidthRegular*<br/>
podczas *nWidthLargeImage*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="sethotribbonbutton"></a>CMFCToolTipCtrl::SetHotRibbonButton

```
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>Parametry

podczas *pRibbonButton*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setlocation"></a>CMFCToolTipCtrl:: SetLocation

```
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>Parametry

podczas *pt*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setparams"></a>CMFCToolTipCtrl:: setparams

Określa wygląd etykietki narzędzia przy użyciu obiektu [klasy CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) .

```
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>Parametry

*pParams*<br/>
podczas Wskaźnik do obiektu [klasy CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) , który zawiera parametry wyświetlania.

### <a name="remarks"></a>Uwagi

Gdy etykietka narzędzia zostanie wyświetlona, zostanie narysowana przy użyciu kolorów i stylów wizualnych, które *pParams* określa. Wartość *pParams* jest przechowywana w chronionej składowej `m_Params`, do której można uzyskać dostęp za pomocą klasy pochodnej, która zastępuje [CMFCToolTipCtrl:: OnDrawBorder](#ondrawborder), [CMFCToolTipCtrl:: OnDrawIcon](#ondrawicon), [CMFCToolTipCtrl:: OnDrawLabel](#ondrawlabel), [CMFCToolTipCtrl:: OnDrawSeparator](#ondrawseparator)lub [CMFCToolTipCtrl:: OnFillBackground](#onfillbackground) w celu utrzymania określonego wyglądu.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)<br/>
[Klasa CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)<br/>
[Klasa CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
