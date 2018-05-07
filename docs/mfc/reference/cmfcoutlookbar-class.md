---
title: Klasa CMFCOutlookBar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar::AllowDestroyEmptyTabbedPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanAcceptPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanSetCaptionTextToTabName
- AFXOUTLOOKBAR/CMFCOutlookBar::Create
- AFXOUTLOOKBAR/CMFCOutlookBar::CreateCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::DoesAllowDynInsertBefore
- AFXOUTLOOKBAR/CMFCOutlookBar::FloatTab
- AFXOUTLOOKBAR/CMFCOutlookBar::GetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::GetTabArea
- AFXOUTLOOKBAR/CMFCOutlookBar::IsMode2003
- AFXOUTLOOKBAR/CMFCOutlookBar::OnAfterAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnBeforeAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnScroll
- AFXOUTLOOKBAR/CMFCOutlookBar::RemoveCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::SetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::SetMode2003
dev_langs:
- C++
helpviewer_keywords:
- CMFCOutlookBar [MFC], AllowDestroyEmptyTabbedPane
- CMFCOutlookBar [MFC], CanAcceptPane
- CMFCOutlookBar [MFC], CanSetCaptionTextToTabName
- CMFCOutlookBar [MFC], Create
- CMFCOutlookBar [MFC], CreateCustomPage
- CMFCOutlookBar [MFC], DoesAllowDynInsertBefore
- CMFCOutlookBar [MFC], FloatTab
- CMFCOutlookBar [MFC], GetButtonsFont
- CMFCOutlookBar [MFC], GetTabArea
- CMFCOutlookBar [MFC], IsMode2003
- CMFCOutlookBar [MFC], OnAfterAnimation
- CMFCOutlookBar [MFC], OnBeforeAnimation
- CMFCOutlookBar [MFC], OnScroll
- CMFCOutlookBar [MFC], RemoveCustomPage
- CMFCOutlookBar [MFC], SetButtonsFont
- CMFCOutlookBar [MFC], SetMode2003
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5640f634276f87d0a41633354a7dde0ed65a2940
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcoutlookbar-class"></a>Klasa CMFCOutlookBar
Okienko z kartami z wygląd **okienka nawigacji** w programie Microsoft Outlook 2000 lub Outlook 2003. `CMFCOutlookBar` Zawiera obiekt [klasy CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md) obiekt i szereg kart. Karty mogą być [klasy CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) obiektów lub `CWnd`-pochodnych obiektów. Do użytkownika zostanie wyświetlony pasek Outlook jako serię przycisków i obszaru wyświetlania. Gdy użytkownik kliknie przycisk, odpowiedniego formantu lub przycisk okienko jest wyświetlana.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCOutlookBar : public CBaseTabbedPane  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCOutlookBar::CMFCOutlookBar`|Domyślny konstruktor.|  
|`CMFCOutlookBar::~CMFCOutlookBar`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Określa, czy puste okienko z kartami może zostać zniszczone. (Przesłania [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|  
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Określa, czy innego okienka może być zadokowany w okienku paska programu Outlook. (Zastępuje CDockablePane::CanAcceptPane).|  
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Określa, czy podpis dla tego okienka z kartami tego samego tekstu jest wyświetlana jako aktywnej karty. (Przesłania [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).)|  
|[CMFCOutlookBar::Create](#create)|Tworzy kontrolkę paska programu Outlook.|  
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|Tworzy niestandardowe kartę pasek programu Outlook.|  
|`CMFCOutlookBar::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Określa, czy użytkownik dokowany pasek sterowania do zewnętrznej krawędzi paska Outlook.|  
|[CMFCOutlookBar::FloatTab](#floattab)|Przesunięty okienku, ale tylko wtedy, jeśli okienku aktualnie znajduje się na karcie odłączane. (Przesłania [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|  
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Zwraca czcionki tekstu na przycisków paska Outlook.|  
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Zwraca rozmiar i położenie obszarów karty na pasku Outlook. (Przesłania [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|  
|`CMFCOutlookBar::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Określa, czy zachowanie paska Outlook naśladuje Microsoft Outlook pakietu Office 2003 (zobacz Uwagi).|  
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Wywoływane przez [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) po active karta została ustawiona przy użyciu animacji.|  
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Wywoływane przez [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) przed karty zostanie ustawiona jako aktywnej karty przy użyciu animacji.|  
|[CMFCOutlookBar::OnScroll](#onscroll)|Wywoływane przez platformę, gdy pasek Outlook jest przewijania w górę lub w dół.|  
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|Usuwa niestandardowego kartę paska programu Outlook.|  
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Ustawia czcionkę tekstu przycisków paska Outlook.|  
|[CMFCOutlookBar::SetMode2003](#setmode2003)|Określa, czy zachowanie paska Outlook naśladuje Outlook 2003 (zobacz Uwagi).|  
  
## <a name="remarks"></a>Uwagi  
 Na przykład paska Outlook zobacz [OutlookDemo próbki: aplikacja OutlookDemo MFC](../../visual-cpp-samples.md).  
  
## <a name="implementing-the-outlook-bar"></a>Implementacja paska Outlook  
 Aby użyć `CMFCOutlookBar` kontroli aplikacji, wykonaj następujące kroki:  
  
1.  Osadź `CMFCOutlookBar` obiektu do klasy okna w ramce głównej.  
  
 ```  
    class CMainFrame : public CMDIFrameWnd  
 { ...  
    CMFCOutlookBar m_wndOutlookBar;  
    CMFCOutlookBarPane m_wndOutlookPane;  
 ... };  
 ```  
2.  Podczas przetwarzania `WM_CREATE` komunikat w ramce głównej wywołania [CMFCOutlookBar::Create](#create) metodę w celu utworzenia paska formantu karty Outlook.  
  
 ```  
    m_wndOutlookBar.Create (_T("Shortcuts"),
    this,
    CRect (0,
    0,
    100,
    100),
    ID_VIEW_OUTLOOKBAR,
    WS_CHILD | WS_VISIBLE | CBRS_LEFT);

 ```  
3.  Uzyskiwanie wskaźnika do odpowiadającego `CMFCOutlookBarTabCtrl` za pomocą [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow).  
  
 ```  
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();

 ```  
4.  Utwórz [klasy CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) obiektu dla każdej karty, który zawiera przyciski.  
  
 ```  
    m_wndOutlookPane.Create (&m_wndOutlookBar,
    AFX_DEFAULT_TOOLBAR_STYLE,
    ID_OUTLOOK_PANE_GENERAL,
    AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);
*// make the Outlook pane detachable (enable docking)  
    m_wndOutlookPane.EnableDocking (CBRS_ALIGN_ANY);
*// add buttons  
    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_MAINFRAME), "About",
    ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON), "Open",
    ID_FILE_OPEN);

 ```  
5.  Wywołanie [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) można dodać każdego nowej karcie. Ustaw `bDetachable` parametr `FALSE` dokonanie niemożliwe do odłączenia strony. Lub użyj [CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) dodać odłączane strony.  
  
 ```  
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1,
    TRUE);

 ```  
6.  Aby dodać `CWnd`— pochodnych kontroli (na przykład [CMFCShellTreeCtrl klasy](../../mfc/reference/cmfcshelltreectrl-class.md)) jako karty, Utwórz kontroli i wywołanie [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) Aby dodać go do paska Outlook.  
  
> [!NOTE]
>  Należy używać formantu unikatowych identyfikatorów dla każdego [klasy CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) obiektu i dla każdego `CWnd`-pochodzi z obiektu.  
  
 Do dynamicznego dodawania i usuwania nowych stron w czasie wykonywania, użyj [CMFCOutlookBar::CreateCustomPage](#createcustompage) i [CMFCOutlookBar::RemoveCustomPage](#removecustompage).  
  
## <a name="outlook-2003-mode"></a>Program Outlook w trybie 2003  
 W trybie Outlook 2003 przycisków karty znajdują się w dolnej części okienka paska programu Outlook. Jeśli nie jest wystarczające miejsca, aby wyświetlić przycisków, zostaną one wyświetlone jako ikony w obszarze pasek narzędzi wzdłuż dolnej części okienka.  
  
 Użyj [CMFCOutlookBar::SetMode2003](#setmode2003) Aby włączyć tryb Outlook 2003. Użyj [CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) można ustawić mapy bitowej, który zawiera ikony, które są wyświetlane w dolnej części paska Outlook. Ikony w mapie bitowej musi zostać określona przez indeks.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxoutlookbar.h  
  
##  <a name="allowdestroyemptytabbedpane"></a>  CMFCOutlookBar::AllowDestroyEmptyTabbedPane  
 Określa, czy puste okienko z kartami może zostać zniszczone.  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli pusty okienko z kartami może zostać zniszczone; w przeciwnym razie `FALSE`. Domyślna implementacja zawsze zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie może zostać zniszczone pusty okienko z kartami, platformę ukrywa on zamiast tego.  
  
##  <a name="canacceptpane"></a>  CMFCOutlookBar::CanAcceptPane  
 Określa, czy innego okienka może być zadokowany w okienku paska programu Outlook.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pBar`  
 Wskaźnik do innego okienka, który jest jest zadokowane do tego okienka.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli innego okienka może być zadokowany w okienku paska Outlook; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli pasek Outlook jest w trybie Outlook 2003, dokowanie nie jest obsługiwany, dlatego zwracana wartość jest `FALSE`.  
  
 Jeśli `pBar` parametr jest `NULL`, ta metoda zwraca `FALSE`.  
  
 W przeciwnym razie ta metoda działa jako podstawowej metody [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane), z wyjątkiem tego, że nawet jeśli nie włączono dokowania, pasek Outlook można włączyć innego paska Outlook możliwości dokowania nad nim.  
  
##  <a name="cansetcaptiontexttotabname"></a>  CMFCOutlookBar::CanSetCaptionTextToTabName  
 Określa, czy podpis dla tego okienka z kartami tego samego tekstu jest wyświetlana jako aktywnej karty.  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli paska tytuł okna Outlook jest automatycznie ustawiana tekst karcie active; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) Aby włączyć lub wyłączyć tę funkcję.  
  
 W trybie 2003 programu Outlook to ustawienie jest zawsze włączone.  
  
##  <a name="create"></a>  CMFCOutlookBar::Create  
 Tworzy kontrolkę paska programu Outlook.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwControlBarStyle=AFX_CBRS_RESIZE,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszCaption`  
 Określa tytuł okna.  
  
 [in] `pParentWnd`  
 Określa wskaźnik do okna nadrzędnego. Nie może być wartością NULL.  
  
 [in] `rect`  
 Określa program outlook paska rozmiar i położenie w pikselach.  
  
 [in] `nID`  
 Określa identyfikator formantu. Musi się różnić od innych kontroli identyfikatory używane w aplikacji.  
  
 [in] `dwStyle`  
 Określa styl paska żądanego formantu. Możliwe wartości, zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] `dwControlBarStyle`  
 Określa specjalne style zdefiniowane w bibliotece.  
  
 [in] `pContext`  
 Tworzenie kontekstu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CMFCOutlookBar` obiektu w dwóch krokach. Pierwsze wywołanie konstruktora, a następnie wywołać `Create`, która tworzy kontrolkę paska outlook i dołącza go do `CMFCOutlookBar` obiektu.  
  
 Zobacz [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) listę dostępnych style zdefiniowane biblioteki określoną przez `dwControlBarStyle`.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `Create` metody `CMFCOutlookBar` klasy. Następujący fragment kodu jest częścią [próbki Outlook wielu widoków](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]  
  
##  <a name="createcustompage"></a>  CMFCOutlookBar::CreateCustomPage  
 Tworzy niestandardowe kartę pasek programu Outlook.  
  
```  
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,  
    BOOL bActivatePage=TRUE,  
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,  
    BOOL bEnableTextLabels=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszPageName`  
 Etykieta strony.  
  
 [in] `bActivatePage`  
 Jeśli `TRUE`, strona staje się aktywny po jego utworzeniu.  
  
 [in] `dwEnabledDocking`  
 Kombinacja flag CBRS_ALIGN_ określa włączone strony dokowania odłączeniem strony.  
  
 [in] `bEnableTextLabels`  
 Jeśli `TRUE`, etykiety są włączone w przypadku przycisków, które znajdują się na stronie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo utworzonej strony, lub `NULL` Jeśli tworzenie nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby użytkownicy mogli tworzyć niestandardowe strony paska programu Outlook. Możesz utworzyć maksymalnie 100 stron w aplikacji. Formant strony identyfikatorów rozpoczyna się od 0xF000. Tworzenie zakończy się niepowodzeniem, jeśli łączna liczba niestandardowe strony paska Outlook przekracza 100.  
  
 Użyj [CMFCOutlookBar::RemoveCustomPage](#removecustompage) można usunąć strony niestandardowe.  
  
##  <a name="doesallowdyninsertbefore"></a>  CMFCOutlookBar::DoesAllowDynInsertBefore  
 Określa, czy użytkownik może dock okienko do zewnętrznej krawędzi paska Outlook.  
  
```  
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania framework `DoesAllowDynInsertBefore` metoda będzie szukał lokalizację do dock dynamiczne okienka. Jeśli funkcja zwraca `FALSE`, platformę nie zezwala na dokowanie wszelkie dynamiczne okienku zewnętrznej krawędzi okienka.  
  
 Zazwyczaj utworzenie paska Outlook jako statyczną kontrolkę niezmienny. Należy przesłonić tę funkcję w klasie pochodnej i zwracać `TRUE` Aby zmienić to zachowanie.  
  
> [!NOTE]
>  Ponieważ dynamiczne okienka sprawdzić stan zadokowanego okienka statycznych podczas dokowania, powinien dock dynamiczne okienka po okienka statycznych, jeśli to możliwe.  
  
##  <a name="floattab"></a>  CMFCOutlookBar::FloatTab  
 Pojawia się okienko.  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pBar`  
 Wskaźnik do typu float w okienku.  
  
 [in] `nTabID`  
 Liczony od zera indeks kartę, aby float.  
  
 [in] `dockMethod`  
 Określa metodę używaną do Dokowanie okienka.  Aby uzyskać więcej informacji, zobacz [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).  
  
 [in] `bHide`  
 `TRUE` Aby ukryć okienko zanim; w przeciwnym razie `FALSE`. W odróżnieniu od klasy podstawowej wersji tej metody ten parametr nie ma wartości domyślnej.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli okienko przestawione; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab) z tą różnicą, że nie pozwala na karcie pozostałych ostatniego formantu paska Outlook float.  
  
##  <a name="getbuttonsfont"></a>  CMFCOutlookBar::GetButtonsFont  
 Zwraca czcionki tekstu na stronie karty przycisk paska Outlook.  
  
```  
CFont* GetButtonsFont() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do obiektu czcionki, który jest używany do wyświetlania tekstu w programie Outlook pasku karty przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do pobierania czcionki, który służy do wyświetlania tekstu na programu Outlook przycisk karty. Czcionkę można ustawić poprzez wywołanie w [CMFCOutlookBar::SetButtonsFont](#setbuttonsfont).  
  
##  <a name="gettabarea"></a>  CMFCOutlookBar::GetTabArea  
 Określa rozmiar i położenie obszarów karty na pasku Outlook.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `rectTabAreaTop`  
 Po powrocie z funkcji zawiera rozmiar i położenie (we współrzędnych klienta) wartości obszar karty top.  
  
 [out] `rectTabAreaBottom`  
 Gdy funkcja zwraca zawiera rozmiar i położenie (we współrzędnych klienta) wartości obszar karty dolnej.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę, aby określić typ Dokowanie do okienka docelowej. Platformę Określa, że użytkownik przeciąga okienko, aby być zadokowane, nad obszarem kartę okienka docelowej, próbuje do dodania pierwszego okienka jako nową kartę okienka docelowej. W przeciwnym razie próby dock pierwszego okienka w odpowiedniej strony panelu docelowego. Platformę tworzy nowy kontener z suwaka, aby zmieścił się w okienku zadokowanych dodatkowe.  
  
 Domyślna implementacja `GetTabArea` zwraca obszaru klienckiego całego paska Outlook, jeśli paska Outlook static; będący, jeśli nie float paska Outlook. W przeciwnym wypadku zwraca obszaru przycisków strony zająć się u góry i u dołu formantu paska programu Outlook.  
  
 Należy przesłonić tę metodę w klasie pochodnej z `CMFCOutlookBar` Aby zmienić to zachowanie.  
  
##  <a name="ismode2003"></a>  CMFCOutlookBar::IsMode2003  
 Określa, czy zachowanie paska Outlook naśladuje Microsoft Office Outlook 2003.  
  
```  
BOOL IsMode2003() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli paska Outlook jest uruchomiony w trybie Microsoft Office 2003; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 W tym trybie można włączyć za pomocą [CMFCOutlookBar::SetMode2003](#setmode2003).  
  
##  <a name="onafteranimation"></a>  CMFCOutlookBar::OnAfterAnimation  
 Wywoływane przez [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) po active karta została ustawiona przy użyciu animacji.  
  
```  
virtual void OnAfterAnimation(int nPage);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nPage`  
 Liczony od zera indeks strony kartę, która ma zostać aktywowane.  
  
### <a name="remarks"></a>Uwagi  
 Efekt ustawienia na karcie active zależy od tego, czy włączono animacji. Aby uzyskać więcej informacji, zobacz [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).  
  
##  <a name="onbeforeanimation"></a>  CMFCOutlookBar::OnBeforeAnimation  
 Wywoływane przez [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) przed karty zostanie ustawiona jako aktywnej karty przy użyciu animacji.  
  
```  
virtual BOOL OnBeforeAnimation(int nPage);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nPage`  
 Liczony od zera indeks strony karty, który ma aktywne.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` czy animacja powinna być używana w karcie active nowe ustawienie lub `FALSE` czy animacja powinna być wyłączona.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onscroll"></a>  CMFCOutlookBar::OnScroll  
 Wywoływane przez platformę, gdy pasek Outlook jest przewijania w górę lub w dół.  
  
```  
virtual void OnScroll(BOOL bDown);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bDown`  
 `TRUE` Jeśli pasek Outlook jest przewijania w dół, lub `FALSE` Jeśli jest przewijanie w górę.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="removecustompage"></a>  CMFCOutlookBar::RemoveCustomPage  
 Usuwa niestandardowe strony karty paska programu Outlook.  
  
```  
BOOL RemoveCustomPage(
    UINT uiPage,  
    CMFCOutlookBarTabCtrl* pTargetWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiPage`  
 Liczony od zera indeks strony w oknie nadrzędnym programu Outlook.  
  
 [in] `pTargetWnd`  
 Pointerto okno nadrzędne programu Outlook.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli niestandardowej strony zostało usunięte pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można usunąć strony niestandardowe. Po usunięciu stronie jego identyfikator formantu jest zwracana do puli dostępnych identyfikatorów.  
  
 Należy podać wskaźnik do [klasy CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md) obiekt, w którym znajduje się strony, aby można obecnie usunąć. Należy pamiętać, że odłączane stron dla użytkownika mogą być przenoszone między różnych pasków programu Outlook, ale informacje o niestandardowej strony znajduje się w obiekcie pasek programu Outlook, dla której wywołano [CMFCOutlookBar::CreateCustomPage](#createcustompage).  
  
 Użyj [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) uzyskać wskaźnik do okna programu Outlook.  
  
##  <a name="setbuttonsfont"></a>  CMFCOutlookBar::SetButtonsFont  
 Ustawia czcionkę tekstu przycisków paska Outlook.  
  
```  
void SetButtonsFont(
    CFont* pFont,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pFont`  
 Określa czcionkę nowego.  
  
 [in] `bRedraw`  
 Jeśli `TRUE`, zostanie narysowany ponownie na pasku programu Outlook.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia Ustaw czcionkę dla tekstu wyświetlanego na przycisków strony karty programu outlook.  
  
##  <a name="setmode2003"></a>  CMFCOutlookBar::SetMode2003  
 Określa, czy zachowanie paska Outlook naśladuje Outlook 2003.  
  
```  
void SetMode2003(BOOL bMode2003=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bMode2003`  
 Jeśli PRAWDA, jest włączony tryb pakietu Office 2003.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji, aby włączyć lub wyłączyć tryb pakietu Office 2003. W tym trybie paska Outlook ma dodatkowych narzędzi z przycisku dostosowywania. Zachowanie paska Outlook jest zgodna z zachowaniem paska Outlook pakietu Microsoft Office 2003.  
  
 Ten tryb jest domyślnie wyłączona.  
  
> [!NOTE]
>  Ta funkcja musi zostać wywołana przed [CMFCOutlookBar::Create](#create).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)   
 [Klasa CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)   
 [Klasa CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)
