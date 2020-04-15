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
ms.openlocfilehash: 17351eaed585ec34117a2ef825964fd51bd0d86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365952"
---
# <a name="ctabbedpane-class"></a>Klasa CTabbedPane

Implementuje funkcjonalność okienka z odłączanymi kartami.

lub więcej szczegółów zobacz kod źródłowy znajdujący się w folderze **VC\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

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
|[CTabbedPane::DetachPane](#detachpane)|(Zastępuje [CBaseTabbedPane::DetachPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|Włącza lub wyłącza automatyczne kolorowanie kart.|
|[CTabbedPane::FloatTab](#floattab)|Unosi okienko, ale tylko wtedy, gdy okienko znajduje się obecnie na odłączanej karcie. (Overrides [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CTabbedPane::GetTabArea](#gettabarea)|Zwraca rozmiar i położenie obszaru karty w oknie z kartami.|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Określa, czy okienko z kartami można przełączyć w tryb autouzusty. (Zastępuje [CBaseTabbedPane::HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|Określa, czy karty znajdują się w dolnej części okna.|
|[CTabbedPane::ResetTabs](#resettabs)|Resetuje wszystkie okienka z kartami do stanu domyślnego.|
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|Ustawia listę kolorów niestandardowych, których można używać po włączeniu funkcji automatycznego koloru.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|Domyślna lokalizacja kart w aplikacji.|
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|Informacje o klasie środowiska `CMFCTabCtrl`uruchomieniowego dla niestandardowego obiektu pochodnego.|

## <a name="remarks"></a>Uwagi

Struktura automatycznie tworzy wystąpienie tej klasy, gdy użytkownik dołącza jedno okienko do innego, wskazując podpis drugiego okienka. Wszystkie okienka z kartami, które są tworzone przez platformę mają identyfikator -1.

Aby określić zwykłe karty zamiast kart w stylu programu Outlook, przekaż styl AFX_CBRS_REGULAR_TABS do metody [CDockablePane::CreateEx.](../../mfc/reference/cdockablepane-class.md#createex)

Jeśli utworzysz okienko z kartami z odłączanymi kartami, okienko może zostać automatycznie zniszczone przez strukturę, więc nie należy przechowywać wskaźnika. Aby uzyskać wskaźnik do okienka z `CBasePane::GetParentTabbedPane` kartami, wywołanie metody.

## <a name="example"></a>Przykład

W tym przykładzie `CTabbedPane` tworzymy obiekt. Następnie używamy [CBaseTabbedPane::AddTab,](../../mfc/reference/cbasetabbedpane-class.md#addtab) aby dołączyć dodatkowe karty.

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

## <a name="example"></a>Przykład

Innym sposobem utworzenia obiektu paska sterowania z kartami jest użycie [CDockablePane::AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). Metoda `AttachToTabWnd` dynamicznie tworzy obiekt okienka z kartami przy użyciu informacji o klasie środowiska uruchomieniowego ustawionych przez [CDockablePane::SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc).

W tym przykładzie dynamicznie tworzymy okienko z kartami, dołączamy dwie karty i nie można odłączyć drugiej karty.

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

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[Cdockablepane](../../mfc/reference/cdockablepane-class.md)

[Cbasetabbedpane](../../mfc/reference/cbasetabbedpane-class.md)

[Ctabbedpane](../../mfc/reference/ctabbedpane-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxTabbedPane.h

## <a name="ctabbedpanedetachpane"></a><a name="detachpane"></a>CTabbedPane::DetachPane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

[w] *pBar*<br/>

[w] *bHide (ur.*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="ctabbedpaneenabletabautocolor"></a><a name="enabletabautocolor"></a>CTabbedPane::EnableTabAutoColor

Włącza lub wyłącza automatyczne kolorowanie kart.

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] PRAWDA, aby włączyć automatyczne kolorowanie kart; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda statyczna służy do włączania lub wyłączania automatycznego kolorowania kart we wszystkich okienkach z kartami w aplikacji. Gdy ta funkcja jest włączona, każda karta jest wypełniona własnym kolorem. Można znaleźć listę kolorów, które są używane do kolorowania kart, wywołując [CMFCBaseTabCtrl::GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) metody.

Można określić listę kolorów, które będą używane dla kart, wywołując [CTabbedPane::SetTabAutoColors](#settabautocolors).

Domyślnie ta opcja jest wyłączona.

## <a name="ctabbedpanefloattab"></a><a name="floattab"></a>CTabbedPane::FloatTab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

[w] *pBar*<br/>
[w] *nTabID (nTabID)*<br/>
[w] *dokMetoda*<br/>
[w] *bHide (ur.*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="ctabbedpanegettabarea"></a><a name="gettabarea"></a>CTabbedPane::GetTabArea

Zwraca rozmiar i położenie obszaru karty w oknie z kartami.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parametry

*reectTabAreaTop*<br/>
[na zewnątrz] Zawiera rozmiar i położenie we współrzędnych ekranu górnego obszaru karty.

*pectTabAreaBottom*<br/>
[na zewnątrz] Zawiera rozmiar i położenie we współrzędnych ekranu dolnego obszaru karty.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, aby określić, jak zadokować okienko, które użytkownik przeciąga. Gdy użytkownik przeciągnie okienko nad obszarem karty okienka docelowego, struktura próbuje dodać go jako nową kartę okienka docelowego. W przeciwnym razie próbuje zadokować okienko z boku okienka docelowego, które polega na utworzeniu nowego kontenera okienka z dzielnikiem okienka, który oddziela dwa okienka.

Zastąpić tę `CTabbedPane`metodę w klasie pochodnej, aby zmienić to zachowanie.

## <a name="ctabbedpanegettabwnd"></a><a name="gettabwnd"></a>CTabbedPane::GetTabWnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="ctabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CTabbedPane::HasAutoHideMode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="ctabbedpaneistablocationbottom"></a><a name="istablocationbottom"></a>CTabbedPane::IsTabLocationBottom

Określa, czy karty znajdują się w dolnej części okna.

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obszar karty znajduje się w dolnej części okna z kartami; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="ctabbedpanem_btabsalwaystop"></a><a name="m_btabsalwaystop"></a>CTabbedPane::m_bTabsAlwaysTop

Domyślna lokalizacja kart w aplikacji.

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>Uwagi

Ustaw ten statyczny element członkowski na TRUE, aby wymusić wszystkie karty w aplikacji, które mają być wyświetlane w górnej części okienka z kartami.

Należy ustawić tę wartość przed utworzeniem okienka z kartami.

Wartością domyślną jest FAŁSZ.

## <a name="ctabbedpanem_ptabwndrtc"></a><a name="m_ptabwndrtc"></a>CTabbedPane::m_pTabWndRTC

Informacje o klasie środowiska `CMFCTabCtrl`uruchomieniowego dla niestandardowego obiektu pochodnego.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>Uwagi

Ustaw tę statyczną zmienną elementów członkowskich na `CMFCTabCtrl`wskaźnik do informacji o klasie środowiska uruchomieniowego obiektu pochodnego, jeśli używasz niestandardowego okna z kartami wewnątrz okienka z kartami.

## <a name="ctabbedpaneresettabs"></a><a name="resettabs"></a>CTabbedPane::ResetTabs

Resetuje wszystkie okienka z kartami do stanu domyślnego.

```
static void ResetTabs();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby przywrócić wszystkie okienka z kartami do stanu domyślnego. Po wywołaniu ta metoda resetuje rozmiary obramowania i stan koloru automatycznego wszystkich okienek z kartami.

## <a name="ctabbedpanesettabautocolors"></a><a name="settabautocolors"></a>CTabbedPane::SetTabAutoColors

Ustawia listę kolorów niestandardowych, które są używane po włączeniu funkcji automatycznego koloru.

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parametry

*arKolory*<br/>
[w] Zawiera tablicę kolorów do skonfigurowania.

### <a name="remarks"></a>Uwagi

Ta metoda służy do dostosowywania listy kolorów, które są używane, gdy funkcja automatycznego koloru jest włączona. Jest to funkcja statyczna i wpływa na wszystkie okienka z kartami w aplikacji.

Użyj [CTabbedPane::EnableTabAutoColor,](#enabletabautocolor) aby włączyć lub wyłączyć funkcję automatycznego koloru.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)<br/>
[Klasa CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)
