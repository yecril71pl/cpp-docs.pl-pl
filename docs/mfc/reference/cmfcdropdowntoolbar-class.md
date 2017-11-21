---
title: "Klasa CMFCDropDownToolbar — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
dev_langs: C++
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
caps.latest.revision: "37"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 50ecdd614aaf3bd81817ff81a68818b6816c9a71
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolbar — klasa
Pasek narzędzi, który jest wyświetlany, gdy użytkownik naciśnie i przechowuje przycisku paska narzędzi najwyższego poziomu.  
  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCDropDownToolBar : public CMFCToolBar  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Przesłania `CPane::AllowShowOnPaneMenu`.)|  
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Przesłania [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|  
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Przesłania [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|  
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||  
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||  
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Przesłania `CMFCToolBar::OnSendCommand`.)|  
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Przesłania [CMFCToolBar::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/571a38ab-2a56-4968-9796-273516126f80).)|  
  
### <a name="remarks"></a>Uwagi  
 A `CMFCDropDownToolBar` obiektu łączy wygląd paska narzędzi z zachowaniem menu podręcznego. Gdy użytkownik naciśnie i przechowuje przycisku paska narzędzi z listy rozwijanej (zobacz [klasy CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), zostanie wyświetlony pasek narzędzi listy rozwijanej, a użytkownik może wybrać przycisk paska narzędzi listy rozwijanej przewijanie do niego i zwolnieniem przycisku myszy przycisk. Po użytkownik wybierze przycisk na pasku narzędzi z listy rozwijanej, ten przycisk jest wyświetlany jako przycisk bieżącego na pasku narzędzi najwyższego poziomu.  
  
 Nie można dostosować lub zadokowany pasek narzędzi listy rozwijanej, a nie ma stanu oderwania.  
  
 Na poniższej ilustracji pokazano `CMFCDropDownToolBar` obiektu:  
  
 ![Przykład CMFCDropDownToolbar —](../../mfc/reference/media/cmfcdropdown.png "cmfcdropdown")  
  
 Możesz utworzyć `CMFCDropDownToolBar` obiekt ten sam sposób utworzyć zwykłej paska narzędzi (zobacz [CMFCToolBar klasy](../../mfc/reference/cmfctoolbar-class.md)).  
  
 Aby wstawić pasek narzędzi listy rozwijanej do narzędzi nadrzędnej:  
  
 1. Zarezerwować Identyfikatora fikcyjnego zasobu dla przycisku w zasobie nadrzędnym paska narzędzi.  
  
 2. Utwórz `CMFCDropDownToolBarButton` obiekt, który zawiera pasek narzędzi listy rozwijanej (Aby uzyskać więcej informacji, zobacz [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).  
  
 3. Zastąp fikcyjny przycisk z `CMFCDropDownToolBarButton` obiektu za pomocą [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Aby uzyskać więcej informacji na temat przycisków paska narzędzi, zobacz [wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md). Na przykład pasek narzędzi listy rozwijanej zobacz przykładowy projekt VisualStudioDemo.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `Create` metoda `CMFCDropDownToolBar` klasy. Następujący fragment kodu jest częścią [programu Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCDropDownToolbar —](../../mfc/reference/cmfcdropdowntoolbar-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdropdowntoolbar.h  
  
##  <a name="allowshowonpanemenu"></a>CMFCDropDownToolBar::AllowShowOnPaneMenu  

  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="loadbitmap"></a>CMFCDropDownToolBar::LoadBitmap  
 Ładuje obrazy pasków narzędzi z zasobów aplikacji.  
  
```  
virtual BOOL LoadBitmap(
    UINT uiResID,  
    UINT uiColdResID=0,  
    UINT uiMenuResID=0,  
    BOOL bLocked=FALSE,  
    UINT uiDisabledResID=0,  
    UINT uiMenuDisabledResID=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiResID`  
 Identyfikator zasobu mapy bitowej, która odwołuje się do obrazów gorących paska narzędzi.  
  
 [in]`uiColdResID`  
 Identyfikator zasobu mapy bitowej, która odwołuje się do obrazów zimnych paska narzędzi.  
  
 [in]`uiMenuResID`  
 Identyfikator zasobu mapy bitowej, która odwołuje się do obrazów regularne menu.  
  
 [in]`bLocked`  
 `TRUE`Aby zablokować narzędzi; w przeciwnym razie `FALSE`.  
  
 [in]`uiDisabledResID`  
 Identyfikator zasobu mapy bitowej, która odwołuje się do obrazów wyłączonego paska narzędzi.  
  
 [in]`uiMenuDisabledResID`  
 Identyfikator zasobu mapy bitowej, która odwołuje się do obrazów menu wyłączone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) metoda wywołuje tę metodę, aby załadować obrazów, które są skojarzone z paska narzędzi. Zastępuje tę metodę do wykonania niestandardowej ładowanie zasobów obrazu.  
  
 Wywołanie `LoadBitmapEx` metodę, aby załadować dodatkowe obrazy po utworzeniu paska narzędzi.  
  
##  <a name="loadtoolbar"></a>CMFCDropDownToolBar::LoadToolBar  

  
```  
virtual BOOL LoadToolBar(
    UINT uiResID,  
    UINT uiColdResID = 0,  
    UINT uiMenuResID = 0,
    BOOL = FALSE,  
    UINT uiDisabledResID = 0,  
    UINT uiMenuDisabledResID = 0,  
    UINT uiHotResID = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiResID`  
 [in]`uiColdResID`  
 [in]`uiMenuResID`  
 [in]`BOOL`  
 [in]`uiDisabledResID`  
 [in]`uiMenuDisabledResID`  
 [in]`uiHotResID`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onlbuttonup"></a>CMFCDropDownToolBar::OnLButtonUp  

  
```  
afx_msg void OnLButtonUp(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nFlags`  
 [in]`point`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onmousemove"></a>CMFCDropDownToolBar::OnMouseMove  

  
```  
afx_msg void OnMouseMove(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nFlags`  
 [in]`point`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onsendcommand"></a>CMFCDropDownToolBar::OnSendCommand  

  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pButton`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onupdatecmdui"></a>CMFCDropDownToolBar::OnUpdateCmdUI  

  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pTarget`  
 [in]`bDisableIfNoHndler`  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Klasa CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)   
 [Wskazówki: Umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)



