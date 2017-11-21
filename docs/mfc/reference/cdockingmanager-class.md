---
title: Klasa CDockingManager | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockingManager
- AFXDOCKINGMANAGER/CDockingManager
- AFXDOCKINGMANAGER/CDockingManager::AddDockSite
- AFXDOCKINGMANAGER/CDockingManager::AddHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::AddMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::AddPane
- AFXDOCKINGMANAGER/CDockingManager::AdjustDockingLayout
- AFXDOCKINGMANAGER/CDockingManager::AdjustPaneFrames
- AFXDOCKINGMANAGER/CDockingManager::AdjustRectToClientArea
- AFXDOCKINGMANAGER/CDockingManager::AlignAutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::AutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::BringBarsToTop
- AFXDOCKINGMANAGER/CDockingManager::BuildPanesMenu
- AFXDOCKINGMANAGER/CDockingManager::CalcExpectedDockedRect
- AFXDOCKINGMANAGER/CDockingManager::Create
- AFXDOCKINGMANAGER/CDockingManager::DeterminePaneAndStatus
- AFXDOCKINGMANAGER/CDockingManager::DisableRestoreDockState
- AFXDOCKINGMANAGER/CDockingManager::DockPane
- AFXDOCKINGMANAGER/CDockingManager::DockPaneLeftOf
- AFXDOCKINGMANAGER/CDockingManager::EnableAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::EnableDocking
- AFXDOCKINGMANAGER/CDockingManager::EnableDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::EnablePaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::FindDockSite
- AFXDOCKINGMANAGER/CDockingManager::FindDockSiteByPane
- AFXDOCKINGMANAGER/CDockingManager::FindPaneByID
- AFXDOCKINGMANAGER/CDockingManager::FixupVirtualRects
- AFXDOCKINGMANAGER/CDockingManager::FrameFromPoint
- AFXDOCKINGMANAGER/CDockingManager::GetClientAreaBounds
- AFXDOCKINGMANAGER/CDockingManager::GetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::GetDockSiteFrameWnd
- AFXDOCKINGMANAGER/CDockingManager::GetEnabledAutoHideAlignment
- AFXDOCKINGMANAGER/CDockingManager::GetMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::GetOuterEdgeBounds
- AFXDOCKINGMANAGER/CDockingManager::GetPaneList
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManager
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManagerPermanent
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingTheme
- AFXDOCKINGMANAGER/CDockingManager::HideAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::InsertDockSite
- AFXDOCKINGMANAGER/CDockingManager::InsertPane
- AFXDOCKINGMANAGER/CDockingManager::IsDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::IsInAdjustLayout
- AFXDOCKINGMANAGER/CDockingManager::IsOLEContainerMode
- AFXDOCKINGMANAGER/CDockingManager::IsPointNearDockSite
- AFXDOCKINGMANAGER/CDockingManager::IsPrintPreviewValid
- AFXDOCKINGMANAGER/CDockingManager::LoadState
- AFXDOCKINGMANAGER/CDockingManager::LockUpdate
- AFXDOCKINGMANAGER/CDockingManager::OnActivateFrame
- AFXDOCKINGMANAGER/CDockingManager::OnClosePopupMenu
- AFXDOCKINGMANAGER/CDockingManager::OnMoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::OnPaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::PaneFromPoint
- AFXDOCKINGMANAGER/CDockingManager::ProcessPaneContextMenuCommand
- AFXDOCKINGMANAGER/CDockingManager::RecalcLayout
- AFXDOCKINGMANAGER/CDockingManager::ReleaseEmptyPaneContainers
- AFXDOCKINGMANAGER/CDockingManager::RemoveHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::RemoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::RemovePaneFromDockManager
- AFXDOCKINGMANAGER/CDockingManager::ReplacePane
- AFXDOCKINGMANAGER/CDockingManager::ResortMiniFramesForZOrder
- AFXDOCKINGMANAGER/CDockingManager::SaveState
- AFXDOCKINGMANAGER/CDockingManager::SendMessageToMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::Serialize
- AFXDOCKINGMANAGER/CDockingManager::SetAutohideZOrder
- AFXDOCKINGMANAGER/CDockingManager::SetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::SetDockState
- AFXDOCKINGMANAGER/CDockingManager::SetPrintPreviewMode
- AFXDOCKINGMANAGER/CDockingManager::SetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::ShowDelayShowMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::ShowPanes
- AFXDOCKINGMANAGER/CDockingManager::StartSDocking
- AFXDOCKINGMANAGER/CDockingManager::StopSDocking
- AFXDOCKINGMANAGER/CDockingManager::m_bHideDockingBarsInContainerMode
- AFXDOCKINGMANAGER/CDockingManager::m_dockModeGlobal
- AFXDOCKINGMANAGER/CDockingManager::m_nDockSensitivity
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeDockingBarDock
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeToolBarDock
dev_langs: C++
helpviewer_keywords:
- CDockingManager [MFC], AddDockSite
- CDockingManager [MFC], AddHiddenMDITabbedBar
- CDockingManager [MFC], AddMiniFrame
- CDockingManager [MFC], AddPane
- CDockingManager [MFC], AdjustDockingLayout
- CDockingManager [MFC], AdjustPaneFrames
- CDockingManager [MFC], AdjustRectToClientArea
- CDockingManager [MFC], AlignAutoHidePane
- CDockingManager [MFC], AutoHidePane
- CDockingManager [MFC], BringBarsToTop
- CDockingManager [MFC], BuildPanesMenu
- CDockingManager [MFC], CalcExpectedDockedRect
- CDockingManager [MFC], Create
- CDockingManager [MFC], DeterminePaneAndStatus
- CDockingManager [MFC], DisableRestoreDockState
- CDockingManager [MFC], DockPane
- CDockingManager [MFC], DockPaneLeftOf
- CDockingManager [MFC], EnableAutoHidePanes
- CDockingManager [MFC], EnableDocking
- CDockingManager [MFC], EnableDockSiteMenu
- CDockingManager [MFC], EnablePaneContextMenu
- CDockingManager [MFC], FindDockSite
- CDockingManager [MFC], FindDockSiteByPane
- CDockingManager [MFC], FindPaneByID
- CDockingManager [MFC], FixupVirtualRects
- CDockingManager [MFC], FrameFromPoint
- CDockingManager [MFC], GetClientAreaBounds
- CDockingManager [MFC], GetDockingMode
- CDockingManager [MFC], GetDockSiteFrameWnd
- CDockingManager [MFC], GetEnabledAutoHideAlignment
- CDockingManager [MFC], GetMiniFrames
- CDockingManager [MFC], GetOuterEdgeBounds
- CDockingManager [MFC], GetPaneList
- CDockingManager [MFC], GetSmartDockingManager
- CDockingManager [MFC], GetSmartDockingManagerPermanent
- CDockingManager [MFC], GetSmartDockingParams
- CDockingManager [MFC], GetSmartDockingTheme
- CDockingManager [MFC], HideAutoHidePanes
- CDockingManager [MFC], InsertDockSite
- CDockingManager [MFC], InsertPane
- CDockingManager [MFC], IsDockSiteMenu
- CDockingManager [MFC], IsInAdjustLayout
- CDockingManager [MFC], IsOLEContainerMode
- CDockingManager [MFC], IsPointNearDockSite
- CDockingManager [MFC], IsPrintPreviewValid
- CDockingManager [MFC], LoadState
- CDockingManager [MFC], LockUpdate
- CDockingManager [MFC], OnActivateFrame
- CDockingManager [MFC], OnClosePopupMenu
- CDockingManager [MFC], OnMoveMiniFrame
- CDockingManager [MFC], OnPaneContextMenu
- CDockingManager [MFC], PaneFromPoint
- CDockingManager [MFC], ProcessPaneContextMenuCommand
- CDockingManager [MFC], RecalcLayout
- CDockingManager [MFC], ReleaseEmptyPaneContainers
- CDockingManager [MFC], RemoveHiddenMDITabbedBar
- CDockingManager [MFC], RemoveMiniFrame
- CDockingManager [MFC], RemovePaneFromDockManager
- CDockingManager [MFC], ReplacePane
- CDockingManager [MFC], ResortMiniFramesForZOrder
- CDockingManager [MFC], SaveState
- CDockingManager [MFC], SendMessageToMiniFrames
- CDockingManager [MFC], Serialize
- CDockingManager [MFC], SetAutohideZOrder
- CDockingManager [MFC], SetDockingMode
- CDockingManager [MFC], SetDockState
- CDockingManager [MFC], SetPrintPreviewMode
- CDockingManager [MFC], SetSmartDockingParams
- CDockingManager [MFC], ShowDelayShowMiniFrames
- CDockingManager [MFC], ShowPanes
- CDockingManager [MFC], StartSDocking
- CDockingManager [MFC], StopSDocking
- CDockingManager [MFC], m_bHideDockingBarsInContainerMode
- CDockingManager [MFC], m_dockModeGlobal
- CDockingManager [MFC], m_nDockSensitivity
- CDockingManager [MFC], m_nTimeOutBeforeDockingBarDock
- CDockingManager [MFC], m_nTimeOutBeforeToolBarDock
ms.assetid: 98e69c43-55d8-4f43-b861-4fda80ec1e32
caps.latest.revision: "37"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a19688b10cb0e3b7966044c725cebb236ca30660
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdockingmanager-class"></a>Klasa CDockingManager
Implementuje kontrolujące dokowania układ główne okno ramowe podstawowych funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDockingManager : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDockingManager::AddDockSite](#adddocksite)|Tworzy okienka dokowania i dodaje go do listy paski sterowania.|  
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|Dodaje dojścia do paska okienko do listy ukrytych MDI kartach paska okienka.|  
|[CDockingManager::AddMiniFrame](#addminiframe)|Dodaje ramki do listy mini ramki.|  
|[CDockingManager::AddPane](#addpane)|Rejestruje okienko dokujące menedżera.|  
|[CDockingManager::AdjustDockingLayout](#adjustdockinglayout)|Ponownie oblicza i dostosowuje układ wszystkie okienka w oknie ramowym.|  
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|Powoduje, że `WM_NCCALCSIZE` komunikat do wysłania do wszystkich okienek i `CPaneFrameWnd` systemu windows.|  
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|Dopasowuje wyrównanie prostokąta.|  
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|Zmienia rozmiar okienko dokujące w trybie autohide — tak, aby zajmuje pełnej szerokości lub wysokości obszaru klienckiego ramki otoczona dock witryn.|  
|[CDockingManager::AutoHidePane](#autohidepane)|Tworzy automatycznie ukrywaj paska narzędzi.|  
|[CDockingManager::BringBarsToTop](#bringbarstotop)|Przełącza zadokowanych pasków, które mają określone wyrównanie do góry.|  
|[CDockingManager::BuildPanesMenu](#buildpanesmenu)|Dodaje nazwy dokowania okienka i paski narzędzi do menu.|  
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|Oblicza oczekiwanego prostokąt zadokowanych okien.|  
|[CDockingManager::Create](#create)|Tworzy Menedżera dokowania.|  
|[CDockingManager::DeterminePaneAndStatus](#determinepaneandstatus)|Określa okienka zawierającego danego punktu i jego stan dokowania.|  
|[CDockingManager::DisableRestoreDockState](#disablerestoredockstate)|Włącza lub wyłącza ładowania dokowania układu z rejestru.|  
|[CDockingManager::DockPane](#dockpane)|Stacje dokujące okienko do innego okienka lub ramki okna.|  
|[CDockingManager::DockPaneLeftOf](#dockpaneleftof)|Stacje dokujące okienko na lewo od innego okienka.|  
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|Włącza Dokowanie okienka do ramki głównej, tworzy okienku dokowania i dodaje go do listy paski sterowania.|  
|[CDockingManager::EnableDocking](#enabledocking)|Tworzy okienka dokowania i umożliwia Dokowanie okienka do ramki głównej.|  
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|Wyświetla dodatkowy przycisk otwiera menu podręczne na podpisy wszystkie okienka dokowania.|  
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|Określa, że biblioteki, aby wyświetlić menu kontekstowe specjalne zawierający listę pasków narzędzi aplikacji i okienka dokowania po kliknięciu prawym przyciskiem myszy i biblioteki przetwarza komunikat WM_CONTEXTMENU.|  
|[CDockingManager::FindDockSite](#finddocksite)|Pobiera pasku okienko jest w określonej pozycji, na którym jest określone wyrównanie.|  
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|Zwraca pasku okienka o identyfikatorze okienku paska docelowej.|  
|[CDockingManager::FindPaneByID](#findpanebyid)|Wyszukuje okienko określony formant identyfikatora.|  
|[CDockingManager::FixupVirtualRects](#fixupvirtualrects)|Zatwierdza wszystkie bieżącej pozycji narzędzi do wirtualnego prostokąty.|  
|[CDockingManager::FrameFromPoint](#framefrompoint)|Zwraca ramki, która zawiera danego punktu.|  
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|Pobiera prostokąt, który zawiera granice obszaru klienckiego.|  
|[CDockingManager::GetDockingMode](#getdockingmode)|Zwraca bieżący tryb dokowania.|  
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|Pobiera wskaźnik do ramki okna nadrzędnego.|  
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|Zwraca włączone wyrównanie okienka.|  
|[CDockingManager::GetMiniFrames](#getminiframes)|Pobiera listę miniframes.|  
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|Pobiera prostokąt, który zawiera zewnętrznej krawędzi ramki.|  
|[CDockingManager::GetPaneList](#getpanelist)|Zwraca listę okienka należące do Menedżera dokowania. Dotyczy to również wszystkich okienka zmiennoprzecinkowych.|  
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|Pobiera wskaźnik inteligentny Menedżera dokowania.|  
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|Pobiera wskaźnik inteligentny Menedżera dokowania.|  
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|Zwraca inteligentne parametry dokowania Menedżera dokowania.|  
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|Metoda statyczna zwraca motyw używany do wyświetlania znaczniki inteligentnego dokowania.|  
|[CDockingManager::HideAutoHidePanes](#hideautohidepanes)|Ukrywa okienko, w którym znajduje się w trybie autohide —.|  
|[CDockingManager::InsertDockSite](#insertdocksite)|Tworzy okienka dokowania i wstawia go do listy paski sterowania.|  
|[CDockingManager::InsertPane](#insertpane)|Wstawia listę pasków kontrolki panelu sterowania.|  
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|Określa, czy menu podręczne jest wyświetlany na podpisy wszystkie okienka.|  
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|Określa, po układów wszystkich okienek zostaną skorygowane.|  
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|Określa, czy dokowania manager jest w trybie kontenera OLE.|  
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|Określa, czy określony punkt znajduje się w pobliżu lokacji dokowania.|  
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|Określa, czy ustawiono tryb podglądu wydruku.|  
|[CDockingManager::LoadState](#loadstate)|Ładuje stan dokowania menedżera z rejestru.|  
|[CDockingManager::LockUpdate](#lockupdate)|Blokuje danego okna.|  
|[CDockingManager::OnActivateFrame](#onactivateframe)|Wywoływane przez platformę, gdy okno ramowe jest aktywowane lub jest dezaktywowana.|  
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|Wywoływane przez platformę, gdy aktywne menu podręczne przetwarza komunikat WM_DESTROY.|  
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|Wywoływane przez platformę, by przenieść okno ramowe minimalnej.|  
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|Wywoływane przez platformę, podczas tworzenia menu, która zawiera listę okienka.|  
|[CDockingManager::PaneFromPoint](#panefrompoint)|Zwraca okienko, który zawiera danego punktu.|  
|[CDockingManager::ProcessPaneContextMenuCommand](#processpanecontextmenucommand)|Metoda wywoływana przez strukturę zaznacz lub usuń zaznaczenie pola wyboru dla określonego polecenia i ponownie Oblicz układ wyświetlane okienku.|  
|[CDockingManager::RecalcLayout](#recalclayout)|Ponownie oblicza układ wewnętrzny formantów występuje na liście kontrolek.|  
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|Zwalnia kontenery okienku puste.|  
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|Usuwa określoną ukryte paska okienka.|  
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|Usuwa określony ramkę z listy ramek mini.|  
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|Wyrejestrowuje okienko i usuwa go z listy w Menedżerze dokowania.|  
|[CDockingManager::ReplacePane](#replacepane)|Zastępuje jedno okienko na inny.|  
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|Uporządkowana ramek na liście mini ramki.|  
|[CDockingManager::SaveState](#savestate)|Zapisuje stan dokowania menedżera w rejestrze.|  
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|Wysyła określoną wiadomość do ramki mini wszystkich.|  
|[CDockingManager::Serialize](#serialize)|Zapisuje dokowania Menedżera do archiwum. (Przesłania [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|Ustawia rozmiar, szerokość i wysokość paski sterowania i okienko określony.|  
|[CDockingManager::SetDockingMode](#setdockingmode)|Ustawia tryb dokowania.|  
|[CDockingManager::SetDockState](#setdockstate)|Ustawia stan dokujące paski sterowania, mini ramki i paski autohide —.|  
|[CDockingManager::SetPrintPreviewMode](#setprintpreviewmode)|Ustawia tryb podglądu wydruku pasków, które są wyświetlane w podglądzie wydruku.|  
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|Ustawia parametrów, które określają zachowanie inteligentne dokowania.|  
|[CDockingManager::ShowDelayShowMiniFrames](#showdelayshowminiframes)|Pokazuje lub ukrywa windows mini ramek.|  
|[CDockingManager::ShowPanes](#showpanes)|Wyświetlenie lub ukrycie okienka pasków sterowania i autohide —.|  
|[CDockingManager::StartSDocking](#startsdocking)|Uruchamia inteligentne dokowania określone okno zgodnie z wyrównanie inteligentne Menedżera dokowania.|  
|[CDockingManager::StopSDocking](#stopsdocking)|Zatrzymuje inteligentne dokowania.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|Określa, czy Menedżer dokowania powoduje ukrycie okienka w trybie kontenera OLE.|  
|[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)|Określa tryb globalny dokowania.|  
|[CDockingManager::m_nDockSensitivity](#m_ndocksensitivity)|Określa czułości dokowania.|  
|[CDockingManager::m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|Określa czas (w milisekundach), zanim dokujące okienko jest zadokowany w trybie natychmiastowym dokowania.|  
|[CDockingManager::m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|Określa czas (w milisekundach), zanim paska narzędzi jest zadokowany do głównego okna ramowego.|  
  
## <a name="remarks"></a>Uwagi  
 Głównego okna ramowego tworzy i inicjuje automatycznie tej klasy.  
  
 Dokowanie obiekt menedżera zawiera listę wszystkich okienek znajdujących się w układzie dokowania, a także listę wszystkich [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) systemu windows, które należą do głównego okna ramowego.  
  
 `CDockingManager` Klasa implementuje niektórych usług, których można znaleźć okienko lub `CPaneFrameWnd` okna. Zazwyczaj nie zostanie wywołana tych usług bezpośrednio, ponieważ są one ujęte w ramce głównej obiekt window. Aby uzyskać więcej informacji, zobacz [CPaneFrameWnd klasy](../../mfc/reference/cpaneframewnd-class.md).  
  
## <a name="customization-tips"></a>Porady dotyczące dostosowywania  
 Poniższe wskazówki dotyczą `CDockingManager` obiektów:  
  
- [Klasa CDockingManager](../../mfc/reference/cdockingmanager-class.md) obsługuje następujące tryby dokowania:  
  
    - `AFX_DOCK_TYPE::DT_IMMEDIATE`  
  
    - `AFX_DOCK_TYPE::DT_STANDARD`  
  
    - `AFX_DOCK_TYPE::DT_SMART`  
  
     Te tryby dokowania są definiowane przez [CDockingManager::m_dockModeGlobal](#m_dockmodeglobal) i są ustawione przez wywołanie metody [CDockingManager::SetDockingMode](#setdockingmode).  
  
-   Jeśli chcesz utworzyć okienku niezmienny, bez zmienny rozmiar, wywołanie [CDockingManager::AddPane](#addpane) metody. Ta metoda rejestruje okienku Menedżera dokowania, który jest odpowiedzialny za układ okienka.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod w `CDockingManager` klasa do konfigurowania `CDockingManager` obiektu. W przykładzie pokazano sposób wyświetlania dodatkowy przycisk otwiera menu podręczne na podpisy wszystkie okienka dokowania i jak ustawić tryb dokowania obiektu. Następujący fragment kodu jest częścią [programu Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDockingManager](../../mfc/reference/cdockingmanager-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxDockingManager.h  
  
##  <a name="adddocksite"></a>CDockingManager::AddDockSite  
 Tworzy okienka dokowania i dodaje go do listy paski sterowania.  
  
```  
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,  
    CDockSite** ppDockBar = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`info`  
 Odwołanie do struktury zawierający informacje o dock wyrównanie okienka.  
  
 [out]`ppDockBar`  
 Wskaźnik na wskaźnik do nowego okienka dokowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli w okienku dokowania została utworzona pomyślnie; `FALSE` inaczej.  
  
##  <a name="addhiddenmditabbedbar"></a>CDockingManager::AddHiddenMDITabbedBar  
 Dodaje dojścia do paska okienko do listy ukrytych MDI kartach paska okienka.  
  
```  
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
 Wskaźnik do paska okienko  
  
##  <a name="addpane"></a>CDockingManager::AddPane  
 Rejestruje okienko dokujące menedżera.  
  
```  
BOOL AddPane(
    CBasePane* pWnd,  
    BOOL bTail = TRUE,  
    BOOL bAutoHide = FALSE,  
    BOOL bInsertForOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [w, out]`pWnd`  
 Określa okienko, aby dodać do Menedżera dokowania.  
  
 [in]`bTail`  
 `TRUE`Aby dodać okienku na końcu listy okienka dokowania Menedżera; w przeciwnym razie `FALSE`.  
  
 [in]`bAutoHide`  
 Tylko do użytku wewnętrznego. Zawsze używać domyślnej wartości `FALSE`.  
  
 [in]`bInsertForOuterEdge`  
 Tylko do użytku wewnętrznego. Zawsze używać domyślnej wartości `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko został pomyślnie zarejestrowany przy użyciu Menedżera dokowania; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby zarejestrować niezmienny, bez zmienny rozmiar okienka przy użyciu Menedżera dokowania. Jeśli nie zarejestrujesz okienka, nie będą wyświetlane prawidłowo gdy Menedżer dokowania jest poukładany.  
  
##  <a name="adjustdockinglayout"></a>CDockingManager::AdjustDockingLayout  
 Ponownie oblicza i dostosowuje układ wszystkie okienka w oknie ramowym.  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`hdwp`  
 Określa strukturę położenie okna opóźnieniem. Aby uzyskać więcej informacji, zobacz [typów danych systemu Windows](http://msdn.microsoft.com/library/windows/desktop/aa383751).  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="addminiframe"></a>CDockingManager::AddMiniFrame  
 Dodaje ramki do listy mini ramki.  
  
```  
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
 Wskaźnik do ramki.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli ramka nie jest na liście mini ramek i został dodany pomyślnie; `FALSE` inaczej.  
  
##  <a name="adjustpaneframes"></a>CDockingManager::AdjustPaneFrames  
 Powoduje, że `WM_NCCALCSIZE` komunikat do wysłania do wszystkich okienek i `CPaneFrameWnd` systemu windows.  
  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="adjustrecttoclientarea"></a>CDockingManager::AdjustRectToClientArea  
 Dopasowuje wyrównanie prostokąta.  
  
```  
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rectResult`  
 Odwołanie do `CRect` obiektu  
  
 [in]`dwAlignment`  
 Wyrównanie `CRect` obiektu  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli wyrównanie `CRect` obiektu została dostosowana; `FALSE` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 `dwAlignment` Parametr może mieć jedną z następujących wartości:  
  
-   CBRS_ALIGN_TOP  
  
-   CBRS_ALIGN_BOTTOM  
  
-   CBRS_ALIGN_LEFT  
  
-   CBRS_ALIGN_RIGHT  
  
##  <a name="alignautohidepane"></a>CDockingManager::AlignAutoHidePane  
 Zmienia rozmiar okienko dokujące w trybie autohide — tak, aby zajmuje pełnej szerokości lub wysokości obszaru klienckiego ramki otoczona dock witryn.  
  
```  
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,  
    BOOL bIsVisible = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDefaultSlider`  
 Okienko dokujące suwaka.  
  
 [in]`bIsVisible`  
 `TRUE`Jeśli okienko dokujące jest widoczna; `FALSE` inaczej.  
  
##  <a name="autohidepane"></a>CDockingManager::AutoHidePane  
 Tworzy automatycznie ukrywaj paska narzędzi.  
  
```  
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,  
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
 Wskaźnik do paska okienka.  
  
 [in]`pCurrAutoHideToolBar`  
 Wskaźnik do automatycznego ukrywanie paska narzędzi.  
  
### <a name="return-value"></a>Wartość zwracana  
 `NULL`Jeśli automatyczne ukrywanie paska narzędzi nie została utworzona; w przeciwnym razie wskaźnik do nowego paska narzędzi.  
  
##  <a name="bringbarstotop"></a>CDockingManager::BringBarsToTop  
 Przełącza zadokowanych pasków, które mają określone wyrównanie do góry.  
  
```  
void BringBarsToTop(
    DWORD dwAlignment = 0,  
    BOOL bExcludeDockedBars = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`dwAlignment`  
 Wyrównanie paski dokowania, których na początku innych okien.  
  
 [in]`bExcludeDockedBars`  
 `TRUE`Aby wykluczyć zadokowanych pasków przed u góry; w przeciwnym razie `FALSE`.  
  
##  <a name="buildpanesmenu"></a>CDockingManager::BuildPanesMenu  
 Dodaje nazwy dokowania okienka i paski narzędzi do menu.  
  
```  
void BuildPanesMenu(
    CMenu& menu,  
    BOOL bToolbarsOnly);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`menu`  
 Menu można dodać nazwy dokowania okienka i pasków narzędzi.  
  
 [in]`bToolbarsOnly`  
 `TRUE`Aby dodać tylko nazwy narzędzi do menu. `FALSE` inaczej.  
  
##  <a name="calcexpecteddockedrect"></a>CDockingManager::CalcExpectedDockedRect  
 Oblicza oczekiwanego prostokąt zadokowanych okien.  
  
```  
void CalcExpectedDockedRect(
    CWnd* pWnd,  
    CPoint ptMouse,  
    CRect& rectResult,  
    BOOL& bDrawTab,  
    CDockablePane** ppTargetBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
 Wskaźnik do okna, aby dokowania.  
  
 [in]`ptMouse`  
 Lokalizacja myszy.  
  
 [out]`rectResult`  
 Obliczony prostokąt.  
  
 [in]`bDrawTab`  
 `TRUE`Rysowanie na karcie; w przeciwnym razie `FALSE`.  
  
 [out]`ppTargetBar`  
 Wskaźnik na wskaźnik do okienka docelowej.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda oblicza prostokąt okna zajmują użytkownika przeciągania okna do punktu określonego przez `ptMouse` i zadokowane go brak.  
  
##  <a name="create"></a>CDockingManager::Create  
 Tworzy Menedżera dokowania.  
  
```  
BOOL Create(CFrameWnd* pParentWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pParentWnd`  
 Wskaźnik do ramki nadrzędnego menedżera dokowania. Ta wartość nie może być `NULL`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`zawsze.  
  
##  <a name="determinepaneandstatus"></a>CDockingManager::DeterminePaneAndStatus  
 Określa okienka zawierającego danego punktu i jego stan dokowania.  
  
```  
virtual AFX_CS_STATUS DeterminePaneAndStatus(
    CPoint pt,  
    int nSensitivity,  
    DWORD dwEnabledAlignment,  
    CBasePane** ppTargetBar,  
    const CBasePane* pBarToIgnore,  
    const CBasePane* pBarToDock);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pt`  
 Lokalizacja okienka do sprawdzenia.  
  
 [in]`nSensitivity`  
 Wartość, aby zwiększyć prostokąt okna każdego zaznaczone okienka. Okienko spełnia kryteria wyszukiwania, jeśli w tym regionie zwiększona danego punktu.  
  
 [in]`dwEnabledAlignment`  
 Wyrównanie dokowania panelu.  
  
 [out]`ppTargetBar`  
 Wskaźnik na wskaźnik do okienka docelowej.  
  
 [in]`pBarToIgnore`  
 Okienka ignoruje metody.  
  
 [in]`pBarToDock`  
 Okienko, w którym jest zadokowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan dokowania.  
  
### <a name="remarks"></a>Uwagi  
 Dokowanie stanu może być jedną z następujących wartości:  
  
|Wartość AFX_CS_STATUS|Znaczenie|  
|---------------------------|-------------|  
|CS_NOTHING|Kursor nie znajduje się za pośrednictwem witryny dokowania. W związku z tym pozostawienie okienka zmiennoprzecinkowych.|  
|CS_DOCK_IMMEDIATELY|Kursor znajduje się nad lokacji dock w trybie natychmiastowym (styl DT_IMMEDIATE jest włączone), więc okienku musi być zadokowane, natychmiast.|  
|CS_DELAY_DOCK|Kursor znajduje się nad innym okienko dokujące lub krawędzi ramki głównej lokacji dokowania.|  
|CS_DELAY_DOCK_TO_TAB|Kursor znajduje się nad dokowania lokacji, która powoduje, że okienko, aby być zadokowane, w oknie z kartami. Dzieje się tak, gdy wskaźnik myszy znajduje się w podpis okienko dokujące w innym lub za pośrednictwem karty części okienka z kartami.|  
  
##  <a name="disablerestoredockstate"></a>CDockingManager::DisableRestoreDockState  
 Włącza lub wyłącza ładowania dokowania układu z rejestru.  
  
```  
void DisableRestoreDockState(BOOL bDisable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bDisable`  
 `TRUE`Aby wyłączyć ładowanie dokowania układu z rejestru; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę można wywołać, gdy musi zachować bieżącego układu dokowania okienka i pasków zadań podczas ładowania stanu aplikacji.  
  
##  <a name="dockpane"></a>CDockingManager::DockPane  
 Stacje dokujące okienko do innego okienka lub ramki okna.  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
 Wskaźnik do paska okienko, aby zostało zadokowane do.  
  
 [in]`nDockBarID`  
 Identyfikator Dokowanie paska.  
  
 [in]`lpRect`  
 Prostokąt docelowy.  
  
##  <a name="dockpaneleftof"></a>CDockingManager::DockPaneLeftOf  
 Stacje dokujące okienko na lewo od innego okienka.  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBarToDock,  
    CPane* pTargetBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBarToDock`  
 Wskaźnik do okienko, aby być zadokowany z lewej strony `pTargetBar`.  
  
 [in]`pTargetBar`  
 Wskaźnik do okienka docelowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko zostało zadokowane pomyślnie; w przeciwnym razie `FALSE`.  
  
##  <a name="enableautohidepanes"></a>CDockingManager::EnableAutoHidePanes  
 Włącza Dokowanie okienka do ramki głównej, tworzy okienku dokowania i dodaje go do listy paski sterowania.  
  
```  
BOOL EnableAutoHidePanes(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`dwStyle`  
 Wyrównanie dokowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli w okienku dokowania została utworzona pomyślnie; `FALSE` inaczej.  
  
##  <a name="enabledocking"></a>CDockingManager::EnableDocking  
 Tworzy okienka dokowania i umożliwia Dokowanie okienka do ramki głównej.  
  
```  
BOOL EnableDocking(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`dwStyle`  
 Wyrównanie dokowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli w okienku dokowania została utworzona pomyślnie; `FALSE` inaczej.  
  
##  <a name="enabledocksitemenu"></a>CDockingManager::EnableDockSiteMenu  
 Wyświetla dodatkowy przycisk otwiera menu podręczne na podpisy wszystkie okienka dokowania.  
  
```  
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 `TRUE`Aby włączyć menu lokacji dokowania. w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Menu lokacji dokowania wyświetla następujące opcje zmiany stanu dokowania okienka:  
  
- `Floating`-Pojawia się okienko  
  
- `Docking`-Stacje dokujące okienko w ramce głównej w lokalizacji, w której został ostatnio zadokowany okienka  
  
- `AutoHide`-Zmienia okienku na tryb autohide —  
  
- `Hide`-Ukrywa okienko  
  
 Domyślnie nie jest wyświetlany w tym menu.  
  
##  <a name="enablepanecontextmenu"></a>CDockingManager::EnablePaneContextMenu  
 Określa, że biblioteki, aby wyświetlić menu kontekstowe specjalne zawierający listę pasków narzędzi aplikacji i okienka dokowania po kliknięciu prawym przyciskiem myszy i biblioteki przetwarza komunikat WM_CONTEXTMENU.  
  
```  
void EnablePaneContextMenu(
    BOOL bEnable,  
    UINT uiCustomizeCmd,  
    const CString& strCustomizeText,  
    BOOL bToolbarsOnly = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 Jeśli `TRUE`, biblioteki włącza obsługę menu kontekstowe automatyczne; Jeśli `FALSE` biblioteki wyłącza obsługę menu kontekstowe automatycznego.  
  
 [in]`uiCustomizeCmd`  
 Identyfikator polecenia **Dostosuj** elementu w menu.  
  
 [in]`strCustomizeText`  
 Tekst **Dostosuj** elementu.  
  
 [in]`bToolbarsOnly`  
 Jeśli `TRUE`, menu wyświetla tylko listę pasków narzędzi aplikacji; Jeśli `FALSE`, biblioteki dodaje okienka dokowania aplikacji do tej listy.  
  
##  <a name="finddocksite"></a>CDockingManager::FindDockSite  
 Pobiera pasku okienko jest w określonej pozycji, na którym jest określone wyrównanie.  
  
```  
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,  
    BOOL bOuter);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`dwAlignment`  
 Wyrównanie paska okienka.  
  
 [in]`bOuter`  
 Jeśli `TRUE`, pobrać pasek head pozycji na liście pasków sterowania. W przeciwnym razie pobrać pasku tail pozycję na liście paski sterowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Okienko dokujące, który ma określone wyrównanie; `NULL` inaczej.  
  
##  <a name="findpanebyid"></a>CDockingManager::FindPaneByID  
 Wyszukuje okienko określony formant identyfikatora.  
  
```  
virtual CBasePane* FindPaneByID(
    UINT uBarID,  
    BOOL bSearchMiniFrames = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uBarID`  
 Określa identyfikator formantu okienka można znaleźć.  
  
 [in]`bSearchMiniFrames`  
 `TRUE`Aby w wyszukiwaniu uwzględnić wszystkie okienka zmiennoprzecinkowych. `FALSE`Aby uwzględnić zadokowanych paneli.  
  
### <a name="return-value"></a>Wartość zwracana  
 [CBasePane](../../mfc/reference/cbasepane-class.md) obiektu, który ma identyfikator określony formant lub `NULL` Jeśli nie można odnaleźć określonego okienka.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="finddocksitebypane"></a>CDockingManager::FindDockSiteByPane  
 Zwraca pasku okienka o identyfikatorze okienku paska docelowej.  
  
```  
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pTargetBar`  
 Wskaźnik do okienka pasek docelowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pasek okienka o identyfikatorze okienku paska docelowej. `NULL` Jeśli nie ma takiej paska okienku istnieje.  
  
##  <a name="fixupvirtualrects"></a>CDockingManager::FixupVirtualRects  
 Zatwierdza wszystkie bieżącej pozycji narzędzi do wirtualnego prostokąty.  
  
```  
virtual void FixupVirtualRects();
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik uruchomi przeciągnij pasek narzędzi, przejściu oryginalnego położenia w *wirtualnego prostokąt*. Gdy użytkownik przesuwa paska narzędzi w swojej witrynie dokowania, pasek narzędzi może przejść pasków narzędzi. Oryginalnego położenia innych pasków narzędzi są przechowywane w odpowiednich prostokąty wirtualnego.  
  
##  <a name="framefrompoint"></a>CDockingManager::FrameFromPoint  
 Zwraca ramki, która zawiera danego punktu.  
  
```  
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,  
    CPaneFrameWnd* pFrameToExclude,  
    BOOL bFloatMultiOnly) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pt`  
 Określa punkt, we współrzędnych ekranu, aby sprawdzić.  
  
 [in]`pFrameToExclude`  
 Wskaźnik do ramki, które mają zostać wykluczone.  
  
 [in]`bFloatMultiOnly`  
 `TRUE`Aby wykluczyć ramki, które nie są wystąpienia `CMultiPaneFrameWnd`; `FALSE` inaczej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ramki, która zawiera danego punktu; `NULL` inaczej.  
  
##  <a name="getclientareabounds"></a>CDockingManager::GetClientAreaBounds  
 Pobiera prostokąt, który zawiera granice obszaru klienckiego.  
  
```  
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rcClient`  
 Odwołanie do prostokąta, który zawiera granice obszaru klienckiego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Prostokąt, który zawiera granice obszaru klienckiego.  
  
##  <a name="getdockingmode"></a>CDockingManager::GetDockingMode  
 Zwraca bieżący tryb dokowania.  
  
```  
static AFX_DOCK_TYPE GetDockingMode();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Moduł wyliczający wartość, która reprezentuje bieżący tryb dokowania. Może być jedną z następujących wartości:  
  
- `DT_STANDARD`  
  
- `DT_IMMEDIATE`  
  
- `DT_SMART`  
  
### <a name="remarks"></a>Uwagi  
 Aby ustawić tryb dokowania, należy wywołać [CDockingManager::SetDockingMode](#setdockingmode).  
  
##  <a name="getdocksiteframewnd"></a>CDockingManager::GetDockSiteFrameWnd  
 Pobiera wskaźnik do ramki okna nadrzędnego.  
  
```  
CFrameWnd* GetDockSiteFrameWnd() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do ramki okna nadrzędnego.  
  
##  <a name="getenabledautohidealignment"></a>CDockingManager::GetEnabledAutoHideAlignment  
 Zwraca włączone wyrównanie okienka.  
  
```  
DWORD GetEnabledAutoHideAlignment() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bitowe połączenie `CBRS_ALIGN_` flagi lub 0, jeśli nie włączono autohide — okienka. Aby uzyskać więcej informacji, zobacz [CFrameWnd::EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking).  
  
### <a name="remarks"></a>Uwagi  
 Metoda zwraca włączone wyrównanie autohide — paski sterowania. Aby włączyć paski autohide —, należy wywołać [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes).  
  
##  <a name="getminiframes"></a>CDockingManager::GetMiniFrames  
 Pobiera listę miniframes.  
  
```  
const CObList& GetMiniFrames() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Lista miniframes, która zawiera należące do Menedżera dokowania pasków kontrolki.  
  
##  <a name="getouteredgebounds"></a>CDockingManager::GetOuterEdgeBounds  
 Pobiera prostokąt, który zawiera zewnętrznej krawędzi ramki.  
  
```  
CRect GetOuterEdgeBounds() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Prostokąt zawiera zewnętrznej krawędzi ramki.  
  
##  <a name="getpanelist"></a>CDockingManager::GetPaneList  
 Zwraca listę okienka należące do Menedżera dokowania. Dotyczy to również wszystkich okienka zmiennoprzecinkowych.  
  
```  
void GetPaneList(
    CObList& lstBars,  
    BOOL bIncludeAutohide = FALSE,  
    CRuntimeClass* pRTCFilter = NULL,  
    BOOL bIncludeTabs = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [w, out]`lstBars`  
 Zawiera wszystkie okienka bieżącego Menedżera dokowania.  
  
 [in]`bIncludeAutohide`  
 `TRUE`Aby uwzględnić okienka, które są w trybie autohide —; w przeciwnym razie `FALSE`.  
  
 [in]`pRTCFilter`  
 Jeśli nie `NULL`, zwracana lista zawiera okienka tylko klasy wykonawcze.  
  
 [in]`bIncludeTabs`  
 `TRUE`Aby uwzględnić kartach. w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku dowolnego z kartami okienka w Menedżerze dokowania, metoda zwraca wskaźniki do [klasy CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md) obiektów i należy wyliczyć kart jawnie.  
  
 Użyj `pRTCFilter` uzyskanie określonej klasy okienka. Na przykład odpowiednio ustawiając tę wartość można uzyskać tylko pasków narzędzi.  
  
##  <a name="getsmartdockingmanager"></a>CDockingManager::GetSmartDockingManager  
 Pobiera wskaźnik inteligentny Menedżera dokowania.  
  
```  
CSmartDockingManager* GetSmartDockingManager();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [inteligentne Menedżera dokowania](http://msdn.microsoft.com/en-us/f537a1a6-fb9e-41d7-952f-0f25d5ee7534).  
  
##  <a name="getsmartdockingmanagerpermanent"></a>CDockingManager::GetSmartDockingManagerPermanent  
 Pobiera wskaźnik inteligentny Menedżera dokowania.  
  
```  
CSmartDockingManager* GetSmartDockingManagerPermanent() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik inteligentny Menedżera dokowania.  
  
##  <a name="getsmartdockingparams"></a>CDockingManager::GetSmartDockingParams  
 Zwraca inteligentne parametry dokowania Menedżera dokowania.  
  
```  
static CSmartDockingInfo& GetSmartDockingParams();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Klasa, która zawiera inteligentne parametry dokowania bieżący Menedżer dokowania. Aby uzyskać więcej informacji, zobacz [CSmartDockingInfo klasy](../../mfc/reference/csmartdockinginfo-class.md).  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="hideautohidepanes"></a>CDockingManager::HideAutoHidePanes  
 Ukrywa okienko, w którym znajduje się w trybie autohide —.  
  
```  
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,  
    BOOL bImmediately = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBarToExclude`  
 Wskaźnik do paska do wykluczenia z ukrytych.  
  
 [in]`bImmediately`  
 `TRUE`Aby ukryć okienko natychmiast; `FALSE` Aby ukryć okienko z mocą autohide —.  
  
##  <a name="insertdocksite"></a>CDockingManager::InsertDockSite  
 Tworzy okienka dokowania i wstawia go do listy paski sterowania.  
  
```  
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,  
    DWORD dwAlignToInsertAfter,  
    CDockSite** ppDockBar = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`info`  
 Struktura, która zawiera informacje wyrównanie dokowania panelu.  
  
 [in]`dwAlignToInsertAfter`  
 Wyrównanie dokowania panelu.  
  
 [out]`ppDockBar`  
 Wskaźnik na wskaźnik do okienka dokowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli w okienku dokowania została utworzona pomyślnie; `FALSE` inaczej.  
  
##  <a name="insertpane"></a>CDockingManager::InsertPane  
 Wstawia listę pasków kontrolki panelu sterowania.  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pControlBar`  
 Wskaźnik do panelu sterowania.  
  
 [in]`pTarget`  
 Wskaźnik do okienka docelowej.  
  
 [in]`bAfter`  
 `TRUE`Wstaw w okienku po pozycji okienka docelowym; `FALSE` inaczej.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko formantu został pomyślnie dodany do listy paski sterowania; `FALSE` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartość false, jeśli w okienku kontroli jest już na liście paski sterowania lub w okienku docelowy nie istnieje na liście paski sterowania.  
  
##  <a name="isdocksitemenu"></a>CDockingManager::IsDockSiteMenu  
 Określa, czy menu podręczne jest wyświetlany na podpisy wszystkie okienka.  
  
```  
static BOOL IsDockSiteMenu();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli menu lokacji dock jest wyświetlany na podpisy wszystkie okienka dokowania; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Można włączyć menu lokacji dokowania przez wywołanie metody [CDockingManager::EnableDockSiteMenu](#enabledocksitemenu).  
  
##  <a name="isinadjustlayout"></a>CDockingManager::IsInAdjustLayout  
 Określa, po układów wszystkich okienek zostaną skorygowane.  
  
```  
BOOL IsInAdjustLayout() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli są dostosowane układów wszystkich okienek; `FALSE` inaczej.  
  
##  <a name="isolecontainermode"></a>CDockingManager::IsOLEContainerMode  
 Określa, czy dokowania manager jest w trybie kontenera OLE.  
  
```  
BOOL IsOLEContainerMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli dokowania manager jest w trybie kontenera OLE w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 W trybie kontenera OLE wszystkie okienka dokowania i pasków narzędzi aplikacji są ukryte. Okienka również są ukryte w tym trybie, jeśli ustawiono [CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode) do `TRUE`.  
  
##  <a name="ispointneardocksite"></a>CDockingManager::IsPointNearDockSite  
 Określa, czy określony punkt znajduje się w pobliżu lokacji dokowania.  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`point`  
 Określony punkt.  
  
 [out]`dwBarAlignment`  
 Określa, które krawędzi punkt znajduje się w pobliżu. Możliwe wartości to `CBRS_ALIGN_LEFT`, `CBRS_ALIGN_RIGHT`, `CBRS_ALIGN_TOP`, i `CBRS_ALIGN_BOTTOM`.  
  
 [out]`bOuterEdge`  
 `TRUE`Jeśli punkt jest bliski zewnętrzną krawędzią dokowania lokacji; `FALSE` inaczej.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli punkt znajduje się w pobliżu lokacji dokowania; w przeciwnym razie `FALSE`.  
  
##  <a name="isprintpreviewvalid"></a>CDockingManager::IsPrintPreviewValid  
 Określa, czy ustawiono tryb podglądu wydruku.  
  
```  
BOOL IsPrintPreviewValid() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli ustawiono tryb podglądu wydruku; `FALSE` inaczej.  
  
##  <a name="loadstate"></a>CDockingManager::LoadState  
 Ładuje stan dokowania menedżera z rejestru.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 Nazwa profilu.  
  
 [in]`uiID`  
 Identyfikator menedżera dokowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli stan dokowania manager został załadowany pomyślnie; w przeciwnym razie `FALSE`.  
  
##  <a name="lockupdate"></a>CDockingManager::LockUpdate  
 Blokuje danego okna.  
  
```  
void LockUpdate(BOOL bLock);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bLock`  
 `TRUE`Jeśli okno jest zablokowany; `FALSE` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Gdy okno jest zablokowany, nie można przenieść i nie może być narysowany ponownie.  
  
##  <a name="m_bhidedockingbarsincontainermode"></a>CDockingManager::m_bHideDockingBarsInContainerMode  
 Określa, czy Menedżer dokowania powoduje ukrycie okienka w trybie kontenera OLE.  
  
```  
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość `FALSE` Jeśli chcesz zachować wszystkie okienka zadokowane do ramki głównej widoczne gdy aplikacja jest w trybie kontenera OLE. Domyślnie ta wartość jest `TRUE`.  
  
##  <a name="m_dockmodeglobal"></a>CDockingManager::m_dockModeGlobal  
 Określa tryb globalny dokowania.  
  
```  
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;  
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie okienko dokujące w każdym korzysta z tego trybu dokowania. Aby uzyskać więcej informacji na temat wartości, które to pole może mieć wartości, zobacz [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).  
  
##  <a name="m_ndocksensitivity"></a>CDockingManager::m_nDockSensitivity  
 Określa czułości dokowania.  
  
```  
AFX_IMPORT_DATA static int m_nDockSensitivity;  
```  
  
### <a name="remarks"></a>Uwagi  
 Czułość dokowania Określa, jak blisko liczbą zmiennoprzecinkową okienku można podejścia okienko dokujące, dokującego witryny lub innego okienka zanim w ramach zmiany stanu do zadokowane.  
  
##  <a name="m_ntimeoutbeforedockingbardock"></a>CDockingManager::m_nTimeOutBeforeDockingBarDock  
 Określa czas (w milisekundach), zanim dokujące okienko jest zadokowany w trybie natychmiastowym dokowania.  
  
```  
static UINT m_nTimeOutBeforeDockingBarDock;  
```  
  
### <a name="remarks"></a>Uwagi  
 Przed panel jest zadokowany, platformę oczekuje określony limit czasu. Zapobiega to przypadkowo jest zadokowany do lokalizacji podczas, gdy użytkownik nadal jest przeciąganie okienka.  
  
##  <a name="m_ntimeoutbeforetoolbardock"></a>CDockingManager::m_nTimeOutBeforeToolBarDock  
 Określa czas (w milisekundach), zanim paska narzędzi jest zadokowany do głównego okna ramowego.  
  
```  
static UINT m_nTimeOutBeforeToolBarDock;  
```  
  
### <a name="remarks"></a>Uwagi  
 Przed paska narzędzi jest zadokowany, platformę oczekuje określony limit czasu. Zapobiega to przypadkowo jest zadokowany do lokalizacji podczas, gdy użytkownik nadal jest przeciąganie paska narzędzi.  
  
##  <a name="onactivateframe"></a>CDockingManager::OnActivateFrame  
 Wywoływane przez platformę, gdy okno ramowe jest aktywowane lub jest dezaktywowana.  
  
```  
virtual void OnActivateFrame(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bActivate`  
 Jeśli `TRUE`, okno ramowe jest aktywowane; Jeśli `FALSE`, okno ramowe zostanie zdezaktywowany.  
  
##  <a name="onclosepopupmenu"></a>CDockingManager::OnClosePopupMenu  
 Wywoływane przez platformę, gdy aktywne menu podręczne przetwarza komunikat WM_DESTROY.  
  
```  
void OnClosePopupMenu();
```  
  
### <a name="remarks"></a>Uwagi  
 Platformę wysyła komunikat WM_DESTROY, gdy jest zamknięcie bieżącego okna głównego. Przesłonić tę metodę obsługi powiadomień z `CMFCPopupMenu` obiektów, które należą do okno ramowe podczas `CMFCPopupMenu` obiekt procesów `WM_DESTROY` wiadomości.  
  
##  <a name="onmoveminiframe"></a>CDockingManager::OnMoveMiniFrame  
 Wywoływane przez platformę, by przenieść okno ramowe minimalnej.  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pFrame`  
 Wskaźnik do okno ramowe minimalnej.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
##  <a name="onpanecontextmenu"></a>CDockingManager::OnPaneContextMenu  
 Wywoływane przez platformę, podczas tworzenia menu, która zawiera listę okienka.  
  
```  
void OnPaneContextMenu(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`point`  
 Określa lokalizację, w menu.  
  
##  <a name="panefrompoint"></a>CDockingManager::PaneFromPoint  
 Zwraca okienko, który zawiera danego punktu.  
  
```  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    bool bExactBar = false,  
    CRuntimeClass* pRTCBarType = NULL,  
    BOOL bCheckVisibility = FALSE,  
    const CBasePane* pBarToIgnore = NULL) const;  
  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    DWORD& dwAlignment,  
    CRuntimeClass* pRTCBarType = NULL,  
    const CBasePane* pBarToIgnore = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`point`  
 Określa punkt, we współrzędnych ekranu, aby sprawdzić.  
  
 [in]`nSensitivity`  
 Wartość do zwiększyć prostokąt okna każdego zaznaczone okienka. Okienko spełnia kryteria wyszukiwania, jeśli w tym regionie nadmuchany danego punktu.  
  
 [in]`bExactBar`  
 `TRUE`ignorowanie `nSensitivity` parametru; w przeciwnym razie `FALSE`.  
  
 [in]`pRTCBarType`  
 Jeśli nie `NULL`, metoda szuka tylko okienka określonego typu.  
  
 [in]`bCheckVisibility`  
 `TRUE`Aby sprawdzić tylko widoczne okienka; w przeciwnym razie `FALSE`.  
  
 [out]`dwAlignment`  
 Jeśli okienko zostanie znaleziony w określonym momencie, ten parametr zawiera po stronie okienka, który był najbardziej zbliżony do określonego punktu. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
 [in]`pBarToIgnore`  
 Jeśli nie `NULL`, metoda ignoruje okienka określonego przez tego parametru.  
  
### <a name="return-value"></a>Wartość zwracana  
 [CBasePane](../../mfc/reference/cbasepane-class.md)-pochodnych obiekt, który zawiera danego punktu lub `NULL` Jeśli okienko nie został znaleziony.  
  
### <a name="remarks"></a>Uwagi  
 Gdy funkcja zwraca i okienku został znaleziony, `dwAlignment` zawiera wyrównanie określony punkt. Na przykład, jeśli punkt się najbliżej w górnej części okienka `dwAlignment` ma ustawioną wartość `CBRS_ALIGN_TOP`.  
  
##  <a name="processpanecontextmenucommand"></a>CDockingManager::ProcessPaneContextMenuCommand  
 Metoda wywoływana przez strukturę zaznacz lub usuń zaznaczenie pola wyboru dla określonego polecenia i ponownie Oblicz układ wyświetlane okienku.  
  
```  
BOOL ProcessPaneContextMenuCommand(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nID`  
 Identyfikator formantu paska menu.  
  
 [in]`nCode`  
 Polecenie kod powiadomienia.  
  
 [in]`pExtra`  
 Wskaźnik do void, który jest rzutowana na wskaźnik do `CCmdUI` Jeśli `nCode` jest CN_UPDATE_COMMAND_UI.  
  
 [in]`pHandlerInfo`  
 Wskaźnik do struktury informacji. Ten parametr nie jest używany.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli `pEXtra` nie ma wartości NULL i `nCode` jest równe CN_UPDATE_COMMAND_UI, lub jeśli brakuje pasek sterowania z określonym `nID`.  
  
##  <a name="recalclayout"></a>CDockingManager::RecalcLayout  
 Ponownie oblicza układ wewnętrzny formantów występuje na liście kontrolek.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bNotify`  
 Ten parametr nie jest używany.  
  
##  <a name="releaseemptypanecontainers"></a>CDockingManager::ReleaseEmptyPaneContainers  
 Zwalnia kontenery okienku puste.  
  
```  
void ReleaseEmptyPaneContainers();
```  
  
##  <a name="removehiddenmditabbedbar"></a>CDockingManager::RemoveHiddenMDITabbedBar  
 Usuwa określoną ukryte paska okienka.  
  
```  
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
 Wskaźnik do paska okienko do usunięcia.  
  
##  <a name="removeminiframe"></a>CDockingManager::RemoveMiniFrame  
 Usuwa określony ramkę z listy ramek mini.  
  
```  
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
 Wskaźnik do ramki do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`usunięcie określonej ramce; `FALSE` inaczej.  
  
##  <a name="removepanefromdockmanager"></a>CDockingManager::RemovePaneFromDockManager  
 Wyrejestrowuje okienko i usuwa go z listy w Menedżerze dokowania.  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pWnd,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide = FALSE,  
    CBasePane* pBarReplacement = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
 Wskaźnik do okienka do usunięcia.  
  
 [in]`bDestroy`  
 Jeśli `TRUE`, usunięto okienko zostanie zniszczony.  
  
 [in]`bAdjustLayout`  
 Jeśli `TRUE`, natychmiast dostosować układ dokowania.  
  
 [in]`bAutoHide`  
 Jeśli `TRUE`, okienku zostanie usunięty z listy paski autohide —. Jeśli `FALSE`, okienku zostanie usunięty z listy regularne okienka.  
  
 [in]`pBarReplacement`  
 Wskaźnik do okienka zastępujący okienku usunięte.  
  
##  <a name="replacepane"></a>CDockingManager::ReplacePane  
 Zastępuje jedno okienko na inny.  
  
```  
BOOL ReplacePane(
    CDockablePane* pOriginalBar,  
    CDockablePane* pNewBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pOriginalBar`  
 Wskaźnik do oryginalnego okienka.  
  
 [in]`pNewBar`  
 Wskaźnik do okienka zastępuje oryginalnego okienka.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko jest pomyślnie zastąpił; `FALSE` inaczej.  
  
##  <a name="resortminiframesforzorder"></a>CDockingManager::ResortMiniFramesForZOrder  
 Uporządkowana ramek na liście mini ramki.  
  
```  
void ResortMiniFramesForZOrder();
```  
  
##  <a name="savestate"></a>CDockingManager::SaveState  
 Zapisuje stan dokowania menedżera w rejestrze.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 Ścieżka do klucza rejestru.  
  
 [in]`uiID`  
 Dokowanie identyfikatora menedżera.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli stan został zapisany pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Zapisywanie do rejestru dokowania manager obejmuje zapisywanie stanów paski sterowania, Stany paski autohide — i stanów mini ramek istnieje w Menedżerze dokowania.  
  
##  <a name="sendmessagetominiframes"></a>CDockingManager::SendMessageToMiniFrames  
 Wysyła określoną wiadomość do ramki mini wszystkich.  
  
```  
BOOL SendMessageToMiniFrames(
    UINT uMessage,  
    WPARAM wParam = 0,  
    LPARAM lParam = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uMessage`  
 Komunikat do wysłania.  
  
 [in]`wParam`  
 Informacje zależne od dodatkowy komunikat.  
  
 [in]`lParam`  
 Informacje zależne od dodatkowy komunikat.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`zawsze.  
  
##  <a name="serialize"></a>CDockingManager::Serialize  
 Zapisuje dokowania Menedżera do archiwum.  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`ar`  
 Odwołanie do obiektu archiwum.  
  
### <a name="remarks"></a>Uwagi  
 Pisanie dokowania Menedżera do archiwum obejmuje określenie, ile dokujące paski sterowania oraz suwaki i zapisywanie paski sterowania, mini ramki paski autohide — i paski z kartami MDI do archiwum.  
  
##  <a name="setautohidezorder"></a>CDockingManager::SetAutohideZOrder  
 Ustawia rozmiar, szerokość i wysokość paski sterowania i okienko określony.  
  
```  
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pAHDockingBar`  
 Wskaźnik do okienka dokującego.  
  
##  <a name="setdockingmode"></a>CDockingManager::SetDockingMode  
 Ustawia tryb dokowania.  
  
```  
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,  
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```  
  
### <a name="parameters"></a>Parametry  
 `dockMode`  
 Określa nowy tryb dokowania. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
 `theme`  
 Określa motyw do zastosowania w przypadku znaczniki inteligentnego dokowania. Może być jedną z następujących wartości: AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania tej metody statycznej można ustawić trybu dokowania.  
  
 `dockMode`może to być jedna z następujących wartości:  
  
- `DT_STANDARD`-Dokowanie tryb zgodnie z implementacją w Visual Studio .NET 2003 standard. Okienka są przeciągane bez kontekstu przeciągania.  
  
- `DT_IMMEDIATE`— Natychmiastowe trybie dokowania jako implementowana w programie Microsoft Visio. Okienka są przeciągane z kontekstem przeciągania, ale są wyświetlane nie znaczniki.  
  
- `DT_SMART`-Inteligentne tryb dokowania, zgodnie z implementacją w programie Visual Studio 2005. Okienka są przeciągane z kontekstem przeciągania i są wyświetlane znaczniki inteligentne który Pokaż, gdzie może być zadokowany okienka.  
  
##  <a name="setdockstate"></a>CDockingManager::SetDockState  
 Ustawia stan dokujące paski sterowania, mini ramki i paski autohide —.  
  
```  
virtual void SetDockState();
```  
  
##  <a name="setprintpreviewmode"></a>CDockingManager::SetPrintPreviewMode  
 Ustawia tryb podglądu wydruku pasków, które są wyświetlane w podglądzie wydruku.  
  
```  
void SetPrintPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bPreview`  
 `TRUE`Jeśli ustawiono tryb podglądu wydruku; `FALSE` inaczej.  
  
 [in]`pState`  
 Wskaźnik do stanu wersji zapoznawczej. Ten parametr nie jest używany.  
  
##  <a name="setsmartdockingparams"></a>CDockingManager::SetSmartDockingParams  
 Ustawia parametrów, które określają zachowanie inteligentne dokowania.  
  
```  
static void SetSmartDockingParams(CSmartDockingInfo& params);
```  
  
### <a name="parameters"></a>Parametry  
 [w, out]`params`  
 Definiuje parametry inteligentne dokowania.  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę można wywołać, jeśli chcesz dostosować wygląd, kolor lub kształt znaczniki inteligentnego dokowania.  
  
 Aby użyć domyślnego wyglądu znaczniki inteligentnego dokowania, przekaż wystąpienie niezainicjowanej [klasy CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) do `params`.  
  
##  <a name="showdelayshowminiframes"></a>CDockingManager::ShowDelayShowMiniFrames  
 Pokazuje lub ukrywa windows mini ramek.  
  
```  
void ShowDelayShowMiniFrames(BOOL bshow);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bShow`  
 `TRUE`Aby uaktywnić oknie pokazano ramki; `FALSE to` ukryć ramki okna.  
  
##  <a name="showpanes"></a>CDockingManager::ShowPanes  
 Wyświetlenie lub ukrycie okienka pasków sterowania i autohide —.  
  
```  
virtual BOOL ShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bShow`  
 `TRUE`Aby pokazać okienka; `FALSE to` ukrywanie okienka.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze `FALSE`.  
  
##  <a name="startsdocking"></a>CDockingManager::StartSDocking  
 Uruchamia inteligentne dokowania określone okno zgodnie z wyrównanie inteligentne Menedżera dokowania.  
  
```  
void StartSDocking(CWnd* pDockingWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDockingWnd`  
 Wskaźnik do okna dokowania.  
  
##  <a name="stopsdocking"></a>CDockingManager::StopSDocking  
 Zatrzymuje inteligentne dokowania.  
  
```  
void StopSDocking();
```  
  
##  <a name="getsmartdockingtheme"></a>CDockingManager::GetSmartDockingTheme  
 Metoda statyczna zwraca motyw używany do wyświetlania znaczniki inteligentnego dokowania.  
  
```  
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości: AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Klasa CFrameWndEx](../../mfc/reference/cframewndex-class.md)   
 [Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)   
 [Klasa CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)
