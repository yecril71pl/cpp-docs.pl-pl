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
ms.openlocfilehash: b3ae0d69c385ba89cf75d682ce12c6f1f4e5112f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752971"
---
# <a name="cbasetabbedpane-class"></a>Klasa CBaseTabbedPane

Rozszerza funkcjonalność [CDockablePane klasy](../../mfc/reference/cdockablepane-class.md) do obsługi tworzenia okien z kartami.

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
|[CBaseTabbedPane::Dodajtab](#addtab)|Dodaje nową kartę do okienka z kartami.|
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Określa, czy puste okienko z kartami może zostać zniszczone.|
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Stosuje ustawienia kart, które są ładowane z rejestru, do okienka z kartami.|
|[CBaseTabbedPane::CanFloat](#canfloat)|Określa, czy okienko może się unosić. (Zastępuje [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Określa, czy podpis okienka z kartami ma być wyświetlany w tym samym tekście co aktywna karta.|
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Zastępuje [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|
|[CBaseTabbedPane::DetachPane](#detachpane)|Konwertuje co najmniej jedno okienka dokowane na dokumenty z kartami MDI.|
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Włącza lub wyłącza możliwość synchronizowania tekstu podpisu z tekstem etykiety na aktywnej karcie.|
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Przywraca wewnętrzną kolejność tabulacji do stanu domyślnego.|
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Zwraca okienko, które znajduje się na karcie, gdy karta jest identyfikowana za pomocą indeksu kart opartych na wartościach zerowych.|
|||
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Zwraca okienko identyfikowane przez identyfikator okienka.|
|[CBaseTabbedPane::FloatTab](#floattab)|Przesuwa okienko, ale tylko wtedy, gdy okienko znajduje się obecnie na odłączanej karcie.|
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Zwraca domyślną kolejność kart w okienku.|
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Pobiera wskaźnik do pierwszej wyświetlanej karty.|
|[CBaseTabbedPane::GetMinSize](#getminsize)|Pobiera minimalny dozwolony rozmiar okienka. (Zastępuje [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Zwraca uchwyt do ikony okienka. (Zastępuje [CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|
|[CBaseTabbedPane::Lista GetPane](#getpanelist)|Zwraca listę okienek znajdujących się w okienku z kartami.|
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Zwraca prostokąty ograniczające dla górnych i dolnych obszarów tabulacji.|
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Zwraca liczbę kart w oknie karty.|
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Pobiera podstawowe (zawinięte) okno karty.|
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Zwraca liczbę wyświetlanych kart.|
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Określa, czy okienko z kartami można przełączyć na tryb automatycznego ukrywania.|
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Określa, czy okienko z kartami jest ukryte, jeśli wyświetlana jest tylko jedna karta.|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Używane wewnętrznie podczas serializacji.|
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Ponownie oblicza informacje o układzie okienka. (Zastępuje [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|
|[CBaseTabbedPane::UsuńPane](#removepane)|Usuwa okienko z okienka z kartami.|
|`CBaseTabbedPane::SaveSiblingBarIDs`|Używane wewnętrznie podczas serializacji.|
|`CBaseTabbedPane::Serialize`|(Zastępuje [CDockablePane::Serialize](cdockablepane-class.md).)|
|`CBaseTabbedPane::SerializeTabWindow`|Używane wewnętrznie podczas serializacji.|
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Określa, czy pasek sterowania z kartami zostanie automatycznie zniszczony.|
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Przełącza okienko dokowania między wyświetlanym trybem a trybem automatycznego ukrywania. (Zastępuje [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|
|[CBaseTabbedPane::Pokażtab](#showtab)|Pokazuje lub ukrywa kartę.|

## <a name="remarks"></a>Uwagi

Ta klasa jest klasą abstrakcyjną i nie można jej utworzyć. Implementuje usługi, które są wspólne dla wszystkich rodzajów okienek z kartami.

Obecnie biblioteka zawiera dwie pochodne klasy okienka z kartami: [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md) i [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

Obiekt `CBaseTabbedPane` zawija wskaźnik do obiektu [CMFCBaseTabCtrl Class.](../../mfc/reference/cmfcbasetabctrl-class.md) [CMFCBaseTabCtrl Klasa](../../mfc/reference/cmfcbasetabctrl-class.md) staje się następnie okno podrzędne okienka z kartami.

Aby uzyskać więcej informacji na temat tworzenia okienek z kartami, zobacz [CDockablePane Class](../../mfc/reference/cdockablepane-class.md), [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md)i [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[Cdockablepane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxBaseTabbedPane.h

## <a name="cbasetabbedpaneaddtab"></a><a name="addtab"></a>CBaseTabbedPane::Dodajtab

Dodaje nową kartę do okienka z kartami.

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>Parametry

*pNowyBar*<br/>
[w, na zewnątrz] Wskaźnik do okienka, aby dodać. Ten wskaźnik może stać się nieprawidłowy po wywołaniu tej metody. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.

*b Widoczne*<br/>
[w] PRAWDA, aby karta była widoczna; w przeciwnym razie FALSE.

*bSetAktywny*<br/>
[w] PRAWDA, aby zakładka była aktywna; w przeciwnym razie FALSE.

*bDetachable*<br/>
[w] PRAWDA, aby zakładka była odłączana; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okienko zostało pomyślnie dodane jako karta i nie zostało zniszczone w procesie. FAŁSZ, jeśli dodawane okienko `CBaseTabbedPane`jest obiektem typu . Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby dodać okienko jako nową kartę w okienku z kartami. Jeśli *pNewBar* wskazuje na `CBaseTabbedPane`obiekt typu, wszystkie jego karty są kopiowane na okienku z kartami, a następnie *pNewBar* jest niszczony. W związku z tym *pNewBar* staje się nieprawidłowy wskaźnik i nie powinny być używane.

## <a name="cbasetabbedpaneallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane

Określa, czy puste okienko z kartami może zostać zniszczone.

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli puste okienko z kartami może zostać zniszczone; w przeciwnym razie FALSE. Domyślna implementacja zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Jeśli puste okienko z kartami nie może zostać zniszczone, struktura ukrywa okienko zamiast tego.

## <a name="cbasetabbedpaneapplyrestoredtabinfo"></a><a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo

Ładuje ustawienia kart z rejestru i stosuje je do okienka z kartami.

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>Parametry

*bUchtabIndeksy*<br/>
[w] Ten parametr jest używany wewnętrznie przez platformę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy ponownie ładuje informacje o stanie dokowania z rejestru. Metoda uzyskuje informacje o kolejności tabulacji i nazwach kart dla okienka z kartami.

## <a name="cbasetabbedpanecanfloat"></a><a name="canfloat"></a>CBaseTabbedPane::CanFloat

Określa, czy okienko z kartami może się unosić.

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okienko może się unosić; w przeciwnym razie FALSE.

## <a name="cbasetabbedpanecansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName

Określa, czy podpis okienka z kartami ma być wyświetlany w tym samym tekście co aktywna karta.

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli tekst podpisu okienka z kartami jest ustawiony na tekst aktywnej karty; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Metoda ta służy do określenia, czy tekst wyświetlany na podpisie okienka z kartami powiela etykietę aktywnej karty. Tę funkcję można włączyć lub wyłączyć, wywołując [cbasetabbedpane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).

## <a name="cbasetabbedpaneconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument

Konwertuje co najmniej jedno okienka dokowane na dokumenty z kartami MDI.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bNataczyni tylko*<br/>
[w] Podczas konwertowania okienka z kartami określ wartość TRUE, aby przekonwertować tylko aktywną kartę.

## <a name="cbasetabbedpanedetachpane"></a><a name="detachpane"></a>CBaseTabbedPane::DetachPane

Odłącza okienko od okienka z kartami.

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[w] Wskaźnik do okienka, aby odłączyć.

*bHide (ur.*<br/>
[w] Parametr logiczny, który określa, czy struktura ukrywa okienko po jego odłączeniu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli struktura pomyślnie odłącza okienko; FAŁSZ, jeśli *pBar* ma wartość NULL lub odwołuje się do okienka, które nie znajduje się w okienku z kartami.

### <a name="remarks"></a>Uwagi

Struktura floats odłączone okienko, jeśli to możliwe. Aby uzyskać więcej informacji, zobacz [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).

## <a name="cbasetabbedpaneenablesetcaptiontexttotabname"></a><a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName

Włącza lub wyłącza możliwość synchronizowania tekstu podpisu z tekstem etykiety na aktywnej karcie.

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] PRAWDA, aby zsynchronizować podpis okienka z kartami z aktywnym podpisem karty; w przeciwnym razie FALSE.

## <a name="cbasetabbedpanefilldefaulttabsorderarray"></a><a name="filldefaulttabsorderarray"></a>CBaseTabbedPane::FillDefaultTabsOrderArray

Przywraca wewnętrzną kolejność tabulacji do stanu domyślnego.

```cpp
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, gdy struktura przywraca pasek programu Outlook do stanu początkowego.

## <a name="cbasetabbedpanefindpanebyid"></a><a name="findpanebyid"></a>CBaseTabbedPane::FindPaneByID

Zwraca okienko identyfikowane przez identyfikator okienka.

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>Parametry

*uBarID*<br/>
[w] Określa identyfikator okienka do znalezienia.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okienka, jeśli został znaleziony; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ta metoda porównuje wszystkie karty w okienku i zwraca jedną z identyfikatorem określonym przez parametr *uBarID.*

## <a name="cbasetabbedpanefindbarbytabnumber"></a><a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber

Zwraca okienko, które znajduje się na karcie.

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>Parametry

*nTabNum*<br/>
[w] Określa indeks od zera karty do pobrania.

*bGetWrappedBar*<br/>
[w] TRUE, aby zwrócić podstawowe (opakowane) okno okienka zamiast samego okienka; w przeciwnym razie FALSE. Dotyczy to tylko okienek pochodzących z [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).

### <a name="return-value"></a>Wartość zwracana

Jeśli zostanie znalezione okienko, zwracany jest prawidłowy wskaźnik do wyszukiwanego okienka; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pobrać okienko zamieszkałe na karcie określonej przez parametr *nTabNum.*

## <a name="cbasetabbedpanefloattab"></a><a name="floattab"></a>CBaseTabbedPane::FloatTab

Przesuwa okienko, ale tylko wtedy, gdy okienko znajduje się obecnie na odłączanej karcie.

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[w, na zewnątrz] Wskaźnik do okienka, aby upłynąć.

*nTabID (nTabID)*<br/>
[w] Określa indeks oparty na wartości zero karty do uchyłkania.

*dokMetoda*<br/>
[w] Określa metodę, która ma być używana do zmiennego okienka. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.

*bHide (ur.*<br/>
[w] PRAWDA, aby ukryć okienko przed unoszenia się na wodzie; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okienko unosiło się na wodzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby float okienka, które obecnie znajduje się w karcie odłączane.

Jeśli chcesz odłączyć okienko programowo, określ DM_SHOW dla parametru *dockMethod.* Jeśli chcesz float okienka w tej samej pozycji, gdzie wcześniej pływał, należy określić DM_DBL_CLICK jako *dockMethod* parametru.

## <a name="cbasetabbedpanegetdefaulttabsorder"></a><a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder

Zwraca domyślną kolejność kart w okienku.

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `CArray` określający domyślną kolejność kart w okienku.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy pasek programu Outlook jest resetowany do stanu początkowego.

## <a name="cbasetabbedpanegetfirstvisibletab"></a><a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab

Pobiera wskaźnik do pierwszej wyświetlanej karty.

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>Parametry

*iTabNum*<br/>
[w] Odwołanie do liczby całkowitej. Ta metoda zapisuje indeks oparty na wartości zero pierwszej wyświetlanej karty do tego parametru lub -1, jeśli nie zostanie znaleziona żadna wyświetlana karta.

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, wskaźnik do pierwszej wyświetlanej karty; w przeciwnym razie NULL.

## <a name="cbasetabbedpanegetminsize"></a><a name="getminsize"></a>CBaseTabbedPane::GetMinSize

Pobiera minimalny dozwolony rozmiar okienka.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
[na zewnątrz] Obiekt, `CSize` który jest wypełniony minimalnym dozwolonym rozmiarem.

### <a name="remarks"></a>Uwagi

Jeśli aktywna jest spójna obsługa minimalnych rozmiarów okienka ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), *rozmiar* jest wypełniony minimalnym dozwolonym rozmiarem dla aktywnej karty. W przeciwnym razie *rozmiar* jest wypełniony zwracaną wartością [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

## <a name="cbasetabbedpanegetpaneicon"></a><a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon

Pobiera minimalny dozwolony rozmiar okienka.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
[na zewnątrz] Obiekt, `CSize` który jest wypełniony minimalnym dozwolonym rozmiarem.

### <a name="remarks"></a>Uwagi

Jeśli aktywna jest spójna obsługa minimalnych rozmiarów okienka ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), *rozmiar* jest wypełniony minimalnym dozwolonym rozmiarem dla aktywnej karty. W przeciwnym razie *rozmiar* jest wypełniony zwracaną wartością [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

## <a name="cbasetabbedpanegetpanelist"></a><a name="getpanelist"></a>CBaseTabbedPane::Lista GetPane

Zwraca listę okienek znajdujących się w okienku z kartami.

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>Parametry

*Lst*<br/>
[na zewnątrz] A, `CObList` który jest wypełniony okienkami, które są zawarte w okienku z kartami.

*pRTCFilter*<br/>
[w] Jeśli nie jest null, zwracana lista zawiera tylko okienka, które są określonej klasy środowiska uruchomieniowego.

## <a name="cbasetabbedpanegettabarea"></a><a name="gettabarea"></a>CBaseTabbedPane::GetTabArea

Zwraca prostokąty ograniczające dla górnych i dolnych obszarów tabulacji.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>Parametry

*reectTabAreaTop*<br/>
[na zewnątrz] Odbiera współrzędne ekranu górnego obszaru karty.

*pectTabAreaBottom*<br/>
[na zewnątrz] Odbiera współrzędne ekranu dolnego obszaru karty.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby określić prostokąty ograniczające, we współrzędnych ekranu, dla górnej i dolnej części karty.

## <a name="cbasetabbedpanegettabsnum"></a><a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum

Zwraca liczbę kart w oknie karty.

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba kart w okienku z kartami.

## <a name="cbasetabbedpanegetunderlyingwindow"></a><a name="getunderlyingwindow"></a>CBaseTabbedPane::GetUnderlyingWindow

Pobiera podstawowe (zawinięte) okno karty.

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna karty podstawowej.

## <a name="cbasetabbedpanegetvisibletabsnum"></a><a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum

Zwraca liczbę widocznych kart.

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba widocznych kart, która będzie większa lub równa zeru.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby określić liczbę widocznych kart w okienku z kartami.

## <a name="cbasetabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CBaseTabbedPane::HasAutoHideMode

Określa, czy okienko z kartami można przełączyć w tryb autouzusty.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okienko można przełączyć na tryb autouszudy; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli tryb autohide jest wyłączony, na podpisie okienka z kartami nie jest wyświetlany żaden przycisk pin.

## <a name="cbasetabbedpaneishidesingletab"></a><a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab

Określa, czy okienko z kartami jest ukryte, jeśli wyświetlana jest tylko jedna karta.

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno karty nie jest wyświetlane, gdy istnieje tylko jedna widoczna karta; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli okienko nie jest wyświetlane, ponieważ tylko jedna karta jest otwarta, można wywołać tę metodę, aby ustalić, czy okienko z kartami działa poprawnie.

## <a name="cbasetabbedpaneremovepane"></a><a name="removepane"></a>CBaseTabbedPane::UsuńPane

Usuwa okienko z okienka z kartami.

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[w, na zewnątrz] Wskaźnik do okienka do usunięcia z okienka z kartami.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okienko zostało pomyślnie usunięte z okienka z kartami i jeśli okienko z kartami jest nadal ważne. FAŁSZ, jeśli ostatnie okienko zostało usunięte z okienka z kartami, a okienko z kartami ma zostać zniszczone. Jeśli zwracana wartość to FAŁSZ, nie należy już używać okienka z kartami.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby usunąć okienko określone przez parametr *pBar* z okienka z kartami.

## <a name="cbasetabbedpanesetautodestroy"></a><a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy

Określa, czy pasek sterowania z kartami zostanie automatycznie zniszczony.

```cpp
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroj*<br/>
[w] PRAWDA, jeśli okienko z kartami zostało utworzone dynamicznie i nie kontrolujesz jego istnienia; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ustaw tryb automatycznego niszczenia na TRUE, jeśli dynamicznie utworzysz okienko z kartami i nie kontrolujesz jego okresu istnienia. Jeśli tryb automatycznego niszczenia jest TRUE, okienko z kartami zostanie automatycznie zniszczone przez platformę.

## <a name="cbasetabbedpaneshowtab"></a><a name="showtab"></a>CBaseTabbedPane::Pokażtab

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
[w] Wskaźnik do okienka, aby pokazać lub ukryć.

*bPokaż*<br/>
[w] PRAWDA, aby wyświetlić okienko; FAŁSZ, aby ukryć okienko.

*bDelay (własówce)*<br/>
[w] PRAWDA, aby opóźnić dostosowanie układu karty; w przeciwnym razie FALSE.

*bAktywowanie*<br/>
[w] PRAWDA, aby zakładka była aktywna; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli karta została wyświetlona lub ukryta pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Po wywołaniu tej metody okienko jest wyświetlane lub ukryte, w zależności od wartości parametru *bShow.* Jeśli ukryjesz kartę i będzie to ostatnia widoczna karta w podstawowym oknie karty, okienko z kartami zostanie ukryte. Jeśli karta zostanie wyświetlona, gdy wcześniej nie było widocznych kart, zostanie wyświetlone okienko z kartami.

## <a name="cbasetabbedpanerecalclayout"></a><a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout

Ponownie oblicza informacje o układzie okienka.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Uwagi

Jeśli okienko jest zmiennoprzecinkowy, ta metoda powiadamia strukturę, aby zmienić rozmiar okienka do bieżącego rozmiaru mini-ramki.

Jeśli okienko jest zadokowany, ta metoda nie robi nic.

## <a name="cbasetabbedpanesetautohidemode"></a><a name="setautohidemode"></a>CBaseTabbedPane::SetAutoHideMode

Ustawia tryb automatycznego ukrywania dla odłączanych okienek w okienku z kartami.

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Parametry

*bMode (tryb)*<br/>
[w] PRAWDA, aby włączyć tryb automatycznego ukrywania; FALSE, aby włączyć zwykły tryb dokowania.

*dwZładna*<br/>
[w] Określa wyrównanie okienka automatycznego ukrywania, które ma zostać utworzone. Aby uzyskać listę możliwych wartości, zobacz [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).

*pCurrAutoHideBar*<br/>
[w, na zewnątrz] Wskaźnik do bieżącego paska narzędzi automatycznego ukrywania. Może mieć wartość NULL.

*bUchocer*<br/>
[w] Określa, czy efekt automatycznego ukrywania ma być używany, gdy użytkownik przełącza okienko w tryb automatycznego ukrywania, czy też natychmiast ukryć okienko.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do paska narzędzi automatycznego ukrywania, który jest tworzony podczas przełączania do trybu automatycznego ukrywania, lub NULL, jeśli nie jest tworzony żaden pasek narzędzi.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy użytkownik wybierze przycisk pin, aby przełączyć okienko z kartami do trybu automatycznego ukrywania lub do zwykłego trybu dokowania.

Tryb automatycznego ukrywania jest ustawiony dla każdego odłączanego okienka w okienku z kartami. Okienka, które nie można odłączać, są ignorowane. Aby uzyskać więcej informacji, zobacz [CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).

Wywołanie tej metody, aby przełączyć okienko z kartami do trybu automatycznego ukrywania programowo. Okienko musi być zadokowane do okna ramki głównej ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) musi zwrócić prawidłowy wskaźnik do [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)
