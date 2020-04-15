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
ms.openlocfilehash: 6c8bb41b82d1dca9235e1184c2152a61c07c8071
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377352"
---
# <a name="cmfctooltipctrl-class"></a>Klasa CMFCToolTipCtrl

Rozszerzona implementacja etykietki narzędzia oparta na [klasie CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md). Etykieta narzędzia oparta `CMFCToolTipCtrl` na klasie może wyświetlać ikonę, etykietę i opis. Jego wygląd można dostosować za pomocą wypełnienia gradientowego, kolorów tekstu niestandardowego i obramowania, tekstu pogrubienia, zaokrąglonych narożników lub stylu odnośnika.

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```cpp
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|Domyślny konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolTipCtrl::GetIconsize](#geticonsize)|Zwraca rozmiar ikony w etykietce narzędzia.|
|[CMFCToolTipCtrl::GetParams](#getparams)|Zwraca ustawienia wyświetlania etykietki narzędzia.|
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|Rysuje obramowanie etykietki narzędzia.|
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||
|[CMFCToolTipCtrl::OnDrawicon](#ondrawicon)|Wyświetla ikonę w etykietce narzędzia.|
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|Rysuje etykietę etykietki narzędzia lub oblicza rozmiar etykiety.|
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|Rysuje separator między etykietą a opisem w etykietce narzędzia.|
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|Wypełnia tło etykietki narzędzia.|
|[CMFCToolTipCtrl::SetDescription](#setdescription)|Ustawia opis, który ma być wyświetlany przez etykietkę narzędzia.|
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl::SetLocation](#setlocation)||
|[CMFCToolTipCtrl::SetParams](#setparams)|Określa wygląd etykietki narzędzia przy użyciu `CMFCToolTipInfo` obiektu.|

## <a name="remarks"></a>Uwagi

Użyj `CMFCToolTipCtrl` `CMFCToolTipInfo`, i [CTooltipManager Klasy](../../mfc/reference/ctooltipmanager-class.md) obiektów razem zaimplementować dostosowane etykietki narzędzi w aplikacji.

Na przykład, aby użyć etykietek narzędzi w stylu dymka, wykonaj następujące kroki:

1. Użyj [CWinAppEx Class](../../mfc/reference/cwinappex-class.md) metody, aby zainicjować menedżera etykietki narzędzia w aplikacji.

2. Utwórz `CMFCToolTipInfo` strukturę, aby określić odpowiedni styl wizualny:

    ```cpp
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

3. Użyj [CTooltipManager::SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) metody, aby ustawić styl wizualny dla wszystkich etykietek narzędzi `CMFCToolTipInfo` w aplikacji przy użyciu stylów zdefiniowanych w obiekcie:

    ```cpp
    theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
        RUNTIME_CLASS (CMFCToolTipCtrl), &params);
    ```

Można również wyprowadzić nową `CMFCToolTipCtrl` klasę z formantu zachowanie etykietki narzędzia i renderowania. Aby określić nową klasę kontroli `CTooltipManager::SetTooltipParams` etykietki narzędzi, należy użyć metody:

```cpp
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```

Aby przywrócić domyślną klasę kontroli etykietki narzędzia i zresetować wygląd etykietki narzędzia do stanu `SetTooltipParams`domyślnego, określ wartość NULL w klasie środowiska uruchomieniowego i parametrach informacji etykietki narzędzia:

```cpp
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    NULL,
    NULL);
```

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonstruować `CMFCToolTipCtrl` obiekt, ustawić opis, który wyświetla etykietka narzędzia i ustawić szerokość formantu etykietki narzędzia.

[!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ctooltipctrl](../../mfc/reference/ctooltipctrl-class.md)

[Cmfctooltipctrl](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtooltipctrl.h

## <a name="cmfctooltipctrlcmfctooltipctrl"></a><a name="cmfctooltipctrl"></a>CMFCToolTipCtrl::CMFCToolTipCtrl

```cpp
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>Parametry

[w] *pParams ( pParams )*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfctooltipctrlgeticonsize"></a><a name="geticonsize"></a>CMFCToolTipCtrl::GetIconsize

Zwraca rozmiar ikony w etykietce narzędzia.

```cpp
virtual CSize GetIconSize();
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar ikony w pikselach.

## <a name="cmfctooltipctrlgetparams"></a><a name="getparams"></a>CMFCToolTipCtrl::GetParams

Zwraca ustawienia wyświetlania etykietki narzędzia.

```cpp
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca etykietka narzędzia wyświetla ustawienia , które są przechowywane w obiekcie [klasy CMFCToolTipInfo.](../../mfc/reference/cmfctooltipinfo-class.md)

## <a name="cmfctooltipctrlondrawborder"></a><a name="ondrawborder"></a>CMFCToolTipCtrl::OnDrawBorder

Rysuje obramowanie etykietki narzędzia.

```cpp
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[w] Prostokąt ograniczający etykietki narzędzia.

*clrLine (linia clrline)*<br/>
[w] Kolor obramowania.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby dostosować wygląd obramowania etykietki narzędzia.

## <a name="cmfctooltipctrlondrawdescription"></a><a name="ondrawdescription"></a>CMFCToolTipCtrl::OnDrawDescription

```cpp
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parametry

[w] *pDC*<br/>
[w] *rect*<br/>
[w] *bCalcOnly*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfctooltipctrlondrawicon"></a><a name="ondrawicon"></a>CMFCToolTipCtrl::OnDrawicon

Wyświetla ikonę w etykietce narzędzia.

```cpp
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*rectImage*<br/>
[w] Współrzędne ikony.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ikona została narysowana. W przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby wyświetlić ikonę niestandardową. Należy również zastąpić [CMFCToolTipCtrl::GetIconSize,](#geticonsize) aby włączyć etykietkę narzędzia, aby poprawnie obliczyć układ tekstu i opisu.

## <a name="cmfctooltipctrlondrawlabel"></a><a name="ondrawlabel"></a>CMFCToolTipCtrl::OnDrawLabel

Rysuje etykietę etykietki narzędzia lub oblicza rozmiar etykiety.

```cpp
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[w] Prostokąt ograniczający obszaru etykiety.

*bCalcOnly*<br/>
[w] Jeśli true, etykieta nie zostanie narysowana.

### <a name="return-value"></a>Wartość zwracana

Rozmiar etykiety w pikselach.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, jeśli chcesz dostosować wygląd etykiety etykietki narzędzia.

## <a name="cmfctooltipctrlondrawseparator"></a><a name="ondrawseparator"></a>CMFCToolTipCtrl::OnDrawSeparator

Rysuje separator między etykietą a opisem w etykietce narzędzia.

```cpp
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*x1*<br/>
[w] Współrzędna pozioma lewego końca separatora.

*x2*<br/>
[w] Współrzędna pozioma prawego końca separatora.

*Tak*<br/>
[w] Pionowa współrzędna separatora.

### <a name="remarks"></a>Uwagi

Domyślna implementacja rysuje linię od punktu (x1, y) do punktu (x2, y).

Zastąpić tę metodę w klasie pochodnej, aby dostosować wygląd separatora.

## <a name="cmfctooltipctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCToolTipCtrl::OnFillBackground

Wypełnia tło etykietki narzędzia.

```cpp
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
[w] Określa prostokąt ograniczający obszaru do wypełnienia.

*clrTekst*<br/>
[w] Etykietka narzędzia kolor pierwszego planu.

*clrLine (linia clrline)*<br/>
[w] Kolor obramowań i linia ogranicznika między etykietą a opisem.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wypełnia prostokąt określony przez *rect* kolorem lub wzorkiem określonym przez ostatnie wywołanie [CMFCToolTipCtrl::SetParams](#setparams).

Zastąp tę metodę w klasie pochodnej, jeśli chcesz dostosować wygląd etykietki narzędzia.

## <a name="cmfctooltipctrlsetdescription"></a><a name="setdescription"></a>CMFCToolTipCtrl::SetDescription

Ustawia opis, który ma być wyświetlany przez etykietkę narzędzia.

```cpp
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>Parametry

*strDesrciption*<br/>
[w] Opis tekstu.

### <a name="remarks"></a>Uwagi

Tekst opisu jest wyświetlany na etykietce narzędzia pod separatorem.

## <a name="cmfctooltipctrlsetfixedwidth"></a><a name="setfixedwidth"></a>CMFCToolTipCtrl::SetFixedWidth

```cpp
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>Parametry

[w] *nWidthRegularne*<br/>
[w] *nWidthLargeImage*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfctooltipctrlsethotribbonbutton"></a><a name="sethotribbonbutton"></a>CMFCToolTipCtrl::SetHotRibbonButton

```cpp
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>Parametry

[w] *PRibbonButton (Przycisk pRibbon)*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfctooltipctrlsetlocation"></a><a name="setlocation"></a>CMFCToolTipCtrl::SetLocation

```cpp
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>Parametry

[w] *pt.*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfctooltipctrlsetparams"></a><a name="setparams"></a>CMFCToolTipCtrl::SetParams

Określa wygląd etykietki narzędzia przy użyciu obiektu [KLASY CMFCToolTipInfo.](../../mfc/reference/cmfctooltipinfo-class.md)

```cpp
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>Parametry

*pParams ( pParams )*<br/>
[w] Wskaźnik do [cmfctooltipinfo klasy](../../mfc/reference/cmfctooltipinfo-class.md) obiektu, który zawiera parametry wyświetlania.

### <a name="remarks"></a>Uwagi

Za każdym razem, gdy etykietka narzędzia jest wyświetlana, jest rysowana przy użyciu kolorów i stylów wizualnych, które określa *pParams.* Wartość *pParams* jest przechowywana w `m_Params`chronionym członku , do którego może uzyskać dostęp klasa pochodna, która zastępuje [CMFCToolTipCtrl::OnDrawBorder](#ondrawborder), [CMFCToolTipCtrl::OnDraw Icon](#ondrawicon), [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel), [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)lub [CMFCToolTipCtrl::OnFillBackground](#onfillbackground) do zachowania określonego wyglądu.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)<br/>
[Klasa CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)<br/>
[Klasa CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
