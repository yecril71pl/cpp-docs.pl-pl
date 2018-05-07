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
ms.openlocfilehash: 7d9c60ee3601cd4055e963997a6cd4f8bbd48b14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcautohidebar-class"></a>Klasa CMFCAutoHideBar
`CMFCAutoHideBar` Klasa jest klasą specjalnych narzędzi implementujący funkcja.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
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
|[CMFCAutoHideBar::Create](#create)|Tworzy pasek sterowania i dołącza go do [CPane](../../mfc/reference/cpane-class.md) obiektu. (Przesłania [CPane::Create](../../mfc/reference/cpane-class.md#create).)|  
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||  
|[CMFCAutoHideBar::GetVisibleCount](#getvisiblecount)||  
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|Wywoływane przez platformę, gdy menu okienka specjalne ma być wyświetlany. (Przesłania [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|  
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||  
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|(Przesłania [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).)|  
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||  
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||  
|[CMFCAutoHideBar::StretchPane](#stretchpane)|Rozciąga się okienko w pionie lub poziomie. (Przesłania [CBasePane::StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane).)|  
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||  
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|Opóźnienie między chwili, gdy użytkownik umieszcza kursor myszy za pośrednictwem [klasy CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) i chwilą, gdy platformę Pokazuje okno skojarzone.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy użytkownik zmienia okienku doku na tryb autoukrywania, platformę automatycznie tworzy `CMFCAutoHideBar` obiektu. Tworzy także niezbędne [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) i [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) obiektów. Każdy `CAutoHideDockSite` obiekt jest skojarzony z osobą `CMFCAutoHideButton`.  
  
 `CMFCAutoHideBar` Klasa implementuje wyświetlanie `CAutoHideDockSite` po użytkownika przesuwania wskaźnika myszy nad `CMFCAutoHideButton`. Pasek narzędzi odebrania wiadomości WM_MOUSEMOVE, `CMFCAutoHideBar` uruchamia czasomierz. Po zakończeniu pracy czasomierza wysyła pasek narzędzi WM_TIMER powiadomienie o zdarzeniu. Pasek narzędzi obsługuje to zdarzenie przez sprawdzenie, czy wskaźnik myszy znajduje się na tej samej przycisku autoukrywania, który został umieszczony nad przy uruchamianiu czasomierza. Jeśli tak jest, dołączonego `CAutoHideDockSite` jest wyświetlany.  
  
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
 Dodaje funkcje do `CDockablePane` okna, który umożliwia automatyczne ukrywanie.  
  
```  
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pAutoHideWnd`  
 W oknie, w którym chcesz ukryć.  
  
 [in] `dwAlignment`  
 Wartość, która określa sposób wyrównania automatyczne ukrywanie przycisku w oknie aplikacji.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 `dwAlignment` Parametr wskazuje, gdzie znajduje się przycisk autoukrywania w aplikacji. Parametr może być jednym z następujących wartości:  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
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
 [in] `bStretch`  
 [in] `bHorz`  
  
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
 [in] `lpszClassName`  
 [in] `dwStyle`  
 [in] `rect`  
 [in] `pParentWnd`  
 [in] `nID`  
 [in] `dwControlBarStyle`  
 [in] `pContext`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getfirstahwindow"></a>  CMFCAutoHideBar::GetFirstAHWindow  
 Zwraca wskaźnik do pierwszego automatyczne ukrywanie okna aplikacji.  
  
```  
CDockablePane* GetFirstAHWindow();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Automatyczne ukrywanie okna pierwszej w aplikacji lub wartość NULL, jeśli nie ma takiego.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getvisiblecount"></a>  CMFCAutoHideBar::GetVisibleCount  
 Pobiera liczbę widocznych autoukrywania przycisków.  
  
```  
int GetVisibleCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę widocznych autoukrywania przycisków.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_nshowahwnddelay"></a>  CMFCAutoHideBar::m_nShowAHWndDelay  
 Opóźnienie między chwili, gdy użytkownik umieszcza kursor myszy za pośrednictwem [klasy CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) i chwilą, gdy platformę Pokazuje okno skojarzone.  
  
```  
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;  
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik umieszcza kursor myszy za pośrednictwem `CMFCAutoHideButton`, występuje niewielkie opóźnienie, zanim w ramach Wyświetla okno skojarzone. Ten parametr określa długość tej opóźnienie w milisekundach.  
  
##  <a name="onshowcontrolbarmenu"></a>  CMFCAutoHideBar::OnShowControlBarMenu  

  
```  
virtual BOOL OnShowControlBarMenu(CPoint);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `CPoint`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="removeautohidewindow"></a>  CMFCAutoHideBar::RemoveAutoHideWindow  
 Usuwa i niszczy okno autoukrywania.  
  
```  
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```  
  
### <a name="parameters"></a>Parametry  
 CDockablePane * `pAutoHideWnd`  
 Automatyczne ukrywanie okna do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setactiveingroup"></a>  CMFCAutoHideBar::SetActiveInGroup  
 Flagi automatyczne ukrywanie paska jako aktywne.  
  
```  
virtual void SetActiveInGroup(BOOL bActive);  
```  
  
### <a name="parameters"></a>Parametry  
 [in] WARTOŚĆ LOGICZNA `bActive`  
 Wartość TRUE, aby aktywna; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).  
  
##  <a name="setrecentvisiblestate"></a>  CMFCAutoHideBar::SetRecentVisibleState  

  
```  
void SetRecentVisibleState(BOOL bState);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bState`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="showautohidewindow"></a>  CMFCAutoHideBar::ShowAutoHideWindow  
 Pokazuje okno autoukrywania.  
  
```  
BOOL ShowAutoHideWindow(
        CDockablePane* pAutoHideWnd,  
        BOOL bShow,  
        BOOL bDelay);  
```  
  
### <a name="parameters"></a>Parametry  
 [in] CDockablePane * `pAutoHideWnd`  
 [in] WARTOŚĆ LOGICZNA `bShow`  
 Wartość TRUE, aby wyświetlić okno.  
  
 [in] WARTOŚĆ LOGICZNA `bDelay`  
 Ten parametr jest ignorowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="stretchpane"></a>  CMFCAutoHideBar::StretchPane  
 Zmienia rozmiar paska autoukrywania w stanie zwinięte, aby dopasować `CMFCAutoHideButton` obiektu.  
  
```  
virtual CSize StretchPane(
    int nLength,   
    BOOL bVert);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nLength`  
 Wartość nie jest używana w implementacji podstawowej. W implementacjach pochodnej Użyj tej wartości, aby określić czas, po zmianie rozmiaru okienka.  
  
 [in] `bVert`  
 Wartość nie jest używana w implementacji podstawowej. W implementacji pochodnej, użyj `TRUE` do obsługi w przypadku, gdy pasek autoukrywania zwinięciu pionowo, i `FALSE` w przypadku, gdy pasek autoukrywania zwinięciu poziomo.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar wynikowy po zmianie rozmiaru okienka.  
  
### <a name="remarks"></a>Uwagi  
 Klasy pochodne mogą przesłaniać tę metodę, aby dostosować zachowanie.  
  
##  <a name="unsetautohidemode"></a>  CMFCAutoHideBar::UnSetAutoHideMode  
 Wyłącza automatyczne ukrywanie tryb dla grupy autoukrywania pasków.  
  
```  
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)  
```  
  
### <a name="parameters"></a>Parametry  
 [in] pFirstBarInGroup  
 Wskaźnik do pierwszego paska autoukrywania w grupie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="updatevisiblestate"></a>  CMFCAutoHideBar::UpdateVisibleState  
 Wywoływane przez platformę, gdy automatyczne ukrywanie paska musi zostać narysowany ponownie.  
  
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
