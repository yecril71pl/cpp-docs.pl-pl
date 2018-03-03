---
title: Klasa CMFCDropDownFrame | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01b3e5b56621d7bf8d42aad12e216208338bbacd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdropdownframe-class"></a>Klasa CMFCDropDownFrame
Udostępnia funkcję okna ramkę z listy rozwijanej do listy rozwijanej paski narzędzi i przycisków paska narzędzi z listy rozwijanej.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCDropDownFrame : public CMiniFrameWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`CMFCDropDownFrame::CMFCDropDownFrame`|Domyślny konstruktor.|  
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCDropDownFrame::Create](#create)|Tworzy `CMFCDropDownFrame` obiektu.|  
|`CMFCDropDownFrame::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Pobiera nadrzędny paska menu ramki listy rozwijanej.|  
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Pobiera menu podręczne nadrzędnego ramki listy rozwijanej.|  
|`CMFCDropDownFrame::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|Zmienia położenie ramki listy rozwijanej.|  
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Określa, czy okno podrzędne pasek narzędzi listy rozwijanej zostanie zniszczony automatycznie.|  
  
### <a name="remarks"></a>Uwagi  
 Ta klasa nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
 Platformę używa tej klasy, aby zapewnić zachowanie ramki do `CMFCDropDownToolbar` i `CMFCDropDownToolbarButton` klasy. Aby uzyskać więcej informacji na temat tych klas, zobacz [CMFCDropDownToolbar — klasa](../../mfc/reference/cmfcdropdowntoolbar-class.md) i [CMFCDropDownToolbarButton klasy](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak pobrać wskaźnik do `CMFCDropDownFrame` obiekt z `CFrameWnd` klasy i jak ustawić podrzędne okno narzędzi listy rozwijanej, aby niszczone automatycznie.  
  
 [!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cframewnd —](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdropdowntoolbar.h  
  
##  <a name="create"></a>CMFCDropDownFrame::Create  
 Tworzy `CMFCDropDownFrame` obiektu.  
  
```  
virtual BOOL Create(
    CWnd* pWndParent,  
    int x,  
    int y,  
    CMFCDropDownToolBar* pWndOriginToolbar);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pWndParent`|Okno nadrzędne ramki listy rozwijanej.|  
|[in]`x`|Współrzędna pozioma ekranu dla lokalizacji ramki rozwijana w dół.|  
|[in]`y`|Współrzędna pionowym ekranie lokalizację ramki, w dół do dołu.|  
|[in]`pWndOriginToolbar`|Pasek narzędzi z przycisków listy rozwijanej, który używa tej metody do wypełnienia nowego obiektu ramkę z listy rozwijanej.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli pomyślnie utworzono ramki listy rozwijanej; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje podstawowym [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) metodę w celu utworzenia listy rozwijanej ramkę okna z `WS_POPUP` stylu. Okno ramowe listy rozwijanej jest wyświetlany na współrzędne ekranu. Ta metoda zakończy się niepowodzeniem, jeśli [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) metoda zwraca `FALSE`.  
  
 `CMFCDropDownFrame` Klasy tworzy kopię dostarczonych `CMFCDropDownToolBar` parametru. Ta metoda umożliwia skopiowanie obrazy dla przycisków i stanów przycisk z `pWndOriginToolbar` parametr `m_pWndOriginToolbar` element członkowski danych.  
  
##  <a name="getparentmenubar"></a>CMFCDropDownFrame::GetParentMenuBar  
 Pobiera nadrzędny paska menu ramki listy rozwijanej.  
  
```  
CMFCMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nadrzędnego paska menu ramki listy rozwijanej lub `NULL` Jeśli ramki nie ma obiektu nadrzędnego.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda pobiera na pasku menu nadrzędnego przycisku nadrzędnej. Ta metoda zwraca `NULL` ma przycisku nadrzędny ma ramki listy rozwijanej lub przycisk nadrzędny nie ma nadrzędny paska menu.  
  
##  <a name="getparentpopupmenu"></a>CMFCDropDownFrame::GetParentPopupMenu  
 Pobiera menu podręczne nadrzędnego ramki listy rozwijanej.  
  
```  
CMFCDropDownFrame* GetParentPopupMenu() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do menu rozwijanego nadrzędnego ramki listy rozwijanej lub `NULL` Jeśli ramki nie ma obiektu nadrzędnego.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda pobiera menu nadrzędnego przycisku nadrzędnej. Ta metoda zwraca `NULL` Jeśli ramki listy rozwijanej ma przycisku nadrzędnej lub przycisk nadrzędnego nie uzyskał menu nie nadrzędnej.  
  
##  <a name="recalclayout"></a>CMFCDropDownFrame::RecalcLayout  
 Zmienia położenie ramki listy rozwijanej.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`bNotify`|Nieużywane.|  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę, po utworzeniu ramki listy rozwijanej lub zmiany rozmiaru okna nadrzędnego. Ta metoda oblicza położenie i rozmiar ramki listy rozwijanej przy użyciu pozycji i rozmiaru okna nadrzędnego.  
  
##  <a name="setautodestroy"></a>CMFCDropDownFrame::SetAutoDestroy  
 Określa, czy okno podrzędne pasek narzędzi listy rozwijanej zostanie zniszczony automatycznie.  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bAutoDestroy`  
 `TRUE`Aby automatycznie zniszczyć okna narzędzi listy rozwijanej skojarzone; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bAutoDestroy` jest `TRUE`, a następnie `CMFCDropDownFrame` destruktora niszczy okno narzędzi listy rozwijanej skojarzone. Wartość domyślna to `TRUE`.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolbar — klasa](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [Klasa CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
