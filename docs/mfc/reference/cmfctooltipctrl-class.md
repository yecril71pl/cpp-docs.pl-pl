---
title: Klasa CMFCToolTipCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f395ae726725507bf27f5033b20a4ece2a226a6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715666"
---
# <a name="cmfctooltipctrl-class"></a>Klasa CMFCToolTipCtrl
Implementacja Rozszerzone etykietki narzędzia oparta na [klasa CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md). Etykietka narzędzia oparta na `CMFCToolTipCtrl` klasy może wyświetlać ikony, etykietę i opis. Jego wygląd można dostosować, używając wypełniacza gradientu, niestandardowego tekstu i kolorów obramowania, pogrubioną czcionką, zaokrąglonych rogów lub stylu balonowego.  

 Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|Zwraca rozmiar ikony w etykietce narzędzia.|  
|[CMFCToolTipCtrl::GetParams](#getparams)|Zwraca wartość ustawienia wyświetlana etykietka narzędzia.|  
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|Rysuje obramowanie etykietki narzędzia.|  
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||  
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|Wyświetla ikonę w etykietce narzędzia.|  
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|Rysuje etykiety etykietka narzędzia, lub oblicza rozmiar etykiety.|  
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|Rysuje separator pomiędzy etykietą i opis w etykietce narzędzia.|  
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|Wypełnia tło etykietek narzędzi.|  
|[CMFCToolTipCtrl::SetDescription](#setdescription)|Określa opis, który ma być wyświetlany w etykietce narzędzia.|  
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||  
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||  
|[CMFCToolTipCtrl::SetLocation](#setlocation)||  
|[CMFCToolTipCtrl::SetParams](#setparams)|Określa wygląd etykietka narzędzia, za pomocą `CMFCToolTipInfo` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `CMFCToolTipCtrl`, `CMFCToolTipInfo`, i [klasa CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) obiektów ze sobą, aby implementować niestandardowe etykietki narzędzi w aplikacji.  
  
 Na przykład aby użyć stylu balonowego etykietki narzędzi, wykonaj następujące kroki:  
  
 1. Użyj [klasa CWinAppEx](../../mfc/reference/cwinappex-class.md) metodę, aby zainicjować Menedżera etykietki narzędzia w aplikacji.  
  
 2. Utwórz `CMFCToolTipInfo` struktury do określania stylu wizualnego, który chcesz:  
  
```  
CMFCToolTipInfo params;  
    params.m_bBoldLabel = FALSE;  
    params.m_bDrawDescription = FALSE;  
    params.m_bDrawIcon = FALSE;  
    params.m_bRoundedCorners = TRUE;  
    params.m_bDrawSeparator = FALSE;  
    if (m_bCustomColors)  
 {  
    params.m_clrFill = RGB (255,
    255,
    255);

    params.m_clrFillGradient = RGB (228,
    228,
    240);

    params.m_clrText = RGB (61,
    83,
    80);

    params.m_clrBorder = RGB (144,
    149,
    168);

 }  
```  
3. Użyj [CTooltipManager::SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) metodę, aby ustawić stylu wizualnego dla wszystkich etykietek narzędzi w aplikacji przy użyciu stylów zdefiniowany w `CMFCToolTipInfo` obiektu:  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);
```  
Można również uzyskać nowe klasy z `CMFCToolTipCtrl` do kontroli zachowania etykietki narzędzia i renderowanie. Aby określić nową klasę formantu etykietki narzędzia, należy użyć `CTooltipManager::SetTooltipParams` metody:  
  
```  
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMyToolTipCtrl))  
```  
Aby przywrócić domyślne etykietka narzędzia kontrolować klasy i Resetuj wygląd etykietkę narzędzia do stanu domyślnego należy określić wartość NULL w środowiska uruchomieniowego klasy i etykietek narzędzi informacje o parametrach `SetTooltipParams`:  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    NULL,
    NULL);
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCToolTipCtrl` obiektu, opis, który wyświetla etykietkę narzędzia zestawu i Ustaw szerokość kontrolki tooltip.  
  
 [!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)  
  
 [CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtooltipctrl.h  
  
##  <a name="cmfctooltipctrl"></a>  CMFCToolTipCtrl::CMFCToolTipCtrl  

  
```  
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pParams*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="geticonsize"></a>  CMFCToolTipCtrl::GetIconSize  
 Zwraca rozmiar ikony w etykietce narzędzia.  
  
```  
virtual CSize GetIconSize();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar ikony, w pikselach.  
  
##  <a name="getparams"></a>  CMFCToolTipCtrl::GetParams  
 Zwraca wartość ustawienia wyświetlana etykietka narzędzia.  
  
```  
const CMFCToolTipInfo& GetParams() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżące ustawienia wyświetlana etykietka narzędzia, które są przechowywane w [klasa CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) obiektu.  
  
##  <a name="ondrawborder"></a>  CMFCToolTipCtrl::OnDrawBorder  
 Rysuje obramowanie etykietki narzędzia.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rect,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.  
  
*Rect*<br/>
[in] Prostokąt otaczający etykietki narzędzia.  
  
*clrLine*<br/>
[in] Kolor obramowania.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę metodę w klasie pochodnej, aby dostosować wygląd obramowanie etykietki narzędziowej.  
  
##  <a name="ondrawdescription"></a>  CMFCToolTipCtrl::OnDrawDescription  

  
```  
virtual CSize OnDrawDescription(
    CDC* pDC,  
    CRect rect,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] [in] *rect*  
 [in] *bCalcOnly*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondrawicon"></a>  CMFCToolTipCtrl::OnDrawIcon  
 Wyświetla ikonę w etykietce narzędzia.  
  
```  
virtual BOOL OnDrawIcon(
    CDC* pDC,  
    CRect rectImage);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.  
  
*rectImage*<br/>
[in] Współrzędne ikony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli została narysowana ikony. W przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę metodę w klasie pochodnej, aby wyświetlić ikonę niestandardową. Konieczne jest również przesłonięcie [CMFCToolTipCtrl::GetIconSize](#geticonsize) umożliwiające etykietki narzędzia poprawnie obliczyć układu tekstu i opis.  
  
##  <a name="ondrawlabel"></a>  CMFCToolTipCtrl::OnDrawLabel  
 Rysuje etykiety etykietka narzędzia, lub oblicza rozmiar etykiety.  
  
```  
virtual CSize OnDrawLabel(
    CDC* pDC,  
    CRect rect,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.  
  
*Rect*<br/>
[in] Prostokąt otaczający obszaru etykiety.  
  
*bCalcOnly*<br/>
[in] W przypadku opcji TRUE etykiety nie będą pobierane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar etykiety, w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę metodę w klasie pochodnej, jeśli chcesz dostosować wygląd etykiety etykietki narzędzia.  
  
##  <a name="ondrawseparator"></a>  CMFCToolTipCtrl::OnDrawSeparator  
 Rysuje separator pomiędzy etykietą i opis w etykietce narzędzia.  
  
```  
virtual void OnDrawSeparator(
    CDC* pDC,  
    int x1,  
    int x2,  
    int y);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.  
  
*x1*<br/>
[in] Poziomy Współrzędna z lewej strony separatora.  
  
*x2*<br/>
[in] Poziomy Współrzędna prawej stronie separatora.  
  
*Y*<br/>
[in] Współrzędna pionowy separatora.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja rysuje linię z punktu (x1, y) w punkcie (x2, y).  
  
 Należy przesłonić tę metodę w klasie pochodnej, aby dostosować wygląd separatora.  
  
##  <a name="onfillbackground"></a>  CMFCToolTipCtrl::OnFillBackground  
 Wypełnia tło etykietek narzędzi.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    CRect rect,  
    COLORREF& clrText,  
    COLORREF& clrLine);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.  
  
*Rect*<br/>
[in] Określa obszar, aby wypełnić prostokąt otaczający.  
  
*clrText*<br/>
[in] Kolor pierwszego planu etykietki narzędzia.  
  
*clrLine*<br/>
[in] Kolor obramowania i linii ogranicznik między etykietę i opis.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wypełnia prostokąt, który jest określony przez *prostokąt* z kolor lub deseń określony przez wywołanie najnowszych [CMFCToolTipCtrl::SetParams](#setparams).  
  
 Przesłonić tę metodę w klasie pochodnej, jeśli chcesz dostosować wygląd etykietki narzędzia.  
  
##  <a name="setdescription"></a>  CMFCToolTipCtrl::SetDescription  
 Określa opis, który ma być wyświetlany w etykietce narzędzia.  
  
```  
virtual void SetDescription(const CString strDesrciption);
```  
  
### <a name="parameters"></a>Parametry  
*strDesrciption*<br/>
[in] Tekst opisu.  
  
### <a name="remarks"></a>Uwagi  
 Tekst opisu jest wyświetlany na etykietki narzędzia w ramach separatora.  
  
##  <a name="setfixedwidth"></a>  CMFCToolTipCtrl::SetFixedWidth  

  
```  
void SetFixedWidth(
    int nWidthRegular,  
    int nWidthLargeImage);
```  
  
### <a name="parameters"></a>Parametry  
*nWidthRegular*<br/>
[in] [in] *nWidthLargeImage*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="sethotribbonbutton"></a>  CMFCToolTipCtrl::SetHotRibbonButton  

  
```  
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pRibbonButton*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setlocation"></a>  CMFCToolTipCtrl::SetLocation  

  
```  
void SetLocation(CPoint pt);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *(czas pacyficzny)*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setparams"></a>  CMFCToolTipCtrl::SetParams  
 Określa wygląd etykietka narzędzia, za pomocą [klasa CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) obiektu.  
  
```  
void SetParams(CMFCToolTipInfo* pParams);
```  
  
### <a name="parameters"></a>Parametry  
*pParams*<br/>
[in] Wskaźnik do [klasa CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) obiekt zawierający parametry wyświetlania.  
  
### <a name="remarks"></a>Uwagi  
 Zawsze, gdy zostanie wyświetlona etykietka narzędzia, jest rysowany przy użyciu kolory i style wizualizacji, które *pParams* określa. Wartość *pParams* znajduje się w chronionej składowej `m_Params`, który może zostać oceniony przez klasę pochodną, która zastępuje [CMFCToolTipCtrl::OnDrawBorder](#ondrawborder), [CMFCToolTipCtrl: : OnDrawIcon](#ondrawicon), [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel), [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator), lub [CMFCToolTipCtrl::OnFillBackground](#onfillbackground)do obsługi określonego wygląd.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Ctooltipctrl — klasa](../../mfc/reference/ctooltipctrl-class.md)   
 [Klasa CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)   
 [Klasa CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)   
 [Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
