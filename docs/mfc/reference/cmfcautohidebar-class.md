---
title: Klasa CMFCAutoHideBar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AddAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AllowShowOnPaneMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CalcFixedLayout
- AFXAUTOHIDEBAR/CMFCAutoHideBar::Create
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetFirstAHWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetVisibleCount
- AFXAUTOHIDEBAR/CMFCAutoHideBar::OnShowControlBarMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::RemoveAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetActiveInGroup
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetRecentVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::ShowAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::StretchPane
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UnSetAutoHideMode
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UpdateVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::m_nShowAHWndDelay
dev_langs:
- C++
helpviewer_keywords:
- CMFCAutoHideBar [MFC], CMFCAutoHideBar
- CMFCAutoHideBar [MFC], AddAutoHideWindow
- CMFCAutoHideBar [MFC], AllowShowOnPaneMenu
- CMFCAutoHideBar [MFC], CalcFixedLayout
- CMFCAutoHideBar [MFC], Create
- CMFCAutoHideBar [MFC], GetFirstAHWindow
- CMFCAutoHideBar [MFC], GetVisibleCount
- CMFCAutoHideBar [MFC], OnShowControlBarMenu
- CMFCAutoHideBar [MFC], RemoveAutoHideWindow
- CMFCAutoHideBar [MFC], SetActiveInGroup
- CMFCAutoHideBar [MFC], SetRecentVisibleState
- CMFCAutoHideBar [MFC], ShowAutoHideWindow
- CMFCAutoHideBar [MFC], StretchPane
- CMFCAutoHideBar [MFC], UnSetAutoHideMode
- CMFCAutoHideBar [MFC], UpdateVisibleState
- CMFCAutoHideBar [MFC], m_nShowAHWndDelay
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9ba9f6c2de8260ea846b51e2192ecfb967c5502
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719982"
---
# <a name="cmfcautohidebar-class"></a>Klasa CMFCAutoHideBar
`CMFCAutoHideBar` Klasa jest klasą specjalny pasek narzędzi, który implementuje funkcję automatycznego ukrywania.  

 Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.    
## <a name="syntax"></a>Składnia  
  
```  
class CMFCAutoHideBar : public CPane  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||  
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Przesłania `CPane::AllowShowOnPaneMenu`.)|  
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|(Przesłania [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCAutoHideBar::Create](#create)|Tworzy pasek sterowania i dołącza je do [CPane](../../mfc/reference/cpane-class.md) obiektu. (Przesłania [CPane::Create](../../mfc/reference/cpane-class.md#create).)|  
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||  
|[CMFCAutoHideBar::GetVisibleCount](#getvisiblecount)||  
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|Wywoływane przez platformę, gdy menu okienka specjalne ma być wyświetlany. (Przesłania [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|  
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||  
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|(Przesłania [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).)|  
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||  
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||  
|[CMFCAutoHideBar::StretchPane](#stretchpane)|Rozciąga okienko w pionie lub poziomie. (Przesłania [CBasePane::StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane).)|  
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||  
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|Czas opóźnienia między odnalezieniem po użytkownik umieszcza kursor myszy nad [klasa CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) , a moment, kiedy struktura Pokazuje okno skojarzone.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy użytkownik zmienia okienko dokowania, tryb automatycznego ukrywania, szablon automatycznie tworzy `CMFCAutoHideBar` obiektu. Tworzy również niezbędne [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) i [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) obiektów. Każdy `CAutoHideDockSite` obiekt jest skojarzony z osobą `CMFCAutoHideButton`.  
  
 `CMFCAutoHideBar` Klasa implementuje wyświetlanie `CAutoHideDockSite` po mysz użytkownika znajduje się nad `CMFCAutoHideButton`. Gdy pasek narzędzi otrzymuje wiadomość WM_MOUSEMOVE `CMFCAutoHideBar` uruchamia czasomierz. Po zakończeniu czasomierz wysyła pasek narzędzi powiadomienie o zdarzeniu WM_TIMER. Pasek narzędzi obsługuje to zdarzenie, sprawdzając, czy wskaźnik myszy znajduje się na tej samej przycisku automatycznego ukrywania, który został umieszczony nad uruchamianiu czasomierza. Jeśli tak jest, dołączony `CAutoHideDockSite` jest wyświetlana.  
  
 Długość opóźnienia czasomierza można kontrolować przez ustawienie `m_nShowAHWndDelay`. Wartość domyślna to 400 ms.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCAutoHideBar` obiektu i używać jej `GetDockSiteRow` metody.  
  
 [!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxautohidebar.h  
  
##  <a name="addautohidewindow"></a>  CMFCAutoHideBar::AddAutoHideWindow  
 Dodaje funkcjonalność do `CDockablePane` okna, która umożliwia automatyczne ukrywanie.  
  
```  
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parametry  
*pAutoHideWnd*<br/>
[in] Okno, które chcesz ukryć.  
  
*dwAlignment*<br/>
[in] Wartość, która określa wyrównanie przycisku automatycznego ukrywania okna aplikacji.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 *DwAlignment* parametr wskazuje, której przycisk Autoukrywanie znajduje się w aplikacji. Parametr może być jednym z następujących wartości:  
  
- CBRS_ALIGN_LEFT  
  
- CBRS_ALIGN_RIGHT  
  
- CBRS_ALIGN_TOP  
  
- CBRS_ALIGN_BOTTOM  
  
##  <a name="allowshowonpanemenu"></a>  CMFCAutoHideBar::AllowShowOnPaneMenu  

  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="calcfixedlayout"></a>  CMFCAutoHideBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
*bStretch*<br/>
[in] [in] *bHorz*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="cmfcautohidebar"></a>  CMFCAutoHideBar::CMFCAutoHideBar  
 Tworzy obiekt CMFCAutoHideBar.  
  
```  
CMFCAutoHideBar();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="create"></a>  CMFCAutoHideBar::Create  

  
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
*lpszClassName*<br/>
[in] [in] *dwStyle*  
*Rect*<br/>
[in] [in] *pParentWnd*  
*nID*<br/>
[in] [in] *dwControlBarStyle*  
 [in] *pContext*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getfirstahwindow"></a>  CMFCAutoHideBar::GetFirstAHWindow  
 Zwraca wskaźnik do pierwszego okna automatycznego ukrywania w aplikacji.  
  
```  
CDockablePane* GetFirstAHWindow();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwsze okno automatycznego ukrywania w aplikacji, lub wartość NULL, jeśli nie istnieje.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getvisiblecount"></a>  CMFCAutoHideBar::GetVisibleCount  
 Pobiera liczbę widocznych Autoukrywanie przycisków.  
  
```  
int GetVisibleCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę widocznych Autoukrywanie przycisków.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_nshowahwnddelay"></a>  CMFCAutoHideBar::m_nShowAHWndDelay  
 Czas opóźnienia między odnalezieniem po użytkownik umieszcza kursor myszy nad [klasa CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) , a moment, kiedy struktura Pokazuje okno skojarzone.  
  
```  
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;  
```  
  
### <a name="remarks"></a>Uwagi  
 Po użytkownik umieszcza kursor myszy nad `CMFCAutoHideButton`, ma niewielkie opóźnienie, zanim ramach wyświetli okno skojarzone. Ten parametr określa długość tej opóźnienie w milisekundach.  
  
##  <a name="onshowcontrolbarmenu"></a>  CMFCAutoHideBar::OnShowControlBarMenu  

  
```  
virtual BOOL OnShowControlBarMenu(CPoint);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *CPoint*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="removeautohidewindow"></a>  CMFCAutoHideBar::RemoveAutoHideWindow  
 Usuwa i niszczy okno automatycznego ukrywania.  
  
```  
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```  
  
### <a name="parameters"></a>Parametry  
 CDockablePane * *pAutoHideWnd*  
 Okno automatycznego ukrywania do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setactiveingroup"></a>  CMFCAutoHideBar::SetActiveInGroup  
 Flagi automatycznie Ukryj pasek jako aktywny.  
  
```  
virtual void SetActiveInGroup(BOOL bActive);  
```  
  
### <a name="parameters"></a>Parametry  
 [in] Wartość logiczna *bWykonywanie aktywnych*  
 Wartość TRUE, aby ustawić aktywny; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).  
  
##  <a name="setrecentvisiblestate"></a>  CMFCAutoHideBar::SetRecentVisibleState  

  
```  
void SetRecentVisibleState(BOOL bState);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bState*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="showautohidewindow"></a>  CMFCAutoHideBar::ShowAutoHideWindow  
 Pokazuje okno automatycznego ukrywania.  
  
```  
BOOL ShowAutoHideWindow(
        CDockablePane* pAutoHideWnd,  
        BOOL bShow,  
        BOOL bDelay);  
```  
  
### <a name="parameters"></a>Parametry  
 [in] CDockablePane * *pAutoHideWnd*  
 [in] Wartość logiczna *bShow*  
 Wartość TRUE, aby wyświetlić okno.  
  
 [in] Wartość logiczna *bDelay*  
 Ten parametr jest ignorowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="stretchpane"></a>  CMFCAutoHideBar::StretchPane  
 Zmienia rozmiar paska automatycznego ukrywania w stanie zwiniętym, aby dopasować `CMFCAutoHideButton` obiektu.  
  
```  
virtual CSize StretchPane(
    int nLength,   
    BOOL bVert);
```  
  
### <a name="parameters"></a>Parametry  
*nLength*<br/>
[in] Wartość jest nieużywana w podstawowej implementacji. W implementacji pochodnej Użyj tej wartości, aby wskazać długość o zmienionym rozmiarze okienka.  
  
*bVert*<br/>
[in] Wartość jest nieużywana w podstawowej implementacji. W implementacji pochodnej Użyj wartość true, uchwyt przypadek, gdzie na pasku autoukrywanie jest zwinięta w pionie, a wartość FALSE w przypadku, gdy pasek autoukrywanie jest zwinięta w poziomie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynikowy rozmiar okienka o zmienionym rozmiarze.  
  
### <a name="remarks"></a>Uwagi  
 Klasy pochodne mogą przesłaniać tę metodę, aby dostosować zachowanie.  
  
##  <a name="unsetautohidemode"></a>  CMFCAutoHideBar::UnSetAutoHideMode  
 Wyłącza automatyczne ukrywanie tryb dla grupy paski Autoukrywanie.  
  
```  
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)  
```  
  
### <a name="parameters"></a>Parametry  
 [in] pFirstBarInGroup  
 Wskaźnik do pierwszego paska automatycznego ukrywania w grupie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="updatevisiblestate"></a>  CMFCAutoHideBar::UpdateVisibleState  
 Wywoływane przez platformę, gdy pasek Autoukrywanie musi być narysowany ponownie.  
  
```  
void UpdateVisibleState();
```  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CPane](../../mfc/reference/cpane-class.md)   
 [Klasa CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)   
 [Klasa CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)
