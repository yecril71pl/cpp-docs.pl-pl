---
title: Klasa CMFCOutlookBar
ms.date: 06/25/2018
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
ms.openlocfilehash: fe328cb0d857ff9154624d218b1b56362890ce81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369651"
---
# <a name="cmfcoutlookbar-class"></a>Klasa CMFCOutlookBar

Okienko z kartami z wyglądem **okienka nawigacji** w programie Microsoft Outlook 2000 lub Outlook 2003. Obiekt `CMFCOutlookBar` zawiera obiekt [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md) i serię kart. Karty mogą być [cmfcoutlookBarpane klasy](../../mfc/reference/cmfcoutlookbarpane-class.md) obiektów `CWnd`lub -pochodnych obiektów. Dla użytkownika pasek programu Outlook jest wyświetlany jako seria przycisków i obszar wyświetlania. Gdy użytkownik kliknie przycisk, zostanie wyświetlone odpowiednie okienko sterowania lub przycisku.

## <a name="syntax"></a>Składnia

```cpp
class CMFCOutlookBar : public CBaseTabbedPane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCOutlookBar::CMFCOutlookBar`|Domyślny konstruktor.|
|`CMFCOutlookBar::~CMFCOutlookBar`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Określa, czy puste okienko z kartami może zostać zniszczone. (Zastępuje [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Określa, czy do okienka paska programu Outlook można zadokować inne okienko. (Zastępuje CDockablePane::CanAcceptPane.)|
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Określa, czy podpis okienka z kartami wyświetla ten sam tekst co [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname)aktywna karta.|
|[CMFCOutlookBar::Tworzenie](#create)|Tworzy kontrolka paska programu Outlook.|
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|Tworzy niestandardową kartę paska programu Outlook.|
|`CMFCOutlookBar::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Określa, czy użytkownik może zadokować pasek sterowania na zewnętrznej krawędzi paska programu Outlook.|
|[CMFCOutlookBar::FloatTab](#floattab)|Unosi okienko, ale tylko wtedy, gdy okienko znajduje się obecnie na odłączanej karcie. (Overrides [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Zwraca czcionkę tekstu na przyciskach paska programu Outlook.|
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Zwraca rozmiar i położenie obszarów tabulacji na pasku programu Outlook. (Zastępuje [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|
|`CMFCOutlookBar::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Określa, czy zachowanie paska programu Outlook naśladuje zachowanie programu Microsoft Office Outlook 2003 (zobacz Uwagi).|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Wywoływana przez [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) po ustawieniu aktywnej karty przy użyciu animacji.|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Wywoływana przez [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) przed ustawioną stroną karty jako aktywną kartę przy użyciu animacji.|
|[CMFCOutlookBar::OnScroll](#onscroll)|Wywoływane przez platformę, jeśli pasek programu Outlook jest przewijanie w górę lub w dół.|
|[CMFCOutlookBar::Usuń Stronę zdejmiem](#removecustompage)|Usuwa niestandardową kartę paska programu Outlook.|
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Ustawia czcionkę tekstu na przyciskach paska programu Outlook.|
|[CMFCOutlookBar::SetMode2003](#setmode2003)|Określa, czy zachowanie paska programu Outlook naśladuje zachowanie programu Outlook 2003 (zobacz Uwagi).|

## <a name="remarks"></a>Uwagi

Na przykład paska programu Outlook zobacz [przykładowy program OutlookDemo: Aplikacja MFC OutlookDemo](../../overview/visual-cpp-samples.md).

## <a name="implementing-the-outlook-bar"></a>Implementowanie paska programu Outlook

Aby użyć `CMFCOutlookBar` formantu w aplikacji, wykonaj następujące kroki:

1. Osadź `CMFCOutlookBar` obiekt w klasie okna ramki głównej.

    ```cpp
    class CMainFrame : public CMDIFrameWnd
    {
        // ...
        CMFCOutlookBar m_wndOutlookBar;
        CMFCOutlookBarPane m_wndOutlookPane;
        // ...
    };
    ```

1. Podczas przetwarzania wiadomości WM_CREATE w ramce głównej należy wywołać [cmfcoutlookBar::Create](#create) metody, aby utworzyć formant karty pasek programu Outlook.

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. Uzyskaj wskaźnik do `CMFCOutlookBarTabCtrl` podstawy za pomocą [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow).

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. Utwórz obiekt [klasy CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) dla każdej karty zawierającej przyciski.

    ```cpp
    m_wndOutlookPane.Create(&m_wndOutlookBar,
        AFX_DEFAULT_TOOLBAR_STYLE,
        ID_OUTLOOK_PANE_GENERAL,
        AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);

    // make the Outlook pane detachable (enable docking)
    m_wndOutlookPane.EnableDocking(CBRS_ALIGN_ANY);

    // add buttons
    m_wndOutlookPane.AddButton(theApp.LoadIcon (IDR_MAINFRAME),
        "About",
        ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON),
        "Open",
        ID_FILE_OPEN);
    ```

1. Wywołaj [POLECENIE CMFCOutlookBarTabCtrl::AddTab,](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) aby *bDetachable* dodać każdą nową kartę. Możesz też użyć [polecenia CMFCOutlookBarTabCtrl::AddControl,](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) aby dodać odłączane strony.

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. Aby dodać `CWnd`formant pochodny (na przykład [CMFCShellTreeCtrl Class)](../../mfc/reference/cmfcshelltreectrl-class.md)jako kartę, utwórz formant i wywołaj [CMFCOutlookBarTabCtrl::AddTab,](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) aby dodać go do paska programu Outlook.

> [!NOTE]
> Należy użyć unikatowych identyfikatorów formantu dla każdego obiektu [klasy CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) i dla każdego `CWnd`obiektu pochodnego.

Aby dynamicznie dodawać lub usuwać nowe strony w czasie wykonywania, użyj [polecenia CMFCOutlookBar::CreateCustomPage](#createcustompage) i [CMFCOutlookBar::RemoveCustomPage](#removecustompage).

## <a name="outlook-2003-mode"></a>Tryb programu Outlook 2003

W trybie programu Outlook 2003 przyciski kart są umieszczone u dołu okienka paska programu Outlook. Jeśli nie ma wystarczającej ilości miejsca do wyświetlania przycisków, są one wyświetlane jako ikony w obszarze przypominającym pasek narzędzi u dołu okienka.

Użyj [CMFCOutlookBar::SetMode2003,](#setmode2003) aby włączyć tryb programu Outlook 2003. Użyj [polecenia CMFCOutlookBarTabCtrl::SetToolbarImageList,](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) aby ustawić mapę bitową zawierającą ikony wyświetlane na dole paska programu Outlook. Ikony na mapie bitowej muszą być uporządkowane według indeksu kart.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[Cdockablepane](../../mfc/reference/cdockablepane-class.md)

[Cbasetabbedpane](../../mfc/reference/cbasetabbedpane-class.md)

[Cmfcoutlookbar](../../mfc/reference/cmfcoutlookbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxoutlookbar.h

## <a name="cmfcoutlookbarallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CMFCOutlookBar::AllowDestroyEmptyTabbedPane

Określa, czy puste okienko z kartami może zostać zniszczone.

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli puste okienko z kartami może zostać zniszczone; w przeciwnym razie FALSE. Domyślna implementacja zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Jeśli nie można zniszczyć pustego okienka z kartami, struktura ukrywa go zamiast tego.

## <a name="cmfcoutlookbarcanacceptpane"></a><a name="canacceptpane"></a>CMFCOutlookBar::CanAcceptPane

Określa, czy do okienka paska programu Outlook można zadokować inne okienko.

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[w] Wskaźnik do innego okienka, które jest zadokowany do tego okienka.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli inne okienko można zadokować do okienka paska programu Outlook; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli pasek programu Outlook jest w trybie programu Outlook 2003, dokowanie nie jest obsługiwane, więc zwracana wartość jest FAŁSZ.

Jeśli parametr *pBar* ma wartość NULL, ta metoda zwraca wartość FAŁSZ.

W przeciwnym razie ta metoda zachowuje się jako metoda podstawowa [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane), z tą różnicą, że nawet jeśli dokowanie nie jest włączone, pasek programu Outlook może nadal włączyć inny pasek programu Outlook do zadokowania nad nim.

## <a name="cmfcoutlookbarcansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CMFCOutlookBar::CanSetCaptionTextToTabName

Określa, czy podpis okienka z kartami wyświetla ten sam tekst co aktywna karta.

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli podpis okna paska programu Outlook jest automatycznie ustawiany na tekst aktywnej karty; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj [CBaseTabbedPane::EnableSetCaptionTextToTabName,](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) aby włączyć lub wyłączyć tę funkcję.

W trybie programu Outlook 2003 to ustawienie jest zawsze włączone.

## <a name="cmfcoutlookbarcreate"></a><a name="create"></a>CMFCOutlookBar::Tworzenie

Tworzy kontrolka paska programu Outlook.

```cpp
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

*lpszCaption (własnowie)*<br/>
[w] Określa podpis okna.

*pParentWnd*<br/>
[w] Określa wskaźnik do okna nadrzędnego. Nie może być null.

*Rect*<br/>
[w] Określa rozmiar i położenie paska programu outlook w pikselach.

*Nid*<br/>
[w] Określa identyfikator formantu. Musi być inny od innych identyfikatorów formantu używanych w aplikacji.

*Dwstyle*<br/>
[w] Określa żądany styl paska sterowania. Aby uzyskać możliwe wartości, zobacz [Style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*styl dwControlBarStyle*<br/>
[w] Określa style zdefiniowane w bibliotece specjalne.

*Pcontext*<br/>
[w] Tworzenie kontekstu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CMFCOutlookBar` obiektu w dwóch krokach. Najpierw wywołać konstruktora, a następnie wywołać `Create`, który `CMFCOutlookBar` tworzy formant paska perspektywy i dołącza go do obiektu.

Zobacz [CBasePane::CreateEx,](../../mfc/reference/cbasepane-class.md#createex) aby uzyskać listę dostępnych stylów zdefiniowanych przez bibliotekę, które mają być określone przez *dwControlBarStyle*.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `Create` metody `CMFCOutlookBar` klasy. Ten fragment kodu jest częścią [przykładu Outlook Multi Views](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

## <a name="cmfcoutlookbarcreatecustompage"></a><a name="createcustompage"></a>CMFCOutlookBar::CreateCustomPage

Tworzy niestandardową kartę paska programu Outlook.

```cpp
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,
    BOOL bActivatePage=TRUE,
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,
    BOOL bEnableTextLabels=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszPageName*<br/>
[w] Etykieta strony.

*bAktywowaniePage*<br/>
[w] Jeśli true, strona staje się aktywna po utworzeniu.

*dwEnabledDocking*<br/>
[w] Kombinacja CBRS_ALIGN_ flag, która określa włączone strony dokowania, gdy strona jest odłączona.

*bUchytextne*<br/>
[w] Jeśli true, etykiety tekstowe są włączone dla przycisków, które znajdują się na stronie.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonej strony lub NULL, jeśli tworzenie nie powiodło się.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia użytkownikom tworzenie niestandardowych stron paska programu Outlook. Można utworzyć maksymalnie 100 stron na aplikację. Identyfikatory formantu strony zaczynają się od 0xF000. Tworzenie kończy się niepowodzeniem, jeśli całkowita liczba niestandardowych stron paska programu Outlook przekracza 100.

Użyj [CMFCOutlookBar::RemoveCustomPage,](#removecustompage) aby usunąć strony niestandardowe.

## <a name="cmfcoutlookbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCOutlookBar::DoesAllowDynInsertBefore

Określa, czy użytkownik może zadokować okienko na zewnętrznej krawędzi paska programu Outlook.

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca WARTOŚĆ FAŁSZ.

### <a name="remarks"></a>Uwagi

Struktura wywołuje `DoesAllowDynInsertBefore` metodę, gdy szuka lokalizacji do zadokowania okienka dynamicznego. Jeśli funkcja zwraca WARTOŚĆ FAŁSZ, struktura nie zezwala na dokowanie dowolnego okienka dynamicznego na zewnętrznych krawędziach okienka.

Zazwyczaj tworzysz pasek programu Outlook jako statyczny formant nieprzesłany. Tę funkcję można zastąpić w klasie pochodnej i zwrócić wartość PRAWDA, aby zmienić to zachowanie.

> [!NOTE]
> Ponieważ okienka dynamiczne sprawdzają stan zadokowanych okienek statycznych podczas dokowania, w miarę możliwości należy dokować okienka dynamiczne po okienkach statycznych.

## <a name="cmfcoutlookbarfloattab"></a><a name="floattab"></a>CMFCOutlookBar::FloatTab

Unosi okienko.

```cpp
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[w] Wskaźnik do okienka, aby upłynąć.

*nTabID (nTabID)*<br/>
[w] Indeks od zera karty do float.

*dokMetoda*<br/>
[w] Określa metodę, która ma być używana do zmiennego okienka.  Aby uzyskać więcej informacji, zobacz [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).

*bHide (ur.*<br/>
[w] PRAWDA, aby ukryć okienko przed unoszenia się na wodzie; w przeciwnym razie FALSE. W przeciwieństwie do wersji klasy podstawowej tej metody, ten parametr nie ma wartości domyślnej.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okienko unosiło się na wodzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda jest jak [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab) z tą różnicą, że nie włącza ostatniej pozostałej karty na formancie paska programu Outlook do float.

## <a name="cmfcoutlookbargetbuttonsfont"></a><a name="getbuttonsfont"></a>CMFCOutlookBar::GetButtonsFont

Zwraca czcionkę tekstu na kartach przycisku strony na pasku programu Outlook.

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu czcionki, który jest używany do wyświetlania tekstu na kartach przycisków strony na pasku programu Outlook.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do pobierania czcionki używanej do wyświetlania tekstu na kartach przycisków strony programu Outlook. Czcionkę można ustawić, wywołując [polecenie CMFCOutlookBar::SetButtonsFont](#setbuttonsfont).

## <a name="cmfcoutlookbargettabarea"></a><a name="gettabarea"></a>CMFCOutlookBar::GetTabArea

Określa rozmiar i położenie obszarów tabulacji na pasku programu Outlook.

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parametry

*reectTabAreaTop*<br/>
[na zewnątrz] Zawiera rozmiar i położenie (we współrzędnych klienta) górnego obszaru tabulacji po powrocie funkcji.

*pectTabAreaBottom*<br/>
[na zewnątrz] Zawiera rozmiar i położenie (we współrzędnych klienta) dolnego obszaru tabulacji po powrocie funkcji.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, aby określić typ dokowania do okienka docelowego. Gdy struktura określa, że użytkownik przeciąga okienko do zadokowania nad obszarem karty okienka docelowego, próbuje dodać pierwsze okienko jako nową kartę okienka docelowego. W przeciwnym razie próbuje zadokować pierwsze okienko po odpowiedniej stronie okienka docelowego. Struktura tworzy nowy kontener z suwakiem, aby pomieścić dodatkowe zadokowane okienko.

Domyślna implementacja `GetTabArea` zwraca cały obszar klienta paska programu Outlook, jeśli pasek programu Outlook jest statyczny; oznacza to, że jeśli pasek programu Outlook nie może float. W przeciwnym razie zwraca obszar, który przyciski strony zajmują u góry i u dołu kontrolki paska programu Outlook.

Zastąpić tę metodę `CMFCOutlookBar` w klasie pochodną, aby zmienić to zachowanie.

## <a name="cmfcoutlookbarismode2003"></a><a name="ismode2003"></a>CMFCOutlookBar::IsMode2003

Określa, czy zachowanie paska programu Outlook naśladuje zachowanie programu Microsoft Office Outlook 2003.

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pasek programu Outlook jest uruchomiony w trybie pakietu Microsoft Office 2003; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ten tryb można włączyć za pomocą [cmfcoutlookBar::SetMode2003](#setmode2003).

## <a name="cmfcoutlookbaronafteranimation"></a><a name="onafteranimation"></a>CMFCOutlookBar::OnAfterAnimation

Wywoływana przez [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) po ustawieniu aktywnej karty przy użyciu animacji.

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>Parametry

*strona nPage*<br/>
[w] Indeks od zera strony karty, która została uaktywnona.

### <a name="remarks"></a>Uwagi

Efekt wizualny ustawienia aktywnej karty zależy od tego, czy włączono animację. Aby uzyskać więcej informacji, zobacz [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).

## <a name="cmfcoutlookbaronbeforeanimation"></a><a name="onbeforeanimation"></a>CMFCOutlookBar::OnBeforeAnimation

Wywoływana przez [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) przed ustawioną stroną karty jako aktywną kartę przy użyciu animacji.

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>Parametry

*strona nPage*<br/>
[w] Indeks od zera strony karty, która ma być ustawiona jako aktywna.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli animacja powinna być używana do ustawiania nowej aktywnej karty, lub FAŁSZ, jeśli animacja powinna być wyłączona.

### <a name="remarks"></a>Uwagi

## <a name="cmfcoutlookbaronscroll"></a><a name="onscroll"></a>CMFCOutlookBar::OnScroll

Wywoływane przez platformę, jeśli pasek programu Outlook jest przewijanie w górę lub w dół.

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>Parametry

*bDown (doł.)*<br/>
[w] PRAWDA, jeśli pasek programu Outlook przewija się w dół, lub FALSE, jeśli jest przewijany w górę.

### <a name="remarks"></a>Uwagi

## <a name="cmfcoutlookbarremovecustompage"></a><a name="removecustompage"></a>CMFCOutlookBar::Usuń Stronę zdejmiem

Usuwa niestandardową stronę karty paska programu Outlook.

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>Parametry

*strona uiPage*<br/>
[w] Indeks od zera strony w nadrzędnym oknie programu Outlook.

*pTargetWnd (CeletWnd)*<br/>
[w] Wskaźnik do nadrzędnego okna programu Outlook.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli strona niestandardowa została pomyślnie usunięta; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby usunąć strony niestandardowe. Po usunięciu strony jego identyfikator formantu jest zwracany do puli dostępnych identyfikatorów.

Należy podać wskaźnik do [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md) obiektu, w którym strona do usunięcia obecnie znajduje się. Należy zauważyć, że użytkownik może przenosić odłączane strony między różnymi paskami programu Outlook, ale informacje o stronie niestandardowej znajdują się w obiekcie paska programu Outlook, dla którego został nazwany [CMFCOutlookBar::CreateCustomPage](#createcustompage).

Użyj [CBaseTabbedPane::GetUnderlyingWindow,](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) aby uzyskać wskaźnik do okna programu Outlook.

## <a name="cmfcoutlookbarsetbuttonsfont"></a><a name="setbuttonsfont"></a>CMFCOutlookBar::SetButtonsFont

Ustawia czcionkę tekstu na przyciskach paska programu Outlook.

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*pFont (pFont)*<br/>
[w] Określa nową czcionkę.

*bRedraw*<br/>
[w] Jeśli true, pasek programu Outlook zostanie ponownie narysowany.

### <a name="remarks"></a>Uwagi

Ta metoda służy do ustawiania czcionki dla tekstu wyświetlanego na przyciskach strony karty programu Outlook.

## <a name="cmfcoutlookbarsetmode2003"></a><a name="setmode2003"></a>CMFCOutlookBar::SetMode2003

Określa, czy zachowanie paska programu Outlook naśladuje zachowanie programu Outlook 2003.

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>Parametry

*bMode2003*<br/>
[w] Jeśli true, tryb pakietu Office 2003 jest włączony.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do włączania lub wyłączania trybu pakietu Office 2003. W tym trybie pasek programu Outlook ma dodatkowy pasek narzędzi z przyciskiem dostosowywania. Zachowanie paska programu Outlook jest zgodne z zachowaniem paska programu Outlook w pakiecie Microsoft Office 2003.

Domyślnie ten tryb jest wyłączony.

> [!NOTE]
> Ta funkcja musi być wywoływana przed [CMFCOutlookBar::Create](#create).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[Klasa CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[Klasa CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)
