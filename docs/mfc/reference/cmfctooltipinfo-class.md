---
title: Klasa CMFCToolTipInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBalloonTooltip
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBoldLabel
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bRoundedCorners
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bVislManagerTheme
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrBorder
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFill
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFillGradient
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrText
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nGradientAngle
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nMaxDescrWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolTipInfo [MFC], m_bBalloonTooltip
- CMFCToolTipInfo [MFC], m_bBoldLabel
- CMFCToolTipInfo [MFC], m_bDrawDescription
- CMFCToolTipInfo [MFC], m_bDrawIcon
- CMFCToolTipInfo [MFC], m_bDrawSeparator
- CMFCToolTipInfo [MFC], m_bRoundedCorners
- CMFCToolTipInfo [MFC], m_bVislManagerTheme
- CMFCToolTipInfo [MFC], m_clrBorder
- CMFCToolTipInfo [MFC], m_clrFill
- CMFCToolTipInfo [MFC], m_clrFillGradient
- CMFCToolTipInfo [MFC], m_clrText
- CMFCToolTipInfo [MFC], m_nGradientAngle
- CMFCToolTipInfo [MFC], m_nMaxDescrWidth
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 325650f35d097b54eda160bbdbbd5c877dbd0242
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368377"
---
# <a name="cmfctooltipinfo-class"></a>Klasa CMFCToolTipInfo
Przechowuje informacje o wygląd etykietek narzędzi.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCToolTipInfo  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolTipInfo::operator =](#operator_eq)||  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolTipInfo::m_bBalloonTooltip](#m_bballoontooltip)|Wartość logiczna wskazująca, czy element tooltip ma wygląd dymka.|  
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|Wartość logiczna wskazująca, czy etykietka narzędzia etykiety są wyświetlane pogrubioną czcionką.|  
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|Wartość logiczna wskazująca, czy etykietka narzędzia zawiera opis.|  
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|Wartość logiczna wskazująca, czy element tooltip jest wyświetlana ikona.|  
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|Wartość logiczna wskazująca, czy między etykietka narzędzia etykiety i opis tooltip jest wyświetlany separator.|  
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|Wartość logiczna wskazująca, czy element tooltip ma zaokrąglone narożniki.|  
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|Zmienną wartości logicznej, która wskazuje, czy wygląd elementu tooltip powinien być kontrolowany przez Menedżera visual (zobacz [CMFCVisualManager klasy](../../mfc/reference/cmfcvisualmanager-class.md)).|  
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|Kolor obramowania etykietka narzędzia.|  
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|Kolor tła etykietka narzędzia.|  
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|Kolor wypełnienia gradientowego w etykietce narzędzia.|  
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|Kolor tekstu w etykietce narzędzia.|  
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|Kąt wypełnieniem gradientowym w etykietce narzędzia.|  
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|Maksymalna możliwa szerokość w pikselach, opisu w etykietce narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj [klasy CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, i [CTooltipManager klasy](../../mfc/reference/ctooltipmanager-class.md) ze sobą w celu wdrożenia dostosowane etykietki narzędzi w aplikacji. Na przykład dotyczące używania tych klas tooltip zobacz [klasy CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md) tematu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób ustawiania wartości poszczególnych zmiennych w `CMFCToolTipInfo` klasy.  
  
 [!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtooltipctrl.h  
  
##  <a name="m_bballoontooltip"></a>  CMFCToolTipInfo::m_bBalloonTooltip  
 Określa styl wyświetlania wszystkich etykietek narzędzi.  
  
```  
BOOL m_bBalloonTooltip;  
```  
  
### <a name="remarks"></a>Uwagi  
 `TRUE` Wskazuje, że elementy ToolTip korzystać styl dymek `FALSE` wskazuje, że elementy ToolTip korzystać prostokątne stylu.  
  
##  <a name="m_bboldlabel"></a>  CMFCToolTipInfo::m_bBoldLabel  
 Określa czcionkę tekstu etykietki narzędzia jest pogrubiony.  
  
```  
BOOL m_bBoldLabel;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw ten element członkowski `TRUE` do wyświetlania tekstu etykietki narzędzia czcionką pogrubioną, lub `FALSE` do wyświetlania etykiet tooltip-pogrubioną czcionką.  
  
##  <a name="m_bdrawdescription"></a>  CMFCToolTipInfo::m_bDrawDescription  
 Określa, czy każdy tooltip Wyświetla tekst opisu.  
  
```  
BOOL m_bDrawDescription;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw ten element członkowski `TRUE` do wyświetlenia opisu, lub `FALSE` ukrycia opis. Można określić opis w etykietce narzędzia wywołując [CMFCToolTipCtrl::SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)  
  
##  <a name="m_bdrawicon"></a>  CMFCToolTipInfo::m_bDrawIcon  
 Określa, czy wszystkie elementy ToolTip wyświetlanie ikon.  
  
```  
BOOL m_bDrawIcon;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw ten element członkowski `TRUE` do wyświetlenia ikony na każdym tooltip lub `FALSE` wyświetlać elementy ToolTip bez ikon.  
  
##  <a name="m_bdrawseparator"></a>  CMFCToolTipInfo::m_bDrawSeparator  
 Określa, czy każda wskazówka ma separatora między etykiety i jego opis.  
  
```  
BOOL m_bDrawSeparator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw ten element członkowski `TRUE` do wyświetlenia separatora między etykietka narzędzia etykiety i opis, lub `FALSE` wyświetlać elementy ToolTip bez separatora.  
  
##  <a name="m_broundedcorners"></a>  CMFCToolTipInfo::m_bRoundedCorners  
 Określa, czy wszystkie elementy ToolTip mają zaokrąglone narożniki.  
  
```  
BOOL m_bRoundedCorners;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw ten element członkowski `TRUE` do wyświetlenia zaokrąglone narożniki na etykietki narzędzi, lub `FALSE` do wyświetlenia rogi prostokątne na elementy ToolTip.  
  
##  <a name="m_clrborder"></a>  CMFCToolTipInfo::m_clrBorder  
 Określa kolor obramowania na wszystkie elementy ToolTip.  
  
```  
COLORREF m_clrBorder;  
```  
  
##  <a name="m_clrfill"></a>  CMFCToolTipInfo::m_clrFill  
 Określa kolor tła etykietka narzędzia.  
  
```  
COLORREF m_clrFill;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) wynosi -1, jest kolor tła etykietek narzędzi `m_clrFill`. W przeciwnym razie `m_clrFill` Określa kolor początkowy gradientu i `m_clrFillGradient` Określa kolor końcowy gradientu. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) Określa kierunek gradientu.  
  
##  <a name="m_clrfillgradient"></a>  CMFCToolTipInfo::m_clrFillGradient  
 Określa kolor końcowy gradientu tła etykietek narzędzi.  
  
```  
COLORREF m_clrFillGradient;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `m_clrFillGradient` wynosi -1, nie istnieje żadne gradientu. W przeciwnym razie kolor początkowy gradientu jest określona przez [CMFCToolTipInfo::m_clrFill](#m_clrfill) i określany przez kolor gradientu Zakończ `m_clrFillGradient`. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) Określa kierunek gradientu.  
  
##  <a name="m_clrtext"></a>  CMFCToolTipInfo::m_clrText  
 Określa kolor tekstu wszystkie elementy ToolTip.  
  
```  
COLORREF m_clrText;  
```  
  
##  <a name="m_ngradientangle"></a>  CMFCToolTipInfo::m_nGradientAngle  
 Określa kąt rysowania gradientu tła etykietek narzędzi.  
  
```  
int m_nGradientAngle;  
```  
  
### <a name="remarks"></a>Uwagi  
 `m_nGradientAngle` Określa kąt w stopniach, czy gradientu tła etykietek narzędzi jest przesunięta w poziomie. Jeśli `m_nGradientAngle` wynosi 0, rysowania gradientu od lewej do prawej. Jeśli `m_nGradientAngle` to od 1 do 360 gradientu jest obracanie wskazówek zegara przez ten numer stopni. Jeśli `m_nGradientAngle` wynosi -1, która jest wartością domyślną, rysowania gradientu od góry do dołu. Jest to taka sama jak ustawienie `m_nGradientAngle` do 90.  
  
 [CMFCToolTipInfo::m_clrFill](#m_clrfill) `clrFill` Określa kolor początkowy gradientu i [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) `clrFillGradient` Określa kolor końcowy gradientu. Jeśli `m_clrFillGradient` wynosi -1, nie istnieje żadne gradientu.  
  
##  <a name="m_nmaxdescrwidth"></a>  CMFCToolTipInfo::m_nMaxDescrWidth  
 Określa maksymalną szerokość opisu wyświetlanej w każdym etykietka narzędzia. Jeśli szerokość opis przekracza określoną wartość, tekst jest zawijany.  
  
```  
int m_nMaxDescrWidth;  
```  
  
##  <a name="m_bvislmanagertheme"></a>  CMFCToolTipInfo::m_bVislManagerTheme  
 Określa, czy visual Menedżera aplikacji steruje wyglądem wszystkie elementy ToolTip.  
  
```  
BOOL m_bVislManagerTheme;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `m_bVislManagerTheme` jest `TRUE`, co tooltip żądań nowy [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) visual Menedżera aplikacji przed ich są wyświetlane na ekranie i używa wartości w tym obiekcie w celu określenia sposobu ich wyświetlania. Elementy członkowskie z Twojej [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) są ignorowane.  
  
##  <a name="operator_eq"></a>  CMFCToolTipInfo::operator =  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `src`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)   
 [Klasa CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)
