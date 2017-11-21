---
title: Klasa CTabbedPane | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTabbedPane
- AFXTABBEDPANE/CTabbedPane
- AFXTABBEDPANE/CTabbedPane::DetachPane
- AFXTABBEDPANE/CTabbedPane::EnableTabAutoColor
- AFXTABBEDPANE/CTabbedPane::FloatTab
- AFXTABBEDPANE/CTabbedPane::GetTabArea
- AFXTABBEDPANE/CTabbedPane::GetTabWnd
- AFXTABBEDPANE/CTabbedPane::HasAutoHideMode
- AFXTABBEDPANE/CTabbedPane::IsTabLocationBottom
- AFXTABBEDPANE/CTabbedPane::ResetTabs
- AFXTABBEDPANE/CTabbedPane::SetTabAutoColors
- AFXTABBEDPANE/CTabbedPane::m_bTabsAlwaysTop
- AFXTABBEDPANE/CTabbedPane::m_pTabWndRTC
dev_langs: C++
helpviewer_keywords:
- CTabbedPane [MFC], DetachPane
- CTabbedPane [MFC], EnableTabAutoColor
- CTabbedPane [MFC], FloatTab
- CTabbedPane [MFC], GetTabArea
- CTabbedPane [MFC], GetTabWnd
- CTabbedPane [MFC], HasAutoHideMode
- CTabbedPane [MFC], IsTabLocationBottom
- CTabbedPane [MFC], ResetTabs
- CTabbedPane [MFC], SetTabAutoColors
- CTabbedPane [MFC], m_bTabsAlwaysTop
- CTabbedPane [MFC], m_pTabWndRTC
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 00bb0d4bcecd40260dd0ce453736e78996309b29
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ctabbedpane-class"></a>Klasa CTabbedPane
Implementuje funkcje okienka zawierającego karty odłączane.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Składnia  
  
```  
class CTabbedPane : public CBaseTabbedPane  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CTabbedPane::CTabbedPane`|Domyślny konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTabbedPane::DetachPane](#detachpane)|(Przesłania [CBaseTabbedPane::DetachPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|  
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|Włącza lub wyłącza automatyczne kolorowanie kart.|  
|[CTabbedPane::FloatTab](#floattab)|Przesunięty okienku, ale tylko wtedy, jeśli okienku aktualnie znajduje się na karcie odłączane. (Przesłania [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|  
|[CTabbedPane::GetTabArea](#gettabarea)|Zwraca rozmiar i położenie wartości obszar karty w oknie z kartami.|  
|[CTabbedPane::GetTabWnd](#gettabwnd)||  
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Określa, czy z kartami okienku może zostać przełączone do trybu autohide —. (Przesłania [CBaseTabbedPane::HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|  
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|Określa, czy karty znajdują się w dolnej części okna.|  
|[CTabbedPane::ResetTabs](#resettabs)|Resetuje wszystkie okienka z kartami do stanu domyślnego.|  
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|Ustawia listę kolorów niestandardowych, które mogą być używane, gdy jest włączona funkcja automatycznego kolorów.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|Domyślna lokalizacja dla kart w aplikacji.|  
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|Informacje o klasie czasu wykonywania dla niestandardowego `CMFCTabCtrl`-pochodzi z obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Platformę automatycznie tworzy wystąpienia tej klasy, gdy użytkownik dołącza jedno okienko na inny poprzez wskazanie podpis drugi okienka. Wszystkie okienka z kartami, które są tworzone przez platformę ma Identyfikatora-1.  
  
 Aby określić zwykłe karty zamiast tabulatorów w stylu programu Outlook, należy przekazać `AFX_CBRS_REGULAR_TABS` stylów do [CDockablePane::CreateEx](../../mfc/reference/cdockablepane-class.md#createex) metody.  
  
 Po utworzeniu okienko z kartami z karty odłączane okienku może zostać zniszczone automatycznie przez platformę, nie należy przechowywać wskaźnika. Aby otrzymywać wskaźnik do okienka z kartami, należy wywołać `CBasePane::GetParentTabbedPane` metody.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tworzymy `CTabbedPane` obiektu. Następnie używamy [CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) można dołączyć dodatkowe karty.  
  
```  
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);

if (!pTabbededBar->Create (_T(""),
    this,
    CRect (0,
    0,
    200,
    200),  
    TRUE, 
 (UINT) -1,  
    WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |  
    WS_CLIPCHILDREN | CBRS_LEFT |    
    CBRS_FLOAT_MULTI)) 
{  
    TRACE0("Failed to create Solution Explorer bar\n");

    return FALSE;      // fail to create  
}  
 
pTabbededBar->AddTab (&m_wndClassView);
pTabbededBar->AddTab (&m_wndResourceView);

pTabbededBar->AddTab (&m_wndFileView);
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);

DockPane(pTabbededBar);
```  
  
## <a name="example"></a>Przykład  
 Innym sposobem tworzenia obiektu z kartami formantu paska jest użycie [CDockablePane::AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). `AttachToTabWnd` Metody dynamicznie tworzy obiekt okienko z kartami przy użyciu informacji o klasie czasu wykonywania ustawiony przez [CDockablePane::SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc).  
  
 W tym przykładzie utworzymy okienko z kartami dynamicznie Dołącz dwie karty i upewnij niemożliwe do odłączenia drugiej karcie.  
  
```  
DockPane(&m_wndClassView);

CTabbedPane* pTabbedBar = NULL;  
m_wndResourceView.AttachToTabWnd (&m_wndClassView,
    DM_SHOW,
    TRUE,  
 (CDockablePane**) &pTabbedBar);

m_wndFileView.AttachToTabWnd (pTabbedBar,
    DM_SHOW,
    TRUE,  
 (CDockablePane**) &pTabbedBar);

pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1,
    FALSE);
```  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CTabbedPane](../../mfc/reference/ctabbedpane-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxTabbedPane.h  
  
##  <a name="detachpane"></a>CTabbedPane::DetachPane  

  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
 [in]`bHide`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="enabletabautocolor"></a>CTabbedPane::EnableTabAutoColor  
 Włącza lub wyłącza automatyczne kolorowanie kart.  
  
```  
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 `TRUE`Aby włączyć automatyczne kolorowanie kart; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody statyczne, aby włączyć lub wyłączyć automatyczne kolorowanie kart w wszystkich kartach okienka w aplikacji. Gdy ta funkcja jest włączona, każda karta jest wypełniane przez własną kolorów. Można znaleźć na liście kolorów, które są używane do kolorów karty przez wywołanie metody [CMFCBaseTabCtrl::GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) metody.  
  
 Można określić listę kolorów, które będą używane dla kart przez wywołanie metody [CTabbedPane::SetTabAutoColors](#settabautocolors).  
  
 Ta opcja jest domyślnie wyłączona.  
  
##  <a name="floattab"></a>CTabbedPane::FloatTab  

  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
 [in]`nTabID`  
 [in]`dockMethod`  
 [in]`bHide`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gettabarea"></a>CTabbedPane::GetTabArea  
 Zwraca rozmiar i położenie wartości obszar karty w oknie z kartami.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rectTabAreaTop`  
 Zawiera rozmiar i położenie wartości obszar karty top, we współrzędnych ekranu.  
  
 [out]`rectTabAreaBottom`  
 Zawiera rozmiar i położenie we współrzędnych ekranu obszaru karty dolnej.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę w celu ustalenia sposobu dock okienko, w którym użytkownik przeciąga. Gdy użytkownik przeciąga okienko nad obszarem kartę okienka docelowej, platformę próbuje dodać ją jako nową kartę okienka docelowej. W przeciwnym razie próby dock w okienku po stronie okienko docelowych, które obejmuje utworzenie nowego kontenera okienko z dzielnik oddziela dwa okienka.  
  
 Należy przesłonić tę metodę w `CTabbedPane`-klasy, aby zmienić to zachowanie.  
  
##  <a name="gettabwnd"></a>CTabbedPane::GetTabWnd  

  
```  
CMFCTabCtrl* GetTabWnd() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="hasautohidemode"></a>CTabbedPane::HasAutoHideMode  

  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="istablocationbottom"></a>CTabbedPane::IsTabLocationBottom  
 Określa, czy karty znajdują się w dolnej części okna.  
  
```  
virtual BOOL IsTabLocationBottom() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli wartości obszar karty znajduje się w dolnej części okna z kartami; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_btabsalwaystop"></a>CTabbedPane::m_bTabsAlwaysTop  
 Domyślna lokalizacja dla kart w aplikacji.  
  
```  
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw ten statyczny element członkowski `TRUE` wymusić wszystkich kartach w aplikacji, który będzie wyświetlany w górnej części okienka z kartami.  
  
 Tę wartość należy ustawić przed utworzeniem okienko z kartami.  
  
 Wartość domyślna to `FALSE`.  
  
##  <a name="m_ptabwndrtc"></a>CTabbedPane::m_pTabWndRTC  
 Informacje o klasie czasu wykonywania dla niestandardowego `CMFCTabCtrl`-pochodzi z obiektu.  
  
```  
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw wartość tej zmiennej statycznego elementu członkowskiego na wskaźnik do informacji o klasie czasu wykonywania o `CMFCTabCtrl`-pochodnych obiektu, jeśli używasz niestandardowych okien z kartami wewnątrz okienka z kartami.  
  
##  <a name="resettabs"></a>CTabbedPane::ResetTabs  
 Resetuje wszystkie okienka z kartami do stanu domyślnego.  
  
```  
static void ResetTabs();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby przywrócić wszystkie okienka z kartami do stanu domyślnego. Po wywołaniu, ta metoda powoduje zresetowanie rozmiary obramowania i automatyczne kolor stanu wszystkich okienek z kartami.  
  
##  <a name="settabautocolors"></a>CTabbedPane::SetTabAutoColors  
 Ustawia listę kolorów niestandardowych, które są używane, gdy jest włączona funkcja automatycznego kolorów.  
  
```  
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`arColors`  
 Zawiera tablicę kolorów, by ustawić.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby dostosować listę kolorów, które są używane, gdy jest włączona funkcja automatycznego kolorów. To jest funkcja statyczna i ma wpływ na wszystkich kartach okienka w aplikacji.  
  
 Użyj [CTabbedPane::EnableTabAutoColor](#enabletabautocolor) Aby włączyć lub wyłączyć funkcję automatycznego kolorów.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)   
 [Klasa CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)   
 [Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)
