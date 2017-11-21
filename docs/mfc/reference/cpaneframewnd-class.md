---
title: Klasa CPaneFrameWnd | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd::AddPane
- AFXPANEFRAMEWND/CPaneFrameWnd::AddRemovePaneFromGlobalList
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustPaneFrames
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcBorderSize
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcExpectedDockedRect
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeAttached
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeDockedToPane
- AFXPANEFRAMEWND/CPaneFrameWnd::CheckGripperVisibility
- AFXPANEFRAMEWND/CPaneFrameWnd::ConvertToTabbedDocument
- AFXPANEFRAMEWND/CPaneFrameWnd::Create
- AFXPANEFRAMEWND/CPaneFrameWnd::CreateEx
- AFXPANEFRAMEWND/CPaneFrameWnd::DockPane
- AFXPANEFRAMEWND/CPaneFrameWnd::FindFloatingPaneByID
- AFXPANEFRAMEWND/CPaneFrameWnd::FrameFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionHeight
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionText
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingMode
- AFXPANEFRAMEWND/CPaneFrameWnd::GetFirstVisiblePane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::GetParent
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPinState
- AFXPANEFRAMEWND/CPaneFrameWnd::GetRecentFloatingRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetVisiblePaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::HitTest
- AFXPANEFRAMEWND/CPaneFrameWnd::IsCaptured
- AFXPANEFRAMEWND/CPaneFrameWnd::IsDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollDown
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollUp
- AFXPANEFRAMEWND/CPaneFrameWnd::KillDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::LoadState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnBeforeDock
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDockToRecentPos
- AFXPANEFRAMEWND/CPaneFrameWnd::OnKillRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnMovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::OnPaneRecalcLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::OnSetRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnShowPane
- AFXPANEFRAMEWND/CPaneFrameWnd::PaneFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::Pin
- AFXPANEFRAMEWND/CPaneFrameWnd::RedrawAll
- AFXPANEFRAMEWND/CPaneFrameWnd::RemoveNonValidPanes
- AFXPANEFRAMEWND/CPaneFrameWnd::RemovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::ReplacePane
- AFXPANEFRAMEWND/CPaneFrameWnd::SaveState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetCaptionButtons
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::SetPreDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SizeToContent
- AFXPANEFRAMEWND/CPaneFrameWnd::StartTearOff
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentDockSiteInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentTabRelatedInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::OnCheckRollState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDrawBorder
- AFXPANEFRAMEWND/CPaneFrameWnd::m_bUseSaveBits
dev_langs: C++
helpviewer_keywords:
- CPaneFrameWnd [MFC], AddPane
- CPaneFrameWnd [MFC], AddRemovePaneFromGlobalList
- CPaneFrameWnd [MFC], AdjustLayout
- CPaneFrameWnd [MFC], AdjustPaneFrames
- CPaneFrameWnd [MFC], CalcBorderSize
- CPaneFrameWnd [MFC], CalcExpectedDockedRect
- CPaneFrameWnd [MFC], CanBeAttached
- CPaneFrameWnd [MFC], CanBeDockedToPane
- CPaneFrameWnd [MFC], CheckGripperVisibility
- CPaneFrameWnd [MFC], ConvertToTabbedDocument
- CPaneFrameWnd [MFC], Create
- CPaneFrameWnd [MFC], CreateEx
- CPaneFrameWnd [MFC], DockPane
- CPaneFrameWnd [MFC], FindFloatingPaneByID
- CPaneFrameWnd [MFC], FrameFromPoint
- CPaneFrameWnd [MFC], GetCaptionHeight
- CPaneFrameWnd [MFC], GetCaptionRect
- CPaneFrameWnd [MFC], GetCaptionText
- CPaneFrameWnd [MFC], GetDockingManager
- CPaneFrameWnd [MFC], GetDockingMode
- CPaneFrameWnd [MFC], GetFirstVisiblePane
- CPaneFrameWnd [MFC], GetHotPoint
- CPaneFrameWnd [MFC], GetPane
- CPaneFrameWnd [MFC], GetPaneCount
- CPaneFrameWnd [MFC], GetParent
- CPaneFrameWnd [MFC], GetPinState
- CPaneFrameWnd [MFC], GetRecentFloatingRect
- CPaneFrameWnd [MFC], GetVisiblePaneCount
- CPaneFrameWnd [MFC], HitTest
- CPaneFrameWnd [MFC], IsCaptured
- CPaneFrameWnd [MFC], IsDelayShow
- CPaneFrameWnd [MFC], IsRollDown
- CPaneFrameWnd [MFC], IsRollUp
- CPaneFrameWnd [MFC], KillDockingTimer
- CPaneFrameWnd [MFC], LoadState
- CPaneFrameWnd [MFC], OnBeforeDock
- CPaneFrameWnd [MFC], OnDockToRecentPos
- CPaneFrameWnd [MFC], OnKillRollUpTimer
- CPaneFrameWnd [MFC], OnMovePane
- CPaneFrameWnd [MFC], OnPaneRecalcLayout
- CPaneFrameWnd [MFC], OnSetRollUpTimer
- CPaneFrameWnd [MFC], OnShowPane
- CPaneFrameWnd [MFC], PaneFromPoint
- CPaneFrameWnd [MFC], Pin
- CPaneFrameWnd [MFC], RedrawAll
- CPaneFrameWnd [MFC], RemoveNonValidPanes
- CPaneFrameWnd [MFC], RemovePane
- CPaneFrameWnd [MFC], ReplacePane
- CPaneFrameWnd [MFC], SaveState
- CPaneFrameWnd [MFC], SetCaptionButtons
- CPaneFrameWnd [MFC], SetDelayShow
- CPaneFrameWnd [MFC], SetDockingManager
- CPaneFrameWnd [MFC], SetDockingTimer
- CPaneFrameWnd [MFC], SetDockState
- CPaneFrameWnd [MFC], SetHotPoint
- CPaneFrameWnd [MFC], SetPreDockState
- CPaneFrameWnd [MFC], SizeToContent
- CPaneFrameWnd [MFC], StartTearOff
- CPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
- CPaneFrameWnd [MFC], OnCheckRollState
- CPaneFrameWnd [MFC], OnDrawBorder
- CPaneFrameWnd [MFC], m_bUseSaveBits
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
caps.latest.revision: "28"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6e115e173d88961d24ed42990ec7bd3d863a404f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cpaneframewnd-class"></a>Klasa CPaneFrameWnd
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Implementuje okno ramowe minimalnej, który zawiera jedno okienko. Okienko wypełnia obszaru klienckiego okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPaneFrameWnd : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPaneFrameWnd::AddPane](#addpane)|Dodaje okienko.|  
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|Dodaje lub usuwa okienko z globalnej listy.|  
|[CPaneFrameWnd::AdjustLayout](#adjustlayout)|Dostosowuje układ okno ramowe minimalnej.|  
|[CPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)||  
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|Oblicza rozmiar obramowania mini ramki okna.|  
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Oblicz oczekiwanego prostokąt zadokowanych okien.|  
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|Określa, czy bieżące okienko może być zadokowany do innego okienka lub ramki okna.|  
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Określa, czy okno ramowe minimalna może być zadokowany do okienka.|  
|[CPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)||  
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|Konwertuje dokument z kartami okienka.|  
|[CPaneFrameWnd::Create](#create)|Tworzy okno ramowe minimalnej i dołącza go do `CPaneFrameWnd` obiektu.|  
|[CPaneFrameWnd::CreateEx](#createex)|Tworzy okno ramowe minimalnej i dołącza go do `CPaneFrameWnd` obiektu.|  
|[CPaneFrameWnd::DockPane](#dockpane)|Stacje dokujące okienko.|  
|[CPaneFrameWnd::FindFloatingPaneByID](#findfloatingpanebyid)|Znajduje okienka o identyfikatorze określonego formantu w globalnej listy przestawne okienka.|  
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|Wyszukuje okno ramowe mini zawierające punkt dostarczone przez użytkownika.|  
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|Zwraca wysokość minimalna ramki tytuł okna.|  
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|Oblicza prostokątem tytuł okna mini ramki.|  
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|Zwraca tekst podpisu.|  
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||  
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|Zwraca tryb dokowania.|  
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Zwraca pierwszy widoczne okienko zawarte w oknie ramowym minimalnej.|  
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||  
|[CPaneFrameWnd::GetPane](#getpane)|Zwraca okienko, w którym znajduje się w oknie ramowym minimalnej.|  
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|Zwraca liczbę okienka, które są zawarte w oknie ramowym minimalnej.|  
|[CPaneFrameWnd::GetParent](#getparent)||  
|[CPaneFrameWnd::GetPinState](#getpinstate)||  
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||  
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Zwraca liczbę widoczne okienka, które są zawarte w oknie ramowym minimalnej.|  
|[CPaneFrameWnd::HitTest](#hittest)|Określa, jaka część okno ramowe mini jest w danym momencie.|  
|[CPaneFrameWnd::IsCaptured](#iscaptured)||  
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||  
|[CPaneFrameWnd::IsRollDown](#isrolldown)|Określa, czy okno ramowe mini powinien wycofana w dół.|  
|[CPaneFrameWnd::IsRollUp](#isrollup)|Określa, czy okno ramowe mini powinny być rzutowane.|  
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|Zatrzymuje dokowania czasomierza.|  
|[CPaneFrameWnd::LoadState](#loadstate)|Ładuje stan okienka z rejestru.|  
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|Określa, czy jest możliwe dokowania.|  
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Stacje dokujące okno ramowe minimalnej na jego ostatniej pozycji.|  
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Zatrzymuje czasomierza rollup.|  
|[CPaneFrameWnd::OnMovePane](#onmovepane)|Przesuwa okno ramowe mini wskazanego przesunięcia.|  
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Dostosowuje układ zawartych w niej okienka.|  
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Ustawia czasomierza rollup.|  
|[CPaneFrameWnd::OnShowPane](#onshowpane)|Wywoływane przez platformę, gdy okienka w oknie ramowym mini jest ukryte lub wyświetlane.|  
|[CPaneFrameWnd::PaneFromPoint](#panefrompoint)|Zwraca okienko, jeśli zawiera ona punkt dostarczone przez użytkownika w oknie ramowym minimalnej.|  
|[CPaneFrameWnd::Pin](#pin)||  
|`CPaneFrameWnd::PreTranslateMessage`|Używane przez klasę [CWinApp](../../mfc/reference/cwinapp-class.md) tłumaczenie komunikaty okna przed wysłaniem do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje systemu Windows.|  
|[CPaneFrameWnd::RedrawAll](#redrawall)|Ponownie rysuje wszystkich okien ramowych minimalnej.|  
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Wywoływane przez platformę, by usunąć okienka nie jest ważna.|  
|[CPaneFrameWnd::RemovePane](#removepane)|Usuwa okienko z okna mini ramki.|  
|[CPaneFrameWnd::ReplacePane](#replacepane)|Zastępuje jedno okienko na inny.|  
|[CPaneFrameWnd::SaveState](#savestate)|Zapisuje stan okienka w rejestrze.|  
|`CPaneFrameWnd::Serialize`|Odczytuje i zapisuje ten obiekt z lub do archiwum.|  
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|Ustawia podpis przycisków.|  
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||  
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||  
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|Ustawia czasomierz dokowania.|  
|[CPaneFrameWnd::SetDockState](#setdockstate)|Ustawia stan dokowania.|  
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||  
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|Wywoływane przez platformę, by ustawić predocking stanu.|  
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|Dopasowuje rozmiar okno ramowe mini tak, aby rozmiar odpowiednikiem zawartych w niej okienka.|  
|[CPaneFrameWnd::StartTearOff](#starttearoff)|Rys poza menu.|  
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||  
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|Określa, czy okno ramowe mini powinien wycofana w górę lub w dół.|  
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|Rysuje obramowanie okno ramowe minimalnej.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|Określa, czy można zarejestrować klasy okna z `CS_SAVEBITS` klasy stylu.|  
  
## <a name="remarks"></a>Uwagi  
 Tworzy automatycznie w ramach `CPaneFrameWnd` obiektu po przełączeniu okienko ze stanu zadokowania do stanu zmiennoprzecinkowych.  
  
 Okno ramowe mini mogą być przeciągnięte wraz z zawartością widoczne (natychmiastowe dokowanie) lub przy użyciu przeciągnij prostokąt (dokowanie standard). Tryb dokowania okienka kontener ramki mini określa ramki mini przez przeciąganie zachowanie. Aby uzyskać więcej informacji, zobacz [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).  
  
 Okno ramowe mini są wyświetlane przyciski na podpis zgodnie z styl zawartych w niej okienka. Jeśli okienko może być zamknięte ( [CBasePane::CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)), zawiera przycisk Zamknij. Jeśli okienko `AFX_CBRS_AUTO_ROLLUP` stylu, wyświetla numeru pin.  
  
 Jeśli pochodzi z klasy `CPaneFrameWnd`, należy wskazać platformę jak go utworzyć. Utwórz klasę przez zastąpienie [CPane::CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe), lub ustaw `CPane::m_pMiniFrameRTC` — członek, którą wskazuje informacje o klasie czasu wykonywania dla klasy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPaneFrameWnd`   
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxPaneFrameWnd.h  
  
##  <a name="addpane"></a>CPaneFrameWnd::AddPane  
 Dodaje okienko.  
  
```  
virtual void AddPane(CBasePane* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
 Okienko, aby dodać.  
  
##  <a name="addremovepanefromgloballist"></a>CPaneFrameWnd::AddRemovePaneFromGlobalList  
 Dodaje lub usuwa okienko z globalnej listy.  
  
```  
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,  
    BOOL bAdd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
 Okienko, aby dodać lub usunąć.  
  
 [in]`bAdd`  
 Jeśli zera, należy dodać okienka. Jeśli jest to 0, Usuń okienko.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli metoda zakończyło się pomyślnie; w przeciwnym razie 0.  
  
##  <a name="adjustlayout"></a>CPaneFrameWnd::AdjustLayout  
 Dostosowuje układ okno ramowe minimalnej.  
  
```  
virtual void AdjustLayout();
```  
  
##  <a name="adjustpaneframes"></a>CPaneFrameWnd::AdjustPaneFrames  

  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="calcbordersize"></a>CPaneFrameWnd::CalcBorderSize  
 Oblicza rozmiar obramowania dla mini okno.  
  
```  
virtual void CalcBorderSize(CRect& rectBorderSize) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rectBorderSize`  
 Zawiera rozmiar wyrażony w pikselach obramowania mini okno.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, by Oblicz rozmiar obramowania mini okno. Rozmiar zwróconego zależy od czy mini okno zawiera pasek narzędzi czy [CDockablePane](../../mfc/reference/cdockablepane-class.md).  
  
##  <a name="calcexpecteddockedrect"></a>CPaneFrameWnd::CalcExpectedDockedRect  
 Oblicz oczekiwanego prostokąt zadokowanych okien.  
  
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
 Wskaźnik do okna, aby dokowania.  
  
 [in]`ptMouse`  
 Lokalizacja myszy.  
  
 [out]`rectResult`  
 Obliczony prostokąt.  
  
 [out]`bDrawTab`  
 Jeśli `TRUE`, Rysuj karty. Jeśli `FALSE`, nie Rysuj karty.  
  
 [out]`ppTargetBar`  
 Wskaźnik do okienka docelowej.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda oblicza prostokąt okna zajmują użytkownika przeciągania okna do punktu określonego przez `ptMouse` i zadokowane go brak.  
  
##  <a name="canbeattached"></a>CPaneFrameWnd::CanBeAttached  
 Określa, czy bieżące okienko może być zadokowany do innego okienka lub ramki okna.  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko może być zadokowany do innego okienka lub ramki okna; w przeciwnym razie `FALSE`.  
  
##  <a name="canbedockedtopane"></a>CPaneFrameWnd::CanBeDockedToPane  
 Określa, czy okno ramowe minimalna może być zadokowany do okienka.  
  
```  
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDockingBar`  
 Okienko.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli można zadokowana mini ramki `pDockingBar`; w przeciwnym razie wartość 0.  
  
##  <a name="checkgrippervisibility"></a>CPaneFrameWnd::CheckGripperVisibility  

  
```  
virtual void CheckGripperVisibility();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="converttotabbeddocument"></a>CPaneFrameWnd::ConvertToTabbedDocument  
 Konwertuje dokument z kartami okienka.  
  
```  
virtual void ConvertToTabbedDocument();
```  
  
##  <a name="create"></a>CPaneFrameWnd::Create  
 Tworzy mini okno i dołącza go do [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) obiektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszWindowName`  
 Określa tekst do wyświetlenia na mini okno.  
  
 [in]`dwStyle`  
 Określa styl okna. Aby uzyskać więcej informacji, zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in]`rect`  
 Określa początkowy rozmiar i położenie okna mini.  
  
 [in] [out]`pParentWnd`  
 Określa ramki mini okno nadrzędne. Ta wartość nie może być `NULL`.  
  
 [in] [out]`pContext`  
 Określa kontekst zdefiniowane przez użytkownika.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okno została utworzona pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Mini okno jest tworzony w dwóch krokach. Najpierw tworzy platformę `CPaneFrameWnd` obiektu. Po drugie, wywołuje `Create` utworzyć mini okno systemu Windows i dołączenie go do `CPaneFrameWnd` obiektu.  
  
##  <a name="createex"></a>CPaneFrameWnd::CreateEx  
 Tworzy mini okno i dołącza go do [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) obiektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`dwStyleEx`  
 Określa styl okna rozszerzonej. Aby uzyskać więcej informacji, zobacz [rozszerzone Style okna](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)  
  
 [in]`lpszWindowName`  
 Określa tekst do wyświetlenia na mini okno.  
  
 [in]`dwStyle`  
 Określa styl okna. Aby uzyskać więcej informacji, zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in]`rect`  
 Określa początkowy rozmiar i położenie okna mini.  
  
 [in] [out]`pParentWnd`  
 Określa ramki mini okno nadrzędne. Ta wartość nie może być `NULL`.  
  
 [in] [out]`pContext`  
 Określa kontekst zdefiniowane przez użytkownika.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okno została utworzona pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Mini okno jest tworzony w dwóch krokach. Najpierw tworzy platformę `CPaneFrameWnd` obiektu. Po drugie, wywołuje `Create` utworzyć mini okno systemu Windows i dołączenie go do `CPaneFrameWnd` obiektu.  
  
##  <a name="dockpane"></a>CPaneFrameWnd::DockPane  
 Stacje dokujące okienko.  
  
```  
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>Parametry  
 [out]`bWasDocked`  
 `TRUE`Jeśli już zostało zadokowane okienku; w przeciwnym razie `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja zakończyła się powodzeniem, `CDockablePane` czy okienku zostało zadokowane do; w przeciwnym razie `NULL`.  
  
##  <a name="findfloatingpanebyid"></a>CPaneFrameWnd::FindFloatingPaneByID  
 Znajduje okienka o identyfikatorze określonego formantu w globalnej listy przestawne okienka.  
  
```  
static CBasePane* FindFloatingPaneByID(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nID`  
 Reprezentuje identyfikator formantu okienka ma zostać znaleziony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Okienko o identyfikatorze określony formant; w przeciwnym razie `NULL`, jeśli nie okienku ma identyfikator określonego formantu.  
  
##  <a name="framefrompoint"></a>CPaneFrameWnd::FrameFromPoint  
 Wyszukuje okno ramowe minimalnej, który zawiera określony punkt.  
  
```  
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,  
    int nSensitivity,  
    CPaneFrameWnd* pFrameToExclude = NULL,  
    BOOL bFloatMultiOnly = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pt`  
 Punkt we współrzędnych ekranu.  
  
 [in]`nSensitivity`  
 Zwiększ obszar wyszukiwania okno ramowe mini przez ten rozmiar. Okno ramowe mini spełnia kryteria wyszukiwania, jeśli znajduje się w obszarze zwiększona danego punktu.  
  
 [in]`pFrameToExclude`  
 Określa okno ramowe mini do wykluczenia z wyszukiwania.  
  
 [in]`bFloatMultiOnly`  
 Jeśli `TRUE`, wyszukiwanie tylko okien ramowych minimalnej, które mają `CBRS_FLOAT_MULTI` stylu. Jeśli `FALSE`, wyszukiwanie wszystkich okien ramowych minimalnej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do mini ramkę okna zawierającą `pt`; w przeciwnym razie `NULL`.  
  
##  <a name="getcaptionheight"></a>CPaneFrameWnd::GetCaptionHeight  
 Zwraca wysokość minimalna ramki tytuł okna.  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wysokość w pikselach okno ramowe minimalnej.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby określić wysokość minimalna ramki okna. Domyślnie, wysokość jest ustawiona wartość `SM_CYSMCAPTION`. Aby uzyskać więcej informacji, zobacz [funkcja GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385).  
  
##  <a name="getcaptionrect"></a>CPaneFrameWnd::GetCaptionRect  
 Oblicza prostokątem tytuł okna mini ramki.  
  
```  
virtual void GetCaptionRect(CRect& rectCaption) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rectCaption`  
 Zawiera rozmiar i położenie tytuł okna mini ramki, we współrzędnych ekranu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, aby obliczyć prostokątem tytuł okna mini ramki.  
  
##  <a name="getcaptiontext"></a>CPaneFrameWnd::GetCaptionText  
 Zwraca tekst podpisu.  
  
```  
virtual CString GetCaptionText();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Tekst podpisu okno ramowe minimalnej.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy Wyświetla tekst podpisu.  
  
##  <a name="getdockingmanager"></a>CPaneFrameWnd::GetDockingManager  

  
```  
CDockingManager* GetDockingManager() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getdockingmode"></a>CPaneFrameWnd::GetDockingMode  
 Zwraca tryb dokowania.  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Tryb dokowania. Jedna z następujących wartości:  
  
- `DT_STANDARD`  
  
- `DT_IMMEDIATE`  
  
- `DT_SMART`  
  
##  <a name="getfirstvisiblepane"></a>CPaneFrameWnd::GetFirstVisiblePane  
 Zwraca pierwszy widoczne okienko zawarte w oknie ramowym minimalnej.  
  
```  
virtual CWnd* GetFirstVisiblePane() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszego okienka w oknie mini ramki lub `NULL` Jeśli okno ramowe minimalnej nie zawiera żadnych okienka.  
  
##  <a name="gethotpoint"></a>CPaneFrameWnd::GetHotPoint  

  
```  
CPoint GetHotPoint() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getpane"></a>CPaneFrameWnd::GetPane  
 Zwraca okienko, w którym znajduje się w oknie ramowym minimalnej.  
  
```  
virtual CWnd* GetPane() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Okienko, w którym znajduje się w ramce mini lub `NULL` Jeśli okno ramowe minimalnej nie zawiera żadnych okienka.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getpanecount"></a>CPaneFrameWnd::GetPaneCount  
 Zwraca liczbę okienka, które są zawarte w oknie ramowym minimalnej.  
  
```  
virtual int GetPaneCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba okienka w oknie ramowym minimalnej. Ta wartość może być równa zero.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getparent"></a>CPaneFrameWnd::GetParent  

  
```  
CWnd* GetParent();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getpinstate"></a>CPaneFrameWnd::GetPinState  

  
```  
BOOL GetPinState() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getrecentfloatingrect"></a>CPaneFrameWnd::GetRecentFloatingRect  

  
```  
CRect GetRecentFloatingRect() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getvisiblepanecount"></a>CPaneFrameWnd::GetVisiblePaneCount  
 Zwraca liczbę widoczne okienka, które są zawarte w oknie ramowym minimalnej.  
  
```  
virtual int GetVisiblePaneCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba widocznych okienka.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="hittest"></a>CPaneFrameWnd::HitTest  
 Określa, jaka część okno ramowe mini jest w danym momencie.  
  
```  
virtual LRESULT HitTest(
    CPoint point,  
    BOOL bDetectCaption);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`point`  
 Punkt do testowania.  
  
 [in]`bDetectCaption`  
 Jeśli `TRUE`, sprawdź punktu przed podpis. Jeśli `FALSE`, zignorować podpis.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jedna z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|`HTNOWHERE`|Punkt znajduje się poza okno ramowe minimalnej.|  
|`HTCLIENT`|Punkt znajduje się w obszarze klienckim.|  
|`HTCAPTION`|Punkt znajduje się na podpis.|  
|`HTTOP`|Punkt znajduje się u góry.|  
|`HTTOPLEFT`|Punkt znajduje się u góry po lewej.|  
|`HTTOPRIGHT`|Punkt znajduje się u góry po prawej.|  
|`HTLEFT`|Punkt znajduje się po lewej stronie.|  
|`HTRIGHT`|Punkt znajduje się w prawym rogu.|  
|`HTBOTTOM`|Punkt znajduje się na dole.|  
|`HTBOTTOMLEFT`|Punkt znajduje się w lewym dolnym rogu.|  
|`HTBOTTOMRIGHT`|Punkt znajduje się w prawym dolnym rogu.|  
  
##  <a name="iscaptured"></a>CPaneFrameWnd::IsCaptured  

  
```  
BOOL IsCaptured() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isdelayshow"></a>CPaneFrameWnd::IsDelayShow  

  
```  
BOOL IsDelayShow() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isrolldown"></a>CPaneFrameWnd::IsRollDown  
 Określa, czy okno ramowe mini powinien wycofana w dół.  
  
```  
virtual BOOL IsRollDown() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okno ramowe minimalnej musi wycofana. w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, by określić, czy okno ramowe mini powinien wycofana w dół. Funkcja rollup/rolldown jest włączona dla okno ramowe minimalnej, jeśli zawiera on co najmniej jeden okienku, który ma `AFX_CBRS_AUTO_ROLLUP` flagi. Ta flaga jest ustawiana po utworzeniu okienko. Aby uzyskać więcej informacji, zobacz [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 Domyślnie platformę sprawdza, czy wskaźnik myszy znajduje się wewnątrz ramki mini okno prostokątem ustalenie, czy okno ma być przetwarzane w dół. Można zmienić to zachowanie w klasie pochodnej.  
  
##  <a name="isrollup"></a>CPaneFrameWnd::IsRollUp  
 Określa, czy okno ramowe mini powinny być rzutowane.  
  
```  
virtual BOOL IsRollUp() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okno ramowe minimalnej musi rzutowane; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, by określić, czy okno ramowe mini powinny być rzutowane. Funkcja rollup/rolldown jest włączona dla okno ramowe minimalnej, jeśli zawiera on co najmniej jeden okienku, który ma `AFX_CBRS_AUTO_ROLLUP` flagi. Ta flaga jest ustawiana po utworzeniu okienko. Aby uzyskać więcej informacji, zobacz [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 Domyślnie platformę sprawdza, czy wskaźnik myszy znajduje się wewnątrz ramki mini okno prostokątem ustalenie, czy okno ma być rzutowane. Można zmienić to zachowanie w klasie pochodnej.  
  
##  <a name="killdockingtimer"></a>CPaneFrameWnd::KillDockingTimer  
 Zatrzymuje dokowania czasomierza.  
  
```  
void KillDockingTimer();
```  
  
##  <a name="loadstate"></a>CPaneFrameWnd::LoadState  
 Ładuje stan okienka z rejestru.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 Nazwa profilu.  
  
 [in]`uiID`  
 Identyfikator okienka.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli stan okienka został załadowany pomyślnie; w przeciwnym razie `FALSE`.  
  
##  <a name="m_busesavebits"></a>CPaneFrameWnd::m_bUseSaveBits  
 Określa, czy rejestrowanie klasy okna, które ma `CS_SAVEBITS` klasy stylu.  
  
```  
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw ten statyczny element członkowski `TRUE` można zarejestrować klasy okna mini ramki, który ma `CS_SAVEBITS` stylu. Może to pomóc w zmniejszeniu, migotanie, gdy użytkownik przeciąga okno ramowe minimalnej.  
  
##  <a name="onbeforedock"></a>CPaneFrameWnd::OnBeforeDock  
 Określa, czy jest możliwe dokowania.  
  
```  
virtual BOOL OnBeforeDock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli dokowanie jest możliwe; w przeciwnym razie `FALSE`.  
  
##  <a name="oncheckrollstate"></a>CPaneFrameWnd::OnCheckRollState  
 Określa, czy okno ramowe mini powinien wycofana w górę lub w dół.  
  
```  
virtual void OnCheckRollState();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, by określić, czy okno ramowe mini powinien wycofana w górę lub w dół.  
  
 Domyślnie struktura wywołuje [CPaneFrameWnd::IsRollUp](#isrollup) i [CPaneFrameWnd::IsRollDown](#isrolldown) tylko rozciąga się i przywraca okno ramowe minimalnej. Mogą przesłaniać tę metodę w klasie pochodnej, aby użyć innego efektem.  
  
##  <a name="ondocktorecentpos"></a>CPaneFrameWnd::OnDockToRecentPos  
 Stacje dokujące okno ramowe minimalnej na jego ostatniej pozycji.  
  
```  
virtual void OnDockToRecentPos();
```  
  
##  <a name="ondrawborder"></a>CPaneFrameWnd::OnDrawBorder  
 Rysuje obramowanie okno ramowe minimalnej.  
  
```  
virtual void OnDrawBorder(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Kontekst urządzenia używany do rysowania obramowania.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, by narysować obramowanie okno ramowe minimalnej.  
  
##  <a name="onkillrolluptimer"></a>CPaneFrameWnd::OnKillRollUpTimer  
 Zatrzymuje czasomierza rollup.  
  
```  
virtual void OnKillRollUpTimer();
```  
  
##  <a name="onmovepane"></a>CPaneFrameWnd::OnMovePane  
 Przesuwa okno ramowe mini wskazanego przesunięcia.  
  
```  
virtual void OnMovePane(
    CPane* pBar,  
    CPoint ptOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
 Wskaźnik do okienka (zignorowany).  
  
 [in]`ptOffset`  
 Przesunięcie, przez którą chcesz przenieść okienko.  
  
##  <a name="onpanerecalclayout"></a>CPaneFrameWnd::OnPaneRecalcLayout  
 Dostosowuje układ okienka w oknie ramowym minimalnej.  
  
```  
virtual void OnPaneRecalcLayout();
```  
  
### <a name="remarks"></a>Uwagi  
 Platformę wywołuje tę metodę, gdy należy dostosować układ okienka w oknie ramowym minimalnej.  
  
 Domyślnie okienku znajduje się do pokrycia obszaru klienckiego pełną okno ramowe minimalnej.  
  
##  <a name="onsetrolluptimer"></a>CPaneFrameWnd::OnSetRollUpTimer  
 Ustawia czasomierza rollup.  
  
```  
virtual void OnSetRollUpTimer();
```  
  
##  <a name="onshowpane"></a>CPaneFrameWnd::OnShowPane  
 Wywoływane przez platformę, gdy okienka w oknie ramowym mini jest ukryte lub wyświetlane.  
  
```  
virtual void OnShowPane(
    CDockablePane* pBar,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
 Okienko, który jest pokazywany lub ukryty.  
  
 [in]`bShow`  
 `TRUE`Jeśli jest wyświetlane okienku; `FALSE` Jeśli okienko jest ukrywane.  
  
### <a name="remarks"></a>Uwagi  
 Wywoływane przez platformę, gdy okienka w oknie ramowym mini jest pokazywany lub ukryty. Domyślna implementacja nie działa.  
  
##  <a name="pin"></a>CPaneFrameWnd::Pin  

  
```  
void Pin(BOOL bPin = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bPin`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="panefrompoint"></a>CPaneFrameWnd::PaneFromPoint  
 Zwraca okienko, jeśli zawiera ona punkt dostarczone przez użytkownika w oknie ramowym minimalnej.  
  
```  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    BOOL bCheckVisibility);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`point`  
 Punkt, który użytkownik kliknął we współrzędnych ekranu.  
  
 [in]`nSensitivity`  
 Ten parametr nie jest używany.  
  
 [in]`bCheckVisibility`  
 `TRUE`Aby określić, że powinny być zwracane tylko widoczne okienka; w przeciwnym razie `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Okienko, w którym użytkownik kliknął, lub `NULL` Jeśli okienko nie istnieje w tej lokalizacji.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę w celu uzyskania okienku, który zawiera danego punktu.  
  
##  <a name="redrawall"></a>CPaneFrameWnd::RedrawAll  
 Ponownie rysuje wszystkich okien ramowych minimalnej.  
  
```  
static void RedrawAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda aktualizacji wszystkich okien ramowych mini wywołując [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) dla każdego okna.  
  
##  <a name="removenonvalidpanes"></a>CPaneFrameWnd::RemoveNonValidPanes  
 Wywoływane przez platformę, by usunąć okienka nie jest ważna.  
  
```  
virtual void RemoveNonValidPanes();
```  
  
##  <a name="removepane"></a>CPaneFrameWnd::RemovePane  
 Usuwa okienko z okna mini ramki.  
  
```  
virtual void RemovePane(
    CBasePane* pWnd,  
    BOOL bDestroy = FALSE,  
    BOOL bNoDelayedDestroy = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
 Wskaźnik do okienka do usunięcia.  
  
 [in]`bDestroy`  
 Określa, co się dzieje z okno ramowe minimalnej. Jeśli `bDestroy` jest `TRUE`, ta metoda niszczy okno ramowe mini natychmiast. Jeśli jest `FALSE`, ta metoda niszczy okno ramowe mini z pewnym opóźnieniem.  
  
 [in]`bNoDelayedDestroy`  
 Jeśli `TRUE`opóźnione zniszczenie jest wyłączona. Jeśli `FALSE`opóźnione zniszczenie jest włączona.  
  
### <a name="remarks"></a>Uwagi  
 Platformę można zniszczyć okna ramowe mini natychmiast, albo z pewnym opóźnieniem. Niszczenie okien ramowych mini opóźnienia należy przekazać `FALSE` w `bNoDelayedDestroy` parametru. Opóźnione zniszczenie występuje podczas przetwarzania w ramach `AFX_WM_CHECKEMPTYMINIFRAME` wiadomości.  
  
##  <a name="replacepane"></a>CPaneFrameWnd::ReplacePane  
 Zastępuje jedno okienko na inny.  
  
```  
virtual void ReplacePane(
    CBasePane* pBarOrg,  
    CBasePane* pBarReplaceWith);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBarOrg`  
 Wskaźnik do oryginalnego okienka.  
  
 [in]`pBarReplaceWith`  
 Wskaźnik do okienka zastępuje oryginalnego okienka.  
  
##  <a name="savestate"></a>CPaneFrameWnd::SaveState  
 Zapisuje stan okienka w rejestrze.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 Nazwa profilu.  
  
 [in]`uiID`  
 Identyfikator okienka.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli stan okienka została zapisana pomyślnie; w przeciwnym razie `FALSE`.  
  
##  <a name="setcaptionbuttons"></a>CPaneFrameWnd::SetCaptionButtons  
 Ustawia podpis przycisków.  
  
```  
virtual void SetCaptionButtons(DWORD dwButtons);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`dwButtons`  
 Alternatywy kombinację następujących wartości:  
  
- `AFX_CAPTION_BTN_CLOSE`  
  
- `AFX_CAPTION_BTN_PIN`  
  
- `AFX_CAPTION_BTN_MENU`  
  
- `AFX_CAPTION_BTN_CUSTOMIZE`  
  
##  <a name="setdelayshow"></a>CPaneFrameWnd::SetDelayShow  

  
```  
void SetDelayShow(BOOL bDelayShow);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bDelayShow`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setdockingmanager"></a>CPaneFrameWnd::SetDockingManager  

  
```  
void SetDockingManager(CDockingManager* pManager);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pManager`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setdockingtimer"></a>CPaneFrameWnd::SetDockingTimer  
 Ustawia czasomierz dokowania.  
  
```  
void SetDockingTimer(UINT nTimeOut);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nTimeOut`  
 Wartość limitu czasu w milisekundach.  
  
##  <a name="setdockstate"></a>CPaneFrameWnd::SetDockState  
 Ustawia stan dokowania.  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDockManager`  
 Wskaźnik do Menedżera dokowania.  
  
##  <a name="sethotpoint"></a>CPaneFrameWnd::SetHotPoint  

  
```  
void SetHotPoint(CPoint& ptNew);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`ptNew`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpredockstate"></a>CPaneFrameWnd::SetPreDockState  
 Wywoływane przez platformę, by ustawić predocking stanu.  
  
```  
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,  
    CBasePane* pBarToDock = NULL,  
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`preDockState`  
 Możliwe wartości:  
  
- `PDS_NOTHING`,  
  
- `PDS_DOCK_REGULAR`,  
  
- `PDS_DOCK_TO_TAB`  
  
 [in]`pBarToDock`  
 Wskaźnik do okienko, aby dokowania.  
  
 [in]`dockMethod`  
 Metoda dokowania. (Ten parametr jest ignorowany.)  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okno ramowe mini jest zadokowany; `FALSE` Jeśli jest zadokowany.  
  
##  <a name="sizetocontent"></a>CPaneFrameWnd::SizeToContent  
 Dopasowuje rozmiar okno ramowe minimalnej, aby była ona odpowiednikiem zawartych w niej okienka.  
  
```  
virtual void SizeToContent();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby dostosować rozmiar ramki mini okno, aby rozmiar okienka zawartych w niej.  
  
##  <a name="starttearoff"></a>CPaneFrameWnd::StartTearOff  
 Rys poza menu.  
  
```  
BOOL StartTearOff(CMFCPopu* pMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pMenu`  
 Wskaźnik do menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `FALSE`.  
  
##  <a name="storerecentdocksiteinfo"></a>CPaneFrameWnd::StoreRecentDockSiteInfo  

  
```  
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="storerecenttabrelatedinfo"></a>CPaneFrameWnd::StoreRecentTabRelatedInfo  

  
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
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)
