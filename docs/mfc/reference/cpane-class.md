---
title: Klasa CPane | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPane
- AFXPANE/CPane
- AFXPANE/CPane::AdjustSizeImmediate
- AFXPANE/CPane::AllocElements
- AFXPANE/CPane::AllowShowOnPaneMenu
- AFXPANE/CPane::CalcAvailableSize
- AFXPANE/CPane::CalcInsideRect
- AFXPANE/CPane::CalcRecentDockedRect
- AFXPANE/CPane::CalcSize
- AFXPANE/CPane::CanBeDocked
- AFXPANE/CPane::CanBeTabbedDocument
- AFXPANE/CPane::ConvertToTabbedDocument
- AFXPANE/CPane::CopyState
- AFXPANE/CPane::Create
- AFXPANE/CPane::CreateDefaultMiniframe
- AFXPANE/CPane::CreateEx
- AFXPANE/CPane::DockByMouse
- AFXPANE/CPane::DockPane
- AFXPANE/CPane::DockPaneStandard
- AFXPANE/CPane::DockToFrameWindow
- AFXPANE/CPane::DoesAllowSiblingBars
- AFXPANE/CPane::FloatPane
- AFXPANE/CPane::GetAvailableExpandSize
- AFXPANE/CPane::GetAvailableStretchSize
- AFXPANE/CPane::GetBorders
- AFXPANE/CPane::GetClientHotSpot
- AFXPANE/CPane::GetDockSiteRow
- AFXPANE/CPane::GetExclusiveRowMode
- AFXPANE/CPane::GetHotSpot
- AFXPANE/CPane::GetMinSize
- AFXPANE/CPane::GetPaneName
- AFXPANE/CPane::GetVirtualRect
- AFXPANE/CPane::IsChangeState
- AFXPANE/CPane::IsDragMode
- AFXPANE/CPane::IsInFloatingMultiPaneFrameWnd
- AFXPANE/CPane::IsLeftOf
- AFXPANE/CPane::IsResizable
- AFXPANE/CPane::IsTabbed
- AFXPANE/CPane::LoadState
- AFXPANE/CPane::MoveByAlignment
- AFXPANE/CPane::MovePane
- AFXPANE/CPane::OnAfterChangeParent
- AFXPANE/CPane::OnBeforeChangeParent
- AFXPANE/CPane::OnPressCloseButton
- AFXPANE/CPane::OnShowControlBarMenu
- AFXPANE/CPane::RecalcLayout
- AFXPANE/CPane::SaveState
- AFXPANE/CPane::SetActiveInGroup
- AFXPANE/CPane::SetBorders
- AFXPANE/CPane::SetClientHotSpot
- AFXPANE/CPane::SetDockState
- AFXPANE/CPane::SetExclusiveRowMode
- AFXPANE/CPane::SetMiniFrameRTC
- AFXPANE/CPane::SetMinSize
- AFXPANE/CPane::SetVirtualRect
- AFXPANE/CPane::StretchPaneDeferWndPos
- AFXPANE/CPane::ToggleAutoHide
- AFXPANE/CPane::UndockPane
- AFXPANE/CPane::UpdateVirtualRect
- AFXPANE/CPane::OnAfterDock
- AFXPANE/CPane::OnAfterFloat
- AFXPANE/CPane::OnBeforeDock
- AFXPANE/CPane::OnBeforeFloat
- AFXPANE/CPane::m_bHandleMinSize
- AFXPANE/CPane::m_recentDockInfo
dev_langs: C++
helpviewer_keywords:
- CPane [MFC], AdjustSizeImmediate
- CPane [MFC], AllocElements
- CPane [MFC], AllowShowOnPaneMenu
- CPane [MFC], CalcAvailableSize
- CPane [MFC], CalcInsideRect
- CPane [MFC], CalcRecentDockedRect
- CPane [MFC], CalcSize
- CPane [MFC], CanBeDocked
- CPane [MFC], CanBeTabbedDocument
- CPane [MFC], ConvertToTabbedDocument
- CPane [MFC], CopyState
- CPane [MFC], Create
- CPane [MFC], CreateDefaultMiniframe
- CPane [MFC], CreateEx
- CPane [MFC], DockByMouse
- CPane [MFC], DockPane
- CPane [MFC], DockPaneStandard
- CPane [MFC], DockToFrameWindow
- CPane [MFC], DoesAllowSiblingBars
- CPane [MFC], FloatPane
- CPane [MFC], GetAvailableExpandSize
- CPane [MFC], GetAvailableStretchSize
- CPane [MFC], GetBorders
- CPane [MFC], GetClientHotSpot
- CPane [MFC], GetDockSiteRow
- CPane [MFC], GetExclusiveRowMode
- CPane [MFC], GetHotSpot
- CPane [MFC], GetMinSize
- CPane [MFC], GetPaneName
- CPane [MFC], GetVirtualRect
- CPane [MFC], IsChangeState
- CPane [MFC], IsDragMode
- CPane [MFC], IsInFloatingMultiPaneFrameWnd
- CPane [MFC], IsLeftOf
- CPane [MFC], IsResizable
- CPane [MFC], IsTabbed
- CPane [MFC], LoadState
- CPane [MFC], MoveByAlignment
- CPane [MFC], MovePane
- CPane [MFC], OnAfterChangeParent
- CPane [MFC], OnBeforeChangeParent
- CPane [MFC], OnPressCloseButton
- CPane [MFC], OnShowControlBarMenu
- CPane [MFC], OnShowControlBarMenu
- CPane [MFC], RecalcLayout
- CPane [MFC], SaveState
- CPane [MFC], SetActiveInGroup
- CPane [MFC], SetBorders
- CPane [MFC], SetClientHotSpot
- CPane [MFC], SetDockState
- CPane [MFC], SetExclusiveRowMode
- CPane [MFC], SetMiniFrameRTC
- CPane [MFC], SetMinSize
- CPane [MFC], SetVirtualRect
- CPane [MFC], StretchPaneDeferWndPos
- CPane [MFC], ToggleAutoHide
- CPane [MFC], UndockPane
- CPane [MFC], UpdateVirtualRect
- CPane [MFC], OnAfterDock
- CPane [MFC], OnAfterFloat
- CPane [MFC], OnBeforeDock
- CPane [MFC], OnBeforeFloat
- CPane [MFC], m_bHandleMinSize
- CPane [MFC], m_recentDockInfo
ms.assetid: 5c651a64-3c79-4d94-9676-45f6402a6bc5
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e078f094e51b022bc697ba44eec47de1bf452c96
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cpane-class"></a>Klasa CPane
`CPane` Klasa jest rozszerzeniem [ccontrolbar — klasa](../../mfc/reference/ccontrolbar-class.md). Jeśli przeprowadzasz uaktualnienie istniejącego projektu MFC, należy zastąpić wszystkie wystąpienia `CControlBar` z `CPane`.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPane : public CBasePane  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CPane::~CPane`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPane::AdjustSizeImmediate](#adjustsizeimmediate)|Natychmiast ponownie oblicza układ okienka.|  
|[CPane::AllocElements](#allocelements)|Przydziela magazynu do użytku wewnętrznego.|  
|[CPane::AllowShowOnPaneMenu](#allowshowonpanemenu)|Określa, czy okienko wymienionej na liście generowanych przez środowisko uruchomieniowe okienka aplikacji.|  
|[CPane::CalcAvailableSize](#calcavailablesize)|Oblicza różnicę o rozmiarze określonym prostokąt i bieżący prostokąt okna.|  
|[CPane::CalcInsideRect](#calcinsiderect)|Oblicza wewnątrz prostokąta okienka, biorąc pod uwagę obramowanie i uchwyty.|  
|[CPane::CalcRecentDockedRect](#calcrecentdockedrect)|Oblicza ostatnio zadokowanych prostokąta.|  
|[CPane::CalcSize](#calcsize)|Oblicza rozmiar okienka.|  
|[CPane::CanBeDocked](#canbedocked)|Określa, czy okienko może być zadokowany w okienku określony podstawowy.|  
|[CPane::CanBeTabbedDocument](#canbetabbeddocument)|Określa, czy okienku można przekonwertować na dokument z kartami.|  
|[CPane::ConvertToTabbedDocument](#converttotabbeddocument)|Konwertuje dokument z kartami dokującego okienka.|  
|[CPane::CopyState](#copystate)|Kopiuje stan okienka. (Przesłania [CBasePane::CopyState](../../mfc/reference/cbasepane-class.md#copystate).)|  
|[CPane::Create](#create)|Tworzy pasek sterowania i dołącza go do `CPane` obiektu.|  
|[CPane::CreateDefaultMiniframe](#createdefaultminiframe)|Tworzy okno ramowe mini przestawne okienka.|  
|[CPane::CreateEx](#createex)|Tworzy pasek sterowania i dołącza go do `CPane` obiektu.|  
|`CPane::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|[CPane::DockByMouse](#dockbymouse)|Stacje dokujące okienko za pomocą myszy dokowanie metody.|  
|[CPane::DockPane](#dockpane)|Stacje dokujące okienko przestawne do podstawowej okienka.|  
|[CPane::DockPaneStandard](#dockpanestandard)|Stacje dokujące okienko przy użyciu konspektu dokowanie (standard).|  
|[CPane::DockToFrameWindow](#docktoframewindow)|Stacje dokujące okienko dokującego do ramki. (Przesłania `CBasePane::DockToFrameWindow`.)|  
|[CPane::DoesAllowSiblingBars](#doesallowsiblingbars)|Wskazuje, czy dokowany innego okienka w tym samym wierszu, gdy jest zadokowany bieżącego okienka.|  
|[CPane::FloatPane](#floatpane)|Pojawia się okienku.|  
|[CPane::GetAvailableExpandSize](#getavailableexpandsize)|Zwraca wartość, w pikselach, którą można rozwinąć okienka.|  
|[CPane::GetAvailableStretchSize](#getavailablestretchsize)|Zwraca wartość, w pikselach, którą można zmniejszyć okienka.|  
|[CPane::GetBorders](#getborders)|Zwraca szerokość obramowań okienka.|  
|[CPane::GetClientHotSpot](#getclienthotspot)|Zwraca *aktywnego* okienka.|  
|[CPane::GetDockSiteRow](#getdocksiterow)|Zwraca wiersz dokowania, w którym jest zadokowany okienka.|  
|[CPane::GetExclusiveRowMode](#getexclusiverowmode)|Określa, czy okienko jest w trybie wyłączności wiersza.|  
|[CPane::GetHotSpot](#gethotspot)|Zwraca punkt aktywny, który jest przechowywany w podstawowej `CMFCDragFrameImpl` obiektu.|  
|[CPane::GetMinSize](#getminsize)|Pobiera minimalny dozwolony rozmiar okienka.|  
|[CPane::GetPaneName](#getpanename)|Pobiera tytuł dla tego okienka.|  
|`CPane::GetResizeStep`|Używane wewnętrznie.|  
|`CPane::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CPane::GetVirtualRect](#getvirtualrect)|Pobiera *wirtualnego prostokąt* okienka.|  
|[CPane::IsChangeState](#ischangestate)|Zgodnie z okienka jest przenoszony, ta metoda analizuje pozycji okienka względem innych okienka, dokowania wierszy i okna ramowe minimalnej i zwraca odpowiednie `AFX_CS_STATUS` wartość.|  
|[CPane::IsDragMode](#isdragmode)|Określa, czy zostanie przeciągnięty okienka.|  
|[CPane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|Określa, czy okienka w oknie ramowym wielu okienka. (Przesłania `CBasePane::IsInFloatingMultiPaneFrameWnd`.)|  
|[CPane::IsLeftOf](#isleftof)|Określa, czy okienko pozostało (lub powyżej) określonego prostokąta.|  
|[CPane::IsResizable](#isresizable)|Określa, czy można zmienić rozmiar okienka. (Przesłania [CBasePane::IsResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|  
|[CPane::IsTabbed](#istabbed)|Określa, czy okienko włożono formantu okna z kartami. (Przesłania [CBasePane::IsTabbed](../../mfc/reference/cbasepane-class.md#istabbed).)|  
|[CPane::LoadState](#loadstate)|Ładuje stan okienka z rejestru. (Przesłania [CBasePane::LoadState](../../mfc/reference/cbasepane-class.md#loadstate).)|  
|[CPane::MoveByAlignment](#movebyalignment)|Przesuwa okienku i wirtualnych prostokąt określony.|  
|[CPane::MovePane](#movepane)|Przenosi okienka określonego prostokąta.|  
|[CPane::OnAfterChangeParent](#onafterchangeparent)|Wywoływane przez platformę, gdy element nadrzędny okienko zostanie zmieniony.|  
|[CPane::OnBeforeChangeParent](#onbeforechangeparent)|Wywoływane przez platformę, gdy element nadrzędny okienka ma zostać zmieniona.|  
|[CPane::OnPressCloseButton](#onpressclosebutton)|Wywoływane przez platformę, gdy użytkownik wybierze przycisk Zamknij na podpis dla tego okienka.|  
|`CPane::OnProcessDblClk`|Używane wewnętrznie.|  
|[CPane::OnShowControlBarMenu](#onshowcontrolbarmenu)|Wywoływane przez platformę, gdy menu okienka specjalne ma być wyświetlany.|  
|[CPane::OnShowControlBarMenu](#onshowcontrolbarmenu)|Wywoływane przez platformę, gdy menu okienka specjalne ma być wyświetlany.|  
|`CPane::PrepareToDock`|Używane wewnętrznie.|  
|[CPane::RecalcLayout](#recalclayout)|Ponownie oblicza informacji o układzie dla tego okienka. (Przesłania [CBasePane::RecalcLayout](../../mfc/reference/cbasepane-class.md#recalclayout).)|  
|[CPane::SaveState](#savestate)|Zapisuje stan okienka w rejestrze. (Przesłania [CBasePane::SaveState](../../mfc/reference/cbasepane-class.md#savestate).)|  
|[CPane::SetActiveInGroup](#setactiveingroup)|Flagi okienko jako aktywne.|  
|[CPane::SetBorders](#setborders)|Ustawia wartości obramowania okienka.|  
|[CPane::SetClientHotSpot](#setclienthotspot)|Ustawia aktywnego okienka.|  
|[CPane::SetDockState](#setdockstate)|Przywraca dokowanie informacji o stanie dla tego okienka.|  
|[CPane::SetExclusiveRowMode](#setexclusiverowmode)|Włącza lub wyłącza tryb wyłączności wiersza.|  
|[CPane::SetMiniFrameRTC](#setminiframertc)|Ustawia informacje o klasie czasu wykonywania dla domyślnego mini ramki okna.|  
|[CPane::SetMinSize](#setminsize)|Ustawia minimalny dozwolony rozmiar okienka.|  
|[CPane::SetVirtualRect](#setvirtualrect)|Ustawia *wirtualnego prostokąt* okienka.|  
|[CPane::StretchPaneDeferWndPos](#stretchpanedeferwndpos)|Rozciąga się okienko w pionie lub poziomie oparte na styl dokowania.|  
|[CPane::ToggleAutoHide](#toggleautohide)|Włącza lub wyłącza automatyczne ukrywanie tryb.|  
|[CPane::UndockPane](#undockpane)|Usuwa okienka z witryny dokowania, suwak domyślne lub minimalnej ramkę okna, w której obecnie jest zadokowany. (Przesłania [CBasePane::UndockPane](../../mfc/reference/cbasepane-class.md#undockpane).)|  
|[CPane::UpdateVirtualRect](#updatevirtualrect)|Aktualizuje wirtualnego prostokąta.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPane::OnAfterDock](#onafterdock)|Wywoływane przez platformę, gdy okienko zostało zadokowane.|  
|[CPane::OnAfterFloat](#onafterfloat)|Wywoływane przez platformę, gdy okienko zostały przestawione.|  
|[CPane::OnBeforeDock](#onbeforedock)|Wywoływane przez platformę, gdy ma zostać zadokowane okienka.|  
|[CPane::OnBeforeFloat](#onbeforefloat)|Wywoływane przez platformę, gdy ma być przestawione okienko.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPane::m_bHandleMinSize](#m_bhandleminsize)|Włącza obsługę spójna minimalny rozmiar okienka.|  
|[CPane::m_recentDockInfo](#m_recentdockinfo)|Zawiera najnowsze informacje dokowania.|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj `CPane` obiekty nie są bezpośrednio tworzone. Jeśli potrzebujesz o funkcji dokujące okienko, pochodzi z obiektu [CDockablePane](../../mfc/reference/cdockablepane-class.md). Jeśli potrzebujesz funkcji narzędzi, pochodzi z obiektu [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md).  
  
 Gdy klasa wyprowadzona z z `CPane`, może być zadokowany w [CDockSite](../../mfc/reference/cdocksite-class.md) i mogą być przestawione w [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxPane.h  
  
##  <a name="adjustsizeimmediate"></a>CPane::AdjustSizeImmediate  
 Natychmiast ponownie oblicza układ okienka.  
  
```  
virtual void AdjustSizeImmediate(BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bRecalcLayout`  
 `TRUE`Aby automatycznie ponownie Oblicz Układ panelu. w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę można wywołać, gdy dynamicznie zmieniać układu Pane. Na przykład można wywołać tej metody, jeśli ukrycie lub pokazanie przycisków paska narzędzi.  
  
##  <a name="allocelements"></a>CPane::AllocElements  
 Przydziela magazynu do użytku wewnętrznego.  
  
```  
BOOL AllocElements(
    int nElements,  
    int cbElement);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nElements`  
 Liczba elementów, dla których ma zostać przydzielony magazynu.  
  
 [in]`cbElement`  
 Rozmiar w bajtach elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `FALSE`Jeśli alokacja pamięci nie powiodło się; w przeciwnym razie `TRUE`.  
  
##  <a name="allowshowonpanemenu"></a>CPane::AllowShowOnPaneMenu  
 Określa, czy okienko wymienionej na liście generowanych przez środowisko uruchomieniowe okienka aplikacji.  
  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko jest wyświetlane na liście; w przeciwnym razie `FALSE`. Podstawowa implementacja zawsze zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Aplikacja wygenerowane z kreatorami AppWizard zawiera opcję menu, która wyświetla okienka, które zawiera. Ta metoda określa, czy okienko jest wyświetlana na liście.  
  
##  <a name="calcavailablesize"></a>CPane::CalcAvailableSize  
 Oblicza różnicę o rozmiarze określonym prostokąt i bieżący prostokąt okna.  
  
```  
virtual CSize CalcAvailableSize(CRect rectRequired);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rectRequired`  
 Prostokąt wymagane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różnica w szerokości i wysokości między `rectRequired` i bieżący prostokąt okna.  
  
##  <a name="calcinsiderect"></a>CPane::CalcInsideRect  
 Oblicza wewnątrz prostokąta okienko, w tym obramowanie i uchwyty.  
  
```  
void CalcInsideRect(
    CRect& rect,  
    BOOL bHorz) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rect`  
 Zawiera rozmiar i Przesunięcie obszaru klienckiego okienka.  
  
 [in]`bHorz`  
 `TRUE`Jeśli okienko jest orientacji poziomej; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy ma się ponownie Oblicz układ dla okienka. `rect` Parametr jest wypełniony rozmiar i Przesunięcie obszaru klienckiego okienka. W tym jego obramowanie i uchwyty.  
  
##  <a name="calcrecentdockedrect"></a>CPane::CalcRecentDockedRect  
 Oblicza ostatnio zadokowanych prostokąta.  
  
```  
void CalcRecentDockedRect();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda aktualizacji [CPane::m_recentDockInfo](#m_recentdockinfo).  
  
##  <a name="calcsize"></a>CPane::CalcSize  
 Oblicza rozmiar okienka.  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bVertDock`  
 `TRUE`Jeśli okienko jest jest zadokowany w pionie, `FALSE` inaczej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja tej metody zwraca rozmiar (0, 0).  
  
### <a name="remarks"></a>Uwagi  
 Klasy pochodne powinny przesłaniać tę metodę.  
  
##  <a name="canbedocked"></a>CPane::CanBeDocked  
 Określa, czy okienku można zadokowany w okienku określony podstawowy.  
  
```  
virtual BOOL CanBeDocked(CBasePane* pDockBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDockBar`  
 Określa okienko, w którym ma być zadokowane, w tym okienku.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli w tym okienku, może być zadokowany w określonej dokowania panelu. w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest zazwyczaj wywoływana przez platformę, by określić, czy okienko może być zadokowany w okienku dokowania określony. Aby ustalić, czy może być zadokowany okienku, metoda ocenia okienku aktualnie włączone dokowania wyrównania.  
  
 Możesz włączyć dokowanie na różnych stronach okno ramowe wywołując [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).  
  
##  <a name="canbetabbeddocument"></a>CPane::CanBeTabbedDocument  
 Określa, czy okienku może zostać przekonwertowany na dokument z kartami.  
  
```  
virtual BOOL CanBeTabbedDocument() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko można przekonwertować na dokument z kartami; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę metodę w klasie pochodnej i zwracać `FALSE` Jeśli chcesz zapobiec okienko przekształcany na dokument z kartami. Dokument z kartami nie będzie wyświetlane w menu położenie okna.  
  
##  <a name="converttotabbeddocument"></a>CPane::ConvertToTabbedDocument  
 Konwertuje dokument z kartami dokującego okienka.  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bActiveTabOnly`  
 Nie używane w `CPane::ConvertToTabbedDocument`.  
  
### <a name="remarks"></a>Uwagi  
 Tylko dokującego okienka może zostać przekonwertowany na dokumenty z kartami. Aby uzyskać informacje, zobacz [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).  
  
##  <a name="copystate"></a>CPane::CopyState  
 Kopiuje stan okienka.  
  
```  
virtual void CopyState(CPane* pOrgBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pOrgBar`  
 Wskaźnik do okienka.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia skopiowanie stan `pOrgBar` do bieżącego okienka.  
  
##  <a name="create"></a>CPane::Create  
 Tworzy pasek sterowania i dołącza go do [CPane](../../mfc/reference/cpane-class.md) obiektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszClassName`  
 Określa nazwę klasy systemu Windows.  
  
 [in]`dwStyle`  
 Określa atrybuty stylu okna. Aby uzyskać więcej informacji, zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in]`rect`  
 Określa początkowy rozmiar i położenie `pParentWnd` okna, we współrzędnych klienta.  
  
 [in] [out]`pParentWnd`  
 Określa okno nadrzędne w tym okienku.  
  
 [in]`nID`  
 Określa identyfikator okienka.  
  
 [in]`dwControlBarStyle`  
 Określa styl okienka. Aby uzyskać więcej informacji, zobacz [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 [in] [out]`pContext`  
 Określa kontekst Utwórz okienka.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko została utworzona pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda tworzy okienku systemu Windows i dołącza go do `CPane` obiektu.  
  
 Jeśli nie ma jawnie zainicjować [CPane::m_recentDockInfo](#m_recentdockinfo) przed wywołaniem `Create`, parametr `rect` będzie służyć jako prostokąt zmiennoprzecinkową lub Dokowanie okienka.  
  
##  <a name="createdefaultminiframe"></a>CPane::CreateDefaultMiniframe  
 Tworzy okno ramowe mini przestawne okienka.  
  
```  
virtual CPaneFrameWnd* CreateDefaultMiniframe(CRect rectInitial);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rectInitial`  
 Określa początkowy rozmiar i pozycja, we współrzędnych ekranu mini ramkę okna do utworzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowo utworzony mini ramkę okna.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, by utworzyć okno ramowe minimalnej, gdy okienko jest przestawione. Okno ramowe minimalna może być typu [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) lub typu [CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md). Okno ramowe mini multi jest tworzony, jeśli ma okienku `AFX_CBRS_FLOAT_MULTI` stylu.  
  
 Informacje o klasie czasu wykonywania dla okno ramowe mini są przechowywane w `CPane::m_pMiniFrameRTC` elementu członkowskiego. Można ustawić tego elementu członkowskiego, jeśli zdecydujesz się tworzenie okien dostosowany ramki minimalnej, można użyć klasy pochodnej.  
  
##  <a name="createex"></a>CPane::CreateEx  
 Tworzy pasek sterowania i dołącza go do [CPane](../../mfc/reference/cpane-class.md) obiektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszClassName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`dwStyleEx`  
 Określa atrybuty stylu rozszerzonej okna. Aby uzyskać więcej informacji, zobacz [rozszerzone Style okna](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).  
  
 [in]`lpszClassName`  
 Określa nazwę klasy systemu Windows.  
  
 [in]`dwStyle`  
 Określa atrybuty stylu okna. Aby uzyskać więcej informacji, zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in]`rect`  
 Określa początkowy rozmiar i położenie `pParentWnd` okna, we współrzędnych klienta.  
  
 [in] [out]`pParentWnd`  
 Określa okno nadrzędne w tym okienku.  
  
 [in]`nID`  
 Określa identyfikator okienka.  
  
 [in]`dwControlBarStyle`  
 Określa styl okienka. Aby uzyskać więcej informacji, zobacz [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 [in] [out]`pContext`  
 Określa kontekst Utwórz okienka.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko została utworzona pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda tworzy okienku systemu Windows i dołącza go do `CPane` obiektu.  
  
 Jeśli nie ma jawnie zainicjować [CPane::m_recentDockInfo](#m_recentdockinfo) przed wywołaniem `CreateEx`, parametr `rect` będzie służyć jako prostokąt zmiennoprzecinkową lub Dokowanie okienka.  
  
##  <a name="dockbymouse"></a>CPane::DockByMouse  
 Stacje dokujące okienko za pomocą myszy.  
  
```  
virtual BOOL DockByMouse(CBasePane* pDockBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDockBar`  
 Określa podstawowy okienko do którego ma zostać dock w tym okienku.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko zostało zadokowane pomyślnie; w przeciwnym razie `FALSE`.  
  
##  <a name="dockpane"></a>CPane::DockPane  
 Stacje dokujące okienko przestawne do podstawowej okienka.  
  
```  
virtual BOOL DockPane(
    CBasePane* pDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out]`pDockBar`  
 Określa podstawowy okienko, aby dock w tym okienku do.  
  
 [in]`lpRect`  
 Określa prostokąt w okienku podstawowej, w którym ma być zadokowane, w tym okienku.  
  
 [in]`dockMethod`  
 Określa metodę dokowania. Opcje dostępne są następujące:  
  
|Opcja|Opis|  
|------------|-----------------|  
|`DM_UNKNOWN`|Ta opcja jest używana w ramach, gdy dokowania metodą jest nieznany. Okienko jego ostatniej pozycji przestawne nie są zapisywane. Można także użyć tej opcji, aby programowo dock okienko, jeśli nie masz do przechowywania ostatnie położenie zmiennoprzecinkowych.|  
|`DM_MOUSE`|Używane wewnętrznie.|  
|`DM_DBL_CLICK`|Ta opcja jest używana po dwukrotnym kliknięciu uchwytu. Okienko zostaje przeniesiony na jego ostatniej pozycji dokowania. Jeśli okienko jest oddokowania komputera, klikając dwukrotnie plik, okienku zostaje przeniesiony na jego ostatniej pozycji zmiennoprzecinkowych.|  
|`DM_SHOW`|Ta opcja umożliwia programowo dock w okienku. Okienko przechowuje najnowszych położenia zmiennoprzecinkowych.|  
|`DM_RECT`|Okienko jest zadokowany w regionie, który jest określony przez `lpRect`.|  
|`DM_STANDARD`|Tej opcji platformę pobiera okienku jako konturu ramki, a jest przenoszony.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko zostało zadokowane pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda stacje dokujące okienko do okienka podstawowego określonego przez `pDockBar` parametru. Należy najpierw włączyć dokowanie wywołując [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).  
  
##  <a name="dockpanestandard"></a>CPane::DockPaneStandard  
 Stacje dokujące okienko przy użyciu konspektu dokowanie (standard).  
  
```  
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bWasDocked`  
 `TRUE`Jeśli okienko został pomyślnie zadokowane; w przeciwnym razie `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zawsze zwraca `this` wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest używana tylko w przypadku okienka pochodzących z [CDockablePane klasy](../../mfc/reference/cdockablepane-class.md). Aby uzyskać więcej informacji, zobacz [CDockablePane::DockPaneStandard](../../mfc/reference/cdockablepane-class.md#dockpanestandard).  
  
##  <a name="docktoframewindow"></a>CPane::DockToFrameWindow  
 Stacje dokujące okienko dokującego do ramki.  
  
```  
virtual BOOL DockToFrameWindow(
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL,  
    DWORD dwDockFlags = DT_DOCK_LAST,  
    CBasePane* pRelativeBar = NULL,  
    int nRelativeIndex = -1,  
    BOOL bOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`dwAlignment`  
 Strona ramki nadrzędnej, który ma zostać dock okienko, aby.  
  
 [in]`lpRect`  
 Określony rozmiar.  
  
 [in]`dwDockFlags`  
 Ignorowane.  
  
 [in]`pRelativeBar`  
 Ignorowane.  
  
 [in]`nRelativeIndex`  
 Ignorowane.  
  
 [in]`bOuterEdge`  
 Jeśli `TRUE` i czy istnieją inne dokującego okienka na stronie, które są określone przez `dwAlignment`, panel jest zadokowany poza inne okienka bliżej krawędzi ramka nadrzędny. Jeśli `FALSE`, okienku jest zadokowany bliżej do centrum obszaru klienckiego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `FALSE`Jeśli dzielnik ( [klasy CPaneDivider](../../mfc/reference/cpanedivider-class.md)) nie może być utworzony; w przeciwnym razie `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="doesallowsiblingbars"></a>CPane::DoesAllowSiblingBars  
 Wskazuje, czy dokowany innego okienka w tym samym wierszu, gdy jest zadokowany bieżącego okienka.  
  
```  
virtual BOOL DoesAllowSiblingBars() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli w tym okienku dokowany do innego okienka w tym samym wierszu. w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Można włączyć lub wyłączyć to zachowanie, wywołując [CPane::SetExclusiveRowMode](#setexclusiverowmode).  
  
 Domyślnie paski narzędzi ma wyłączono tryb wyłączności wiersza, a następnie na pasku menu ma włączony tryb wyłączności wiersza.  
  
##  <a name="floatpane"></a>CPane::FloatPane  
 Pojawia się okienku.  
  
```  
virtual BOOL FloatPane(
    CRect rectFloat,  
    AFX_DOCK_METHOD dockMethod = DM_UNKNOWN,  
    bool bShow = true);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rectFloat`  
 Określa lokalizację, we współrzędnych ekranu, pozycja w okienku, gdy jest on przestawione do.  
  
 [in]`dockMethod`  
 Określa metodę dokowania do użycia podczas okienku jest przestawione. Aby uzyskać listę możliwych wartości, zobacz [CPane::DockPane](#dockpane).  
  
 [in]`bShow`  
 `TRUE`Aby wyświetlić w okienku po przestawione; w przeciwnym razie `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienku został pomyślnie przestawione lub nie może być przestawione okienku, ponieważ [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat) zwraca `FALSE`; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody do float okienko w miejscu określonym przez `rectFloat` parametru. Ta metoda tworzy automatycznie okno ramowe mini nadrzędnego dla tego okienka.  
  
##  <a name="getavailableexpandsize"></a>CPane::GetAvailableExpandSize  
 Zwraca wartość, w pikselach, którą można rozwinąć okienka.  
  
```  
virtual int GetAvailableExpandSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli panel jest zadokowany poziomo, zwracana wartość jest dostępna szerokość; w przeciwnym razie wartość zwracana jest dostępne wysokość.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getavailablestretchsize"></a>CPane::GetAvailableStretchSize  
 Zwraca wartość, w pikselach, którą można zmniejszyć okienka.  
  
```  
virtual int GetAvailableStretchSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kwota w pikselach, którą można zmniejszyć okienka. Jeśli panel jest zadokowany poziomo, ta wartość jest dostępna szerokość; w przeciwnym razie jest dostępne wysokość.  
  
### <a name="remarks"></a>Uwagi  
 Dostępny rozmiar stretch jest obliczana przez odjęcie ilości dozwolony rozmiar okienka ( [CPane::GetMinSize](#getminsize)) z bieżącego rozmiaru ( [CWnd::GetWindowRect](../../mfc/reference/cwnd-class.md#getwindowrect)).  
  
##  <a name="getborders"></a>CPane::GetBorders  
 Zwraca szerokość obramowań okienka.  
  
```  
CRect GetBorders() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który zawiera Bieżąca szerokość w pikselach każdej strony panelu. Na przykład wartość `left` członkiem `CRect` obiektu jest szerokość lewej krawędzi.  
  
### <a name="remarks"></a>Uwagi  
 Aby ustawić rozmiar obramowania, należy wywołać [CPane::SetBorders](#setborders).  
  
##  <a name="getclienthotspot"></a>CPane::GetClientHotSpot  
 Zwraca *aktywnego* okienka.  
  
```  
CPoint GetClientHotSpot() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 *Aktywnego* punktu, w okienku, który użytkownik wybiera i posiada, aby przenieść okienko. Punkt aktywny służy do sprawnego animacji po przeniesieniu z pozycji zadokowanego okienka.  
  
##  <a name="getdocksiterow"></a>CPane::GetDockSiteRow  
 Zwraca wiersz dokowania ( [klasy CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)), w którym jest zadokowany w okienku.  
  
```  
CDockingPanesRow* GetDockSiteRow() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CDockingPanesRow`* wskazującego wiersz dokowania, w którym jest zadokowany okienku, lub `NULL` Jeśli okienku nie jest zadokowany.  
  
##  <a name="getexclusiverowmode"></a>CPane::GetExclusiveRowMode  
 Określa, czy okienko jest w trybie wyłączności wiersza.  
  
```  
virtual BOOL GetExclusiveRowMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko jest w trybie wyłączności wiersza; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji o trybie wyłączności wiersza, zobacz [CPane::SetExclusiveRowMode](#setexclusiverowmode).  
  
##  <a name="gethotspot"></a>CPane::GetHotSpot  
 Zwraca punkt aktywny, który jest przechowywany w podstawowej `CMFCDragFrameImpl` obiektu.  
  
```  
CPoint GetHotSpot() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 `CPane` Klasa zawiera `CMFCDragFrameImpl` obiektu `m_dragFrameImpl`, która jest odpowiedzialna za rysowania prostokąta, który jest wyświetlany, gdy użytkownik przesuwa okienko w trybie standardowym dokowania. Punkt aktywny jest używany do rysowania prostokąta względem bieżącego położenia kursora myszy, gdy użytkownik przechodzi okienka.  
  
##  <a name="getminsize"></a>CPane::GetMinSize  
 Pobiera minimalny dozwolony rozmiar okienka.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`size`  
 A `CSize` obiekt, który jest wypełniony dozwolony rozmiar.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getpanename"></a>CPane::GetPaneName  
 Pobiera tytuł dla tego okienka.  
  
```  
virtual void GetPaneName(CString& strName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`strName`  
 A `CString` obiekt, który jest wypełniony nazwy podpisu.  
  
### <a name="remarks"></a>Uwagi  
 Tytuł okienko jest wyświetlany w obszarze podpis, gdy okienko jest zadokowane i przestawne. Jeśli okienko jest częścią grupy z kartami, tytuł jest wyświetlany w obszarze kartę. Jeśli okienko jest w trybie autoukrywania, tytuł jest wyświetlany na `CMFCAutoHideButton`.  
  
##  <a name="getvirtualrect"></a>CPane::GetVirtualRect  
 Pobiera *wirtualnego prostokąt* okienka.  
  
```  
void GetVirtualRect(CRect& rectVirtual) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rectVirtual`  
 A `CRect` obiekt, który jest wypełniony prostokąt wirtualnego.  
  
### <a name="remarks"></a>Uwagi  
 Po przeniesieniu okienko platformę przechowuje oryginalnego położenia okienka w prostokącie wirtualnego. Platformę można użyć wirtualnych prostokąta do przywrócenia oryginalnej pozycji okienka.  
  
 Nie wywołuj metody, które są związane z wirtualnych prostokąty, chyba że przenosisz okienka programowo.  
  
##  <a name="ischangestate"></a>CPane::IsChangeState  
 Zgodnie z okienka jest przenoszony, ta metoda analizuje położenia względem innych okienka, dokowania wierszy i okna ramowe minimalnej i zwraca odpowiednie `AFX_CS_STATUS` wartość.  
  
```  
virtual AFX_CS_STATUS IsChangeState(
    int nOffset,  
    CBasePane** ppTargetBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nOffset`  
 Określa czułości dokowania. Na przykład okienko zostanie przeniesiony w `nOffset` pikseli z wierszem dokowania zostanie zadokowany.  
  
 [in]`ppTargetBar`  
 Gdy metoda zwróci wartość, `ppTargetBar` zawiera wskaźnik do obiektu, do którego jest zadokowany bieżącego okienka, lub `NULL` jeśli bez dokowania powinna się odbyć.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jedną z następujących `AFX_CS_STATUS` wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`CS_NOTHING`|Okienko nie jest niemal lokacji dokowania. Platformę nie dock okienka.|  
|`CS_DOCK_IMMEDIATELY`|Okienka znajduje się nad witryną dock i `DT_IMMEDIATE` styl jest włączony. Platformę stacje dokujące okienko natychmiast.|  
|`CS_DELAY_DOCK`|Okienka znajduje się nad innym okienko dokujące lub krawędź ramki głównej lokacji dokowania. Stacje dokujące okienko platformę, gdy użytkownik zwalnia przeniesienie.|  
|`CS_DELAY_DOCK_TO_TAB`|Okienko jest za pośrednictwem witryny dokowania, która powoduje, że okienko, aby być zadokowane, w oknie z kartami. Dzieje się tak, gdy okienko jest za pośrednictwem podpis okienko dokujące w innym lub nad obszarem kartę okienka z kartami. Stacje dokujące okienko platformę, gdy użytkownik zwalnia przeniesienie.|  
  
##  <a name="isdragmode"></a>CPane::IsDragMode  
 Określa, czy okienko jest przenoszony.  
  
```  
virtual BOOL IsDragMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko jest przenoszony; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isinfloatingmultipaneframewnd"></a>CPane::IsInFloatingMultiPaneFrameWnd  
 Określa, czy okienka w oknie ramowym wielu okienka ( [CMultiPaneFrameWnd klasy](../../mfc/reference/cmultipaneframewnd-class.md)).  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko jest w oknie ramowym wielu okienka; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Tylko dokującego okienka poruszać się w oknie ramowym wielu okienka. W związku z tym `CPane::IsInFloatingMultiPaneFrameWnd` zawsze zwraca `FALSE`.  
  
##  <a name="isleftof"></a>CPane::IsLeftOf  
 Określa, czy okienko pozostało (lub powyżej) określonego prostokąta.  
  
```  
bool IsLeftOf(
    CRect rect,  
    bool bWindowRect = true) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rect`  
 A `CRect` obiekt, który jest używany do porównania.  
  
 [in]`bWindowRect`  
 Jeśli `TRUE`, `rect` zakłada się, że zawiera współrzędne ekranu; Jeśli `FALSE`, `rect` muszą zawierać współrzędne klienta.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Jeśli panel jest zadokowany poziomo, ta metoda sprawdza, czy jego lokalizacji pozostanie z `rect`. W przeciwnym razie ta metoda sprawdza, czy lokalizacja jest powyżej `rect`.  
  
##  <a name="isresizable"></a>CPane::IsResizable  
 Określa, czy okienko jest zmieniana.  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko jest zmieniana; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Podstawa `CPane` obiekty nie znajdują się o zmiennym rozmiarze.  
  
 Dokujące manager używa o zmiennym rozmiarze flagi określa układ okienka. Bez zmienny rozmiar okienka zawsze znajdują się w zewnętrznej krawędzi ramki nadrzędnej.  
  
 Bez zmienny rozmiar okienka nie mogą znajdować się w dokowanie kontenerów.  
  
##  <a name="istabbed"></a>CPane::IsTabbed  
 Określa, czy okienko został wstawiony do formantu karty z kartami okna.  
  
```  
virtual BOOL IsTabbed() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko jest kartach; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Okno stanu jest traktowana oddzielnie z typu zmiennoprzecinkowego, zadokowane i autoukrywania stanów.  
  
##  <a name="loadstate"></a>CPane::LoadState  
 Ładuje stan okienka z rejestru.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 Nazwa profilu.  
  
 [in]`nIndex`  
 Indeks profilu.  
  
 [in]`uiID`  
 Identyfikator okienka.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli stan okienka został załadowany pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę, aby załadować stan okienka z rejestru. Zastąp go w klasie pochodnej załadować dodatkowych informacji zapisanych przez [CPane::SaveState](#savestate).  
  
 Po przesłonięcia tej metody należy także wywołać metodę podstawową i wróć `FALSE` Jeśli podstawowa metoda zwraca `FALSE`.  
  
##  <a name="m_bhandleminsize"></a>CPane::m_bHandleMinSize  
 Włącza obsługę spójna minimalny okienka rozmiary.  
  
```  
AFX_IMPORT_DATA static BOOL m_bHandleMinSize;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli zastąpienie co najmniej jednego okienka dokowania w aplikacji `GetMinSize`, lub jeśli aplikację `SetMinSize`, można ustawić ten statyczny element członkowski `TRUE` Aby włączyć platformę, by spójnie obsługi, jaki mają rozmiar okienka.  
  
 Jeśli ta wartość jest równa `TRUE`, powoduje wszystkie okienka, których rozmiar należy zmniejszyć poniżej ich minimalny rozmiar, nie jest rozciągana. Ponieważ platformę używa regionów okna do celów zmiany rozmiaru okienka, nie należy zmieniać rozmiar regionu okna dla okienka dokowania, jeśli ta wartość jest równa `TRUE`.  
  
##  <a name="m_recentdockinfo"></a>CPane::m_recentDockInfo  
 Zawiera najnowsze informacje dokowania.  
  
```  
CRecentDockSiteInfo m_recentDockInfo;  
```  
  
### <a name="remarks"></a>Uwagi  
 Platformę przechowuje dokowania najnowsze informacje o stanie dla tego okienka w tym elemencie członkowskim.  
  
##  <a name="movebyalignment"></a>CPane::MoveByAlignment  
 Przesuwa okienku i wirtualnych prostokąt określony.  
  
```  
BOOL MoveByAlignment(
    DWORD dwAlignment,  
    int nOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`dwAlignment`  
 Określa wyrównanie okienka.  
  
 [in]`nOffset`  
 Kwota w pikselach, za pomocą którego można przenieść wirtualnego prostokąt i okienka.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 `dwAlignment`Możesz użyć dowolnej z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|Umożliwia okienko, aby być zadokowany u góry obszaru klienckiego okna ramowe.|  
|`CBRS_ALIGN_BOTTOM`|Umożliwia okienko, aby być zadokowany z dolną krawędzią obszaru klienckiego okno ramowe.|  
|`CBRS_ALIGN_LEFT`|Umożliwia okienko, aby być zadokowane po lewej stronie obszaru klienckiego okna ramki.|  
|`CBRS_ALIGN_RIGHT`|Umożliwia okienko, aby być zadokowany do prawej krawędzi obszaru klienckiego okna ramki.|  
|`CBRS_ALIGN_ANY`|Umożliwia okienko, aby być zadokowany do dowolnej krawędzi obszaru klienckiego okna ramki.|  
  
 Jeśli `dwAlignment` zawiera `CBRS_ALIGN_LEFT` lub `CBRS_ALIGN_RIGHT` flagi, okienko i prostokąt wirtualnych są przenoszone w poziomie, a w przeciwnym razie jeśli `dwAlignment` zawiera `CBRS_ALIGN_TOP` lub `CBRS_ALIGN_BOTTOM` flagi, okienko i prostokąt wirtualne są przenoszone w pionie.  
  
##  <a name="movepane"></a>CPane::MovePane  
 Przenosi okienka określonego prostokąta.  
  
```  
virtual CSize MovePane(
    CRect rectNew,  
    BOOL bForceMove,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rectNew`  
 Określa nowy prostokąt dla tego okienka.  
  
 [in]`bForceMove`  
 Jeśli `TRUE`, ta metoda ignoruje rozmiar minimalny okienka dozwolonych ( [CPane::GetMinSize](#getminsize)); w przeciwnym razie okienku jest korygowana, jeśli to konieczne upewnić się, czy jest niższy niż minimalny dozwolony rozmiar.  
  
 [in]`hdwp`  
 Nie używany.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CSize` obiekt, który zawiera różnice w szerokości i wysokości prostokąty nowym i starym (stary prostokąt - `rectNew`).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest używana tylko w przypadku dokującego okienka.  
  
##  <a name="onafterchangeparent"></a>CPane::OnAfterChangeParent  
 Wywoływane przez platformę, gdy element nadrzędny okienko zostanie zmieniony.  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out]`pWndOldParent`  
 W okienku poprzedniego okna nadrzędnego.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy element nadrzędny okienko zmienił się z powodu operacji dokowania lub zmiennoprzecinkową.  
  
##  <a name="onafterdock"></a>CPane::OnAfterDock  
 Wywoływane przez platformę, gdy okienko zostało zadokowane.  
  
```  
virtual void OnAfterDock(
    CBasePane* pBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
 Ten parametr nie jest używany.  
  
 [in]`lpRect`  
 Ten parametr nie jest używany.  
  
 [in]`dockMethod`  
 Ten parametr nie jest używany.  
  
##  <a name="onafterfloat"></a>CPane::OnAfterFloat  
 Wywoływane przez platformę po okienko jest wyświetlany.  
  
```  
virtual void OnAfterFloat();
```  
  
### <a name="remarks"></a>Uwagi  
 Można zastąpić tę metodę w klasie pochodnej, jeśli chcesz wykonać wszelkie przetwarzania po okienko jest wyświetlany.  
  
##  <a name="onbeforechangeparent"></a>CPane::OnBeforeChangeParent  
 Wywoływane przez platformę, gdy element nadrzędny okienka ma zostać zmieniona.  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out]`pWndNewParent`  
 Określa nowe okno nadrzędne.  
  
 [in]`bDelay`  
 `TRUE`opóźnienia globalne dokowania dopasowanie układu; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy element nadrzędny okienka ma zostać zmieniona, ponieważ okienku jest zadokowany lub przestawione.  
  
 Domyślnie okienko jest niezarejestrowany dokujące okienko przez wywołanie metody `CDockSite::RemovePane`.  
  
##  <a name="onbeforedock"></a>CPane::OnBeforeDock  
 Wywoływane przez platformę, gdy ma dock okienka.  
  
```  
virtual BOOL OnBeforeDock(
    CBasePane** ppDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out]`ppDockBar`  
 Określa okienka w tym okienku jest Dokowanie do.  
  
 [in]`lpRect`  
 Określa prostokątne dokowania.  
  
 [in]`dockMethod`  
 Określa metodę dokowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko może być zadokowany. Jeśli funkcja zwraca `FALSE`, dokującego. Operacja zostanie przerwana.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy ma zostać zadokowane okienko. Można zastąpić tę metodę w klasie pochodnej, jeśli chcesz wykonać wszelkie przetwarzania przed okienko finally jest zadokowany.  
  
##  <a name="onbeforefloat"></a>CPane::OnBeforeFloat  
 Wywoływane przez platformę, gdy nastąpi okienko float.  
  
```  
virtual BOOL OnBeforeFloat(
    CRect& rectFloat,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rectFloat`  
 Określa położenie i rozmiar okienka, gdy jest on w stanie zmiennoprzecinkowych.  
  
 [in]`dockMethod`  
 Określa metodę dokowania okienka.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli w okienku można przestawione; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy okienko jest o float. Można zastąpić tę metodę w klasie pochodnej, jeśli chcesz wykonać wszelkie przetwarzania przed okienku finally jest wyświetlany.  
  
##  <a name="onpressclosebutton"></a>CPane::OnPressCloseButton  
 Wywoływane przez platformę, gdy użytkownik naciśnie przycisk Zamknij na podpis dla tego okienka.  
  
```  
virtual void OnPressCloseButton();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy użytkownik naciśnie **Zamknij** przycisk w okienku podpis. Aby otrzymywać powiadomienia o **Zamknij** zdarzeń, można przesłonić tę metodę w klasie pochodnej.  
  
##  <a name="onshowcontrolbarmenu"></a>CPane::OnShowControlBarMenu  
 Wywoływane przez platformę, gdy menu okienka specjalne ma być wyświetlany.  
  
```  
virtual BOOL OnShowControlBarMenu(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`point`  
 Określa lokalizację, w menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli menu mogą być wyświetlane; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Menu zawiera kilka elementów, które umożliwiają określenie zachowania w okienku, to znaczy: **przestawne**, **dokowanie**, **autohide —**, i **Ukryj**. Można włączyć tego menu dla wszystkich okienka przez wywołanie metody [CDockingManager::EnableDockSiteMenu](../../mfc/reference/cdockingmanager-class.md#enabledocksitemenu).  
  
##  <a name="recalclayout"></a>CPane::RecalcLayout  
 Ponownie oblicza informacji o układzie dla tego okienka.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli panel jest zadokowany, ta metoda aktualizacji wirtualnych prostokąt dla tego okienka przez ustawienie rozmiaru do bieżącego rozmiaru okienka.  
  
 Jeśli okienko jest przestawne, ta metoda powiadamia ramki mini nadrzędnej, aby dostosować rozmiar okienka, aby rozmiar ramki minimalnej. Platformę zapewnia, że minimalna ramki jest co najmniej minimalny dozwolony rozmiar okienka ( [CPane::GetMinSize](#getminsize)) i zmienia rozmiar ramki minimalnej, jeśli to konieczne.  
  
##  <a name="savestate"></a>CPane::SaveState  
 Zapisuje stan okienka w rejestrze.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 Nazwa profilu.  
  
 [in]`nIndex`  
 Indeks profilu.  
  
 [in]`uiID`  
 Identyfikator okienka.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli stan został zapisany pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Platformę wywołuje tę metodę, gdy stan okienka jest zapisywany w rejestrze. Zastąpienie `SaveState` w klasie pochodnej, aby przechowywać dodatkowe informacje.  
  
 Po przesłonięcia tej metody należy także wywołać metodę podstawową i wróć `FALSE` Jeśli podstawowa metoda zwraca `FALSE`.  
  
##  <a name="setactiveingroup"></a>CPane::SetActiveInGroup  
 Flagi okienko jako aktywne.  
  
```  
virtual void SetActiveInGroup(BOOL bActive);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bActive`  
 A `BOOL` Określa, czy okienko jest oznaczony jako aktywne.  
  
### <a name="remarks"></a>Uwagi  
 Gdy jest wyświetlany w okienku dokującego lub automatycznie Ukryj przycisk zostanie wybrany, odpowiedniego automatyczne ukrywanie okienka jest oznaczony jako aktywne.  
  
 Wygląd przycisku autoukrywania, który jest skojarzony z okienka opiera się na dwa czynniki. Jeśli okienko jest aktywna oraz `static BOOL CMFCAutoHideButton::m_bOverlappingTabs` jest `TRUE`, platformę wyświetlany przycisk autoukrywania jako ikonę i etykietę. Nieaktywne okienka platformę Wyświetla ikonę autoukrywania.  
  
 Jeśli `CMFCAutoHideButton::m_bOverlappingTabs` jest `FALSE`, lub jeśli okienku nie znajduje się w grupie, platformę wyświetlany przycisk skojarzone autoukrywania jako ikonę i etykietę.  
  
##  <a name="setborders"></a>CPane::SetBorders  
 Ustawia wartości obramowania okienka.  
  
```  
void SetBorders(
    int cxLeft = 0,  
    int cyTop = 0,  
    int cxRight = 0,  
    int cyBottom = 0);  
  
void SetBorders(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`cxLeft`  
 Określa szerokość w pikselach, lewej krawędzi okienka.  
  
 [in]`cyTop`  
 Określa szerokość w pikselach, krawędzi górnej części okienka.  
  
 [in]`cxRight`  
 Określa szerokość w pikselach, prawej krawędzi okienka.  
  
 [in]`cyBottom`  
 Określa szerokość w pikselach, krawędzi dolnej części okienka.  
  
 [in]`lpRect`  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który zawiera szerokość w pikselach każdego obramowanie okienka.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby ustawić rozmiar obramowania panelu.  
  
##  <a name="setclienthotspot"></a>CPane::SetClientHotSpot  
 Ustawia *aktywnego* okienka.  
  
```  
void SetClientHotSpot(const CPoint& ptNew);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`ptNew`  
 A `CPoint` obiekt, który określa nowy punkt aktywny.  
  
### <a name="remarks"></a>Uwagi  
 *Aktywnego* punktu, w okienku, który użytkownik wybiera i posiada, aby przenieść okienko. Punkt aktywny jest używana do sprawnego animacji przeciągnięte okienku od pozycji zadokowanego.  
  
##  <a name="setdockstate"></a>CPane::SetDockState  
 Przywraca dokowanie informacji o stanie dla tego okienka.  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDockManager`  
 Wskaźnik do Menedżera dokowania dla głównego okna ramowego.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, aby przywrócić bieżące informacje o stanie dokowania okienka. Okienko przechowuje najnowsze informacje o stanie dokowania w [CPane::m_recentDockInfo](#m_recentdockinfo). Aby uzyskać więcej informacji, zobacz [CRecentDockSiteInfo klasy](../../mfc/reference/crecentdocksiteinfo-class.md).  
  
 Można również wywołać tę metodę, aby ustawić stan dokowania podczas ładowania okienku informacji ze źródła zewnętrznego.  
  
##  <a name="setexclusiverowmode"></a>CPane::SetExclusiveRowMode  
 Włącza lub wyłącza tryb wyłączności wiersza.  
  
```  
virtual void SetExclusiveRowMode(BOOL bExclusive = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bExclusive`  
 `TRUE`Aby włączyć tryb wyłączności wiersza; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby włączyć lub wyłączyć tryb wyłączności wiersza. Jeśli okienko jest w trybie wyłączności wiersza, go nie mogą mieć tego samego wiersza innych pasków narzędzi.  
  
 Domyślnie wszystkie paski ma wyłączono tryb wyłączności wiersza, a następnie na pasku menu ma włączony tryb wyłączności wiersza.  
  
##  <a name="setminsize"></a>CPane::SetMinSize  
 Ustawia minimalny dozwolony rozmiar okienka.  
  
```  
void SetMinSize(const CSize& size);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`size`  
 A `CSize` obiekt, który zawiera dozwolony rozmiar okienka.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setvirtualrect"></a>CPane::SetVirtualRect  
 Ustawia *wirtualnego prostokąt* okienka.  
  
```  
void SetVirtualRect(
    const CRect& rect,  
    BOOL bMapToParent = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rect`  
 A `CRect` obiekt, który określa wirtualny prostokąt należy ustawić wartość.  
  
 [in]`bMapToParent`  
 Określ `TRUE` Jeśli `rect` zawiera punkty względem okno nadrzędne.  
  
### <a name="remarks"></a>Uwagi  
 A *wirtualnego prostokąt* przechowuje oryginalnej pozycji w okienku, gdy jest przenoszony. Platformę można użyć wirtualnych prostokąta do przywrócenia oryginalnej pozycji.  
  
 Nie wywołuj metody, które są związane z wirtualnych prostokąty, chyba że przenosisz okienka programowo.  
  
##  <a name="setminiframertc"></a>CPane::SetMiniFrameRTC  
 Ustawia informacje o klasie czasu wykonywania dla domyślnego mini ramki okna.  
  
```  
void SetMiniFrameRTC(CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out]`pClass`  
 Określa informacje o klasie czasu wykonywania minimalnej ramki okna.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli okienko jest przestawione, zawiesić [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) okna (minimalna ramki). Można podać niestandardowy `CPaneFrameWnd`-klasy, która zostanie użyta, gdy [CPane::CreateDefaultMiniframe](#createdefaultminiframe) jest wywoływana.  
  
##  <a name="stretchpanedeferwndpos"></a>CPane::StretchPaneDeferWndPos  
 Rozciąga się okienko w pionie lub poziomie oparte na styl dokowania.  
  
```  
virtual int StretchPaneDeferWndPos(
    int nStretchSize,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nStretchSize`  
 Kwota w pikselach do rozciągania okienka. Użyj wartości ujemnej zmniejszyć w okienku.  
  
 [in]`hdwp`  
 Nie używany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rzeczywista ilość w pikselach, że został rozciągany w okienku.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli to konieczne, ta metoda modyfikuje `nStretchSize` do zapewnienia, że okienka przekracza ograniczenia rozmiaru. Ograniczenia te są uzyskiwane przez wywołanie metody [CPane::GetAvailableStretchSize](#getavailablestretchsize) i [CPane::GetAvailableExpandSize](#getavailableexpandsize).  
  
##  <a name="toggleautohide"></a>CPane::ToggleAutoHide  
 Włącza lub wyłącza automatyczne ukrywanie tryb.  
  
```  
virtual void ToggleAutoHide();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby przełączyć tryb autoukrywania. Okienko musi być zadokowane do główne okno ramowe, aby mogła być Przełącz do trybu autoukrywania.  
  
##  <a name="undockpane"></a>CPane::UndockPane  
 Usuwa okienka z witryny dokowania, suwak domyślne lub minimalnej ramkę okna, w której obecnie jest zadokowany.  
  
```  
virtual void UndockPane(BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bDelay`  
 Jeśli `FALSE`, wywołania framework [CBasePane::AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout) Aby dostosować układ dokowania.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia programowo Oddokuj okienko.  
  
##  <a name="updatevirtualrect"></a>CPane::UpdateVirtualRect  
 Aktualizuje wirtualnego prostokąta.  
  
```  
void UpdateVirtualRect();  
void UpdateVirtualRect(CPoint ptOffset);  
  void UpdateVirtualRect(CSize sizeNew);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`ptOffset`  
 A `CPoint` obiekt, który określa przesunięcie za pomocą którego przesunięcie w okienku.  
  
 [in]`sizeNew`  
 A `CSize` obiekt, który określa nowy rozmiar okienka.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy przeciążenia ustawia prostokąt wirtualnego przy użyciu bieżącego położenia i rozmiaru okienka.  
  
 Drugi przeciążenia przewiduje wirtualnego prostokąt o szerokości określonej przez `ptOffset`.  
  
 Trzeci przeciążenia ustawia prostokąt wirtualnego przy użyciu okienka i rozmiar, który jest określony przez bieżącą pozycję `sizeNew`.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CBasePane](../../mfc/reference/cbasepane-class.md)
