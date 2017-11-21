---
title: Klasa CMFCToolTipCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 83fe6fc144f4a8864cccb68edef230ba91364416
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfctooltipctrl-class"></a>Klasa CMFCToolTipCtrl
Implementacja tooltip rozszerzonej na podstawie [CToolTipCtrl — klasa](../../mfc/reference/ctooltipctrl-class.md). Etykietka narzędzia na podstawie `CMFCToolTipCtrl` klasy można wyświetlać ikony, etykiety i opis. Jego wygląd można dostosować za pomocą wypełnienia gradientowego, niestandardowego tekstu i kolory obramowania, pogrubioną, zaokrąglonymi narożnikami lub styl dymek.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
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
|[CMFCToolTipCtrl::GetParams](#getparams)|Zwraca ustawienia wyświetlana etykietka narzędzia.|  
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|Rysuje obramowanie etykietka narzędzia.|  
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||  
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|Wyświetla ikonę w etykietce narzędzia.|  
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|Pobiera etykietę etykietka narzędzia lub oblicza rozmiar etykiety.|  
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|Rysuje separatora między etykiety i opis w etykietce narzędzia.|  
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|Wypełnia tło etykietek narzędzi.|  
|[CMFCToolTipCtrl::SetDescription](#setdescription)|Określa opis, który będzie wyświetlany przez etykietkę narzędzia.|  
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||  
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||  
|[CMFCToolTipCtrl::SetLocation](#setlocation)||  
|[CMFCToolTipCtrl::SetParams](#setparams)|Określa wygląd etykietka narzędzia, za pomocą `CMFCToolTipInfo` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `CMFCToolTipCtrl`, `CMFCToolTipInfo`, i [klasy CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) obiektów ze sobą w celu wdrożenia dostosowane etykietki narzędzi w aplikacji.  
  
 Na przykład aby użyć elementy ToolTip dymka stylu, wykonaj następujące kroki:  
  
 1. Użyj [klasy CWinAppEx](../../mfc/reference/cwinappex-class.md) metody zainicjować Menedżera etykietki narzędzia w aplikacji.  
  
 2. Utwórz `CMFCToolTipInfo` struktury, określ styl wizualny, który chcesz:  
  
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
3. Użyj [CTooltipManager::SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) metodę, aby ustawić stylu dla wszystkich etykietek narzędzi w aplikacji przy użyciu style zdefiniowane w `CMFCToolTipInfo` obiektu:  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);
```  
Można również pochodzić z nową klasę `CMFCToolTipCtrl` formantu tooltip zachowania i renderowania. Aby określić nową klasę formantu tooltip, użyj `CTooltipManager::SetTooltipParams` metody:  
  
```  
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMyToolTipCtrl))  
```  
Aby przywrócić domyślne tooltip kontrolować klasy i zresetuj wygląd etykietkę narzędzia do stanu domyślnego Określ wartość NULL w środowiska uruchomieniowego klasy i etykietek narzędzi informacje o parametrach `SetTooltipParams`:  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    NULL,
    NULL);
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCToolTipCtrl` obiektu, ustawić opis, który wyświetla etykietki narzędzia i ustawia szerokość formantu tooltip.  
  
 [!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)  
  
 [CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtooltipctrl.h  
  
##  <a name="cmfctooltipctrl"></a>CMFCToolTipCtrl::CMFCToolTipCtrl  

  
```  
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pParams`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="geticonsize"></a>CMFCToolTipCtrl::GetIconSize  
 Zwraca rozmiar ikony w etykietce narzędzia.  
  
```  
virtual CSize GetIconSize();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar ikony, w pikselach.  
  
##  <a name="getparams"></a>CMFCToolTipCtrl::GetParams  
 Zwraca ustawienia wyświetlana etykietka narzędzia.  
  
```  
const CMFCToolTipInfo& GetParams() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżące ustawienia wyświetlana etykietka narzędzia, które są przechowywane w [klasy CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) obiektu.  
  
##  <a name="ondrawborder"></a>CMFCToolTipCtrl::OnDrawBorder  
 Rysuje obramowanie etykietka narzędzia.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rect,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 `[in] rect`  
 Prostokąt ograniczający element tooltip.  
  
 `[in] clrLine`  
 Kolor obramowania.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej, aby dostosować wygląd obramowania etykietka narzędzia.  
  
##  <a name="ondrawdescription"></a>CMFCToolTipCtrl::OnDrawDescription  

  
```  
virtual CSize OnDrawDescription(
    CDC* pDC,  
    CRect rect,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 [in]`rect`  
 [in]`bCalcOnly`  
  
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
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in]`rectImage`  
 Współrzędne ikony.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli ikona został wystawiony. W przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej do wyświetlania ikon niestandardowych. Konieczne jest również przesłonięcie [CMFCToolTipCtrl::GetIconSize](#geticonsize) umożliwiające etykietki narzędzia w celu obliczenia poprawnie układu tekstu i opis.  
  
##  <a name="ondrawlabel"></a>CMFCToolTipCtrl::OnDrawLabel  
 Pobiera etykietę etykietka narzędzia lub oblicza rozmiar etykiety.  
  
```  
virtual CSize OnDrawLabel(
    CDC* pDC,  
    CRect rect,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 `[in] rect`  
 Prostokąt ograniczający obszaru etykiety.  
  
 `[in] bCalcOnly`  
 Jeśli `TRUE`, etykiety nie będą pobierane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar etykiety, w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę metodę w klasie pochodnej, jeśli chcesz dostosować wygląd etykietka narzędzia etykiety.  
  
##  <a name="ondrawseparator"></a>CMFCToolTipCtrl::OnDrawSeparator  
 Rysuje separatora między etykiety i opis w etykietce narzędzia.  
  
```  
virtual void OnDrawSeparator(
    CDC* pDC,  
    int x1,  
    int x2,  
    int y);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in]`x1`  
 Poziomy Współrzędna z lewej strony separatora.  
  
 [in]`x2`  
 Poziomy Współrzędna prawej stronie separatora.  
  
 [in]`Y`  
 Pionowy Współrzędna separatora.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja rysuje linię z punktu (x1, y) w punkcie (x2, y).  
  
 Zastępuje tę metodę w klasie pochodnej, aby dostosować wygląd separatora.  
  
##  <a name="onfillbackground"></a>CMFCToolTipCtrl::OnFillBackground  
 Wypełnia tło etykietek narzędzi.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    CRect rect,  
    COLORREF& clrText,  
    COLORREF& clrLine);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 `[in] rect`  
 Określa prostokąt ograniczający obszar, aby wypełnić.  
  
 `[in] clrText`  
 Kolor pierwszego planu etykietka narzędzia.  
  
 `[in] clrLine`  
 Kolor obramowania i linii ogranicznik między etykiety i opis.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wypełnia prostokąt określony przez `rect` z kolor lub deseń określony przez wywołanie najnowszych [CMFCToolTipCtrl::SetParams](#setparams).  
  
 Należy przesłonić tę metodę w klasie pochodnej, jeśli chcesz dostosować wygląd elementu tooltip.  
  
##  <a name="setdescription"></a>CMFCToolTipCtrl::SetDescription  
 Określa opis, który będzie wyświetlany przez etykietkę narzędzia.  
  
```  
virtual void SetDescription(const CString strDesrciption);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] strDesrciption`  
 Tekst opisu.  
  
### <a name="remarks"></a>Uwagi  
 Tekst opisu description jest wyświetlany na elemencie tooltip w separatorze.  
  
##  <a name="setfixedwidth"></a>CMFCToolTipCtrl::SetFixedWidth  

  
```  
void SetFixedWidth(
    int nWidthRegular,  
    int nWidthLargeImage);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nWidthRegular`  
 [in]`nWidthLargeImage`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="sethotribbonbutton"></a>CMFCToolTipCtrl::SetHotRibbonButton  

  
```  
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pRibbonButton`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setlocation"></a>CMFCToolTipCtrl::SetLocation  

  
```  
void SetLocation(CPoint pt);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pt`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setparams"></a>CMFCToolTipCtrl::SetParams  
 Określa wygląd etykietka narzędzia, za pomocą [klasy CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) obiektu.  
  
```  
void SetParams(CMFCToolTipInfo* pParams);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] pParams`  
 Wskaźnik do [klasy CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) obiekt, który zawiera parametry wyświetlania.  
  
### <a name="remarks"></a>Uwagi  
 Zawsze, gdy etykietka narzędzia jest wyświetlana, jest rysowane przy użyciu kolorów i visual style, które `pParams` określa. Wartość `pParams` są przechowywane w chroniony element członkowski `m_Params`, który jest dostępny przez klasę pochodną, która zastępuje [CMFCToolTipCtrl::OnDrawBorder](#ondrawborder), [CMFCToolTipCtrl::OnDrawIcon](#ondrawicon), [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel), [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator), lub [CMFCToolTipCtrl::OnFillBackground](#onfillbackground) do zachowania wygląd określony.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [CToolTipCtrl — klasa](../../mfc/reference/ctooltipctrl-class.md)   
 [Klasa CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)   
 [Klasa CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)   
 [Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
