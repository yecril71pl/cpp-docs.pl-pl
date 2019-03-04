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
ms.openlocfilehash: be11bcd4cdbcd8448cc54f688d7dab9b61f49a57
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304083"
---
# <a name="cmfcoutlookbar-class"></a>Klasa CMFCOutlookBar

Okienka z zakładkami z wygląd **okienka nawigacji** w programie Microsoft Outlook 2000 lub Outlook 2003. `CMFCOutlookBar` Obiekt zawiera [klasa CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md) obiektu i szereg kart. Karty mogą być [klasa CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) obiektów lub `CWnd`-obiektami wywodzącymi. Użytkownikowi jako seria przycisków i obszar wyświetlacza zostanie wyświetlony pasek programu Outlook. Gdy użytkownik kliknie przycisk, wyświetlany jest odpowiedni formant lub okienko przycisku.

## <a name="syntax"></a>Składnia

```cpp
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
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Określa, czy mogą zostać zniszczone pustego okienka z zakładkami. (Overrides [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Określa, czy do okienko paska Outlook może być zadokowane innego okienka. (Przesłania CDockablePane::CanAcceptPane).|
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Określa, czy podpisu dla okienka z zakładkami ten sam tekst jest wyświetlany jako aktywną kartę. (Przesłania [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).)|
|[CMFCOutlookBar::Create](#create)|Tworzy kontrolkę paska Outlook.|
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|Tworzy niestandardowej karty pasek programu Outlook.|
|`CMFCOutlookBar::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Określa, czy użytkownik dokowany pasek sterowania do zewnętrznej krawędzi paska Outlook.|
|[CMFCOutlookBar::FloatTab](#floattab)|Liczby zmiennoprzecinkowe okienko, ale tylko wtedy, jeśli zawartość okienka aktualnie znajduje się na karcie odłączane. (Przesłania [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Zwraca czcionkę tekstu, przycisków paska Outlook.|
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Zwraca rozmiar i położenie obszarów kartę paska Outlook. (Przesłania [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|
|`CMFCOutlookBar::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Określa, czy zachowanie paska Outlook naśladuje Microsoft Office Outlook 2003 (zobacz Uwagi).|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Wywoływane przez [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) po aktywną kartę została ustawiona za pomocą animacji.|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Wywoływane przez [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) przed karta zostanie ustawiona jako aktywną kartę za pomocą animacji.|
|[CMFCOutlookBar::OnScroll](#onscroll)|Wywoływane przez platformę, gdy pasek programu Outlook jest przewijanie w górę lub w dół.|
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|Usuwa niestandardowej karty pasek programu Outlook.|
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Ustawia czcionkę tekstu przycisków paska Outlook.|
|[CMFCOutlookBar::SetMode2003](#setmode2003)|Określa, czy zachowanie paska Outlook naśladuje Outlook 2003 (zobacz Uwagi).|

## <a name="remarks"></a>Uwagi

Na przykład paska Outlook zobacz [OutlookDemo próbki: Aplikacja OutlookDemo MFC](../../visual-cpp-samples.md).

## <a name="implementing-the-outlook-bar"></a>Implementacja paska Outlook

Aby użyć `CMFCOutlookBar` kontrolkę w aplikacji, wykonaj następujące kroki:

1. Osadzanie `CMFCOutlookBar` obiektu do klasy okna głównej ramki.

    ```cpp
    class CMainFrame : public CMDIFrameWnd
    {
        // ...
        CMFCOutlookBar m_wndOutlookBar;
        CMFCOutlookBarPane m_wndOutlookPane;
        // ...
    };
    ```

1. Podczas przetwarzania komunikatu WM_CREATE w ramce głównej, należy wywołać [CMFCOutlookBar::Create](#create) metody tworzenia paska sterowania kartę Outlook.

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. Uzyskiwanie wskaźnika do bazowego `CMFCOutlookBarTabCtrl` przy użyciu [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow).

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. Tworzenie [klasa CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) obiektu dla każdej karty, który zawiera przyciski.

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

1. Wywołaj [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) dodać każdej nowej karty. Ustaw *bDetachable* parametru na wartość FALSE, aby nadać stronie niemożliwe do odłączenia. Możesz też korzystać z [CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) dodać odłączane strony.

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. Aby dodać `CWnd`— pochodne kontroli (na przykład [klasa CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)) jako znak tabulatora, tworzyć formantu i wywołaniu [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) ją dodać do paska Outlook.

> [!NOTE]
>  Należy używać kontroli unikatowych identyfikatorów dla każdego [klasa CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) obiektu i dla każdego `CWnd`-pochodnych obiektu.

Aby dynamicznie dodać lub usunąć nowych stron w czasie wykonywania, należy użyć [CMFCOutlookBar::CreateCustomPage](#createcustompage) i [CMFCOutlookBar::RemoveCustomPage](#removecustompage).

## <a name="outlook-2003-mode"></a>Program Outlook 2003 w trybie

W trybie Outlook 2003 przycisków karty są umieszczane w dolnej części okienka paska Outlook. Jeśli nie ma wystarczającej ilości miejsca do wyświetlenia przycisków, zostaną one wyświetlone jako ikony w obszarze pasek narzędzi wzdłuż dolnej części okienka.

Użyj [CMFCOutlookBar::SetMode2003](#setmode2003) Aby włączyć tryb Outlook 2003. Użyj [CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) można ustawić mapy bitowej, który zawiera ikony, które są wyświetlane w dolnej części paska Outlook. Ikony w mapie bitowej muszą być uporządkowane według kolejność tabulacji.

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

Określa, czy mogą zostać zniszczone pustego okienka z zakładkami.

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pustego może zostać zniszczone okienka z zakładkami; w przeciwnym razie wartość FALSE. Domyślna implementacja zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Jeśli nie może zostać zniszczone pustego okienka z zakładkami, struktura ukrywa on zamiast tego.

##  <a name="canacceptpane"></a>  CMFCOutlookBar::CanAcceptPane

Określa, czy do okienko paska Outlook może być zadokowane innego okienka.

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Wskaźnik do innego okienka, który jest jest zadokowany do to okienko.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli w kolejnym okienku może być zadokowane, aby okienko paska Outlook; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Jeśli program Outlook, pasek jest w trybie Outlook 2003 dokowanie nie jest obsługiwany, więc wartość zwracana jest wartość FALSE.

Jeśli *pBar* parametr ma wartość NULL, ta metoda zwraca wartość FALSE.

W przeciwnym razie metoda ta działa jako podstawowej metody [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane), z tą różnicą, że nawet jeśli nie włączono dokowania, paska Outlook można włączyć innego paska Outlook bez możliwości dokowania nad nim.

##  <a name="cansetcaptiontexttotabname"></a>  CMFCOutlookBar::CanSetCaptionTextToTabName

Określa, czy podpisu dla okienka z zakładkami ten sam tekst jest wyświetlany jako aktywną kartę.

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli program Outlook paska tytuł okna jest automatycznie ustawiana na tekst aktywną kartę; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Użyj [CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) Aby włączyć lub wyłączyć tę funkcję.

W trybie Outlook 2003 to ustawienie jest zawsze włączone.

##  <a name="create"></a>  CMFCOutlookBar::Create

Tworzy kontrolkę paska Outlook.

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

*lpszCaption*<br/>
[in] Określa tytuł okna.

*pParentWnd*<br/>
[in] Określa wskaźnik do okna nadrzędnego. Nie może być równa NULL.

*Rect*<br/>
[in] Określa program outlook paska rozmiar i położenie w pikselach.

*nID*<br/>
[in] Określa identyfikator kontrolki. Musi się różnić od innego formantu identyfikatory używane w aplikacji.

*dwStyle*<br/>
[in] Określa styl paska sterowania żądaną. Możliwe wartości, zobacz [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwControlBarStyle*<br/>
[in] Określa specjalne style zdefiniowane przez bibliotekę.

*pContext*<br/>
[in] Utwórz kontekst.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli metoda się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CMFCOutlookBar` obiektu w dwóch krokach. Pierwsze wywołanie konstruktora, a następnie wywołaj `Create`, która tworzy kontrolkę paska outlook i dołącza go do `CMFCOutlookBar` obiektu.

Zobacz [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) listę dostępnych stylów zdefiniowany w bibliotece określoną przez *dwControlBarStyle*.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `Create` metody `CMFCOutlookBar` klasy. Ten fragment kodu jest częścią [przykładowy program Outlook wielu widoków](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

##  <a name="createcustompage"></a>  CMFCOutlookBar::CreateCustomPage

Tworzy niestandardowej karty pasek programu Outlook.

```cpp
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,
    BOOL bActivatePage=TRUE,
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,
    BOOL bEnableTextLabels=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszPageName*<br/>
[in] Etykieta strony.

*bActivatePage*<br/>
[in] W przypadku opcji TRUE stronie staje się aktywny przy jej tworzeniu.

*dwEnabledDocking*<br/>
[in] Kombinacja flag CBRS_ALIGN_ określa włączone strony dokowania, gdy strona jest odłączona.

*bEnableTextLabels*<br/>
[in] W przypadku opcji TRUE etykiety tekstowe są włączone dla przycisków, które znajdują się na stronie.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonej stronie, lub wartość NULL, jeśli nie można utworzyć.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia Zezwól użytkownikom na tworzenie niestandardowych stron pasek programu Outlook. Możesz utworzyć maksymalnie 100 stron w aplikacji. Kontrolka strony identyfikatory rozpoczynają się od 0xF000. Tworzenie zakończy się niepowodzeniem, jeśli łączna liczba stron niestandardowych paska Outlook przekracza 100.

Użyj [CMFCOutlookBar::RemoveCustomPage](#removecustompage) można usunąć strony niestandardowe.

##  <a name="doesallowdyninsertbefore"></a>  CMFCOutlookBar::DoesAllowDynInsertBefore

Określa, czy użytkownika można zadokować okienko do zewnętrznej krawędzi paska Outlook.

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Struktura wywołuje `DoesAllowDynInsertBefore` metody podczas wyszukiwania lokalizacji zadokować okienku dynamicznej. Jeśli funkcja zwraca wartość FALSE, struktura nie zezwala na dokowanie wszelkie dynamiczne okienku u zewnętrznych krawędzi okienka.

Zazwyczaj należy utworzyć paska Outlook jako formant statyczny niezmienny. Można zastąpić tę funkcję w klasie pochodnej i zwraca wartość TRUE, aby zmienić to zachowanie.

> [!NOTE]
>  Ponieważ okienka dynamicznej sprawdzić stan zadokowanego okienka statycznego, gdy dokowania, powinien zadokować okienka dynamicznej po statyczne okienek, jeśli to możliwe.

##  <a name="floattab"></a>  CMFCOutlookBar::FloatTab

Liczby zmiennoprzecinkowe okienko.

```cpp
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Wskaźnik do okienka na typ zmiennoprzecinkowy.

*nTabID*<br/>
[in] Liczony od zera indeks karty na typ zmiennoprzecinkowy.

*dockMethod*<br/>
[in] Określa metodę używaną do dokowanie panelu.  Aby uzyskać więcej informacji, zobacz [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).

*bHide*<br/>
[in] Wartość TRUE, aby ukryć okienko przed liczb zmiennoprzecinkowych; w przeciwnym razie wartość FALSE. W odróżnieniu od klasy bazowej wersję tej metody ten parametr nie ma wartości domyślnej.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zawartość okienka przestawione; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda przypomina [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab) z tą różnicą, że nie uwzględnia ostatnią kartę pozostałe w formancie paska Outlook na typ zmiennoprzecinkowy.

##  <a name="getbuttonsfont"></a>  CMFCOutlookBar::GetButtonsFont

Zwraca czcionki tekstu na stronie karty przycisk paska Outlook.

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu czcionki, który jest używany do wyświetlania tekstu w programie Outlook paska kart przycisk strony.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do pobierania czcionka, która jest używana do wyświetlania tekstu w kartach przycisk Strona programu Outlook. Czcionkę można ustawić za pomocą wywołania na [CMFCOutlookBar::SetButtonsFont](#setbuttonsfont).

##  <a name="gettabarea"></a>  CMFCOutlookBar::GetTabArea

Określa rozmiar i położenie karty obszarów paska Outlook.

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parametry

*rectTabAreaTop*<br/>
[out] Zawiera rozmiar i położenie (we współrzędnych klienta) obszaru górnej karty, jeśli funkcja zwraca.

*rectTabAreaBottom*<br/>
[out] Zawiera rozmiar i położenie (we współrzędnych klienta) wartości obszar karty w dół, gdy funkcja zwraca.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, aby określić rodzaj Dokowanie do okienka docelowego. Gdy struktura okaże się, że użytkownik przeciągnie okienko aby być zadokowane, za pośrednictwem obszaru karty w okienku docelowego, próbuje dodać pierwszego okienka jako na nowej karcie w okienku docelowego. W przeciwnym razie próbuje zadokować pierwszego okienka boku odpowiednie okienko docelowego. Szablon tworzy nowy kontener za pomocą suwaka, aby uwzględnić dodatkowe zadokowanego okienka.

Domyślna implementacja klasy `GetTabArea` zwraca cały obszar klienta paska Outlook, jeśli pasek programu Outlook jest statyczna; będącego, jeśli pasek programu Outlook nie liczb zmiennoprzecinkowych. W przeciwnym razie zwraca obszaru przyciski strony zająć się u góry i u dołu kontrolki paska.

Należy przesłonić tę metodę w klasie pochodnej od `CMFCOutlookBar` Aby zmienić to zachowanie.

##  <a name="ismode2003"></a>  CMFCOutlookBar::IsMode2003

Określa, czy zachowanie paska Outlook naśladuje Microsoft Office Outlook 2003.

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli pasek programu Outlook działa w trybie Microsoft Office 2003; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Możesz włączyć ten tryb, za pomocą [CMFCOutlookBar::SetMode2003](#setmode2003).

##  <a name="onafteranimation"></a>  CMFCOutlookBar::OnAfterAnimation

Wywoływane przez [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) po aktywną kartę została ustawiona za pomocą animacji.

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>Parametry

*nPage*<br/>
[in] Liczony od zera indeks strony karty, który ma zostać aktywowane.

### <a name="remarks"></a>Uwagi

Efekt wizualny ustawienia aktywnej karcie zależy od tego, czy włączono animacji. Aby uzyskać więcej informacji, zobacz [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).

##  <a name="onbeforeanimation"></a>  CMFCOutlookBar::OnBeforeAnimation

Wywoływane przez [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) przed karta zostanie ustawiona jako aktywną kartę za pomocą animacji.

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>Parametry

*nPage*<br/>
[in] Liczony od zera indeks strony karty, który ma aktywne.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli animacje powinny być używane w nowej karcie aktywne ustawienia, lub FAŁSZ, jeśli animacja powinna być wyłączona.

### <a name="remarks"></a>Uwagi

##  <a name="onscroll"></a>  CMFCOutlookBar::OnScroll

Wywoływane przez platformę, gdy pasek programu Outlook jest przewijanie w górę lub w dół.

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>Parametry

*bDown*<br/>
[in] Wartość TRUE, jeśli pasek programu Outlook jest przewinięcie w dół, lub FAŁSZ, jeśli jest przewijanie w górę.

### <a name="remarks"></a>Uwagi

##  <a name="removecustompage"></a>  CMFCOutlookBar::RemoveCustomPage

Usuwa niestandardowej strony karty pasek programu Outlook.

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>Parametry

*uiPage*<br/>
[in] Liczony od zera indeks strony w oknie nadrzędnym programu Outlook.

*pTargetWnd*<br/>
[in] Pointerto okno nadrzędne programu Outlook.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli niestandardowy strona została usunięta pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję można usunąć strony niestandardowe. Gdy strona zostaje usunięta jego identyfikator kontrolki są zwracane do puli dostępnych identyfikatorów.

Należy podać wskaźnik do [klasa CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md) obiekt, w którym znajduje się Strona ma zostać usunięty obecnie. Należy pamiętać, że odłączane stron dla użytkownika mogą być przenoszone między różne słupki programu Outlook, ale informacje o niestandardowej strony znajduje się w obiekcie pasek programu Outlook, dla którego należy wywoływana [CMFCOutlookBar::CreateCustomPage](#createcustompage).

Użyj [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) uzyskać wskaźnik do okna programu Outlook.

##  <a name="setbuttonsfont"></a>  CMFCOutlookBar::SetButtonsFont

Ustawia czcionkę tekstu przycisków paska Outlook.

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
[in] Określa czcionkę nowe.

*bRedraw*<br/>
[in] W przypadku opcji TRUE pasek programu Outlook zostanie narysowany ponownie.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia ustawianie czcionki dla tekstu wyświetlanego na przyciskach strony karty programu outlook.

##  <a name="setmode2003"></a>  CMFCOutlookBar::SetMode2003

Określa, czy zachowanie paska Outlook naśladuje Outlook 2003.

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>Parametry

*bMode2003*<br/>
[in] W przypadku opcji TRUE jest włączony tryb Office 2003.

### <a name="remarks"></a>Uwagi

Aby włączyć lub wyłączyć tryb Office 2003, należy użyć tej funkcji. W tym trybie paska Outlook zawiera dodatkowych narzędzi, za pomocą przycisku dostosowywania. Zachowanie paska Outlook jest zgodny z zachowaniem paska Outlook, Microsoft Office 2003.

Domyślnie ten tryb jest wyłączona.

> [!NOTE]
>  Ta funkcja musi zostać wywołana przed [CMFCOutlookBar::Create](#create).

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[Klasa CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[Klasa CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)
