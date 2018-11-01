---
title: Klasa CBaseTabbedPane
ms.date: 11/04/2016
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
helpviewer_keywords:
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
ms.openlocfilehash: 51344a8cd0e5671f81e608b74363ed06c9200324
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640898"
---
# <a name="cbasetabbedpane-class"></a>Klasa CBaseTabbedPane

Rozszerza funkcjonalność [klasa CDockablePane](../../mfc/reference/cdockablepane-class.md) aby obsługiwać tworzenie okien z zakładkami.

## <a name="syntax"></a>Składnia

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|Domyślny konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBaseTabbedPane::AddTab](#addtab)|Dodaje nową kartę do okienka z zakładkami.|
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Określa, czy mogą zostać zniszczone pustego okienka z zakładkami.|
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Stosuje ustawienia karty, które są ładowane z rejestru, do okienka z zakładkami.|
|[CBaseTabbedPane::CanFloat](#canfloat)|Określa, czy można przestawić okienka. (Przesłania [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Określa, czy podpisu dla okienka z zakładkami powinny wyświetlać ten sam tekst jako aktywną kartę.|
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Przesłania [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|
|[CBaseTabbedPane::DetachPane](#detachpane)|Konwertuje co najmniej jeden okienek dokowalnych dokumenty z kartami MDI.|
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Włącza lub wyłącza możliwość synchronizowania tekst podpisu przy użyciu tekstu etykiety na karcie aktywne okienko z kartami.|
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Przywraca kolejność tabulacji wewnętrznej do stanu domyślnego.|
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Zwraca okienko, w którym znajduje się na karcie, gdy karta jest identyfikowane za pomocą liczony od zera indeks.|
|||
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Zwraca okienko, która jest identyfikowana przez identyfikator okienka.|
|[CBaseTabbedPane::FloatTab](#floattab)|Liczby zmiennoprzecinkowe okienko, ale tylko wtedy, jeśli zawartość okienka aktualnie znajduje się na karcie odłączane.|
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Zwraca domyślną kolejność kart w okienku.|
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Pobiera wskaźnik do pierwszej karcie wyświetlane.|
|[CBaseTabbedPane::GetMinSize](#getminsize)|Pobiera minimalną dozwoloną rozmiar okienka. (Przesłania [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Zwraca uchwyt do ikony okienka. (Przesłania [CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|
|[CBaseTabbedPane::GetPaneList](#getpanelist)|Zwraca listę okienek, które są zawarte w okienku z kartami.|
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Zwraca prostokąty dla obszarów kartę górny i dolny.|
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Zwraca liczbę karty w oknie kartę.|
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Pobiera bazowego okno karty (opakowana).|
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Zwraca liczbę wyświetlanych kart.|
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Określa, czy okienka z zakładkami mogą być przełączane do trybu Autoukrywanie.|
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Określa, czy okienka z zakładkami jest ukryty, jeśli tylko jedna karta jest wyświetlana.|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Używane wewnętrznie, podczas serializacji.|
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Ponownie oblicza układ informacji dla tego okienka. (Przesłania [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|
|[CBaseTabbedPane::RemovePane](#removepane)|Usuwa okienko z poziomu okienka z zakładkami.|
|`CBaseTabbedPane::SaveSiblingBarIDs`|Używane wewnętrznie, podczas serializacji.|
|`CBaseTabbedPane::Serialize`|(Przesłania [CDockablePane::Serialize](cdockablepane-class.md).)|
|`CBaseTabbedPane::SerializeTabWindow`|Używane wewnętrznie, podczas serializacji.|
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Określa, czy pasek sterowania z kartami zostaną automatycznie usunięte.|
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Włącza lub wyłącza okienko dokowania między wyświetlane i trybie autoukrywania. (Przesłania [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|
|[CBaseTabbedPane::ShowTab](#showtab)|Pokazuje lub ukrywa kartę.|

## <a name="remarks"></a>Uwagi

Ta klasa jest klasą abstrakcyjną i nie można utworzyć wystąpienia. Implementuje usługi, które są wspólne dla wszystkich rodzajów okienka z zakładkami.

Obecnie biblioteki zawiera dwie klasy pochodne okienka z zakładkami: [klasa CTabbedPane](../../mfc/reference/ctabbedpane-class.md) i [klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).

A `CBaseTabbedPane` obiektu otacza wskaźnik do [klasa CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) obiektu. [Klasa CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) staje się oknem podrzędnym okienka z zakładkami.

Aby uzyskać więcej informacji o sposobie tworzenia okienka z zakładkami, zobacz [klasa CDockablePane](../../mfc/reference/cdockablepane-class.md), [klasa CTabbedPane](../../mfc/reference/ctabbedpane-class.md), i [klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxBaseTabbedPane.h

##  <a name="addtab"></a>  CBaseTabbedPane::AddTab

Dodaje nową kartę do okienka z zakładkami.

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>Parametry

*pNewBar*<br/>
[out w] Wskaźnik do okienka, aby dodać. This, wskaźnik może stać się nieprawidłowe po wywołaniu tej metody. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.

*bVisible*<br/>
[in] Wartość TRUE, aby uwidocznić karcie; w przeciwnym razie wartość FALSE.

*bSetActive*<br/>
[in] Wartość TRUE, aby wprowadzić na karcie aktywną kartę; w przeciwnym razie wartość FALSE.

*bDetachable*<br/>
[in] Wartość TRUE, aby wprowadzić na karcie odłączane; w przeciwnym razie wartość FALSE.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli okienko został pomyślnie dodany jako karty i nie została zniszczona w procesie. Wartość FALSE, jeśli okienko dodawany jest obiekt typu `CBaseTabbedPane`. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby dodać okienka jako nowa karta w okienku z kartami. Jeśli *pNewBar* wskazuje na obiekt typu `CBaseTabbedPane`, wszystkie jego kartach są kopiowane do okienka z zakładkami i następnie *pNewBar* zostanie zniszczony. W efekcie *pNewBar* staje się nieprawidłowy wskaźnik i nie powinna być używana.

##  <a name="allowdestroyemptytabbedpane"></a>  CBaseTabbedPane::AllowDestroyEmptyTabbedPane

Określa, czy mogą zostać zniszczone pustego okienka z zakładkami.

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pustego może zostać zniszczone okienka z zakładkami; w przeciwnym razie wartość FALSE. Domyślna implementacja zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Pusty okienka z zakładkami nie może zostać zniszczone, struktura ukrywa okienko zamiast tego.

##  <a name="applyrestoredtabinfo"></a>  CBaseTabbedPane::ApplyRestoredTabInfo

Ładuje ustawienia karty z rejestru, a następnie zastosuje je do okienka z zakładkami.

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>Parametry

*bUseTabIndexes*<br/>
[in] Ten parametr jest używana wewnętrznie przez platformę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy się ponownie ładuje informacje o stanie dokowania z rejestru. Metoda uzyskuje informacje o kolejności tabulacji i nazwy kart dla okienka z zakładkami.

##  <a name="canfloat"></a>  CBaseTabbedPane::CanFloat

Określa, czy można przestawić okienka z zakładkami.

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli można przestawić okienka; w przeciwnym razie wartość FALSE.

##  <a name="cansetcaptiontexttotabname"></a>  CBaseTabbedPane::CanSetCaptionTextToTabName

Określa, czy podpisu dla okienka z zakładkami powinny wyświetlać ten sam tekst jako aktywną kartę.

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli tekst podpisu okienka z zakładkami w tekście aktywną kartę; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Metoda jest używana do określają, czy tekst wyświetlany na duplikaty podpis okienka z zakładkami etykieta karty aktywne. Można włączyć lub wyłączyć tę funkcję, wywołując [CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).

##  <a name="converttotabbeddocument"></a>  CBaseTabbedPane::ConvertToTabbedDocument

Konwertuje co najmniej jeden okienek dokowalnych dokumenty z kartami MDI.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bActiveTabOnly*<br/>
[in] Podczas konwersji okienka z zakładkami, określ wartość PRAWDA, aby przekonwertować tylko aktywną kartę. Określ wartość FALSE, aby przekonwertować wszystkie karty w okienku.

##  <a name="detachpane"></a>  CBaseTabbedPane::DetachPane

Odłącza okienko z poziomu okienka z zakładkami.

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Wskaźnik do okienka, aby odłączyć.

*bHide*<br/>
[in] Parametr logiczny, który określa, czy strukturze ukrywa okienko po jest odłączony od.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli w ramach pomyślnie odłącza okienko; FAŁSZ Jeśli *pBar* ma wartość NULL lub odwołuje się do okienka, który nie znajduje się w okienku z kartami.

### <a name="remarks"></a>Uwagi

Struktura liczby zmiennoprzecinkowe okienka odłączony, jeśli jest to możliwe. Aby uzyskać więcej informacji, zobacz [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).

##  <a name="enablesetcaptiontexttotabname"></a>  CBaseTabbedPane::EnableSetCaptionTextToTabName

Włącza lub wyłącza możliwość synchronizowania tekst podpisu przy użyciu tekstu etykiety na karcie aktywne okienko z kartami.

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Wartość TRUE, aby zsynchronizować podpis okienka z zakładkami z aktywną kartę podpis; w przeciwnym razie wartość FALSE.

##  <a name="filldefaulttabsorderarray"></a>  CBaseTabbedPane::FillDefaultTabsOrderArray

Przywraca kolejność tabulacji wewnętrznej do stanu domyślnego.

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, gdy w ramach przywraca paska Outlook do stanu początkowego.

##  <a name="findpanebyid"></a>  CBaseTabbedPane::FindPaneByID

Zwraca okienko identyfikowane przez identyfikator okienka.

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>Parametry

*uBarID*<br/>
[in] Określa identyfikator okienka, aby znaleźć.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okienka, jeśli znaleziono; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ta metoda porównuje wszystkie karty w okienku i zwraca jeden z Identyfikatorem określony przez *uBarID* parametru.

##  <a name="findbarbytabnumber"></a>  CBaseTabbedPane::FindBarByTabNumber

Zwraca okienko, w którym znajduje się na karcie.

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>Parametry

*nTabNum*<br/>
[in] Określa liczony od zera indeks karty do pobrania.

*bGetWrappedBar*<br/>
[in] Wartość TRUE, aby zwrócić podstawowej (opakowana) okno okienka zamiast okienka. w przeciwnym razie wartość FALSE. Dotyczy to tylko okienka pochodną [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).

### <a name="return-value"></a>Wartość zwracana

Jeśli okienko zostanie znaleziony, zwracana jest prawidłowy wskaźnik do okienka wyszukane; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę w celu pobrania okienka znajdującej się na karcie określony przez *nTabNum* parametru.

##  <a name="floattab"></a>  CBaseTabbedPane::FloatTab

Liczby zmiennoprzecinkowe okienko, ale tylko wtedy, jeśli zawartość okienka aktualnie znajduje się na karcie odłączane.

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[out w] Wskaźnik do okienka na typ zmiennoprzecinkowy.

*nTabID*<br/>
[in] Określa liczony od zera indeks karty na typ zmiennoprzecinkowy.

*dockMethod*<br/>
[in] Określa metodę używaną do dokowanie panelu. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.

*bHide*<br/>
[in] Wartość TRUE, aby ukryć okienko przed liczb zmiennoprzecinkowych; w przeciwnym razie wartość FALSE.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zawartość okienka przestawione; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, float okienka w którym aktualnie znajduje się na karcie odłączane.

Jeśli chcesz odłączyć okienko programowo, należy określić DM_SHOW dla *dockMethod* parametru. Jeśli chcesz float okienka, w tym samym miejscu, gdzie przestawione wcześniej, należy określić DM_DBL_CLICK jako *dockMethod* parametru.

##  <a name="getdefaulttabsorder"></a>  CBaseTabbedPane::GetDefaultTabsOrder

Zwraca domyślną kolejność kart w okienku.

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>Wartość zwracana

A `CArray` obiekt, który określa domyślną kolejność kart w okienku.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy pasek programu Outlook jest resetowany do stanu początkowego.

##  <a name="getfirstvisibletab"></a>  CBaseTabbedPane::GetFirstVisibleTab

Pobiera wskaźnik do pierwszej karcie wyświetlane.

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>Parametry

*iTabNum*<br/>
[in] Odwołanie do wartości całkowitej. Ta metoda zapisuje liczony od zera indeks pierwszej karcie wyświetlany ten parametr lub wartość -1 Jeśli wyświetlane nie znajduje się karta.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, wskaźnik do pierwszej karcie wyświetlane; w przeciwnym razie wartość NULL.

##  <a name="getminsize"></a>  CBaseTabbedPane::GetMinSize

Pobiera minimalną dozwoloną rozmiar okienka.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
[out] A `CSize` obiekt, który zostanie wypełniony kolorem minimalny dozwolony rozmiar.

### <a name="remarks"></a>Uwagi

Jeśli aktywne jest spójne obsługi rozmiary okienka minimalną ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), *rozmiar* jest wypełniany minimalny dozwolony rozmiar dla aktywnej karty. W przeciwnym razie *rozmiar* jest wypełniany wartość zwracaną przez [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

##  <a name="getpaneicon"></a>  CBaseTabbedPane::GetPaneIcon

Pobiera minimalną dozwoloną rozmiar okienka.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
[out] A `CSize` obiekt, który zostanie wypełniony kolorem minimalny dozwolony rozmiar.

### <a name="remarks"></a>Uwagi

Jeśli aktywne jest spójne obsługi rozmiary okienka minimalną ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), *rozmiar* jest wypełniany minimalny dozwolony rozmiar dla aktywnej karty. W przeciwnym razie *rozmiar* jest wypełniany wartość zwracaną przez [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

##  <a name="getpanelist"></a>  CBaseTabbedPane::GetPaneList

Zwraca listę okienek, które są zawarte w okienku z kartami.

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>Parametry

*dzieł*<br/>
[out] A `CObList` , jest wypełniany okienek, które są zawarte w okienku z kartami.

*pRTCFilter*<br/>
[in] Jeśli nie ma wartość NULL, tego zwracana lista zawiera tylko okienek, które są klasy określonego środowiska uruchomieniowego.

##  <a name="gettabarea"></a>  CBaseTabbedPane::GetTabArea

Zwraca prostokąty dla obszarów kartę górny i dolny.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>Parametry

*rectTabAreaTop*<br/>
[out] Odbiera współrzędne ekranu obszaru górnej karty.

*rectTabAreaBottom*<br/>
[out] Odbiera współrzędne ekranu dolny obszar karty.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę pozwala ustalić prostokąty, we współrzędnych ekranu, obszarów górny i dolny kartę.

##  <a name="gettabsnum"></a>  CBaseTabbedPane::GetTabsNum

Zwraca liczbę karty w oknie kartę.

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba kart w okienku z kartami.

##  <a name="getunderlyingwindow"></a>  CBaseTabbedPane::GetUnderlyingWindow

Pobiera bazowego okno karty (opakowana).

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do podstawowego okna karty.

##  <a name="getvisibletabsnum"></a>  CBaseTabbedPane::GetVisibleTabsNum

Zwraca liczbę kart widocznych.

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba widocznych kart, które będzie większa lub równa zero.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić liczbę kart widocznych w okienku z kartami.

##  <a name="hasautohidemode"></a>  CBaseTabbedPane::HasAutoHideMode

Określa, czy okienka z zakładkami mogą być przełączane do trybu Autoukrywanie.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zawartość okienka mogą być przełączane do trybu autoukrywania; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Po wyłączeniu trybu autoukrywania ma przycisku numer pin jest wyświetlany na podpis okienka z zakładkami.

##  <a name="ishidesingletab"></a>  CBaseTabbedPane::IsHideSingleTab

Określa, czy okienka z zakładkami jest ukryty, jeśli tylko jedna karta jest wyświetlana.

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli okno karta nie jest wyświetlany, gdy istnieje tylko jedna karta widoczne; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Jeśli okienko nie jest wyświetlany, ponieważ tylko jedna karta jest otwarty, możesz wywołać tę metodę w celu określenia, czy okienko z kartami działa poprawnie.

##  <a name="removepane"></a>  CBaseTabbedPane::RemovePane

Usuwa okienko z poziomu okienka z zakładkami.

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[out w] Wskaźnik do okienka, aby usunąć z okienka z zakładkami.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli okienka został pomyślnie usunięty z poziomu okienka z zakładkami i okienka z zakładkami jest nadal ważny. Wartość FALSE, jeśli okienko ostatnie została usunięta z poziomu okienka z zakładkami, a ma zostać zniszczone okienka z zakładkami. Jeśli wartość zwracana jest wartość FALSE, nie należy używać okienka z zakładkami więcej.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody można usunąć okienka określony przez *pBar* parametrów z okienka z zakładkami.

##  <a name="setautodestroy"></a>  CBaseTabbedPane::SetAutoDestroy

Określa, czy pasek sterowania z kartami zostaną automatycznie usunięte.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroy*<br/>
[in] Wartość TRUE, jeśli okienka z zakładkami został utworzony dynamicznie i nie możesz kontrolować jego trwania. w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ustaw automatyczne zniszczyć tryb na wartość TRUE, jeśli dynamicznie utworzyć okienka z zakładkami, a nie sterowanej cały okres ich istnienia. Jeśli zniszczyć automatyczny tryb ma wartość PRAWDA, okienka z zakładkami jest niszczony automatycznie przez platformę.

##  <a name="showtab"></a>  CBaseTabbedPane::ShowTab

Pokazuje lub ukrywa kartę.

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Wskaźnik do okienka, aby pokazać lub ukryć.

*bShow*<br/>
[in] Wartość TRUE, aby wyświetlić okienko; Wartość FALSE, aby ukryć okienko.

*bDelay*<br/>
[in] Wartość TRUE, aby opóźnić dostosowania układu kartę; w przeciwnym razie wartość FALSE.

*bActivate*<br/>
[in] Wartość TRUE, aby wprowadzić na karcie aktywną kartę; w przeciwnym razie wartość FALSE.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli karta został pokazane lub ukryte pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Po wywołaniu tej metody, okienko jest pokazane lub ukryte, w zależności od wartości *bShow* parametru. Ukrywanie karty jest ostatnią kartę widoczne w oknie podstawowej karty, zostanie ukryte okienka z zakładkami. Jeśli karta jest pokazywać, gdy wcześniej były widoczne żadne karty, wyświetlany jest okienka z zakładkami.

##  <a name="recalclayout"></a>  CBaseTabbedPane::RecalcLayout

Ponownie oblicza układ informacji dla tego okienka.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Uwagi

Jeśli okienko jest Opływanie, ta metoda powiadamia platformę, by zmienić rozmiar okienka, aby bieżący rozmiar mini ramki.

Jeśli panel jest zadokowany, ta metoda nie działa.

##  <a name="setautohidemode"></a>  CBaseTabbedPane::SetAutoHideMode

Ustawia tryb automatyczne ukrywanie okienka z odłączanymi okienka z zakładkami.

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Parametry

*bMode*<br/>
[in] Wartość TRUE, aby włączyć tryb autoukrywania; Wartość FALSE, aby włączyć do trybu normalnego dokowania.

*dwAlignment*<br/>
[in] Określa wyrównanie okienko automatycznego ukrywania, w którym ma zostać utworzony. Aby uzyskać listę możliwych wartości, zobacz [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).

*pCurrAutoHideBar*<br/>
[out w] Wskaźnik do bieżącego automatyczne ukrywanie paska narzędzi. Może mieć wartości NULL.

*bUseTimer*<br/>
[in] Określa, czy gdy użytkownik zmienia okienka tryb automatycznego ukrywania za pomocą automatyczne ukrywanie efektu lub ukrywanie okienka natychmiast.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do paska narzędzi automatycznego ukrywania, który jest tworzony podczas przełączania trybie autoukrywania lub wartość NULL, jeśli brak paska narzędzi jest tworzony.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy użytkownik wybierze przycisk numeru pin, aby przełączyć okienka z zakładkami w trybie autoukrywania lub do trybu normalnego dokowania.

Autoukrywanie tryb jest ustawiony dla każdego odłączane okienka, w okienku z kartami. Okienek, które są niemożliwe do odłączenia są ignorowane. Aby uzyskać więcej informacji, zobacz [CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).

Wywołaj tę metodę, aby włączyć tryb automatyczne ukrywanie okienka z zakładkami programowo. Musi być zadokowane okienka w oknie głównym ramki ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) musi zwracać ważnym wskaźnik do [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)
