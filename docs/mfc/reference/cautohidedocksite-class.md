---
title: Klasa CAutoHideDockSite | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::CanAcceptPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::DockPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::GetAlignRect
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::RepositionPanes
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetLeft
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetRight
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::UnSetAutoHideMode
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::m_nExtraSpace
dev_langs:
- C++
helpviewer_keywords:
- CAutoHideDockSite [MFC], CanAcceptPane
- CAutoHideDockSite [MFC], DockPane
- CAutoHideDockSite [MFC], GetAlignRect
- CAutoHideDockSite [MFC], RepositionPanes
- CAutoHideDockSite [MFC], SetOffsetLeft
- CAutoHideDockSite [MFC], SetOffsetRight
- CAutoHideDockSite [MFC], UnSetAutoHideMode
- CAutoHideDockSite [MFC], m_nExtraSpace
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e8cc4e9158ae9ff2ef6fd4d48483aa5a75dd9617
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cautohidedocksite-class"></a>Klasa CAutoHideDockSite
`CAutoHideDockSite` Rozszerza [klasy CDockSite](../../mfc/reference/cdocksite-class.md) do zaimplementowania autoukrywania dock okienka.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAutoHideDockSite : public CDockSite  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`CAutoHideDockSite::CAutoHideDockSite`|Konstruuje `CAutoHideDockSite` obiektu.|  
|`CAutoHideDockSite::~CAutoHideDockSite`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Wskazuje, czy `CAutoHideDockSite` jest wyświetlany w menu okienka.|  
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|Określa, czy obiekt podstawowy okienko jest pochodną [CMFCAutoHideBar klasy](../../mfc/reference/cmfcautohidebar-class.md).|  
|[CAutoHideDockSite::DockPane](#dockpane)|Stacje dokujące okienko tej `CAuotHideDockSite` obiektu.|  
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|Pobiera informacje o rozmiarze lokacji dokowania we współrzędnych ekranu.|  
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|Ponownie rysuje okienku na `CAutoHideDockSite` z marginesami globalne i odstęp.|  
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|Ustawia margines po lewej stronie dokowania paska.|  
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|Ustawia margines po prawej stronie paska dokowania.|  
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|Wywołania [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) dla obiektów w `CAutoHideDockSite`.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|Określa rozmiar odstęp między paski narzędzi i krawędzi dokowania paska. Ta przestrzeń jest mierzony z lewej lub górnej krawędzi, w zależności od wyrównania dla miejsca dokowania.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas wywoływania [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes), automatycznie tworzy platformę `CAutoHideDockSite` obiektu. W większości przypadków należy trzeba utworzyć wystąpienia lub bezpośrednio za pomocą tej klasy.  
  
 Odstęp między z lewej strony panelu dok i z lewej strony jest dokowania paska [CMFCAutoHideButton klasy](../../mfc/reference/cmfcautohidebutton-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak pobrać `CAutoHideDockSite` obiekt z `CMFCAutoHideBar` obiektu oraz jak ustawić marginesy lewy i prawy dokowania paska.  
  
 [!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxautohidedocksite.h  
  
##  <a name="canacceptpane"></a>CAutoHideDockSite::CanAcceptPane  
 Określa, czy podstawowy okienko jest [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) obiekt lub typ pochodzący od `CMFCAutoHideBar`.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pBar`|Okienko podstawową platformę testów.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli `pBar` jest pochodną `CMFCAutoHideBar`; `FALSE` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekt podstawowy okienko jest pochodną `CMFCAutoHideBar`, może zawierać `CAutoHideDockSite`.  
  
##  <a name="dockpane"></a>CAutoHideDockSite::DockPane  
 Stacje dokujące okienko tej [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) obiektu.  
  
```  
virtual void DockPane(
    CPane* pWnd,  
    AFX_DOCK_METHOD dockMethod,  
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pWnd`|Okienka stacje dokujące platformę.|  
|[in]`dockMethod`|Dokowanie opcje okienka.|  
|[in]`lpRect`|Prostokąt określa granice zadokowanego panelu.|  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja nie używa parametru `dockMethod`, które jest dostarczane do użytku w przyszłości.  
  
 Jeśli `lpRect` jest `NULL`, platformę umieszcza okienka w domyślnej lokalizacji w witrynie dokowania. Jeśli witryna dock jest poziomy, domyślna lokalizacja to lewej strony witryny dokowania. W przeciwnym razie wartość domyślna lokalizacja to u góry lokacji dokowania.  
  
##  <a name="getalignrect"></a>CAutoHideDockSite::GetAlignRect  
 Pobiera informacje o rozmiarze lokacji dokowania we współrzędnych ekranu.  
  
```  
void GetAlignRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`rect`|Odwołanie do prostokąta. Metoda przechowuje rozmiar lokacji dock w tym prostokącie.|  
  
### <a name="remarks"></a>Uwagi  
 Prostokąt zostanie zmieniona dla przesunięcia marginesów tak, aby nie są uwzględniane.  
  
##  <a name="m_nextraspace"></a>CAutoHideDockSite::m_nExtraSpace  
 Wielkość odstępów między krawędzi [klasy CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) i [klasy CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) obiektów.  
  
```  
static int m_nExtraSpace;  
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy `CMFCAutoHideBar` jest zadokowany w `CAutoHideDockSite`, nie będzie zajmować dokowania całej lokacji. Tę zmienną globalną określa dodatkowe miejsce od lewej lub górnej krawędzi elementu `CMFCAutoHideBar` i odpowiadający mu `CAutoHideDockSite` krawędzi. Czy używany jest góry lub lewej krawędzi zależy od bieżącego wyrównania.  
  
##  <a name="setoffsetleft"></a>CAutoHideDockSite::SetOffsetLeft  
 Ustawia margines po lewej stronie dokowania paska.  
  
```  
void SetOffsetLeft(int nOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nOffset`  
 Przesunięcie nowe.  
  
### <a name="remarks"></a>Uwagi  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) obiekty są rozmieszczone na statycznie `CAutoHideDockSite` obiektu. Oznacza to, że użytkownik nie może ręcznie zmienić lokalizację `CMFCAutoHideBar` obiektów. `SetOffsetLeft` Metody Określa odstępy między lewej skrajnej lewej `CMFCAutoHideBar` i z lewej strony `CAutoHideDockSite`.  
  
##  <a name="setoffsetright"></a>CAutoHideDockSite::SetOffsetRight  
 Ustawia margines po prawej stronie paska dokowania.  
  
```  
void SetOffsetRight(int nOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nOffset`  
 Przesunięcie nowe.  
  
### <a name="remarks"></a>Uwagi  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) obiekty są rozmieszczone na statycznie `CAutoHideDockSite` obiektu. Oznacza to, że użytkownik nie może ręcznie zmienić lokalizację `CMFCAutoHideBar` obiektów. `SetOffsetRight` Metody Określa odstępy między po prawej stronie prawej krawędzi `CMFCAutoHideBar` i po prawej stronie `CAutoHideDockSite`.  
  
##  <a name="repositionpanes"></a>CAutoHideDockSite::RepositionPanes  
 Ponownie rysuje okienka na [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md).  
  
```  
virtual void RepositionPanes(CRect& rectNewClientArea);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`rectNewClientArea`|Wartością zastrzeżoną.|  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja używa `rectNewClientArea`. Ponownie go rysuje okienka z marginesami globalne narzędzi i odstęp.  
  
##  <a name="unsetautohidemode"></a>CAutoHideDockSite::UnSetAutoHideMode  
 Wywołania [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) dla obiektów w lokacji dokowania.  
  
```  
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pAutoHideToolbar`|Wskaźnik do [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) okienko obiektów znajdujących się na `CAutoHideDockSite`.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda szuka wiersza, który zawiera `pAutoHideToolbar`. Wywołuje `CMFCAutoHideBar.UnSetAutoHideMode` dla wszystkich `CMFCAutoHideBar` obiektów w tym wierszu. Jeśli `pAutoHideToolbar` nie można odnaleźć lub jest ona `NULL`, ta metoda wywołuje `CMFCAutoHideBar.UnSetAutoHideMode` dla wszystkich `CMFCAutoHideBar` obiektów na `CAutoHideDockSite`.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CDockSite](../../mfc/reference/cdocksite-class.md)
