---
title: Klasa CMFCDropDownToolBar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b227f9d2fdd43b576f89b74f43e4cdce8476bf9
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692386"
---
# <a name="cmfcdropdowntoolbar-class"></a>Klasa CMFCDropDownToolBar
Pasek narzędzi, który pojawia się po naciśnięciu i przytrzymaniu przycisku paska narzędzi najwyższego poziomu.  
  
   Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.  
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
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Przesłania [CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md).|  
  
### <a name="remarks"></a>Uwagi  
 Element `CMFCDropDownToolBar` obiektu łączy wygląd paska narzędzi z zachowaniem menu podręcznego. Po naciśnięciu i przytrzymaniu przycisku paska narzędzi z listy rozwijanej (zobacz [klasa CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), zostanie wyświetlony pasek narzędzi listy rozwijanej i użytkownik może wybrać przycisk na pasku narzędzi listy rozwijanej, przewijania do niego i zwolnieniem przycisku myszy przycisk. Po użytkownik wybierze przycisk na pasku narzędzi listy rozwijanej, ten przycisk jest wyświetlana jako bieżący przycisk na pasku narzędzi najwyższego poziomu.  
  
 Rozwijany pasek narzędzi nie może zostać dostosowany lub zadokowane, a nie ma stanu odrywania.  
  
 Poniższa ilustracja przedstawia `CMFCDropDownToolBar` obiektu:  
  
 ![Przykład CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "cmfcdropdown")  
  
 Możesz utworzyć `CMFCDropDownToolBar` obiektu taki sam sposób utworzyć zwykłej paska narzędzi (zobacz [klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)).  
  
 Aby wstawić rozwijany pasek narzędzi do narzędzi nadrzędnego:  
  
 1. Zarezerwuj identyfikator zasobu fikcyjnego przycisku w nadrzędnej zasób paska narzędzi.  
  
 2. Tworzenie `CMFCDropDownToolBarButton` obiekt, który zawiera rozwijany pasek narzędzi (Aby uzyskać więcej informacji, zobacz [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).  
  
 3. Zamień zastępczy button z `CMFCDropDownToolBarButton` obiektu za pomocą [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Aby uzyskać więcej informacji na temat przycisków paska narzędzi, zobacz [wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md). Aby uzyskać przykład rozwijany pasek narzędzi zobacz przykładowy projekt VisualStudioDemo.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób użycia `Create` method in Class metoda `CMFCDropDownToolBar` klasy. Ten fragment kodu jest częścią [Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdropdowntoolbar.h  
  
##  <a name="allowshowonpanemenu"></a>  CMFCDropDownToolBar::AllowShowOnPaneMenu  

  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="loadbitmap"></a>  CMFCDropDownToolBar::LoadBitmap  
 Wczytuje obrazy paska narzędzi z zasobów aplikacji.  
  
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
 [in] *uiResID*  
 Identyfikator zasobu mapy bitowej, która odwołuje się do gorąca paska narzędzi obrazów.  
  
 [in] *uiColdResID*  
 Identyfikator zasobu mapy bitowej, która odwołuje się do zimnej paska narzędzi obrazów.  
  
 [in] *uiMenuResID*  
 Identyfikator zasobu mapy bitowej, która odwołuje się do obrazów regularne menu.  
  
 [in] *zablokowane*  
 Wartość TRUE, aby zablokować narzędzi; w przeciwnym razie wartość FALSE.  
  
 [in] *uiDisabledResID*  
 Identyfikator zasobu mapy bitowej, która odwołuje się do wyłączonego paska narzędzi obrazów.  
  
 [in] *uiMenuDisabledResID*  
 Identyfikator zasobu mapy bitowej, która odwołuje się do obrazów menu wyłączone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli metoda się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) metoda wywołuje tę metodę, aby załadować obrazy, które są skojarzone z paska narzędzi. Zastępuje tę metodę do wykonywania niestandardowych ładowanie zasobów obrazu.  
  
 Wywołaj `LoadBitmapEx` metodę, aby załadować dodatkowe obrazy, po utworzeniu paska narzędzi.  
  
##  <a name="loadtoolbar"></a>  CMFCDropDownToolBar::LoadToolBar  

  
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
 [in] *uiResID*  
 [in] *uiColdResID*  
 [in] *uiMenuResID*  
 [in] *BOOL*  
 [in] *uiDisabledResID*  
 [in] *uiMenuDisabledResID*  
 [in] *uiHotResID*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onlbuttonup"></a>  CMFCDropDownToolBar::OnLButtonUp  

  
```  
afx_msg void OnLButtonUp(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nFlags*  
 [in] *punktu*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onmousemove"></a>  CMFCDropDownToolBar::OnMouseMove  

  
```  
afx_msg void OnMouseMove(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nFlags*  
 [in] *punktu*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onsendcommand"></a>  CMFCDropDownToolBar::OnSendCommand  

  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pButton*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onupdatecmdui"></a>  CMFCDropDownToolBar::OnUpdateCmdUI  

  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pTarget*  
 [in] *bDisableIfNoHndler*  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Klasa CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)   
 [Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)



