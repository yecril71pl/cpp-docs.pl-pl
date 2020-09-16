---
title: Klasa CTabbedPane
ms.date: 11/04/2016
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
ms.openlocfilehash: cfc0a3099b1d5ff9bd1093cc911745bd61cde64c
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686642"
---
# <a name="ctabbedpane-class"></a>Klasa CTabbedPane

Implementuje funkcje okienka z kartami do odłączenia.

lub więcej szczegółów można znaleźć w dokumencie kod źródłowy znajdujący się w folderze **VC \\ atlmfc \\ src \\ MFC** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CTabbedPane : public CBaseTabbedPane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CTabbedPane::CTabbedPane`|Konstruktor domyślny.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTabbedPane::D etachPane](#detachpane)|(Przesłania [CBaseTabbedPane::D etachpane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|Włącza lub wyłącza automatyczne Kolorowanie kart.|
|[CTabbedPane::FloatTab](#floattab)|Przepływa z okienka, ale tylko wtedy, gdy okienko znajduje się obecnie na karcie odłączalnej. (Zastępuje [CBaseTabbedPane:: FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CTabbedPane::GetTabArea](#gettabarea)|Zwraca rozmiar i położenie obszaru karty w oknie z kartami.|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Określa, czy okienko z kartami może być przełączane w tryb autoukrywania. (Przesłania [CBaseTabbedPane:: HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|Określa, czy karty znajdują się u dołu okna.|
|[CTabbedPane::ResetTabs](#resettabs)|Resetuje wszystkie okienka z kartami do stanu domyślnego.|
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|Ustawia listę niestandardowych kolorów, które mogą być używane, gdy funkcja Autocolor jest włączona.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CTabbedPane:: m_bTabsAlwaysTop](#m_btabsalwaystop)|Domyślna lokalizacja dla kart w aplikacji.|
|[CTabbedPane:: m_pTabWndRTC](#m_ptabwndrtc)|Informacje o klasie środowiska uruchomieniowego dla `CMFCTabCtrl` obiektu pochodnego niestandardowego.|

## <a name="remarks"></a>Uwagi

Struktura automatycznie tworzy wystąpienie tej klasy, gdy użytkownik dołącza jedno okienko do drugiego, wskazując podpis w drugim okienku. Wszystkie okienka z kartami, które są tworzone przez platformę, mają identyfikator-1.

Aby określić regularne karty zamiast kart w stylu programu Outlook, Przekaż styl AFX_CBRS_REGULAR_TABS do metody [CDockablePane:: CreateEx](../../mfc/reference/cdockablepane-class.md#createex) .

Jeśli utworzysz okienko z kartami z odłączalnymi kartami, okienko może zostać zniszczone automatycznie przez platformę, więc nie należy przechowywać wskaźnika. Aby uzyskać wskaźnik do okienka z kartami, wywołaj `CBasePane::GetParentTabbedPane` metodę.

## <a name="examples"></a>Przykłady

W tym przykładzie tworzymy `CTabbedPane` obiekt. Następnie użyjemy [CBaseTabbedPane:: AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) w celu dołączenia dodatkowych kart.

```cpp
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

Innym sposobem na utworzenie obiektu paska sterowania z kartami jest użycie [CDockablePane:: AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). `AttachToTabWnd`Metoda dynamicznie tworzy obiekt okienka z kartami przy użyciu informacji o klasie środowiska uruchomieniowego ustawionych przez [CDockablePane:: SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc).

W tym przykładzie utworzysz dynamicznie okienko z kartami, dołączysz dwie karty i nie odłączasz drugiej karty.

```cpp
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

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxTabbedPane. h

## <a name="ctabbedpanedetachpane"></a><a name="detachpane"></a> CTabbedPane::D etachPane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

podczas *pBar*<br/>

podczas *bHide*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="ctabbedpaneenabletabautocolor"></a><a name="enabletabautocolor"></a> CTabbedPane::EnableTabAutoColor

Włącza lub wyłącza automatyczne Kolorowanie kart.

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
podczas Wartość TRUE, aby włączyć funkcję autokolorowania kart; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj tej metody statycznej, aby włączyć lub wyłączyć automatyczne Kolorowanie kart we wszystkich okienkach z kartami w aplikacji. Gdy ta funkcja jest włączona, każda karta jest wypełniana własnym kolorem. Możesz znaleźć listę kolorów, które są używane do kolorowania kart, wywołując metodę [CMFCBaseTabCtrl:: GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) .

Możesz określić listę kolorów, które będą używane dla kart przez wywołanie [CTabbedPane:: SetTabAutoColors](#settabautocolors).

Domyślnie ta opcja jest wyłączona.

## <a name="ctabbedpanefloattab"></a><a name="floattab"></a> CTabbedPane::FloatTab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

podczas *pBar*<br/>
podczas *nTabID*<br/>
podczas *dockMethod*<br/>
podczas *bHide*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="ctabbedpanegettabarea"></a><a name="gettabarea"></a> CTabbedPane::GetTabArea

Zwraca rozmiar i położenie obszaru karty w oknie z kartami.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parametry

*rectTabAreaTop*<br/>
określoną Zawiera rozmiar i położenie w obszarze Współrzędne ekranu w górnym obszarze karty.

*rectTabAreaBottom*<br/>
określoną Zawiera rozmiar i położenie w obszarze Współrzędne ekranu w dolnym obszarze karty.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, aby określić sposób dokowania okienka przeciąganego przez użytkownika. Gdy użytkownik przeciągnie okienko nad obszar karty okienka Target, struktura próbuje dodać ją jako nową kartę w okienku Target. W przeciwnym razie próbuje zadokować okienko po stronie okienka Target, co obejmuje utworzenie nowego kontenera okienka z separatorem okienka, który oddziela dwa okienka.

Zastąp tę metodę w `CTabbedPane` klasie pochodnej, aby zmienić to zachowanie.

## <a name="ctabbedpanegettabwnd"></a><a name="gettabwnd"></a> CTabbedPane::GetTabWnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="ctabbedpanehasautohidemode"></a><a name="hasautohidemode"></a> CTabbedPane::HasAutoHideMode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="ctabbedpaneistablocationbottom"></a><a name="istablocationbottom"></a> CTabbedPane::IsTabLocationBottom

Określa, czy karty znajdują się u dołu okna.

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli obszar karty znajduje się u dołu okna z kartami; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="ctabbedpanem_btabsalwaystop"></a><a name="m_btabsalwaystop"></a> CTabbedPane:: m_bTabsAlwaysTop

Domyślna lokalizacja dla kart w aplikacji.

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>Uwagi

Ustaw ten statyczny element członkowski na wartość TRUE, aby wymusić wyświetlanie wszystkich kart w aplikacji w górnej części okienka z kartami.

Należy ustawić tę wartość przed utworzeniem okienka z kartami.

Wartość domyślna to FALSE.

## <a name="ctabbedpanem_ptabwndrtc"></a><a name="m_ptabwndrtc"></a> CTabbedPane:: m_pTabWndRTC

Informacje o klasie środowiska uruchomieniowego dla `CMFCTabCtrl` obiektu pochodnego niestandardowego.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>Uwagi

Ustaw tę statyczną zmienną członkowską na wskaźnik do informacji o klasie środowiska uruchomieniowego `CMFCTabCtrl` obiektu pochodnego, jeśli używasz niestandardowego okna z kartami w okienku z kartami.

## <a name="ctabbedpaneresettabs"></a><a name="resettabs"></a> CTabbedPane::ResetTabs

Resetuje wszystkie okienka z kartami do stanu domyślnego.

```
static void ResetTabs();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby przywrócić domyślny stan wszystkich okienek z kartami. Po wywołaniu ta metoda resetuje rozmiary obramowania i stan Autokolor wszystkich okienek z kartami.

## <a name="ctabbedpanesettabautocolors"></a><a name="settabautocolors"></a> CTabbedPane::SetTabAutoColors

Ustawia listę kolorów niestandardowych, które są używane, gdy funkcja Autocolor jest włączona.

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parametry

*arColors*<br/>
podczas Zawiera tablicę kolorów do ustawienia.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby dostosować listę kolorów, które są używane, gdy funkcja Autocolor jest włączona. Jest to funkcja statyczna i ma wpływ na wszystkie okienka z kartami w aplikacji.

Użyj [CTabbedPane:: EnableTabAutoColor](#enabletabautocolor) , aby włączyć lub wyłączyć funkcję Autocolor.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)<br/>
[Klasa CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)
