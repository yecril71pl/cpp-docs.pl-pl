---
title: Klasa COleControlContainer | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleControlContainer
- AFXOCC/COleControlContainer
- AFXOCC/COleControlContainer::COleControlContainer
- AFXOCC/COleControlContainer::AttachControlSite
- AFXOCC/COleControlContainer::BroadcastAmbientPropertyChange
- AFXOCC/COleControlContainer::CheckDlgButton
- AFXOCC/COleControlContainer::CheckRadioButton
- AFXOCC/COleControlContainer::CreateControl
- AFXOCC/COleControlContainer::CreateOleFont
- AFXOCC/COleControlContainer::FindItem
- AFXOCC/COleControlContainer::FreezeAllEvents
- AFXOCC/COleControlContainer::GetAmbientProp
- AFXOCC/COleControlContainer::GetDlgItem
- AFXOCC/COleControlContainer::GetDlgItemInt
- AFXOCC/COleControlContainer::GetDlgItemText
- AFXOCC/COleControlContainer::HandleSetFocus
- AFXOCC/COleControlContainer::HandleWindowlessMessage
- AFXOCC/COleControlContainer::IsDlgButtonChecked
- AFXOCC/COleControlContainer::OnPaint
- AFXOCC/COleControlContainer::OnUIActivate
- AFXOCC/COleControlContainer::OnUIDeactivate
- AFXOCC/COleControlContainer::ScrollChildren
- AFXOCC/COleControlContainer::SendDlgItemMessage
- AFXOCC/COleControlContainer::SetDlgItemInt
- AFXOCC/COleControlContainer::SetDlgItemText
- AFXOCC/COleControlContainer::m_crBack
- AFXOCC/COleControlContainer::m_crFore
- AFXOCC/COleControlContainer::m_listSitesOrWnds
- AFXOCC/COleControlContainer::m_nWindowlessControls
- AFXOCC/COleControlContainer::m_pOleFont
- AFXOCC/COleControlContainer::m_pSiteCapture
- AFXOCC/COleControlContainer::m_pSiteFocus
- AFXOCC/COleControlContainer::m_pSiteUIActive
- AFXOCC/COleControlContainer::m_pWnd
- AFXOCC/COleControlContainer::m_siteMap
dev_langs:
- C++
helpviewer_keywords:
- COleControlContainer [MFC], COleControlContainer
- COleControlContainer [MFC], AttachControlSite
- COleControlContainer [MFC], BroadcastAmbientPropertyChange
- COleControlContainer [MFC], CheckDlgButton
- COleControlContainer [MFC], CheckRadioButton
- COleControlContainer [MFC], CreateControl
- COleControlContainer [MFC], CreateOleFont
- COleControlContainer [MFC], FindItem
- COleControlContainer [MFC], FreezeAllEvents
- COleControlContainer [MFC], GetAmbientProp
- COleControlContainer [MFC], GetDlgItem
- COleControlContainer [MFC], GetDlgItemInt
- COleControlContainer [MFC], GetDlgItemText
- COleControlContainer [MFC], HandleSetFocus
- COleControlContainer [MFC], HandleWindowlessMessage
- COleControlContainer [MFC], IsDlgButtonChecked
- COleControlContainer [MFC], OnPaint
- COleControlContainer [MFC], OnUIActivate
- COleControlContainer [MFC], OnUIDeactivate
- COleControlContainer [MFC], ScrollChildren
- COleControlContainer [MFC], SendDlgItemMessage
- COleControlContainer [MFC], SetDlgItemInt
- COleControlContainer [MFC], SetDlgItemText
- COleControlContainer [MFC], m_crBack
- COleControlContainer [MFC], m_crFore
- COleControlContainer [MFC], m_listSitesOrWnds
- COleControlContainer [MFC], m_nWindowlessControls
- COleControlContainer [MFC], m_pOleFont
- COleControlContainer [MFC], m_pSiteCapture
- COleControlContainer [MFC], m_pSiteFocus
- COleControlContainer [MFC], m_pSiteUIActive
- COleControlContainer [MFC], m_pWnd
- COleControlContainer [MFC], m_siteMap
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6d04faa904eba416b290515e5e6773ac6ef9837
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="colecontrolcontainer-class"></a>Klasa COleControlContainer
Działa jako kontener kontroli dla formantów ActiveX.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleControlContainer : public CCmdTarget  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|Konstruuje `COleControlContainer` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Tworzy witrynę kontroli, obsługiwanych przez kontener.|  
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informuje o hostowanej wszystkie formanty, które zmieniono właściwość otoczenia.|  
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Modyfikuje kontroli określonego przycisku.|  
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Wybiera przycisk radiowy określonej grupy.|  
|[COleControlContainer::CreateControl](#createcontrol)|Tworzy obsługiwanego formantu ActiveX.|  
|[COleControlContainer::CreateOleFont](#createolefont)|Tworzy czcionkę OLE.|  
|[COleControlContainer::FindItem](#finditem)|Zwraca niestandardową witrynę określonego formantu.|  
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Określa, czy kontroli lokacji akceptuje zdarzenia.|  
|[COleControlContainer::GetAmbientProp](#getambientprop)|Pobiera określona właściwość otoczenia.|  
|[COleControlContainer::GetDlgItem](#getdlgitem)|Pobiera formant określonego okna dialogowego.|  
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Pobiera wartość określonego okna dialogowego formantu.|  
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Pobiera Podpis formantu określonego okna dialogowego.|  
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Określa, czy kontener obsługuje `WM_SETFOCUS` wiadomości.|  
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Obsługuje komunikatów wysyłanych z formantem bez okien.|  
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Określa stan określonego przycisku.|  
|[COleControlContainer::OnPaint](#onpaint)|Wywoływane w celu odświeżenia część kontenera.|  
|[COleControlContainer::OnUIActivate](#onuiactivate)|Wywoływane, gdy formant ma być aktywowana w miejscu.|  
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Wywoływane, gdy formant ma być dezaktywowane.|  
|[COleControlContainer::ScrollChildren](#scrollchildren)|Wywoływane przez platformę, gdy przewijania komunikaty są odbierane z okna podrzędnego.|  
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Wysyła komunikat do określonego formantu.|  
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Ustawia wartość określonego formantu.|  
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Ustawia tekst określonego formantu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleControlContainer::m_crBack](#m_crback)|Kolor tła kontenera.|  
|[COleControlContainer::m_crFore](#m_crfore)|Kolor pierwszego planu kontenera.|  
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Listę obsługiwanych kontroli lokacji.|  
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|Liczba obsługiwanych kontrolek bez okien.|  
|[COleControlContainer::m_pOleFont](#m_polefont)|Wskaźnik do czcionki OLE witryny kontrolki niestandardowej.|  
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Wskaźnik do przechwytywania kontroli lokacji.|  
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Wskaźnik do formantu, który aktualnie ma fokus wprowadzania.|  
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Wskaźnik do formantu, który jest obecnie w miejscu aktywowany.|  
|[COleControlContainer::m_pWnd](#m_pwnd)|Wskaźnik do okna wykonania formantu kontenera.|  
|[COleControlContainer::m_siteMap](#m_sitemap)|Mapy witryny.|  
  
## <a name="remarks"></a>Uwagi  
 Jest to zrobić przez zapewnienie wsparcia dla przynajmniej jednej lokacji formantu ActiveX (implementowane przez `COleControlSite`). `COleControlContainer`implementuje w pełni [IOleInPlaceFrame](http://msdn.microsoft.com/library/windows/desktop/ms692770) i [IOleContainer](http://msdn.microsoft.com/library/windows/desktop/ms690103) interfejsów, dzięki czemu zawartych w niej formantów ActiveX do zrealizowania ich kwalifikacji jako elementy w miejscu.  
  
 Zazwyczaj ta klasa jest używana w połączeniu z `COccManager` i `COleControlSite` do zaimplementowania niestandardowego kontenera formantu ActiveX, z niestandardowych witryn dla jednego lub kilku formantów ActiveX.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlContainer`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxocc.h  
  
##  <a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite  
 Wywoływane przez platformę, by Utwórz i Dołącz kontroli lokacji.  
  
```  
virtual void AttachControlSite(
    CWnd* pWnd,  
    UINT nIDC = 0);

 
void AttachControlSite(
    CWnd* pWnd,  
    UINT nIDC = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do `CWnd` obiektu.  
  
 `nIDC`  
 Identyfikator formantu jest dołączony.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, jeśli chcesz dostosować ten proces.  
  
> [!NOTE]
>  Formularz pierwszy tej funkcji statycznie łączenia biblioteki MFC. Drugi formularz dynamicznie łączenia biblioteki MFC.  
  
##  <a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange  
 Informuje o hostowanej wszystkie formanty, które zmieniono właściwość otoczenia.  
  
```  
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="parameters"></a>Parametry  
 `dispid`  
 Identyfikator wysyłania właściwość otoczenia zmieniane.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana przez platformę, gdy zmieniono właściwość zostanie zmieniona wartość. Przesłonić tę funkcję, aby dostosować ten problem.  
  
##  <a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton  
 Zmienia bieżący stan przycisku.  
  
```  
virtual void CheckDlgButton(
    int nIDButton,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDButton`  
 Identyfikator przycisku do zmodyfikowania.  
  
 `nCheck`  
 Określa stan przycisku. Może to być jedna z następujących czynności:  
  
- **BST_CHECKED** ustawia stan przycisku do zaznaczenia.  
  
- **BST_INDETERMINATE** ustawia stan przycisku na wygaszone, wskazując dla niego stan nieokreślony. Użyj tej wartości, tylko wtedy, gdy przycisk **bs_3state —** lub **bs_auto3state —** stylu.  
  
- **BST_UNCHECKED** ustawia stan przycisku wyczyszczone.  
  
##  <a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton  
 Wybranie przycisku radiowego określony w grupie i czyści pozostałych przycisków w grupie.  
  
```  
virtual void CheckRadioButton(
    int nIDFirstButton,  
    int nIDLastButton,  
    int nIDCheckButton);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDFirstButton`  
 Określa identyfikator pierwszego przycisku radiowego w grupie.  
  
 `nIDLastButton`  
 Określa identyfikator ostatniego przycisku radiowego w grupie.  
  
 `nIDCheckButton`  
 Określa identyfikator przycisku radiowego jest sprawdzane.  
  
##  <a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer  
 Konstruuje `COleControlContainer` obiektu.  
  
```  
explicit COleControlContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do okna nadrzędnego formantu kontenera.  
  
### <a name="remarks"></a>Uwagi  
 Po pomyślnym utworzeniu obiekt dodać witrynę formant niestandardowy z wywołaniem do `AttachControlSite`.  
  
##  <a name="createcontrol"></a>COleControlContainer::CreateControl  
 Tworzy formantu ActiveX, obsługiwanych przez określony `COleControlSite` obiektu.  
  
```  
BOOL CreateControl(
    CWnd* pWndCtrl,  
    REFCLSID clsid,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    UINT nID,  
    CFile* pPersist =NULL,  
    BOOL bStorage =FALSE,  
    BSTR bstrLicKey =NULL,  
    COleControlSite** ppNewSite =NULL);

 
BOOL CreateControl(
    CWnd* pWndCtrl,  
    REFCLSID clsid,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const POINT* ppt,  
    const SIZE* psize,  
    UINT nID,  
    CFile* pPersist =NULL,  
    BOOL bStorage =FALSE,  
    BSTR bstrLicKey =NULL,  
    COleControlSite** ppNewSite =NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndCtrl`  
 Wskaźnik do obiekt window reprezentujący formantu.  
  
 `clsid`  
 Identyfikator unikatowy klasy formantu.  
  
 `lpszWindowName`  
 Wskaźnik do tekstu wyświetlanego w formancie. Ustawia wartości właściwości podpisu lub tekst formantu (jeśli istnieje). Jeśli **NULL**, właściwości podpisu lub tekst formantu nie ulega zmianie.  
  
 `dwStyle`  
 Style systemu Windows. Dostępne style są wyświetlane w obszarze **uwagi** sekcji.  
  
 `rect`  
 Określa rozmiar i położenie formantu. Może być albo `CRect` obiektu lub `RECT` struktury.  
  
 `nID`  
 Określa identyfikator formantu podrzędnego okna.  
  
 `pPersist`  
 Wskaźnik do `CFile` zawierający trwały stan formantu. Wartość domyślna to **NULL**, wskazującą, czy formant inicjuje się bez przywracania stanu z dowolnego magazynu trwałego. Jeśli nie **NULL**, powinny być wskaźnikiem do `CFile`-pochodnych obiekt, który zawiera trwałych danych formantu w postaci strumienia lub magazynu. Można te dane zostały zapisane w poprzednim aktywacji klienta. `CFile` Może zawierać innych danych, lecz musi mieć jego wskaźnika odczytu i zapisu, ustaw do pierwszego bajtu trwałych danych w momencie wywołania `CreateControl`.  
  
 `bStorage`  
 Wskazuje, czy dane w `pPersist` powinny być rozumiane jako `IStorage` lub `IStream` danych. Jeśli dane w `pPersist` magazynu, `bStorage` powinien być **TRUE**. Jeśli dane w `pPersist` jest typu stream, `bStorage` powinien być **FALSE**. Wartość domyślna to **FALSE**.  
  
 `bstrLicKey`  
 Opcjonalne dane klucza licencji. Tych danych jest konieczne tylko w przypadku tworzenia formantów, które wymagają klucz licencji środowiska wykonawczego. Jeśli formant obsługuje licencjonowania, należy podać klucz licencji w celu utworzenia kontrolki została wykonana pomyślnie. Wartość domyślna to **NULL**.  
  
 *ppNewSite*  
 Wskaźnik do istniejącej lokacji kontroli obsługującym kontrolka tworzona. Wartość domyślna to **NULL**, wskazujący, że nowej lokacji sterowania zostanie automatycznie utworzona i dołączony do nowego formantu.  
  
 `ppt`  
 Wskaźnik do **punktu** struktury, która zawiera górnego lewego rogu formantu. Rozmiar formantu jest określana przez wartość *psize*. `ppt` i *psize* wartości są opcjonalne metodę określania rozmiaru i pozycji formantu.  
  
 *psize*  
 Wskaźnik do **rozmiar** struktury, która zawiera rozmiar formantu. Lewy górny róg jest określana przez wartość `ppt`. `ppt` i *psize* wartości są opcjonalne metodę określania rozmiaru i pozycji formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Tylko podzestaw systemu Windows `dwStyle` flagi są obsługiwane przez `CreateControl`:  
  
- **Ws_visible —** tworzy okna, które jest początkowo widoczne. Wymagane, jeśli formantu ma być widoczna od razu, takich jak zwykłe systemu windows.  
  
- **Ws_disabled —** tworzy okno, które jest początkowo wyłączone. Wyłączone okna nie mogą otrzymywać dane wejściowe użytkownika. Można ustawić, jeśli formant ma właściwość Enabled.  
  
- `WS_BORDER`Tworzy okno z elastycznej linii obramowania. Można ustawić, jeśli formant ma właściwości BorderStyle.  
  
- **Ws_group —** Określa pierwszą kontrolkę grupy formantów. Użytkownik może zmienić fokus klawiatury z jednego formantu w grupie do następnego przy użyciu kluczy kierunku. Wszystkie formanty zdefiniowane z **ws_group —** styl po pierwszą kontrolkę należą do tej samej grupy. Następnego formantu z **ws_group —** styl kończy się grupie i uruchamia następnej grupy.  
  
- **Ws_tabstop —** Określa formant może przyjmować fokus klawiatury, gdy użytkownik naciśnie klawisz TAB. Naciśnięcie klawisza TAB zmienia fokus klawiatury do następnej kontrolki z **ws_tabstop —** stylu.  
  
 Drugi przeciążenie umożliwia tworzenie formantów o rozmiarze domyślnym.  
  
##  <a name="createolefont"></a>COleControlContainer::CreateOleFont  
 Tworzy czcionkę OLE.  
  
```  
void CreateOleFont(CFont* pFont);
```  
  
### <a name="parameters"></a>Parametry  
 `pFont`  
 Wskaźnik do czcionki do użycia przez kontener formantu.  
  
##  <a name="finditem"></a>COleControlContainer::FindItem  
 Umożliwia znalezienie niestandardowej witryny, który jest hostem określonego elementu.  
  
```  
virtual COleControlSite* FindItem(UINT nID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identyfikator elementu, który ma zostać odnaleziona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do niestandardowej witryny określonego elementu.  
  
##  <a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents  
 Określa Jeśli kontener będzie Ignoruj zdarzenia z witryn dołączone kontroli lub je zaakceptować.  
  
```  
void FreezeAllEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>Parametry  
 `bFreeze`  
 Różna od zera, jeśli zdarzenia zostaną przetworzone; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Formant nie jest wymagane do zatrzymania wyzwalania zdarzenia żądanie kontenera formantu. Można kontynuować uruchamiania, ale wszystkie kolejne zdarzenia zostaną zignorowane przez kontener formantu.  
  
##  <a name="getambientprop"></a>COleControlContainer::GetAmbientProp  
 Pobiera wartość określonej właściwości otoczenia.  
  
```  
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,  
    DISPID dispid,  
    VARIANT* pvarResult);
```  
  
### <a name="parameters"></a>Parametry  
 `pSite`  
 Wskaźnik do lokacji formantu, z którego będzie można pobrać właściwości otoczenia.  
  
 `dispid`  
 Identyfikator wysyłania żądanej właściwości otoczenia.  
  
 *pVarResult*  
 Wskaźnik do wartości właściwości otoczenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
##  <a name="getdlgitem"></a>COleControlContainer::GetDlgItem  
 Pobiera wskaźnik do określonego formantu podrzędnego okna lub w oknie dialogowym lub inne okna.  
  
```  
virtual CWnd* GetDlgItem(int nID) const;  
  
virtual void GetDlgItem(
    int nID,  
    HWND* phWnd) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identyfikator elementu okna dialogowego do pobrania.  
  
 `phWnd`  
 Wskaźnik do uchwytu elementu okna dialogowego określony obiekt window.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do elementu okna dialogowego okna.  
  
##  <a name="getdlgitemint"></a>COleControlContainer::GetDlgItemInt  
 Pobiera wartość tłumaczenia danego formantu.  
  
```  
virtual UINT GetDlgItemInt(
    int nID,  
    BOOL* lpTrans,  
    BOOL bSigned) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identyfikator formantu.  
  
 `lpTrans`  
 Wskaźnik do zmiennej typu Boolean, który odbiera wartość powodzeń/niepowodzeń funkcji ( **TRUE** oznacza Powodzenie, **FALSE** wskazuje niepowodzenie).  
  
 `bSigned`  
 Określa, czy funkcja należy zbadać tekst znakiem minus na początku i zwraca wartość liczby całkowitej ze znakiem, jeśli zostanie znaleziony. Jeśli `bSigned` parametr jest **TRUE**, określając, że wartość do pobrania jest wartość całkowita rzutowania wartości zwracanej do `int` typu. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli się powiedzie, zmienna wskazywana przez `lpTrans` ma ustawioną wartość **TRUE**, i wartość zwracana jest wartość przetłumaczonego tekstu formantu.  
  
 W przypadku niepowodzenia funkcji zmiennej wskazywana przez `lpTrans` ustawiono **FALSE**, i wartość zwracana jest wartość zero. Należy pamiętać, że od zera jest możliwa wartość przetłumaczonego, zwracana wartość zero nie samodzielnie wskazania błędu.  
  
 Jeśli `lpTrans` jest **NULL**, funkcja zwraca żadnych informacji o powodzeniu lub niepowodzeniu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja tłumaczy tekst pobrane przez usuwanie dodatkowe spacje na początku tekstu, a następnie konwertując cyfr dziesiętnych. Funkcja zatrzymuje tłumaczenia, gdy osiągnie koniec tekstu lub napotka liczbą znaków.  
  
 Ta funkcja zwraca zero, jeśli przetłumaczonego wartość jest większa niż **int_max —** (dla podpisane cyfry) lub **uint_max —** (dla numerów bez znaku).  
  
##  <a name="getdlgitemtext"></a>COleControlContainer::GetDlgItemText  
 Pobiera tekst danego formantu.  
  
```  
virtual int GetDlgItemText(
    int nID,  
    LPTSTR lpStr,  
    int nMaxCount) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identyfikator formantu.  
  
 `lpStr`  
 Wskaźnik do tekst formantu.  
  
 `nMaxCount`  
 Określa maksymalną długość w znakach ciąg, który ma zostać skopiowany na bufor wskazywany przez `lpStr`. Jeśli długość ciągu przekracza limit, ciąg został obcięty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, zwracana wartość określa liczbę znaków kopiowania do buforu, nie włączając znak końcowy null.  
  
 Jeśli funkcja nie powiedzie się, zwracana wartość wynosi zero. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
##  <a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus  
 Określa, czy kontener obsługuje `WM_SETFOCUS` wiadomości.  
  
```  
virtual BOOL HandleSetFocus();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli kontener obsługuje `WM_SETFOCUS` wiadomości; w przeciwnym razie wartość zero.  
  
##  <a name="handlewindowlessmessage"></a>COleControlContainer::HandleWindowlessMessage  
 Przetwarza komunikatów okien kontrolek bez okien.  
  
```  
virtual BOOL HandleWindowlessMessage(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam,  
    LRESULT* plResult);
```  
  
### <a name="parameters"></a>Parametry  
 `message`  
 Identyfikator komunikatu w oknie, dostarczonymi przez system Windows.  
  
 `wParam`  
 Parametr message; dostępna w systemie Windows. Określa dodatkowe informacje specyficzne dla wiadomości. Zawartość tego parametru zależy od wartości `message` parametru.  
  
 `lParam`  
 Parametr message; dostępna w systemie Windows. Określa dodatkowe informacje specyficzne dla wiadomości. Zawartość tego parametru zależy od wartości `message` parametru.  
  
 *plResult*  
 Kod wyniku systemu Windows. Określa wynik przetwarzania komunikatów i jest zależna od wiadomość została wysłana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, aby dostosować obsługi komunikatów formantu bez okien.  
  
##  <a name="isdlgbuttonchecked"></a>COleControlContainer::IsDlgButtonChecked  
 Określa stan określonego przycisku.  
  
```  
virtual UINT IsDlgButtonChecked(int nIDButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIDButton`  
 Identyfikator formantu przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość zwrotną z elementu utworzone za pomocą przycisku **bs_autocheckbox —**, **bs_autoradiobutton —**, **bs_auto3state —**, **bs_checkbox —**, **Bs_radiobutton —**, lub **bs_3state —** stylu. Może to być jedna z następujących czynności:  
  
- **BST_CHECKED** przycisk jest zaznaczony.  
  
- **BST_INDETERMINATE** przycisk jest niedostępny, wskazując dla niego stan nieokreślony (ma zastosowanie tylko wtedy, gdy przycisk **bs_3state —** lub **bs_auto3state —** styl).  
  
- **BST_UNCHECKED** przycisku jest wyczyszczone.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli przycisk jest trójstanowy, funkcja członkowska Określa, czy jego jest wygaszone, zaznaczone, albo nie.  
  
##  <a name="m_crback"></a>COleControlContainer::m_crBack  
 Kolor tła kontenera.  
  
```  
COLORREF m_crBack;  
```  
  
##  <a name="m_crfore"></a>COleControlContainer::m_crFore  
 Kolor pierwszego planu kontenera.  
  
```  
COLORREF m_crFore;  
```  
  
##  <a name="m_listsitesorwnds"></a>COleControlContainer::m_listSitesOrWnds  
 Lista witryn kontroli, obsługiwanych przez kontener.  
  
```  
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;  
```  
  
##  <a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls  
 Liczba obsługiwanych przez kontener formantu kontrolek bez okien.  
  
```  
int m_nWindowlessControls;  
```  
  
##  <a name="m_polefont"></a>COleControlContainer::m_pOleFont  
 Wskaźnik do czcionki OLE witryny kontrolki niestandardowej.  
  
```  
LPFONTDISP m_pOleFont;  
```  
  
##  <a name="m_psitecapture"></a>COleControlContainer::m_pSiteCapture  
 Wskaźnik do przechwytywania kontroli lokacji.  
  
```  
COleControlSite* m_pSiteCapture;  
```  
  
##  <a name="m_psitefocus"></a>COleControlContainer::m_pSiteFocus  
 Wskaźnik do lokacji formant, który aktualnie ma fokus wprowadzania.  
  
```  
COleControlSite* m_pSiteFocus;  
```  
  
##  <a name="m_psiteuiactive"></a>COleControlContainer::m_pSiteUIActive  
 Wskaźnik do lokacji formant, który jest aktywowana w miejscu.  
  
```  
COleControlSite* m_pSiteUIActive;  
```  
  
##  <a name="m_pwnd"></a>COleControlContainer::m_pWnd  
 Wskaźnik do obiektu okna skojarzony z kontenerem.  
  
```  
CWnd* m_pWnd;  
```  
  
##  <a name="m_sitemap"></a>COleControlContainer::m_siteMap  
 Mapy witryny.  
  
```  
CMapPtrToPtr m_siteMap;  
```  
  
##  <a name="onpaint"></a>COleControlContainer::OnPaint  
 Wywoływane przez platformę, by obsłużyć `WM_PAINT` żądań.  
  
```  
virtual BOOL OnPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskaźnik do kontekstu urządzenia używane przez kontener.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli komunikat został obsłużony; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji w celu dostosowania procesu malowania.  
  
##  <a name="onuiactivate"></a>COleControlContainer::OnUIActivate  
 Wywoływane przez platformę, gdy lokacji kontroli wskazywana przez `pSite`, ma być aktywowana w miejscu.  
  
```  
virtual void OnUIActivate(COleControlSite* pSite);
```  
  
### <a name="parameters"></a>Parametry  
 `pSite`  
 Wskaźnik do sterowania lokacji zostanie aktywowana w miejscu.  
  
### <a name="remarks"></a>Uwagi  
 Aktywacja w miejscu oznacza kontenera menu główne zostanie zastąpiony w miejscu złożone menu.  
  
##  <a name="onuideactivate"></a>COleControlContainer::OnUIDeactivate  
 Wywoływane przez platformę, gdy lokacji kontroli wskazywana przez `pSite`, ma być dezaktywowane.  
  
```  
virtual void OnUIDeactivate(COleControlSite* pSite);
```  
  
### <a name="parameters"></a>Parametry  
 `pSite`  
 Wskaźnik do sterowania lokacji o dezaktywowane.  
  
### <a name="remarks"></a>Uwagi  
 Po odebraniu tego powiadomienia kontenera należy ponownie zainstalować interfejs użytkownika i przyjąć fokusu.  
  
##  <a name="scrollchildren"></a>COleControlContainer::ScrollChildren  
 Wywoływane przez platformę, gdy przewijania komunikaty są odbierane z okna podrzędnego.  
  
```  
virtual void ScrollChildren(
    int dx,  
    int dy);
```  
  
### <a name="parameters"></a>Parametry  
 `dx`  
 Wielkość, wyrażoną w pikselach przewijanie wzdłuż osi x.  
  
 *dy*  
 Wielkość, wyrażoną w pikselach przewijanie wzdłuż osi y.  
  
##  <a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage  
 Wysyła komunikat do określonego formantu.  
  
```  
virtual LRESULT SendDlgItemMessage(
    int nID,  
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Określa identyfikator formantu, który odbiera wiadomości.  
  
 `message`  
 Określa komunikat do wysłania.  
  
 `wParam`  
 Określa dodatkowe informacje specyficzne dla wiadomości.  
  
 `lParam`  
 Określa dodatkowe informacje specyficzne dla wiadomości.  
  
##  <a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt  
 Ustawia tekst formantu w oknie dialogowym do reprezentację ciągu określonej liczby całkowitej.  
  
```  
virtual void SetDlgItemInt(
    int nID,  
    UINT nValue,  
    BOOL bSigned);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identyfikator formantu.  
  
 `nValue`  
 Wartość całkowita, która ma być wyświetlany.  
  
 `bSigned`  
 Określa, czy `nValue` parametr został podpisany ani bez znaku. Jeśli ten parametr ma **TRUE**, `nValue` jest podpisany. Jeśli ten parametr ma **TRUE** i `nValue` jest mniejsza od zera, minus znak jest umieszczony przed pierwszą cyfrą w ciągu. Jeśli ten parametr ma **FALSE**, `nValue` nie jest podpisany.  
  
##  <a name="setdlgitemtext"></a>COleControlContainer::SetDlgItemText  
 Ustawia tekst określony formant przy użyciu tekstu zawartych w `lpszString`.  
  
```  
virtual void SetDlgItemText(
    int nID,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identyfikator formantu.  
  
 `lpszString`  
 Wskaźnik do tekst formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleControlSite](../../mfc/reference/colecontrolsite-class.md)   
 [Klasa COccManager](../../mfc/reference/coccmanager-class.md)
