---
title: Klasa CMFCPropertyGridToolTipCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a0b4a43da8943bc196a799ca4419dea7f34ed76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>Klasa CMFCPropertyGridToolTipCtrl
Implementuje w etykietce narzędzia kontrolować, które [klasy CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) używa wyświetlać elementy ToolTip.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCPropertyGridToolTipCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Konstruuje `CMFCPropertyGridToolTipCtrl` obiektu.|  
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCPropertyGridToolTipCtrl::Create](#create)|Utworzenie okna dla formantu tooltip.|  
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Dezaktywuje i ukrywa formantu tooltip.|  
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Zwraca współrzędne ostatniej pozycji formantu tooltip.|  
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|Ukrywa formantu tooltip.|  
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Używane przez klasę [CWinApp](../../mfc/reference/cwinapp-class.md) tłumaczenie komunikaty okna przed wysłaniem do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje systemu Windows. (Przesłania [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Ustawia odstęp między tekst etykietki narzędzia i krawędź okna etykietki narzędzia.|  
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Wyświetla formantu tooltip.|  
  
## <a name="remarks"></a>Uwagi  
 Etykietki narzędzi są wyświetlane, gdy wskaźnik znajduje się na nazwę właściwości. [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) klasa wyświetla etykietkę narzędzia tak, aby łatwo odczytać przez użytkownika. Zwykle pozycja etykietka narzędzia jest określana przez położenia wskaźnika. Za pomocą tej klasy, etykietkę narzędzia pojawi się nad nazwę właściwości i podobny rozszerzenie właściwości fizyczne, aby w pełni widoczna jest nazwa właściwości.  
  
 MFC automatycznie tworzy ten formant i używa go w [CMFCPropertyGridCtrl klasy](../../mfc/reference/cmfcpropertygridctrl-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCPropertyGridToolTipCtrl` klasy i sposób wyświetlania formantu tooltip.  
  
 [!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpropertygridtooltipctrl.h  
  
##  <a name="cmfcpropertygridtooltipctrl"></a>CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl  
 Konstruuje `CMFCPropertyGridToolTipCtrl` obiektu.  
  
```  
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```  
  
##  <a name="create"></a>CMFCPropertyGridToolTipCtrl::Create  
 Utworzenie okna dla formantu tooltip.  
  
```  
BOOL Create(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWndParent`  
 Wskaźnik do okna nadrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pomyślnie utworzono okna; w przeciwnym razie wartość FALSE.  
  
##  <a name="deactivate"></a>CMFCPropertyGridToolTipCtrl::Deactivate  
 Dezaktywuje i ukrywa formantu tooltip.  
  
```  
void Deactivate();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ustawia ostatniej pozycji i tekst puste wartości, tak, aby w przyszłości wywołań [CMFCPropertyGridToolTipCtrl::Track](#track) wyświetlenia wskazówki.  
  
##  <a name="getlastrect"></a>CMFCPropertyGridToolTipCtrl::GetLastRect  
 Zwraca współrzędne ostatniej pozycji formantu tooltip.  
  
```  
void GetLastRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rect`  
 Zawiera ostatniej pozycji formantu tooltip.  
  
##  <a name="hide"></a>CMFCPropertyGridToolTipCtrl::Hide  
 Ukrywa formantu tooltip.  
  
```  
void Hide();
```  
  
##  <a name="settextmargin"></a>CMFCPropertyGridToolTipCtrl::SetTextMargin  
 Ustawia odstęp między tekst etykietki narzędzia i krawędź okna etykietki narzędzia.  
  
```  
void SetTextMargin(int nTextMargin);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nTextMargin`  
 Określa odstępy między tekst formantu tooltip i krawędź okna etykietki narzędzia. Wartość domyślna to 10 pikseli.  
  
##  <a name="track"></a>CMFCPropertyGridToolTipCtrl::Track  
 Wyświetla formantu tooltip.  
  
```  
void Track(
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rect`  
 Określa położenie i rozmiar formantu tooltip.  
  
 [in]`strText`  
 Określa tekst, który ma być wyświetlany w etykietce narzędzia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda Wyświetla formantu tooltip pozycji i rozmiaru określonego przez `rect`. Jeśli pozycja, rozmiar i tekst nie uległy zmianie od czasu, gdy ta metoda została wywołana, ta metoda nie ma znaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
