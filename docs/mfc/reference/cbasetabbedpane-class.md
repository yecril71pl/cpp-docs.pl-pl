---
title: Klasa CBaseTabbedPane | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: be9752822ee009ceddb735806d36ea3507242951
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cbasetabbedpane-class"></a>Klasa CBaseTabbedPane
Rozszerza funkcjonalność [klasy CDockablePane](../../mfc/reference/cdockablepane-class.md) do obsługi tworzenia systemu windows z kartami.  
  
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
|[CBaseTabbedPane::AddTab](#addtab)|Dodaje nową kartę do okienka z kartami.|  
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Określa, czy puste okienko z kartami może zostać zniszczone.|  
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Stosuje ustawienia kart, które są ładowane z rejestru, w okienku z kartami.|  
|[CBaseTabbedPane::CanFloat](#canfloat)|Określa, czy można float okienka. (Przesłania [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|  
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Określa, czy podpis dla tego okienka z kartami powinien wyświetlać tego samego tekstu jako aktywnej karty.|  
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Przesłania [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|  
|[CBaseTabbedPane::DetachPane](#detachpane)|Konwertuje co najmniej jednego okienka dokującego dokumenty z kartami MDI.|  
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Włącza lub wyłącza możliwość synchronizowania tekst podpisu z tekst etykiety na karcie aktywne okienko z kartami.|  
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Przywraca kolejności tabulacji wewnętrzny do stanu domyślnego.|  
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Zwraca okienko, w którym znajduje się na karcie, gdy karcie jest identyfikowany przez liczony od zera indeks.|  
|||  
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Zwraca okienko, który jest identyfikowany przez identyfikator okienka.|  
|[CBaseTabbedPane::FloatTab](#floattab)|Przesunięty okienku, ale tylko wtedy, jeśli okienku aktualnie znajduje się na karcie odłączane.|  
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Zwraca domyślną kolejność kart, w okienku.|  
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Pobiera wskaźnik do pierwszej karcie wyświetlane.|  
|[CBaseTabbedPane::GetMinSize](#getminsize)|Pobiera minimalny dozwolony rozmiar okienka. (Przesłania [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|  
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Zwraca dojście do ikony okienka. (Przesłania [CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|  
|[CBaseTabbedPane::GetPaneList](#getpanelist)|Zwraca listę okienka, które są zawarte w okienku z kartami.|  
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Zwraca prostokąty obszarów kartę górny i dolny.|  
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Zwraca liczbę karty w oknie kartę.|  
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Pobiera podstawowy okno karty (opakowana).|  
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Zwraca liczbę wyświetlanych kart.|  
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Określa, czy z kartami okienku może zostać przełączone do trybu autoukrywania.|  
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Określa, czy okienko z kartami jest ukryty, jeśli tylko jedna karta jest wyświetlana.|  
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Podczas serializacji używać wewnętrznie.|  
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Ponownie oblicza informacji o układzie dla tego okienka. (Przesłania [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|  
|[CBaseTabbedPane::RemovePane](#removepane)|Usuwa okienko z okienka z kartami.|  
|`CBaseTabbedPane::SaveSiblingBarIDs`|Podczas serializacji używać wewnętrznie.|  
|`CBaseTabbedPane::Serialize`|(Przesłania [CDockablePane::Serialize](http://msdn.microsoft.com/en-us/09787e59-e446-4e76-894b-206d303dcfd6).)|  
|`CBaseTabbedPane::SerializeTabWindow`|Podczas serializacji używać wewnętrznie.|  
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Określa, czy pasek sterowania z kartami zostaną automatycznie usunięte.|  
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Włącza lub wyłącza okienko dokujące między wyświetlane i autoukrywania tryb. (Przesłania [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|  
|[CBaseTabbedPane::ShowTab](#showtab)|Pokazuje lub ukrywa karty.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa jest klasą abstrakcyjną i nie można utworzyć wystąpienia. Implementuje usługi, które są wspólne dla wszystkich rodzajów okienka z kartami.  
  
 Obecnie biblioteka zawiera dwie klasy pochodnej okienko z kartami: [klasy CTabbedPane](../../mfc/reference/ctabbedpane-class.md) i [CMFCOutlookBar klasy](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 A `CBaseTabbedPane` obiektu opakowuje wskaźnik do [klasy CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) obiektu. [Klasa CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) staje się oknem podrzędnym okienka z kartami.  
  
 Aby uzyskać więcej informacji o sposobie tworzenia okienka z kartami, zobacz [klasy CDockablePane](../../mfc/reference/cdockablepane-class.md), [klasy CTabbedPane](../../mfc/reference/ctabbedpane-class.md), i [CMFCOutlookBar klasy](../../mfc/reference/cmfcoutlookbar-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 `CBaseTabbedPane`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxBaseTabbedPane.h  
  
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
 [in] [out]`pNewBar`  
 Wskaźnik do okienka do dodania. This, wskaźnik może stać się nieprawidłowy po wywołaniu tej metody. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
 [in]`bVisible`  
 `TRUE`Aby wyświetlić na karcie; w przeciwnym razie `FALSE`.  
  
 [in]`bSetActive`  
 `TRUE`Aby na karcie karcie active; w przeciwnym razie `FALSE`.  
  
 [in]`bDetachable`  
 `TRUE`Aby wprowadzić na karcie odłączane; w przeciwnym razie `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko został pomyślnie dodany jako karty i nie została zniszczona w procesie. `FALSE`Jeśli okienko dodawany jest obiekt typu `CBaseTabbedPane`. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby dodać okienka jako nową kartę w okienku z kartami. Jeśli `pNewBar` wskazuje na obiekt typu `CBaseTabbedPane`, wszystkie jego karty są kopiowane na kartach okienka, a następnie `pNewBar` zostanie zniszczony. W związku z tym `pNewBar` staje się nieprawidłowy wskaźnik i nie powinna być używana.  
  
##  <a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane  
 Określa, czy puste okienko z kartami może zostać zniszczone.  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli pusty okienko z kartami może zostać zniszczone; w przeciwnym razie `FALSE`. Domyślna implementacja zawsze zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Pusty okienko z kartami nie może zostać zniszczone, platformę ukrywa okienka zamiast tego.  
  
##  <a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo  
 Ładuje ustawienia na karcie z rejestru i stosuje je do okienka z kartami.  
  
```  
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bUseTabIndexes`  
 Ten parametr jest używana wewnętrznie przez platformę.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy jego ponowne załadowanie dokowania informacji o stanie z rejestru. Metoda uzyskuje informacje o kolejności tabulacji i nazwy kart dla okienka z kartami.  
  
##  <a name="canfloat"></a>CBaseTabbedPane::CanFloat  
 Określa, czy można float okienka z kartami.  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli w okienku można float; w przeciwnym razie `FALSE`.  
  
##  <a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName  
 Określa, czy podpis dla tego okienka z kartami powinien wyświetlać tego samego tekstu jako aktywnej karty.  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli tekst podpisu z kartami okienka tekstu karcie active; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Metoda służy do określają, czy tekst wyświetlany na duplikaty podpis okienko z kartami etykietę active karty. Można włączyć lub wyłączyć tę funkcję, wywołując [CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).  
  
##  <a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument  
 Konwertuje co najmniej jednego okienka dokującego dokumenty z kartami MDI.  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bActiveTabOnly`  
 Podczas konwertowania z kartami okienku określ `TRUE` przekonwertować aktywnej karty. Określ `FALSE` można przekonwertować wszystkie karty w okienku.  
  
##  <a name="detachpane"></a>CBaseTabbedPane::DetachPane  
 Odłącza okienko z okienka z kartami.  
  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
 Wskaźnik do okienko, aby odłączyć.  
  
 [in]`bHide`  
 Wartość logiczna parametr, który określa, czy platformę powoduje ukrycie okienka po jest ona odłączona.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli w ramach pomyślnie odłącza okienku. `FALSE` Jeśli `pBar` jest `NULL` lub odwołuje się do okienka, który nie znajduje się w okienku z kartami.  
  
### <a name="remarks"></a>Uwagi  
 Odłączony okienko jest wyświetlany w ramach Jeśli to możliwe. Aby uzyskać więcej informacji, zobacz [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).  
  
##  <a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName  
 Włącza lub wyłącza możliwość synchronizowania tekst podpisu z tekst etykiety na karcie aktywne okienko z kartami.  
  
```  
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 `TRUE`Aby zsynchronizować podpis okienko z kartami z podpisem aktywnej karcie; w przeciwnym razie `FALSE`.  
  
##  <a name="filldefaulttabsorderarray"></a>CBaseTabbedPane::FillDefaultTabsOrderArray  
 Przywraca kolejności tabulacji wewnętrzny do stanu domyślnego.  
  
```  
void FillDefaultTabsOrderArray();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana, gdy platformę przywraca stan początkowy paska Outlook.  
  
##  <a name="findpanebyid"></a>CBaseTabbedPane::FindPaneByID  
 Zwraca okienko identyfikowany przez identyfikator okienka.  
  
```  
virtual CWnd* FindPaneByID(UINT uBarID);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uBarID`  
 Określa identyfikator okienku można znaleźć.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do okienka, jeśli został znaleziony; w przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda porównuje wszystkie karty w okienku i zwraca z określonej przez identyfikator `uBarID` parametru.  
  
##  <a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber  
 Zwraca okienko, w którym znajduje się na karcie.  
  
```  
virtual CWnd* FindBarByTabNumber(
    int nTabNum,  
    BOOL bGetWrappedBar = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nTabNum`  
 Określa liczony od zera indeks kartę, aby pobrać.  
  
 [in]`bGetWrappedBar`  
 `TRUE`Aby przywrócić źródłowy okna (opakowana) okienka zamiast okienka. w przeciwnym razie `FALSE`. Dotyczy to tylko okienka pochodną [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli okienko zostanie znaleziony, zwracana jest nieprawidłowy wskaźnik do okienka wyszukane; w przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody można pobrać okienku znajdującej się na karcie określony przez `nTabNum` parametru.  
  
##  <a name="floattab"></a>CBaseTabbedPane::FloatTab  
 Przesunięty okienku, ale tylko wtedy, jeśli okienku aktualnie znajduje się na karcie odłączane.  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out]`pBar`  
 Wskaźnik do typu float w okienku.  
  
 [in]`nTabID`  
 Określa liczony od zera indeks kartę, aby float.  
  
 [in]`dockMethod`  
 Określa metodę używaną do Dokowanie okienka. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
 [in]`bHide`  
 `TRUE`Aby ukryć okienko zanim; w przeciwnym razie `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienko przestawione; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę w celu float okienko, w którym aktualnie znajduje się na karcie odłączane.  
  
 Jeśli chcesz odłączyć okienko programowo, określ `DM_SHOW` dla `dockMethod` parametru. Jeśli chcesz float okienka w tym samym miejscu, gdzie przestawione wcześniej, określ `DM_DBL_CLICK` jako `dockMethod` parametru.  
  
##  <a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder  
 Zwraca domyślną kolejność kart, w okienku.  
  
```  
const CArray<int,int>& GetDefaultTabsOrder();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CArray` obiekt, który określa domyślną kolejność kart w okienku.  
  
### <a name="remarks"></a>Uwagi  
 Platformę wywołuje tę metodę, gdy pasek Outlook jest resetowany do stanu początkowego.  
  
##  <a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab  
 Pobiera wskaźnik do pierwszej karcie wyświetlane.  
  
```  
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iTabNum`  
 Odwołanie do liczby całkowitej. Ta metoda zapisuje liczony od zera indeks pierwszej karcie wyświetlane do tego parametru lub wartość -1 Jeśli wyświetlane nie znaleziono kartę.  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia wskaźnik do pierwszej karcie wyświetlane; w przeciwnym razie `NULL`.  
  
##  <a name="getminsize"></a>CBaseTabbedPane::GetMinSize  
 Pobiera minimalny dozwolony rozmiar okienka.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`size`  
 A `CSize` obiekt, który jest wypełniony dozwolony rozmiar.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aktywne jest spójne obsługi rozmiar minimalny okienka ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), `size` jest wypełniony dozwolony rozmiar dla aktywnej karty. W przeciwnym razie `size` jest wypełniony wartość zwracaną [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).  
  
##  <a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon  
 Pobiera minimalny dozwolony rozmiar okienka.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`size`  
 A `CSize` obiekt, który jest wypełniony dozwolony rozmiar.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aktywne jest spójne obsługi rozmiar minimalny okienka ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), `size` jest wypełniony dozwolony rozmiar dla aktywnej karty. W przeciwnym razie `size` jest wypełniony wartość zwracaną [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).  
  
##  <a name="getpanelist"></a>CBaseTabbedPane::GetPaneList  
 Zwraca listę okienka, które są zawarte w okienku z kartami.  
  
```  
virtual void GetPaneList(
    CObList& lst,  
    CRuntimeClass* pRTCFilter = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [out]`lst`  
 A `CObList` który jest wypełniony okienka, które są zawarte w okienku z kartami.  
  
 [in]`pRTCFilter`  
 Jeśli nie jest `NULL`, zwracana lista zawiera tylko okienek klasy wykonawcze.  
  
##  <a name="gettabarea"></a>CBaseTabbedPane::GetTabArea  
 Zwraca prostokąty obszarów kartę górny i dolny.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rectTabAreaTop`  
 Odbiera współrzędne ekranu obszaru górny karty.  
  
 [out]`rectTabAreaBottom`  
 Odbiera współrzędne ekranu dolnej kartę.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby określić prostokąty, we współrzędnych ekranu dla obszarów górny i dolny kartę.  
  
##  <a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum  
 Zwraca liczbę karty w oknie kartę.  
  
```  
virtual int GetTabsNum() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba kart w okienku z kartami.  
  
##  <a name="getunderlyingwindow"></a>CBaseTabbedPane::GetUnderlyingWindow  
 Pobiera podstawowy okno karty (opakowana).  
  
```  
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do podstawowego okno karty.  
  
##  <a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum  
 Zwraca liczbę kart widocznych.  
  
```  
virtual int GetVisibleTabsNum() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba widocznych kart, które będzie większa lub równa zero.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby określić liczbę kart widocznych w okienku z kartami.  
  
##  <a name="hasautohidemode"></a>CBaseTabbedPane::HasAutoHideMode  
 Określa, czy z kartami okienku może zostać przełączone do trybu autohide —.  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli w okienku może zostać przełączone do trybu autohide —; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Po wyłączeniu trybu autohide — ma przycisku numer pin jest wyświetlany na podpis okienko z kartami.  
  
##  <a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab  
 Określa, czy okienko z kartami jest ukryty, jeśli tylko jedna karta jest wyświetlana.  
  
```  
virtual BOOL IsHideSingleTab() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okno karty nie jest wyświetlany, jeśli istnieje tylko jedna karta widoczne; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli okienko nie jest wyświetlany, ponieważ tylko jedną kartę jest otwarte, należy wywołać tę metodę, aby określić, czy okienko z kartami działa poprawnie.  
  
##  <a name="removepane"></a>CBaseTabbedPane::RemovePane  
 Usuwa okienko z okienka z kartami.  
  
```  
virtual BOOL RemovePane(CWnd* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out]`pBar`  
 Wskaźnik do okienko, aby usunąć z okienka z kartami.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okienku został pomyślnie usunięty z okienka z kartami i kartach okienko jest nadal ważny. `FALSE`Jeśli okienko ostatniego został usunięty z okienka z kartami i okienka z kartami ma zostać zniszczone. Jeśli wartość zwracana jest `FALSE`, nie używaj więcej okienka z kartami.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby usunąć okienko określony przez `pBar` parametrów z okienka z kartami.  
  
##  <a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy  
 Określa, czy pasek sterowania z kartami zostaną automatycznie usunięte.  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bAutoDestroy`  
 `TRUE`Jeśli okienko z kartami został utworzony dynamicznie, a nie sterowanej jego trwania. w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ustaw tryb zniszczyć automatycznie `TRUE` Jeśli dynamicznie Utwórz okienko z kartami i nie są kontrolowanie swojego okresu istnienia. Jeśli zniszczyć automatycznie jest tryb `TRUE`, kartach okienko zostanie zniszczona automatycznie przez platformę.  
  
##  <a name="showtab"></a>CBaseTabbedPane::ShowTab  
 Pokazuje lub ukrywa karty.  
  
```  
virtual BOOL ShowTab(
    CWnd* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pBar`  
 Wskaźnik do okienka, aby pokazać lub ukryć.  
  
 [in]`bShow`  
 `TRUE`Aby wyświetlić okienko; `FALSE` Aby ukryć okienko.  
  
 [in]`bDelay`  
 `TRUE`opóźnienia dostosowania układu kartę; w przeciwnym razie `FALSE`.  
  
 [in]`bActivate`  
 `TRUE`Aby na karcie karcie active; w przeciwnym razie `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli na karcie został pokazywane lub ukryte pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Gdy ta metoda jest wywoływana, okienko jest pokazywany lub ukryty, w zależności od wartości `bShow` parametru. Ukryj karty jest ostatni kartę widoczne w oknie kartę podstawowej, zostanie ukryte okienka z kartami. Pokaż kartę, jeśli wcześniej zostały widoczne żadne karty, przedstawiono okienko z kartami.  
  
##  <a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout  
 Ponownie oblicza informacji o układzie dla tego okienka.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli okienko jest przestawne, ta metoda powiadamia platformę, by zmienić rozmiar okienka, aby bieżący rozmiar ramki minimalnej.  
  
 Jeśli panel jest zadokowany, ta metoda nie działa.  
  
##  <a name="setautohidemode"></a>CBaseTabbedPane::SetAutoHideMode  
 Ustawia tryb automatyczne ukrywanie okienka odłączane w okienku z kartami.  
  
```  
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bMode`  
 `TRUE`Aby włączyć tryb autoukrywania; `FALSE` Aby włączyć tryb dokowania regularne.  
  
 [in]`dwAlignment`  
 Określa wyrównanie w okienku autoukrywania, który ma być utworzony. Aby uzyskać listę możliwych wartości, zobacz [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).  
  
 [in] [out]`pCurrAutoHideBar`  
 Wskaźnik do bieżącego automatyczne ukrywanie paska narzędzi. Może być `NULL`.  
  
 [in]`bUseTimer`  
 Określa, czy efekt autoukrywania stosować, gdy użytkownik zmienia okienku na tryb autoukrywania lub ukrywanie okienka natychmiast.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do narzędzi autoukrywania, który jest tworzony podczas przełączania do trybu autoukrywania lub `NULL` narzędzi nie zostanie utworzony.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tej metody, gdy użytkownik wybierze przycisk numeru pin, aby przełączyć okienko z kartami tryb autoukrywania lub regularnych tryb dokowania.  
  
 Tryb autoukrywania jest ustawiony dla każdego odłączane okienka w okienku z kartami. Okienka, które są niemożliwe do odłączenia są ignorowane. Aby uzyskać więcej informacji, zobacz [CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).  
  
 Wywołanie tej metody, aby włączyć tryb automatyczne ukrywanie okienka z kartami programowo. Okienko musi być zadokowane do głównego okna ramowego ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) musi zwracać prawidłowy wskaźnik do [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)
