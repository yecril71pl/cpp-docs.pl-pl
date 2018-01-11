---
title: Klasa CMultiPaneFrameWnd | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddRecentPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustPaneFrames
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CalcExpectedDockedRect
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeAttached
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeDockedToPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CheckGripperVisibility
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CloseMiniFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ConvertToTabbedDocument
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockRecentPaneToMainFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetCaptionText
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneContainerManager
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetFirstVisiblePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetVisiblePaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::InsertPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::LoadState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnDockToRecentPos
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnKillRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnPaneRecalcLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnSetRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnShowPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::PaneFromPoint
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemoveNonValidPanes
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemovePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ReplacePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SaveState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::Serialize
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetLastFocusedPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetPreDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentDockSiteInfo
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentTabRelatedInfo
dev_langs: C++
helpviewer_keywords:
- CMultiPaneFrameWnd [MFC], AddPane
- CMultiPaneFrameWnd [MFC], AddRecentPane
- CMultiPaneFrameWnd [MFC], AdjustLayout
- CMultiPaneFrameWnd [MFC], AdjustPaneFrames
- CMultiPaneFrameWnd [MFC], CalcExpectedDockedRect
- CMultiPaneFrameWnd [MFC], CanBeAttached
- CMultiPaneFrameWnd [MFC], CanBeDockedToPane
- CMultiPaneFrameWnd [MFC], CheckGripperVisibility
- CMultiPaneFrameWnd [MFC], CloseMiniFrame
- CMultiPaneFrameWnd [MFC], ConvertToTabbedDocument
- CMultiPaneFrameWnd [MFC], DockFrame
- CMultiPaneFrameWnd [MFC], DockPane
- CMultiPaneFrameWnd [MFC], DockRecentPaneToMainFrame
- CMultiPaneFrameWnd [MFC], GetCaptionText
- CMultiPaneFrameWnd [MFC], GetPaneContainerManager
- CMultiPaneFrameWnd [MFC], GetFirstVisiblePane
- CMultiPaneFrameWnd [MFC], GetPane
- CMultiPaneFrameWnd [MFC], GetPaneCount
- CMultiPaneFrameWnd [MFC], GetVisiblePaneCount
- CMultiPaneFrameWnd [MFC], InsertPane
- CMultiPaneFrameWnd [MFC], LoadState
- CMultiPaneFrameWnd [MFC], OnDockToRecentPos
- CMultiPaneFrameWnd [MFC], OnKillRollUpTimer
- CMultiPaneFrameWnd [MFC], OnPaneRecalcLayout
- CMultiPaneFrameWnd [MFC], OnSetRollUpTimer
- CMultiPaneFrameWnd [MFC], OnShowPane
- CMultiPaneFrameWnd [MFC], PaneFromPoint
- CMultiPaneFrameWnd [MFC], RemoveNonValidPanes
- CMultiPaneFrameWnd [MFC], RemovePane
- CMultiPaneFrameWnd [MFC], ReplacePane
- CMultiPaneFrameWnd [MFC], SaveState
- CMultiPaneFrameWnd [MFC], Serialize
- CMultiPaneFrameWnd [MFC], SetDockState
- CMultiPaneFrameWnd [MFC], SetLastFocusedPane
- CMultiPaneFrameWnd [MFC], SetPreDockState
- CMultiPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CMultiPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
ms.assetid: 989a548e-0d70-46b7-a513-8cf740e1be3e
caps.latest.revision: "36"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed8ccb584b9bf750e1f17da9ce3e0bf71058abbc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmultipaneframewnd-class"></a>Klasa CMultiPaneFrameWnd
`CMultiPaneFrameWnd` Rozszerza klasy [CPaneFrameWnd klasy](../../mfc/reference/cpaneframewnd-class.md). Może obsługiwać wiele okienek. Zamiast pojedynczego osadzonych dojścia do pasek sterowania `CMultiPaneFrameWnd` zawiera [klasy CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md) obiekt, który umożliwia użytkownikowi dock jedną `CMultiPaneFrameWnd` na inny i dynamicznie utworzyć wiele przestawne, z kartami systemu Windows.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMultiPaneFrameWnd : public CPaneFrameWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMultiPaneFrameWnd::AddPane](#addpane)|Dodaje okienko. (Przesłania [CPaneFrameWnd::AddPane](../../mfc/reference/cpaneframewnd-class.md#addpane).)|  
|[CMultiPaneFrameWnd::AddRecentPane](#addrecentpane)||  
|[CMultiPaneFrameWnd::AdjustLayout](#adjustlayout)|Dostosowuje układ okno ramowe minimalnej. (Przesłania [CPaneFrameWnd::AdjustLayout](../../mfc/reference/cpaneframewnd-class.md#adjustlayout).)|  
|[CMultiPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)|(Przesłania [CPaneFrameWnd::AdjustPaneFrames](../../mfc/reference/cpaneframewnd-class.md#adjustpaneframes).)|  
|[CMultiPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Oblicza oczekiwanego prostokąt zadokowanych okien. (Przesłania [CPaneFrameWnd::CalcExpectedDockedRect](../../mfc/reference/cpaneframewnd-class.md#calcexpecteddockedrect).)|  
|[CMultiPaneFrameWnd::CanBeAttached](#canbeattached)|Określa, czy bieżące okienko dokowany do innego okienka lub ramki okna. (Przesłania [CPaneFrameWnd::CanBeAttached](../../mfc/reference/cpaneframewnd-class.md#canbeattached).)|  
|[CMultiPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Określa, czy okno ramowe mini dokowany do okienka. (Przesłania [CPaneFrameWnd::CanBeDockedToPane](../../mfc/reference/cpaneframewnd-class.md#canbedockedtopane).)|  
|[CMultiPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)|(Przesłania [CPaneFrameWnd::CheckGripperVisibility](../../mfc/reference/cpaneframewnd-class.md#checkgrippervisibility).)|  
|[CMultiPaneFrameWnd::CloseMiniFrame](#closeminiframe)|(Przesłania `CPaneFrameWnd::CloseMiniFrame`.)|  
|[CMultiPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|Konwertuje dokument z kartami okienka. (Przesłania [CPaneFrameWnd::ConvertToTabbedDocument](../../mfc/reference/cpaneframewnd-class.md#converttotabbeddocument).)|  
|[CMultiPaneFrameWnd::DockFrame](#dockframe)||  
|[CMultiPaneFrameWnd::DockPane](#dockpane)|Stacje dokujące okienko. (Przesłania [CPaneFrameWnd::DockPane](../../mfc/reference/cpaneframewnd-class.md#dockpane).)|  
|[CMultiPaneFrameWnd::DockRecentPaneToMainFrame](#dockrecentpanetomainframe)||  
|[CMultiPaneFrameWnd::GetCaptionText](#getcaptiontext)|Zwraca tekst podpisu. (Przesłania [CPaneFrameWnd::GetCaptionText](../../mfc/reference/cpaneframewnd-class.md#getcaptiontext).)|  
|[CMultiPaneFrameWnd::GetPaneContainerManager](#getpanecontainermanager)|Zwraca odwołanie do kontenera wewnętrzny obiekt menedżera.|  
|[CMultiPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Zwraca pierwszy widoczne okienko zawarte w oknie ramowym minimalnej. (Przesłania [CPaneFrameWnd::GetFirstVisiblePane](../../mfc/reference/cpaneframewnd-class.md#getfirstvisiblepane).)|  
|[CMultiPaneFrameWnd::GetPane](#getpane)|Zwraca okienko, w którym znajduje się w oknie ramowym minimalnej. (Przesłania [CPaneFrameWnd::GetPane](../../mfc/reference/cpaneframewnd-class.md#getpane).)|  
|[CMultiPaneFrameWnd::GetPaneCount](#getpanecount)|Zwraca liczbę okienka, które są zawarte w oknie ramowym minimalnej. (Przesłania [CPaneFrameWnd::GetPaneCount](../../mfc/reference/cpaneframewnd-class.md#getpanecount).)|  
|[CMultiPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Zwraca liczbę widoczne okienka, które są zawarte w oknie ramowym minimalnej. (Przesłania [CPaneFrameWnd::GetVisiblePaneCount](../../mfc/reference/cpaneframewnd-class.md#getvisiblepanecount).)|  
|[CMultiPaneFrameWnd::InsertPane](#insertpane)||  
|[CMultiPaneFrameWnd::LoadState](#loadstate)|Ładuje stan okienka z rejestru. (Przesłania [CPaneFrameWnd::LoadState](../../mfc/reference/cpaneframewnd-class.md#loadstate).)|  
|[CMultiPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Stacje dokujące okno ramowe minimalnej na jego ostatniej pozycji. (Przesłania [CPaneFrameWnd::OnDockToRecentPos](../../mfc/reference/cpaneframewnd-class.md#ondocktorecentpos).)|  
|[CMultiPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Zatrzymuje czasomierza rollup. (Przesłania [CPaneFrameWnd::OnKillRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onkillrolluptimer).)|  
|[CMultiPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Dostosowuje układ okienka w oknie ramowym minimalnej. (Przesłania [CPaneFrameWnd::OnPaneRecalcLayout](../../mfc/reference/cpaneframewnd-class.md#onpanerecalclayout).)|  
|[CMultiPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Ustawia czasomierza rollup. (Przesłania [CPaneFrameWnd::OnSetRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onsetrolluptimer).)|  
|[CMultiPaneFrameWnd::OnShowPane](#onshowpane)|Wywoływane przez platformę, gdy okienka w oknie ramowym mini jest ukryte lub wyświetlane. (Przesłania [CPaneFrameWnd::OnShowPane](../../mfc/reference/cpaneframewnd-class.md#onshowpane).)|  
|[CMultiPaneFrameWnd::PaneFromPoint](#panefrompoint)|Zwraca okienko, jeśli zawiera ona punkt dostarczone przez użytkownika w oknie ramowym minimalnej. (Przesłania [CPaneFrameWnd::PaneFromPoint](../../mfc/reference/cpaneframewnd-class.md#panefrompoint).)|  
|[CMultiPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Wywoływane przez platformę, by usunąć okienka nie jest ważna. (Przesłania [CPaneFrameWnd::RemoveNonValidPanes](../../mfc/reference/cpaneframewnd-class.md#removenonvalidpanes).)|  
|[CMultiPaneFrameWnd::RemovePane](#removepane)|Usuwa okienko z okna mini ramki. (Przesłania [CPaneFrameWnd::RemovePane](../../mfc/reference/cpaneframewnd-class.md#removepane).)|  
|[CMultiPaneFrameWnd::ReplacePane](#replacepane)|Zastępuje jedno okienko na inny. (Przesłania [CPaneFrameWnd::ReplacePane](../../mfc/reference/cpaneframewnd-class.md#replacepane).)|  
|[CMultiPaneFrameWnd::SaveState](#savestate)|Zapisuje stan okienka w rejestrze. (Przesłania [CPaneFrameWnd::SaveState](../../mfc/reference/cpaneframewnd-class.md#savestate).)|  
|[CMultiPaneFrameWnd::Serialize](#serialize)|(Przesłania `CPaneFrameWnd::Serialize`.)|  
|[CMultiPaneFrameWnd::SetDockState](#setdockstate)|Ustawia stan dokowania. (Przesłania [CPaneFrameWnd::SetDockState](../../mfc/reference/cpaneframewnd-class.md#setdockstate).)|  
|[CMultiPaneFrameWnd::SetLastFocusedPane](#setlastfocusedpane)||  
|[CMultiPaneFrameWnd::SetPreDockState](#setpredockstate)|Ustawia stan predocking. (Przesłania [CPaneFrameWnd::SetPreDockState](../../mfc/reference/cpaneframewnd-class.md#setpredockstate).)|  
|[CMultiPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)|(Przesłania [CPaneFrameWnd::StoreRecentDockSiteInfo](../../mfc/reference/cpaneframewnd-class.md#storerecentdocksiteinfo).)|  
|[CMultiPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)|(Przesłania [CPaneFrameWnd::StoreRecentTabRelatedInfo](../../mfc/reference/cpaneframewnd-class.md#storerecenttabrelatedinfo).)|  
  
## <a name="remarks"></a>Uwagi  
 Większość metody tej klasy Przesłaniaj metody w [klasy CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) klasy.  
  
 Jeśli okienko używa `AFX_CBRS_AUTO_ROLLUP` styl i użytkownik stacje dokujące okienka okna wielu okienka ramki, użytkownik może zbiorczy okna niezależnie od ustawień stylu innych zadokowanych paneli.  
  
 Tworzy automatycznie w ramach `CMultiPaneFrameWnd` obiektu, gdy użytkownik pojawia się okienko, która używa `CBRS_FLOAT_MULTI` stylu.  
  
 Aby uzyskać informacje na temat wyprowadzanie klasy z `CPaneFrameWnd` klasy i tworzenie dynamicznie, zobacz [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak pobrać wskaźnik do `CMultiPaneFrameWnd` obiektu. Następujący fragment kodu jest częścią [próbki Ustaw rozmiar okienka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_SetPaneSize#4](../../mfc/reference/codesnippet/cpp/cmultipaneframewnd-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)  
  
 [CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxMultiPaneFrameWnd.h  
  
##  <a name="addpane"></a>CMultiPaneFrameWnd::AddPane  

  
```  
virtual void AddPane(CBasePane* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="addrecentpane"></a>CMultiPaneFrameWnd::AddRecentPane  

  
```  
virtual BOOL AddRecentPane(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="adjustlayout"></a>CMultiPaneFrameWnd::AdjustLayout  

  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="adjustpaneframes"></a>CMultiPaneFrameWnd::AdjustPaneFrames  

  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="calcexpecteddockedrect"></a>CMultiPaneFrameWnd::CalcExpectedDockedRect  

  
```  
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,  
    CPoint ptMouse,  
    CRect& rectResult,  
    BOOL& bDrawTab,  
    CDockablePane** ppTargetBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWndToDock`  
 [in]`ptMouse`  
 [in]`rectResult`  
 [in]`bDrawTab`  
 [in]`ppTargetBar`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="canbeattached"></a>CMultiPaneFrameWnd::CanBeAttached  

  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="canbedockedtopane"></a>CMultiPaneFrameWnd::CanBeDockedToPane  

  
```  
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDockingBar`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="checkgrippervisibility"></a>CMultiPaneFrameWnd::CheckGripperVisibility  

  
```  
virtual void CheckGripperVisibility();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="closeminiframe"></a>CMultiPaneFrameWnd::CloseMiniFrame  

  
```  
virtual void CloseMiniFrame();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="converttotabbeddocument"></a>CMultiPaneFrameWnd::ConvertToTabbedDocument  

  
```  
virtual void ConvertToTabbedDocument();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="dockframe"></a>CMultiPaneFrameWnd::DockFrame  

  
```  
virtual BOOL DockFrame(
    CPaneFrameWnd* pDockedFrame,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDockedFrame`  
 [in]`dockMethod`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="dockpane"></a>CMultiPaneFrameWnd::DockPane  

  
```  
virtual BOOL DockPane(CDockablePane* pDockedBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDockedBar`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="dockrecentpanetomainframe"></a>CMultiPaneFrameWnd::DockRecentPaneToMainFrame  

  
```  
virtual void DockRecentPaneToMainFrame(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcaptiontext"></a>CMultiPaneFrameWnd::GetCaptionText  

  
```  
virtual CString GetCaptionText();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getfirstvisiblepane"></a>CMultiPaneFrameWnd::GetFirstVisiblePane  

  
```  
virtual CWnd* GetFirstVisiblePane() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getpane"></a>CMultiPaneFrameWnd::GetPane  

  
```  
virtual CWnd* GetPane() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getpanecontainermanager"></a>CMultiPaneFrameWnd::GetPaneContainerManager  
 Zwraca odwołanie do kontenera wewnętrzny obiekt menedżera.  
  
```  
CPaneContainerManager& GetPaneContainerManager();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do kontenera wewnętrzny obiekt menedżera.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia dostęp do wewnętrznego [klasy CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md) obiektu.  
  
##  <a name="getpanecount"></a>CMultiPaneFrameWnd::GetPaneCount  

  
```  
virtual int GetPaneCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getvisiblepanecount"></a>CMultiPaneFrameWnd::GetVisiblePaneCount  

  
```  
virtual int GetVisiblePaneCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="insertpane"></a>CMultiPaneFrameWnd::InsertPane  

  
```  
virtual BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pControlBar`  
 [in]`pTarget`  
 [in]`bAfter`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="loadstate"></a>CMultiPaneFrameWnd::LoadState  

  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 [in]`uiID`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondocktorecentpos"></a>CMultiPaneFrameWnd::OnDockToRecentPos  

  
```  
virtual void OnDockToRecentPos();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onkillrolluptimer"></a>CMultiPaneFrameWnd::OnKillRollUpTimer  

  
```  
virtual void OnKillRollUpTimer();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onpanerecalclayout"></a>CMultiPaneFrameWnd::OnPaneRecalcLayout  

  
```  
virtual void OnPaneRecalcLayout();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onsetrolluptimer"></a>CMultiPaneFrameWnd::OnSetRollUpTimer  

  
```  
virtual void OnSetRollUpTimer();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onshowpane"></a>CMultiPaneFrameWnd::OnShowPane  

  
```  
virtual void OnShowPane(
    CDockablePane* pBar,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
 [in]`bShow`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="panefrompoint"></a>CMultiPaneFrameWnd::PaneFromPoint  

  
```  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    BOOL bCheckVisibility);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`point`  
 [in]`nSensitivity`  
 [in]`bCheckVisibility`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="removenonvalidpanes"></a>CMultiPaneFrameWnd::RemoveNonValidPanes  

  
```  
virtual void RemoveNonValidPanes();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="removepane"></a>CMultiPaneFrameWnd::RemovePane  

  
```  
virtual void RemovePane(
    CBasePane* pBar,  
    BOOL bDestroy = FALSE,  
    BOOL bNoDelayedDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
 [in]`bDestroy`  
 [in]`bNoDelayedDestroy`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="replacepane"></a>CMultiPaneFrameWnd::ReplacePane  

  
```  
virtual void ReplacePane(
    CBasePane* pBarOrg,  
    CBasePane* pBarReplaceWith);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBarOrg`  
 [in]`pBarReplaceWith`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="savestate"></a>CMultiPaneFrameWnd::SaveState  

  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 [in]`uiID`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="serialize"></a>CMultiPaneFrameWnd::Serialize  

  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`ar`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setdockstate"></a>CMultiPaneFrameWnd::SetDockState  

  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDockManager`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setlastfocusedpane"></a>CMultiPaneFrameWnd::SetLastFocusedPane  

  
```  
void SetLastFocusedPane(HWND hwnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`hwnd`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpredockstate"></a>CMultiPaneFrameWnd::SetPreDockState  

  
```  
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,  
    CBasePane* pBarToDock = NULL,  
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`preDockState`  
 [in]`pBarToDock`  
 [in]`dockMethod`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="storerecentdocksiteinfo"></a>CMultiPaneFrameWnd::StoreRecentDockSiteInfo  

  
```  
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="storerecenttabrelatedinfo"></a>CMultiPaneFrameWnd::StoreRecentTabRelatedInfo  

  
```  
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,  
    CDockablePane* pTabbedBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDockingBar`  
 [in]`pTabbedBar`  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)
