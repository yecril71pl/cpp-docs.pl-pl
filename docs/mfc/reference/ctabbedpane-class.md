---
title: Klasa CTabbedPane | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a73d5bb3ef67469ad1cc12b2a2c2757cf1ce137
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712840"
---
# <a name="ctabbedpane-class"></a>Klasa CTabbedPane

Implementuje funkcje okienka z odłączanymi zakładkami.

lub więcej szczegółów, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

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
|[CTabbedPane::FloatTab](#floattab)|Liczby zmiennoprzecinkowe okienko, ale tylko wtedy, jeśli zawartość okienka aktualnie znajduje się na karcie odłączane. (Przesłania [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CTabbedPane::GetTabArea](#gettabarea)|Zwraca rozmiar i położenie wartości obszar karty w oknie z kartami.|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Określa, czy okienka z zakładkami mogą być przełączane do trybu Autoukrywanie. (Przesłania [CBaseTabbedPane::HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|Określa, czy kartach znajdują się w dolnej części okna.|
|[CTabbedPane::ResetTabs](#resettabs)|Resetuje wszystkie okienka z zakładkami do stanu domyślnego.|
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|Ustawia listę kolorów niestandardowych, których można użyć, gdy jest włączona funkcja automatycznego kolor.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|Domyślna lokalizacja dla kart w aplikacji.|
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|Informacje o klasie czasu wykonywania niestandardowych `CMFCTabCtrl`-pochodnych obiektu.|

## <a name="remarks"></a>Uwagi

Struktura automatycznie tworzy wystąpienie tej klasy, po użytkownik dołącza jedno okienko do innego wskazując podpis okienka drugiego. Wszystkie z kartami okienek, które są tworzone przez platformę mieć identyfikator-1.

Aby określić zwykłe karty zamiast tabulatorów stylu dla programu Outlook, należy przekazać do stylu AFX_CBRS_REGULAR_TABS [CDockablePane::CreateEx](../../mfc/reference/cdockablepane-class.md#createex) metody.

Jeśli tworzysz kartach okienka z odłączanymi zakładkami okienka może zostać zniszczone automatycznie przez platformę, więc nie należy przechowywać wskaźnika. Aby uzyskać wskaźnik do okienka z zakładkami, należy wywołać `CBasePane::GetParentTabbedPane` metody.

## <a name="example"></a>Przykład

W tym przykładzie tworzymy `CTabbedPane` obiektu. Następnie używamy [CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) można dołączyć dodatkowe karty.

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

Innym sposobem na utworzenie obiektu pasek sterowania z kartami jest użycie [CDockablePane::AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). `AttachToTabWnd` Metoda dynamicznie tworzy obiekt okienka z zakładkami, przy użyciu informacji o klasie czasu wykonywania ustawiony przez [CDockablePane::SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc).

W tym przykładzie tworzymy dynamicznie okienka z zakładkami Dołącz dwie karty i wybierz drugiej karcie niemożliwe do odłączenia.

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

**Nagłówek:** afxTabbedPane.h

##  <a name="detachpane"></a>  CTabbedPane::DetachPane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

[in] *pBar*  

[in] *bHide*  

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="enabletabautocolor"></a>  CTabbedPane::EnableTabAutoColor

Włącza lub wyłącza automatyczne kolorowanie kart.

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Wartość TRUE, aby włączyć automatyczne kolorowanie kart; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Aby włączyć lub wyłączyć automatyczne kolorowanie kart w wszystkich kartach okienka w aplikacji, należy użyć tej metody statycznej. Gdy ta funkcja jest włączona, każda karta jest wypełniane przez swój własny kolorów. Można znaleźć listę kolorów, które są używane do koloru na kartach, wywołując [CMFCBaseTabCtrl::GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) metody.

Można określić listę kolorów, które będą używane dla karty, wywołując [CTabbedPane::SetTabAutoColors](#settabautocolors).

Domyślnie ta opcja jest wyłączona.

##  <a name="floattab"></a>  CTabbedPane::FloatTab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] [in] *nTabID*  
*dockMethod*<br/>
[in] [in] *bHide*  

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="gettabarea"></a>  CTabbedPane::GetTabArea

Zwraca rozmiar i położenie wartości obszar karty w oknie z kartami.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parametry

*rectTabAreaTop*<br/>
[out] Zawiera rozmiar i położenie we współrzędnych ekranu obszaru górnej karty.

*rectTabAreaBottom*<br/>
[out] Zawiera rozmiar i położenie we współrzędnych ekranu wartości obszar karty w dolnej.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, aby określić sposób zadokować okienko, w którym użytkownik przeciąga. Gdy użytkownik przeciągnie okienko za pośrednictwem obszaru karty w okienku docelowego, struktura próbuje dodać je jako nową kartę w okienku docelowego. W przeciwnym razie próbuje zadokować okienka boku okienko docelowych, które obejmuje utworzenie nowego kontenera okienko z Dzielnik rozdziela dwa okienka.

Należy przesłonić tę metodę w `CTabbedPane`-klasy, aby zmienić to zachowanie.

##  <a name="gettabwnd"></a>  CTabbedPane::GetTabWnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="hasautohidemode"></a>  CTabbedPane::HasAutoHideMode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="istablocationbottom"></a>  CTabbedPane::IsTabLocationBottom

Określa, czy kartach znajdują się w dolnej części okna.

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli wartości obszar karty znajduje się w dolnej części okna z kartami; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="m_btabsalwaystop"></a>  CTabbedPane::m_bTabsAlwaysTop

Domyślna lokalizacja dla kart w aplikacji.

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>Uwagi

Ustaw ten statyczny element członkowski na wartość true, wymuś wszystkie karty w aplikacji, które mają być wyświetlane w górnej części okienka z zakładkami.

Przed okno zakładki, która została utworzona, należy ustawić tę wartość.

Wartość domyślna to FALSE.

##  <a name="m_ptabwndrtc"></a>  CTabbedPane::m_pTabWndRTC
Informacje o klasie czasu wykonywania niestandardowych `CMFCTabCtrl`-pochodnych obiektu.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>Uwagi

Ustaw wartość tej zmiennej statycznej składowej na wskaźnik do informacji o klasie czasu wykonywania o `CMFCTabCtrl`-pochodnych obiektu, jeśli używasz niestandardowego okna z kartami wewnątrz okienka z zakładkami.

##  <a name="resettabs"></a>  CTabbedPane::ResetTabs

Resetuje wszystkie okienka z zakładkami do stanu domyślnego.

```
static void ResetTabs();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby przywrócić wszystkie okienka z zakładkami do stanu domyślnego. Gdy zostanie wywołana, ta metoda powoduje zresetowanie rozmiary obramowania i automatyczne kolor stanu wszystkich okienek z kartami.

##  <a name="settabautocolors"></a>  CTabbedPane::SetTabAutoColors

Ustawia listę kolorów niestandardowych, które są używane, gdy jest włączona funkcja automatycznego kolorów.

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parametry

*arColors*<br/>
[in] Zawiera tablicę kolorów do ustawienia.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia dostosowywanie listy kolorów, które są używane, gdy jest włączona funkcja automatycznego kolorów. To jest funkcję statyczną i wpływa na wszystkich kartach okienka w aplikacji.

Użyj [CTabbedPane::EnableTabAutoColor](#enabletabautocolor) Aby włączyć lub wyłączyć funkcję automatycznego kolor.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)  
[Klasy](../../mfc/reference/mfc-classes.md)  
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)  
[Klasa CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
[Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)  
