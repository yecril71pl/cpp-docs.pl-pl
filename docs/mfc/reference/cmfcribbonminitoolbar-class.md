---
title: Klasa CMFCRibbonMiniToolBar | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonMiniToolBar [MFC], IsContextMenuMode
- CMFCRibbonMiniToolBar [MFC], IsRibbonMiniToolBar
- CMFCRibbonMiniToolBar [MFC], SetCommands
- CMFCRibbonMiniToolBar [MFC], Show
- CMFCRibbonMiniToolBar [MFC], ShowWithContextMenu
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 62a2006423f8e6196f9fac4d8f336ced8b5416f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonminitoolbar-class"></a>Klasa CMFCRibbonMiniToolBar
Implementuje kontekstowe podręcznego paska narzędzi.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|Domyślny konstruktor.|  
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CMFCRibbonMiniToolBar::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||  
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|(Przesłania `CMFCPopupMenu::IsRibbonMiniToolBar`.)|  
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|Ustawia listę poleceń, który będzie wyświetlany na pasku narzędzi.|  
|[CMFCRibbonMiniToolBar::Show](#show)|Wyświetla współrzędne ekranu podręcznego paska narzędzi.|  
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|Wyświetla podręczny pasek narzędzi wraz z menu kontekstowego.|  
  
## <a name="remarks"></a>Uwagi  
 Podręczny pasek narzędzi jest zwykle wyświetlany po użytkownik wybierze obiekt w dokumencie. Na przykład po wybraniu bloku tekstu w edytorze tekstu, aplikacja wyświetla podręczny pasek narzędzi, który zawiera polecenia formatowania tekstu.  
  
 Przezroczysty podręczny pasek narzędzi, gdy wskaźnik myszy znajduje się poza granicami podręczny pasek narzędzi.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cframewnd —](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 `CMFCRibbonPanelMenu`  
  
 [CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxRibbonMiniToolBar.h  
  
##  <a name="setcommands"></a>CMFCRibbonMiniToolBar::SetCommands  
 Ustawia listę poleceń, który będzie wyświetlany na pasku narzędzi.  
  
```  
void SetCommands(
    CMFCRibbonBar* pRibbonBar,  
    const CList<UINT,UINT>& lstCommands);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pRibbonBar`  
 Na pasku wstążki, wyszukująca w przypadku przycisków wyświetlić podręczny pasek narzędzi.  
  
 [in]`lstCommands`  
 Listę poleceń, który będzie wyświetlany na podręczny pasek narzędzi. Aby znaleźć skojarzone przycisków przeszukiwane są wszystkie kategorie wstążki.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji, aby ustawić listę poleceń, które mają być wyświetlane w podręczny pasek narzędzi.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `SetCommands` metody `CMFCRibbonMiniToolBar` klasy. Następujący fragment kodu jest częścią [próbka MS Office 2007 Demo](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]  
  
##  <a name="show"></a>CMFCRibbonMiniToolBar::Show  
 Wyświetla współrzędne ekranu podręcznego paska narzędzi.  
  
```  
BOOL Show(
    int x,  
    int y);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`x`  
 Określa położenie paska we współrzędnych ekranu.  
  
 [in]`y`  
 Określa położenie w pionie podręczny pasek narzędzi we współrzędnych ekranu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli podręczny pasek narzędzi został wyświetlony pomyślnie; w przeciwnym razie `FALSE`.  
  
##  <a name="showwithcontextmenu"></a>CMFCRibbonMiniToolBar::ShowWithContextMenu  
 Wyświetla podręczny pasek narzędzi wraz z menu kontekstowego.  
  
```  
BOOL ShowWithContextMenu(
    int x,  
    int y,  
    UINT uiMenuResID,  
    CWnd* pWndOwner);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`x`  
 Określa położenie menu kontekstowe we współrzędnych ekranu.  
  
 [in]`y`  
 Określa położenie w pionie menu kontekstowe we współrzędnych ekranu.  
  
 [in]`uiMenuResID`  
 Określa identyfikator zasobu menu kontekstowe do wyświetlenia.  
  
 [in]`pWndOwner`  
 Określa okno, który odbiera komunikaty z menu kontekstowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli menu kontekstowe został wyświetlony pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do wyświetlenia podręczny pasek narzędzi, z menu kontekstowego. Menu kontekstowe jest rozmieszczanych 15 pikseli poniżej paska.  
  
##  <a name="iscontextmenumode"></a>CMFCRibbonMiniToolBar::IsContextMenuMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsContextMenuMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isribbonminitoolbar"></a>CMFCRibbonMiniToolBar::IsRibbonMiniToolBar  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsRibbonMiniToolBar() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
