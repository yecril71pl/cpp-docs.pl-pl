---
title: CBaseTabbedPane Class
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
ms.openlocfilehash: d7ffaa7274a8ed12944cdbc5dcbbdcb8fd3fd2b9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883677"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane Class

Rozszerza funkcjonalność [klasy CDockablePane](../../mfc/reference/cdockablepane-class.md) w celu obsługi tworzenia okien z kartami.

## <a name="syntax"></a>Składnia

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|Konstruktor domyślny.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBaseTabbedPane::AddTab](#addtab)|Dodaje nową kartę do okienka z kartami.|
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Określa, czy puste okienko z kartami może zostać zniszczone.|
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Stosuje ustawienia karty, które są ładowane z rejestru, do okienka z kartami.|
|[CBaseTabbedPane:: onfloat](#canfloat)|Określa, czy okienko może być zmiennoprzecinkowe. (Przesłania [CBasePane:: onfloat](../../mfc/reference/cbasepane-class.md#canfloat)).|
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Określa, czy podpis okienka z kartami powinien wyświetlać ten sam tekst co karta aktywna.|
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Przesłania [CDockablePane:: ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|
|[CBaseTabbedPane::D etachPane](#detachpane)|Konwertuje co najmniej jedno okienko było dokować na dokumenty z kartami MDI.|
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Włącza lub wyłącza możliwość okienka z kartami do synchronizowania tekstu podpisu z tekstem etykiety na aktywnej karcie.|
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Przywraca stan domyślny kolejności tabulacji.|
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Zwraca okienko, które znajduje się na karcie, gdy karta jest identyfikowana przez indeks karty liczony od zera.|
|||
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Zwraca okienko identyfikowane przez identyfikator okienka.|
|[CBaseTabbedPane::FloatTab](#floattab)|Przepływa z okienka, ale tylko wtedy, gdy okienko znajduje się obecnie na karcie odłączalnej.|
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Zwraca domyślną kolejność kart w okienku.|
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Pobiera wskaźnik do pierwszej wyświetlanej karty.|
|[CBaseTabbedPane::GetMinSize](#getminsize)|Pobiera minimalny dozwolony rozmiar okienka. (Przesłania [CPane:: GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Zwraca dojście do ikony okienka. (Przesłania [CBasePane:: GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|
|[CBaseTabbedPane:: getpanelname](#getpanelist)|Zwraca listę okienek, które znajdują się w okienku z kartami.|
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Zwraca prostokąty związane z górnymi i dolnymi obszarami tabulacji.|
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Zwraca liczbę kart w oknie karty.|
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Pobiera bazowe (opakowane) okno kart.|
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Zwraca liczbę wyświetlanych kart.|
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Określa, czy okienko z kartami może być przełączane do trybu autoukrywania.|
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Określa, czy okienko z kartami jest ukryte, gdy zostanie wyświetlona tylko jedna karta.|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Używane wewnętrznie podczas serializacji.|
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Ponownie oblicza informacje o układzie dla okienka. (Przesłania [CPane:: RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|
|[CBaseTabbedPane::RemovePane](#removepane)|Usuwa okienko z okienka z kartami.|
|`CBaseTabbedPane::SaveSiblingBarIDs`|Używane wewnętrznie podczas serializacji.|
|`CBaseTabbedPane::Serialize`|(Przesłania [CDockablePane:: serializować](cdockablepane-class.md)).|
|`CBaseTabbedPane::SerializeTabWindow`|Używane wewnętrznie podczas serializacji.|
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Określa, czy pasek sterowania z kartami zostanie zniszczony automatycznie.|
|[CBaseTabbedPane:: autoukrywaniemode](#setautohidemode)|Włącza lub wyłącza okienko dokowania między wyświetlonym i autoukrywaniem trybem. (Przesłania [CDockablePane:: autoukrywaniemode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|
|[CBaseTabbedPane:: ShowTab](#showtab)|Pokazuje lub ukrywa kartę.|

## <a name="remarks"></a>Uwagi

Ta klasa jest klasą abstrakcyjną i nie można utworzyć jej wystąpienia. Implementuje ona usługi, które są wspólne dla wszystkich rodzajów okienek z kartami.

Obecnie Biblioteka zawiera dwie pochodne klasy okienka z kartami: [Klasa CTabbedPane](../../mfc/reference/ctabbedpane-class.md) i [Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).

Obiekt `CBaseTabbedPane` otacza wskaźnik do obiektu [klasy CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) . [Klasa CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) zostaje następnie oknem podrzędnym okienka z kartami.

Aby uzyskać więcej informacji na temat tworzenia okienek z kartami, zobacz Klasa [CDockablePane](../../mfc/reference/cdockablepane-class.md), [Klasa CTabbedPane](../../mfc/reference/ctabbedpane-class.md)i [Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxBaseTabbedPane. h

##  <a name="addtab"></a>CBaseTabbedPane::AddTab

Dodaje nową kartę do okienka z kartami.

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>Parametry

*pNewBar*<br/>
[in. out] Wskaźnik do okienka do dodania. Ten wskaźnik może stać się nieprawidłowy po wywołaniu tej metody. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.

*bVisible*<br/>
podczas PRAWDA, aby karta była widoczna; w przeciwnym razie FALSE.

*bSetActive*<br/>
podczas PRAWDA, aby karta była aktywna; w przeciwnym razie FALSE.

*bDetachable*<br/>
podczas PRAWDA, aby można było odłączać kartę; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli okienko zostało pomyślnie dodane jako karta i nie zostało zniszczone w procesie. FAŁSZ, jeśli dodawane okienko jest obiektem typu `CBaseTabbedPane`. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby dodać okienko jako nową kartę w okienku z kartami. Jeśli *pNewBar* wskazuje obiekt typu `CBaseTabbedPane`, wszystkie jego karty są kopiowane do okienka z kartami, a następnie *pNewBar* jest niszczona. W rezultacie *pNewBar* jest nieprawidłowym wskaźnikiem i nie należy go używać.

##  <a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane

Określa, czy puste okienko z kartami może zostać zniszczone.

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli puste okienko z kartami może zostać zniszczone; w przeciwnym razie FALSE. Domyślna implementacja zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Jeśli puste okienko z kartami nie może zostać zniszczone, struktura spowoduje ukrycie okienka.

##  <a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo

Ładuje ustawienia karty z rejestru i stosuje je do okienka z kartami.

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>Parametry

*bUseTabIndexes*<br/>
podczas Ten parametr jest używany wewnętrznie przez strukturę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy ponownie ładuje informacje o stanie dokowania z rejestru. Metoda uzyskuje informacje o kolejności tabulacji i nazwach kart dla okienka z kartami.

##  <a name="canfloat"></a>CBaseTabbedPane:: onfloat

Określa, czy okienko z kartami może być zmiennoprzecinkowe.

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okienko może być zmiennoprzecinkowe; w przeciwnym razie FALSE.

##  <a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName

Określa, czy podpis okienka z kartami powinien wyświetlać ten sam tekst co karta aktywna.

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli tekst nagłówka okienka z kartami jest ustawiony na tekst aktywnej karty; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Metoda jest używana do określenia, czy tekst wyświetlany w okienku z kartami jest duplikatem etykiety aktywnej karty. Tę funkcję można włączyć lub wyłączyć, wywołując [CBaseTabbedPane:: EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).

##  <a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument

Konwertuje co najmniej jedno okienko było dokować na dokumenty z kartami MDI.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bActiveTabOnly*<br/>
podczas Podczas konwertowania okienka z kartami należy określić wartość TRUE, aby przekonwertować tylko aktywną kartę. Określ wartość FALSE, aby przekonwertować wszystkie karty w okienku.

##  <a name="detachpane"></a>CBaseTabbedPane::D etachPane

Odłącza okienko od okienka z kartami.

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
podczas Wskaźnik do okienka, aby odłączyć.

*bHide*<br/>
podczas Wartość logiczna określająca, czy struktura ukrywa okienko po odłączeniu.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli struktura pomyślnie odłącza okienko; Wartość FALSE, jeśli *pBar* ma wartość null lub odwołuje się do okienka, które nie znajduje się w okienku z kartami.

### <a name="remarks"></a>Uwagi

W miarę możliwości struktura przepływa z okienka. Aby uzyskać więcej informacji, zobacz [CBasePane:: onfloat](../../mfc/reference/cbasepane-class.md#canfloat).

##  <a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName

Włącza lub wyłącza możliwość okienka z kartami do synchronizowania tekstu podpisu z tekstem etykiety na aktywnej karcie.

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
podczas Wartość TRUE, aby zsynchronizować podpis okienka z kartami z aktywną etykietą karty; w przeciwnym razie FALSE.

##  <a name="filldefaulttabsorderarray"></a>CBaseTabbedPane::FillDefaultTabsOrderArray

Przywraca stan domyślny kolejności tabulacji.

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, gdy struktura przywraca stan początkowy paska programu Outlook.

##  <a name="findpanebyid"></a>CBaseTabbedPane::FindPaneByID

Zwraca okienko identyfikowane przez identyfikator okienka.

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>Parametry

*uBarID*<br/>
podczas Określa identyfikator okienka do znalezienia.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okienka, jeśli został odnaleziony; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ta metoda porównuje wszystkie karty w okienku i zwraca jeden z IDENTYFIKATORem określonym przez parametr *uBarID* .

##  <a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber

Zwraca okienko, które znajduje się na karcie.

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>Parametry

*nTabNum*<br/>
podczas Określa indeks (liczony od zera) karty do pobrania.

*bGetWrappedBar*<br/>
podczas Wartość TRUE powoduje zwrócenie okna bazowego (opakowanego) okienka zamiast samego okienka; w przeciwnym razie FALSE. Dotyczy to tylko okienek pochodnych z [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).

### <a name="return-value"></a>Wartość zwracana

Jeśli okienko zostanie znalezione, zwracany jest prawidłowy wskaźnik do przeszukiwanego okienka; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać okienko znajdujące się na karcie określonej przez parametr *nTabNum* .

##  <a name="floattab"></a>CBaseTabbedPane::FloatTab

Przepływa z okienka, ale tylko wtedy, gdy okienko znajduje się obecnie na karcie odłączalnej.

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in. out] Wskaźnik do okienka, które ma być zmiennoprzecinkowe.

*nTabID*<br/>
podczas Określa indeks (liczony od zera) tabulacji.

*dockMethod*<br/>
podczas Określa metodę, która ma być używana do przesunięcia okienka. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.

*bHide*<br/>
podczas Wartość TRUE powoduje ukrycie okienka przed liczbą zmiennoprzecinkową; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli okienko jest przepływane; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby wystawić okienko znajdujące się obecnie w odłączalnej karcie.

Aby programowo odłączyć okienko, określ DM_SHOW parametru *dockMethod* . Jeśli chcesz przestawić okienko w tym samym miejscu, w którym jest ono wcześniej przepływane, określ DM_DBL_CLICK jako parametr *dockMethod* .

##  <a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder

Zwraca domyślną kolejność kart w okienku.

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `CArray`, który określa domyślną kolejność kart w okienku.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy pasek programu Outlook zostanie zresetowany do stanu początkowego.

##  <a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab

Pobiera wskaźnik do pierwszej wyświetlanej karty.

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>Parametry

*iTabNum*<br/>
podczas Odwołanie do liczby całkowitej. Ta metoda zapisuje indeks (liczony od zera) pierwszej wyświetlanej karty do tego parametru lub-1, jeśli nie zostanie znaleziona żadna wyświetlana karta.

### <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, wskaźnik do pierwszej wyświetlonej karty; w przeciwnym razie wartość NULL.

##  <a name="getminsize"></a>CBaseTabbedPane::GetMinSize

Pobiera minimalny dozwolony rozmiar okienka.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
określoną Obiekt `CSize`, który jest wypełniony minimalnym dozwolonym rozmiarem.

### <a name="remarks"></a>Uwagi

Jeśli aktywna jest spójna obsługa minimalnych rozmiarów okien ( [CPane:: m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), *rozmiar* jest wypełniony minimalnym dozwolonym rozmiarem karty aktywne. w przeciwnym razie *rozmiar* jest wypełniony wartością zwracaną [CPane:: GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

##  <a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon

Pobiera minimalny dozwolony rozmiar okienka.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
określoną Obiekt `CSize`, który jest wypełniony minimalnym dozwolonym rozmiarem.

### <a name="remarks"></a>Uwagi

Jeśli aktywna jest spójna obsługa minimalnych rozmiarów okien ( [CPane:: m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), *rozmiar* jest wypełniony minimalnym dozwolonym rozmiarem karty aktywne. w przeciwnym razie *rozmiar* jest wypełniony wartością zwracaną [CPane:: GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

##  <a name="getpanelist"></a>CBaseTabbedPane:: getpanelname

Zwraca listę okienek, które znajdują się w okienku z kartami.

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>Parametry

*dzieł*<br/>
określoną `CObList` wypełniane okienkami, które znajdują się w okienku z kartami.

*pRTCFilter*<br/>
podczas Jeśli wartość nie jest równa NULL, zwracana lista zawiera tylko okienka należące do określonej klasy środowiska uruchomieniowego.

##  <a name="gettabarea"></a>CBaseTabbedPane::GetTabArea

Zwraca prostokąty związane z górnymi i dolnymi obszarami tabulacji.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>Parametry

*rectTabAreaTop*<br/>
określoną Odbiera Współrzędne ekranu górnego obszaru kart.

*rectTabAreaBottom*<br/>
określoną Odbiera Współrzędne ekranu dolnego obszaru kart.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić prostokąty ograniczające w obszarze Współrzędne ekranu dla górnego i dolnego obszaru kart.

##  <a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum

Zwraca liczbę kart w oknie karty.

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba kart w okienku z kartami.

##  <a name="getunderlyingwindow"></a>CBaseTabbedPane::GetUnderlyingWindow

Pobiera bazowe (opakowane) okno kart.

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna bazowej karty.

##  <a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum

Zwraca liczbę widocznych kart.

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba widocznych kart, które będą większe lub równe zeru.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić liczbę widocznych kart w okienku z kartami.

##  <a name="hasautohidemode"></a>CBaseTabbedPane::HasAutoHideMode

Określa, czy okienko z kartami może być przełączane w tryb autoukrywania.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okienko można przełączyć w tryb Autoukrywanie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli tryb Autoukrywanie jest wyłączony, na podpisie okienka z kartami nie jest wyświetlany przycisk Przypnij.

##  <a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab

Określa, czy okienko z kartami jest ukryte, gdy zostanie wyświetlona tylko jedna karta.

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli okno karty nie jest wyświetlane, gdy istnieje tylko jedna widoczna karta; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli okienko nie jest wyświetlane, ponieważ tylko jedna karta jest otwarta, można wywołać tę metodę, aby określić, czy okienko z kartami działa poprawnie.

##  <a name="removepane"></a>CBaseTabbedPane::RemovePane

Usuwa okienko z okienka z kartami.

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in. out] Wskaźnik do okienka, które ma zostać usunięte z okienka z kartami.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli okienko zostało pomyślnie usunięte z okienka z kartami i jeśli okienko z kartami jest nadal ważne. Wartość FALSE, jeśli ostatnie okienko zostało usunięte z okienka z kartami, a okienko z kartami zostanie zniszczone. Jeśli zwracaną wartością jest FALSE, nie należy używać okienka z kartami więcej.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby usunąć okienko określone przez parametr *pBar* z okienka z kartami.

##  <a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy

Określa, czy pasek sterowania z kartami zostanie zniszczony automatycznie.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroy*<br/>
podczas Ma wartość TRUE, jeśli okienko z kartami zostało utworzone dynamicznie i nie kontrolujesz jego okresu istnienia. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ustaw tryb autoniszczenia na TRUE, jeśli utworzysz okienko z kartami dynamicznie i jeśli nie kontrolujesz jego okresu istnienia. Jeśli tryb autoniszczenia ma wartość TRUE, okienko z kartami zostanie zniszczone automatycznie przez strukturę.

##  <a name="showtab"></a>CBaseTabbedPane:: ShowTab

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
podczas Wskaźnik do okienka, aby pokazać lub ukryć.

*bShow*<br/>
podczas Wartość TRUE, aby wyświetlić okienko; Wartość FALSE, aby ukryć okienko.

*bDelay*<br/>
podczas PRAWDA, aby opóźnić korektę układu karty; w przeciwnym razie FALSE.

*bActivate*<br/>
podczas PRAWDA, aby karta była aktywna; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli karta została pokazana lub Ukryta pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Po wywołaniu tej metody okienko jest wyświetlane lub ukrywane, w zależności od wartości parametru *bShow* . Jeśli ukryjesz kartę i jest to Ostatnia widoczna karta w oknie podstawowej karty, okienko z kartami jest ukryte. Jeśli zostanie wyświetlona karta, gdy nie ma żadnych widocznych kart, wyświetlane jest okienko z kartami.

##  <a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout

Ponownie oblicza informacje o układzie dla okienka.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Uwagi

Jeśli okienko jest przestawne, ta metoda powiadamia platformę o zmianie rozmiaru okienka na bieżący rozmiar mini-frame.

Jeśli okienko jest zadokowane, ta metoda nie wykonuje żadnych operacji.

##  <a name="setautohidemode"></a>CBaseTabbedPane:: autoukrywaniemode

Ustawia tryb autoukrywania dla odłączalnych okienek w okienku z kartami.

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Parametry

*bMode*<br/>
podczas Wartość TRUE, aby włączyć tryb autoukrywania; Wartość FALSE, aby włączyć tryb regularnego dokowania.

*dwAlignment*<br/>
podczas Określa wyrównanie okienka Autoukrywanie, które ma zostać utworzone. Aby uzyskać listę możliwych wartości, zobacz [CPane:: MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).

*pCurrAutoHideBar*<br/>
[in. out] Wskaźnik do bieżącego paska narzędzi Autoukrywanie. Może mieć wartość NULL.

*bUseTimer*<br/>
podczas Określa, czy ma być używany efekt Autoukrywanie, gdy użytkownik przełącza okienko do trybu autoukrywania, lub w celu natychmiastowego ukrycia okienka.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do paska narzędzi Autoukrywanie, który jest tworzony podczas przełączania do trybu autoukrywania, lub wartość NULL, jeśli nie jest tworzony żaden pasek narzędzi.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy użytkownik wybierze przycisk pinezki w celu przełączenia okienka z kartami do trybu Autoukrywanie lub do zwykłego trybu dokowania.

Tryb autoukrywania jest ustawiany dla każdego okienka, które ma zostać odłączalne w okienku z kartami. Okienka, które nie są odłączane, są ignorowane. Aby uzyskać więcej informacji, zobacz [CMFCBaseTabCtrl:: EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).

Wywołaj tę metodę, aby programowo włączyć tryb ukrywania okienka z kartami. Okienko musi być zadokowane do głównego okna ramki ( [CDockablePane:: GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) musi zwrócić prawidłowy wskaźnik do [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)
