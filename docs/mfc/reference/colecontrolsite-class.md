---
title: Klasa COleControlSite | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleControlSite
- AFXOCC/COleControlSite
- AFXOCC/COleControlSite::COleControlSite
- AFXOCC/COleControlSite::BindDefaultProperty
- AFXOCC/COleControlSite::BindProperty
- AFXOCC/COleControlSite::CreateControl
- AFXOCC/COleControlSite::DestroyControl
- AFXOCC/COleControlSite::DoVerb
- AFXOCC/COleControlSite::EnableDSC
- AFXOCC/COleControlSite::EnableWindow
- AFXOCC/COleControlSite::FreezeEvents
- AFXOCC/COleControlSite::GetDefBtnCode
- AFXOCC/COleControlSite::GetDlgCtrlID
- AFXOCC/COleControlSite::GetEventIID
- AFXOCC/COleControlSite::GetExStyle
- AFXOCC/COleControlSite::GetProperty
- AFXOCC/COleControlSite::GetStyle
- AFXOCC/COleControlSite::GetWindowText
- AFXOCC/COleControlSite::InvokeHelper
- AFXOCC/COleControlSite::InvokeHelperV
- AFXOCC/COleControlSite::IsDefaultButton
- AFXOCC/COleControlSite::IsWindowEnabled
- AFXOCC/COleControlSite::ModifyStyle
- AFXOCC/COleControlSite::ModifyStyleEx
- AFXOCC/COleControlSite::MoveWindow
- AFXOCC/COleControlSite::QuickActivate
- AFXOCC/COleControlSite::SafeSetProperty
- AFXOCC/COleControlSite::SetDefaultButton
- AFXOCC/COleControlSite::SetDlgCtrlID
- AFXOCC/COleControlSite::SetFocus
- AFXOCC/COleControlSite::SetProperty
- AFXOCC/COleControlSite::SetPropertyV
- AFXOCC/COleControlSite::SetWindowPos
- AFXOCC/COleControlSite::SetWindowText
- AFXOCC/COleControlSite::ShowWindow
- AFXOCC/COleControlSite::GetControlInfo
- AFXOCC/COleControlSite::m_bIsWindowless
- AFXOCC/COleControlSite::m_ctlInfo
- AFXOCC/COleControlSite::m_dwEventSink
- AFXOCC/COleControlSite::m_dwMiscStatus
- AFXOCC/COleControlSite::m_dwPropNotifySink
- AFXOCC/COleControlSite::m_dwStyle
- AFXOCC/COleControlSite::m_hWnd
- AFXOCC/COleControlSite::m_iidEvents
- AFXOCC/COleControlSite::m_nID
- AFXOCC/COleControlSite::m_pActiveObject
- AFXOCC/COleControlSite::m_pCtrlCont
- AFXOCC/COleControlSite::m_pInPlaceObject
- AFXOCC/COleControlSite::m_pObject
- AFXOCC/COleControlSite::m_pWindowlessObject
- AFXOCC/COleControlSite::m_pWndCtrl
- AFXOCC/COleControlSite::m_rect
dev_langs:
- C++
helpviewer_keywords:
- COleControlSite [MFC], COleControlSite
- COleControlSite [MFC], BindDefaultProperty
- COleControlSite [MFC], BindProperty
- COleControlSite [MFC], CreateControl
- COleControlSite [MFC], DestroyControl
- COleControlSite [MFC], DoVerb
- COleControlSite [MFC], EnableDSC
- COleControlSite [MFC], EnableWindow
- COleControlSite [MFC], FreezeEvents
- COleControlSite [MFC], GetDefBtnCode
- COleControlSite [MFC], GetDlgCtrlID
- COleControlSite [MFC], GetEventIID
- COleControlSite [MFC], GetExStyle
- COleControlSite [MFC], GetProperty
- COleControlSite [MFC], GetStyle
- COleControlSite [MFC], GetWindowText
- COleControlSite [MFC], InvokeHelper
- COleControlSite [MFC], InvokeHelperV
- COleControlSite [MFC], IsDefaultButton
- COleControlSite [MFC], IsWindowEnabled
- COleControlSite [MFC], ModifyStyle
- COleControlSite [MFC], ModifyStyleEx
- COleControlSite [MFC], MoveWindow
- COleControlSite [MFC], QuickActivate
- COleControlSite [MFC], SafeSetProperty
- COleControlSite [MFC], SetDefaultButton
- COleControlSite [MFC], SetDlgCtrlID
- COleControlSite [MFC], SetFocus
- COleControlSite [MFC], SetProperty
- COleControlSite [MFC], SetPropertyV
- COleControlSite [MFC], SetWindowPos
- COleControlSite [MFC], SetWindowText
- COleControlSite [MFC], ShowWindow
- COleControlSite [MFC], GetControlInfo
- COleControlSite [MFC], m_bIsWindowless
- COleControlSite [MFC], m_ctlInfo
- COleControlSite [MFC], m_dwEventSink
- COleControlSite [MFC], m_dwMiscStatus
- COleControlSite [MFC], m_dwPropNotifySink
- COleControlSite [MFC], m_dwStyle
- COleControlSite [MFC], m_hWnd
- COleControlSite [MFC], m_iidEvents
- COleControlSite [MFC], m_nID
- COleControlSite [MFC], m_pActiveObject
- COleControlSite [MFC], m_pCtrlCont
- COleControlSite [MFC], m_pInPlaceObject
- COleControlSite [MFC], m_pObject
- COleControlSite [MFC], m_pWindowlessObject
- COleControlSite [MFC], m_pWndCtrl
- COleControlSite [MFC], m_rect
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c6f84f575edbcaf8ecc64f424f3225d969d6a7f
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850358"
---
# <a name="colecontrolsite-class"></a>Klasa COleControlSite
Zapewnia obsługę interfejsów kontrolki niestandardowej po stronie klienta.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleControlSite : public CCmdTarget  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleControlSite::COleControlSite](#colecontrolsite)|Konstruuje `COleControlSite` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|Wiąże domyślną właściwość hostowanej formant ze źródłem danych.|  
|[COleControlSite::BindProperty](#bindproperty)|Tworzy powiązanie z właściwością kontrolki hostowanej ze źródłem danych.|  
|[COleControlSite::CreateControl](#createcontrol)|Tworzy formant ActiveX hostowanej.|  
|[COleControlSite::DestroyControl](#destroycontrol)|Niszczy obsługiwanego formantu.|  
|[COleControlSite::DoVerb](#doverb)|Wykonuje określone zlecenie obsługiwanego formantu.|  
|[COleControlSite::EnableDSC](#enabledsc)|Umożliwia określanie źródła dla witryny kontroli danych.|  
|[COleControlSite::EnableWindow](#enablewindow)|Umożliwia kontroli lokacji.|  
|[COleControlSite::FreezeEvents](#freezeevents)|Określa, jeśli witryna kontroli akceptuje zdarzenia.|  
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Pobiera domyślny kod obsługiwanego formantu przycisku.|  
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Pobiera identyfikator kontrolki.|  
|[COleControlSite::GetEventIID](#geteventiid)|Pobiera identyfikator interfejs zdarzenie dla obsługiwanego formantu.|  
|[COleControlSite::GetExStyle](#getexstyle)|Pobiera rozszerzone style kontroli lokacji.|  
|[COleControlSite::GetProperty](#getproperty)|Pobiera określoną właściwością kontrolki hostowanej.|  
|[COleControlSite::GetStyle](#getstyle)|Pobiera style kontroli lokacji.|  
|[COleControlSite::GetWindowText](#getwindowtext)|Pobiera tekst hostowanej formantu.|  
|[COleControlSite::InvokeHelper](#invokehelper)|Wywoływanie metody określonego obsługiwanego formantu.|  
|[COleControlSite::InvokeHelperV](#invokehelperv)|Wywoływanie metody określonego obsługiwanego formantu przy użyciu listy zmiennych argumentów.|  
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|Określa, czy kontrolka jest przycisk domyślny w oknie.|  
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|Sprawdza, czy wyświetlany stan kontroli lokacji.|  
|[COleControlSite::ModifyStyle](#modifystyle)|Modyfikuje bieżącego rozszerzone style kontroli lokacji.|  
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Modyfikuje style bieżącego kontroli lokacji.|  
|[COleControlSite::MoveWindow](#movewindow)|Zmienia położenie obiektu formantu.|  
|[COleControlSite::QuickActivate](#quickactivate)|Szybkie aktywuje obsługiwanego formantu.|  
|[COleControlSite::SafeSetProperty](#safesetproperty)|Ustawia właściwości lub metody kontroli bez prawdopodobieństwo zostanie zgłoszony wyjątek.|  
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Określa przycisk domyślny w oknie.|  
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Pobiera identyfikator kontrolki.|  
|[COleControlSite::SetFocus](#setfocus)|Ustawia fokus do kontroli lokacji.|  
|[COleControlSite::SetProperty](#setproperty)|Ustawia określoną właściwością kontrolki hostowanej.|  
|[COleControlSite::SetPropertyV](#setpropertyv)|Ustawia określoną właściwością kontrolki hostowanej przy użyciu listy zmiennych argumentów.|  
|[COleControlSite::SetWindowPos](#setwindowpos)|Ustawia położenie kontroli lokacji.|  
|[COleControlSite::SetWindowText](#setwindowtext)|Ustawia tekst obsługiwanego formantu.|  
|[COleControlSite::ShowWindow](#showwindow)|Pokazuje lub ukrywa kontroli lokacji.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Pobiera informacje o klawiatury i symboli dla obsługiwanego formantu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Określa, czy kontrolka hostowanej kontrolce.|  
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Zawiera informacje na temat formantu za pomocą klawiatury.|  
|[COleControlSite::m_dwEventSink](#m_dweventsink)|Plik cookie punkt połączenia z formantu.|  
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Różne stany dla obsługiwanego formantu.|  
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|`IPropertyNotifySink` Plik cookie formantu.|  
|[COleControlSite::m_dwStyle](#m_dwstyle)|Style formantu hostowanej.|  
|[COleControlSite::m_hWnd](#m_hwnd)|Uchwyt kontroli lokacji.|  
|[COleControlSite::m_iidEvents](#m_iidevents)|Identyfikator interfejsu zdarzenia dla obsługiwanego formantu.|  
|[COleControlSite::m_nID](#m_nid)|Identyfikator obsługiwanego formantu.|  
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|Wskaźnik do `IOleInPlaceActiveObject` obiektu obsługiwanego formantu.|  
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|Kontener obsługiwanego formantu.|  
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|Wskaźnik do `IOleInPlaceObject` obiektu obsługiwanego formantu.|  
|[COleControlSite::m_pObject](#m_pobject)|Wskaźnik do `IOleObjectInterface` interfejsu formantu.|  
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|Wskaźnik do `IOleInPlaceObjectWindowless` interfejsu formantu.|  
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|Wskaźnik do obiektu okna dla kontrolki hostowanej.|  
|[COleControlSite::m_rect](#m_rect)|Wymiary kontroli lokacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest podstawowym elementem używanym za pomocą którego osadzonego formantu ActiveX uzyskuje informacje o lokalizacji i zasięg swojej witryny wyświetlania, jego nazwie, interfejs użytkownika, jego właściwości otoczenia i innych zasobów dostarczanych przez kontener. `COleControlSite` w pełni zaimplementowano [IOleControlSite](http://msdn.microsoft.com/library/windows/desktop/ms688502), [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706), [ipropertynotifysink —](http://msdn.microsoft.com/library/windows/desktop/ms692638), `IBoundObjectSite`, `INotifyDBEvents`, [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md) interfejsów. Ponadto jest również implementowana interfejsu IDispatch (świadczenie pomocy technicznej dla właściwości otoczenia i ujścia zdarzeń).  
  
 Aby utworzyć ActiveX sterowania lokacji za pomocą `COleControlSite`, wyprowadzić klasę z `COleControlSite`. W swojej `CWnd`— zastąpienie klasy pochodnej dla kontenera (na przykład Twoje okno dialogowe) `CWnd::CreateControlSite` funkcji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlSite`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxocc.h  
  
##  <a name="binddefaultproperty"></a>  COleControlSite::BindDefaultProperty  
 Wiąże obiekt wywołujący domyślne proste właściwości powiązanej, jako oznaczony w bibliotece typów do kursora podstawowej, który jest definiowany przez właściwości źródła danych, nazwę użytkownika, hasło i SQL do kontroli źródła danych.  
  
```  
virtual void BindDefaultProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    LPCTSTR szFieldName,  
    CWnd* pDSCWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Określa identyfikator DISPID właściwości kontrolki powiązania danych, który ma zostać powiązany do kontroli źródła danych.  
  
 *vtProp*  
 Określa typ właściwości powiązać — na przykład VT_BSTR, VT_VARIANT i tak dalej.  
  
 *szFieldName*  
 Określa nazwę kolumny, w kursorze dostarczane przez kontrolę źródła danych, do którego będą powiązane właściwości.  
  
 *pDSCWnd*  
 Wskaźnik do `CWnd`-pochodnych obiekt, który hostuje kontroli źródła danych, do którego będą powiązane właściwości.  
  
### <a name="remarks"></a>Uwagi  
 `CWnd` Obiektu, na którym Wywołaj tę funkcję, musi być kontrolki powiązania danych.  
  
##  <a name="bindproperty"></a>  COleControlSite::BindProperty  
 Wiąże obiekt wywołujący powiązanych właściwości prostej, jako oznaczony w bibliotece typów podstawowych kursora, jest definiowana przez właściwości źródła danych, nazwę użytkownika, hasło i SQL do kontroli źródła danych.  
  
```  
virtual void BindProperty(
    DISPID dwDispId,  
    CWnd* pWndDSC);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispId*  
 Określa identyfikator DISPID właściwości kontrolki powiązania danych, który ma zostać powiązany do kontroli źródła danych.  
  
 *pWndDSC*  
 Wskaźnik do `CWnd`-pochodnych obiekt, który hostuje kontroli źródła danych, do którego będą powiązane właściwości.  
  
### <a name="remarks"></a>Uwagi  
 `CWnd` Obiektu, na którym Wywołaj tę funkcję, musi być kontrolki powiązania danych.  
  
##  <a name="colecontrolsite"></a>  COleControlSite::COleControlSite  
 Tworzy nowy `COleControlSite` obiektu.  
  
```  
explicit COleControlSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>Parametry  
 *pCtrlCont*  
 Wskaźnik do kontrolki kontenera, (który reprezentuje okno, które obsługuje formant AtiveX).  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana [COccManager::CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer) funkcji. Aby uzyskać więcej informacji na temat dostosowywania tworzenia kontenerów, zobacz [COccManager::CreateSite](../../mfc/reference/coccmanager-class.md#createsite).  
  
##  <a name="createcontrol"></a>  COleControlSite::CreateControl  
 Tworzy formant ActiveX, hostowane przez `COleControlSite` obiektu.  
  
```  
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,  
    REFCLSID clsid,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    UINT nID,  
    CFile* pPersist = NULL,  
    BOOL bStorage = FALSE,  
    BSTR bstrLicKey = NULL);

 
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,  
    REFCLSID clsid,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const POINT* ppt,  
    const SIZE* psize,  
    UINT nID,  
    CFile* pPersist = NULL,  
    BOOL bStorage = FALSE,  
    BSTR bstrLicKey = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndCtrl*  
 Wskaźnik do obiektu okna, reprezentujący formantu.  
  
 *Identyfikator klasy*  
 Identyfikator unikatowy klasy kontrolki.  
  
 *lpszWindowName*  
 Wskaźnik na tekst, który ma być wyświetlany w formancie. Ustawia wartość właściwości podpisu lub tekst winodw (jeśli istnieje).  
  
 *dwStyle*  
 Style Windows. Dostępne style są wyświetlane w obszarze **uwagi** sekcji.  
  
 *Rect*  
 Określa rozmiar i położenie formantu. Może być albo `CRect` obiektu lub `RECT` struktury.  
  
 *nID*  
 Określa identyfikator. okno podrzędne kontrolki  
  
 *pPersist*  
 Wskaźnik do `CFile` zawierający trwały stan dla formantu. Wartość domyślna to NULL, wskazujący, że kontrolka inicjalizuje bez przywracania stanu z dowolnego magazynu trwałego. Jeśli nie ma wartość NULL, powinna to być wskaźnik do `CFile`-pochodzi obiekt, który zawiera trwałych danych formantu w formie strumienia lub magazynu. Można te dane zostały zapisane w poprzednim aktywacji klienta. `CFile` Może zawierać innych danych, ale musi mieć swojego wskaźnika odczytu i zapisu, ustaw do pierwszego bajtu trwałych danych w czasie wywołania `CreateControl`.  
  
 *bStorage*  
 Wskazuje, czy dane w *pPersist* powinno być interpretowane jako `IStorage` lub `IStream` danych. Jeśli dane w *pPersist* magazynu *bStorage* powinien mieć wartość PRAWDA. Jeśli dane w *pPersist* jest strumieniem, *bStorage* powinna być równa FALSE. Wartość domyślna to FALSE.  
  
 *bstrLicKey*  
 Opcjonalne dane klucza licencji. Tych danych jest konieczne tylko w przypadku tworzenia formantów, które wymagają klucz licencji środowiska wykonawczego. Jeśli są obsługiwane przez kontrolkę licencjonowania, musisz podać klucz licencji do tworzenia kontrolki została wykonana pomyślnie. Wartością domyślną jest NULL.  
  
 *ppt*  
 Wskaźnik do `POINT` strukturę, która zawiera lewego górnego rogu kontrolki. Rozmiar kontrolki jest określany przez wartość *psize*. *Ppt* i *psize* wartości są opcjonalne metodę określania rozmiaru i pozycji opf formantu.  
  
 *psize*  
 Wskaźnik do `SIZE` strukturę, która zawiera rozmiar formantu. Lewy górny róg jest określana przez wartość *ppt*. *Ppt* i *psize* wartości są opcjonalne metodę określania rozmiaru i pozycji opf formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Tylko podzbiór Windows *dwStyle* flagi są obsługiwane przez `CreateControl`:  
  
- WS_VISIBLE tworzy okno, które jest początkowo widoczne. Wymagane, jeśli formant aby były widoczne natychmiast, takich jak zwykłe systemu windows.  
  
- WS_DISABLED tworzy okno, które jest początkowo wyłączone. Wyłączone okno nie może odbierać dane wejściowe od użytkownika. Można ustawić, jeśli kontrolka ma właściwość Enabled.  
  
- WS_BORDER tworzy okno z obramowaniem alokowanych wiersza. Można ustawić, jeśli kontrolka ma właściwości BorderStyle.  
  
- WS_GROUP Określa pierwszy formant grupy formantów. Użytkownik może zmienić fokus klawiatury w jeden formant w grupie do następnego przy użyciu kluczy kierunku. Wszystkie formanty zdefiniowane przy użyciu stylu WS_GROUP po pierwszej kontroli należą do tej samej grupy. Następny formant ze stylem WS_GROUP kończy grupy i rozpoczyna następną grupę.  
  
- WS_TABSTOP Określa formant, który może odebrać fokus klawiatury, gdy użytkownik naciśnie klawisz TAB. Naciskając klawisz TAB, zmienia się na następnej kontrolki stylu WS_TABSTOP fokus klawiatury.  
  
 Drugie przeciążenie umożliwia tworzenie formantów o rozmiarze domyślnym.  
  
##  <a name="destroycontrol"></a>  COleControlSite::DestroyControl  
 Niszczy `COleControlSite` obiektu.  
  
```  
virtual BOOL DestroyControl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie, w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Po zakończeniu obiekt zostanie zwolniony z pamięci i wszystkie wskaźniki do obiektu nie są już prawidłowe.  
  
##  <a name="doverb"></a>  COleControlSite::DoVerb  
 Wykonuje określone zlecenie.  
  
```  
virtual HRESULT DoVerb(
    LONG nVerb,  
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nVerb*  
 Określa polecenie do wykonania. Może ono obejmować jedną z następujących czynności:  
  
|Wartość|Znaczenie|Symbol|  
|-----------|-------------|------------|  
|0|Primary — Zlecenie|OLEIVERB_PRIMARY|  
|-1|Pomocniczy zlecenia|(Brak)|  
|1|Wyświetla obiekt do edycji.|OLEIVERB_SHOW|  
|-2|Edytuje element w osobnym oknie.|OLEIVERB_OPEN|  
|-3|Ukrywa obiektu.|OLEIVERB_HIDE|  
|-4|Aktywuje formant w miejscu.|OLEIVERB_UIACTIVATE|  
|-5|Aktywuje formant w miejscu, bez dodatkowe elementy interfejsu użytkownika.|OLEIVERB_INPLACEACTIVATE|  
|-7|Wyświetlanie właściwości formantu.|OLEIVERB_PROPERTIES|  
  
 *lpMsg*  
 Wskaźnik na komunikat, który spowodował elementu zostanie uaktywniony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja odwołuje się bezpośrednio za pośrednictwem formantu `IOleObject` interfejsu, aby wykonać określone zlecenie. Jeśli wyjątek jest generowany w wyniku tego wywołania funkcji, zwracany jest kod błędu HRESULT.  
  
 Aby uzyskać więcej informacji, zobacz [IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) w zestawie Windows SDK.  
  
##  <a name="enabledsc"></a>  COleControlSite::EnableDSC  
 Umożliwia określanie źródła dla tej witryny kontroli danych.  
  
```  
virtual void EnableDSC();
```  
  
### <a name="remarks"></a>Uwagi  
 Metoda wywoływana przez platformę, by włączyć i zainicjuj danych sourcing kontroli lokacji. Należy przesłonić tę funkcję, aby zapewnić zachowanie niestandardowe.  
  
##  <a name="enablewindow"></a>  COleControlSite::EnableWindow  
 Włącza lub wyłącza myszy i klawiatury do kontroli lokacji.  
  
```  
virtual BOOL EnableWindow(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 *bWłączenie*  
 Określa, czy włączać lub wyłączać okna: wartość TRUE, jeśli dane wejściowe z okna, które ma być włączone, w przeciwnym razie wartość FALSE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wcześniej była wyłączona okna, w przeciwnym razie 0.  
  
##  <a name="freezeevents"></a>  COleControlSite::FreezeEvents  
 Określa, czy witryny kontroli będzie obsługiwać Ignoruj zdarzenia zwolnione z formantu.  
  
```  
void FreezeEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>Parametry  
 *bFreeze*  
 Określa witryny kontroli chce akceptować zdarzenia. Wartość różną od zera, jeśli formant nie akceptuje zdarzeń; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *bFreeze* ma wartość PRAWDA, witrynie kontroli żądań formant Aby zatrzymać Przenieś zdarzenia. Jeśli *bFreeze* ma wartość FAŁSZ, witrynie kontroli żądań formant aby kontynuować, wyzwalanie zdarzeń.  
  
> [!NOTE]
>  Kontrolka nie jest wymagane przestanie wyzwalanie zdarzeń, jeśli jest to wymagane przez lokację kontroli. Może kontynuować uruchomieniu którego, ale wszystkie kolejne zdarzenia zostaną zignorowane przez lokację kontroli.  
  
##  <a name="getcontrolinfo"></a>  COleControlSite::GetControlInfo  
 Pobiera informacje o kontroli klawiszy skrótu klawiatury i zachowanie klawiatury.  
  
```  
void GetControlInfo();
```  
  
### <a name="remarks"></a>Uwagi  
 Informacje są przechowywane w [COleControlSite::m_ctlInfo](#m_ctlinfo).  
  
##  <a name="getdefbtncode"></a>  COleControlSite::GetDefBtnCode  
 Określa, czy formant przycisku domyślnego.  
  
```  
DWORD GetDefBtnCode();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Może być jednym z następujących wartości:  
  
- Kontrolka DLGC_DEFPUSHBUTTON jest przycisk domyślny w oknie dialogowym.  
  
- Kontrolka DLGC_UNDEFPUSHBUTTON nie jest przycisk domyślny w oknie dialogowym.  
  
- **0** kontrolki nie jest przyciskiem.  
  
##  <a name="getdlgctrlid"></a>  COleControlSite::GetDlgCtrlID  
 Pobiera identyfikator kontrolki.  
  
```  
virtual int GetDlgCtrlID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator elementu okno dialogowe formantu.  
  
##  <a name="geteventiid"></a>  COleControlSite::GetEventIID  
 Pobiera wskaźnik do interfejsu zdarzenia domyślne formantu.  
  
```  
BOOL GetEventIID(IID* piid);
```  
  
### <a name="parameters"></a>Parametry  
 *piid*  
 Wskaźnik do interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie, w przeciwnym razie 0. W przypadku powodzenia *piid* zawiera identyfikator interfejsu dla interfejsu zdarzenia domyślne formantu.  
  
##  <a name="getexstyle"></a>  COleControlSite::GetExStyle  
 Pobiera rozszerzone Style okna.  
  
```  
virtual DWORD GetExStyle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Okno kontrolki użytkownika rozszerzone style.  
  
### <a name="remarks"></a>Uwagi  
 Aby pobrać regularne style, wywołania [COleControlSite::GetStyle](#getstyle).  
  
##  <a name="getproperty"></a>  COleControlSite::GetProperty  
 Pobiera określony przez właściwość formantu *dwDispID*.  
  
```  
virtual void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Określa identyfikator wysyłania odnaleziono na formantu domyślnych właściwości `IDispatch` interfejsu do pobrania.  
  
 *vtProp*  
 Określa typ właściwości, które mają zostać pobrane. Aby uzyskać możliwych wartości, zobacz sekcję Spostrzeżenia, aby [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *pvProp*  
 Adres zmiennej, która otrzyma wartość właściwości. Musi być zgodny z typem określonym przez *vtProp*.  
  
### <a name="remarks"></a>Uwagi  
 Wartość jest zwracana za pośrednictwem *pvProp*.  
  
##  <a name="getstyle"></a>  COleControlSite::GetStyle  
 Pobiera style kontroli lokacji.  
  
```  
virtual DWORD GetStyle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Style okna.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać listę możliwych wartości, zobacz [style Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles). Aby pobrać rozszerzone style lokacji kontrolki, należy wywołać [COleControlSite::GetExStyle](#getexstyle).  
  
##  <a name="getwindowtext"></a>  COleControlSite::GetWindowText  
 Pobiera tekst kontrolki.  
  
```  
virtual void GetWindowText(CString& str) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *str*  
 Odwołanie do `CString` obiekt, który zawiera tekst kontrolki.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli są obsługiwane przez kontrolkę podstawowe właściwości podpisu, ta wartość jest zwracana. Jeśli właściwości podstawowych podpis nie jest obsługiwana, jest zwracana wartość właściwości Text.  
  
##  <a name="invokehelper"></a>  COleControlSite::InvokeHelper  
 Wywołuje metodę lub właściwość określoną przez *dwDispID*, w kontekście określonej przez *wFlags*.  
  
```  
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,  
    WORD wFlags,  
    VARTYPE vtRet,  
    void* pvRet,  
    const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Określa identyfikator wysyłania odnaleziono właściwości lub metody, na kontrolce `IDispatch` interfejsu do wywołania.  
  
 *wFlags*  
 Flagi opisujące Kontekst wywołania uwzględniając. Do ewentualnego *wFlags* wartości, zobacz `IDispatch::Invoke` w zestawie Windows SDK.  
  
 *vtRet*  
 Określa typ wartości zwracanej. Aby uzyskać możliwych wartości, zobacz sekcję Spostrzeżenia, aby [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *pvRet*  
 Adres zmiennej, która będzie odbierać wartość właściwości lub wartości zwracanej. Musi być zgodny z typem określonym przez *vtRet*.  
  
 *pbParamInfo*  
 Wskaźnik na ciąg zakończony znakiem null bajtów, określając typy parametrów, zgodnie z *pbParamInfo*. Aby uzyskać możliwych wartości, zobacz sekcję Spostrzeżenia, aby [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Zmiennej listy parametrów typów określonych w *pbParamInfo*.  
  
### <a name="remarks"></a>Uwagi  
 *PbParamInfo* parametr określa typy parametrów przekazanych do metody lub właściwości. Listy zmiennych argumentów jest reprezentowany przez... w składni deklaracji.  
  
 Ta funkcja konwertuje parametry VARIANTARG wartości, a następnie wywołuje `IDispatch::Invoke` metody dla kontrolki. Jeśli wywołanie `IDispatch::Invoke` zakończy się niepowodzeniem, ta funkcja spowoduje zgłoszenie wyjątku. Jeśli kod stanu zwrócony przez `IDispatch::Invoke` jest `DISP_E_EXCEPTION`, ta funkcja zgłosi `COleDispatchException` obiektu, w przeciwnym razie wyniku weryfikacji zgłasza wyjątek `COleException`.  
  
##  <a name="invokehelperv"></a>  COleControlSite::InvokeHelperV  
 Wywołuje metodę lub właściwość określoną przez *dwDispID*, w kontekście określonej przez *wFlags*.  
  
```  
virtual void InvokeHelperV(
    DISPID dwDispID,  
    WORD wFlags,  
    VARTYPE vtRet,  
    void* pvRet,  
    const BYTE* pbParamInfo,  
    va_list argList);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Określa identyfikator wysyłania odnaleziono właściwości lub metody, na kontrolce `IDispatch` interfejsu do wywołania.  
  
 *wFlags*  
 Flagi opisujące Kontekst wywołania uwzględniając.  
  
 *vtRet*  
 Określa typ wartości zwracanej. Aby uzyskać możliwych wartości, zobacz sekcję Spostrzeżenia, aby [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *pvRet*  
 Adres zmiennej, która będzie odbierać wartość właściwości lub wartości zwracanej. Musi być zgodny z typem określonym przez *vtRet*.  
  
 *pbParamInfo*  
 Wskaźnik na ciąg zakończony znakiem null bajtów, określając typy parametrów, zgodnie z *pbParamInfo*. Aby uzyskać możliwych wartości, zobacz sekcję Spostrzeżenia, aby [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *Lista_argumentów*  
 Wskaźnik do listy zmiennych argumentów.  
  
### <a name="remarks"></a>Uwagi  
 *PbParamInfo* parametr określa typy parametrów przekazanych do metody lub właściwości. Mogą być przekazywane dodatkowe parametry dla metody lub właściwości, które są wywoływane przy użyciu *va_list* parametru.  
  
 Typowo, ta funkcja jest wywoływana `COleControlSite::InvokeHelper`.  
  
##  <a name="isdefaultbutton"></a>  COleControlSite::IsDefaultButton  
 Określa, czy kontrolka jest przycisk domyślny.  
  
```  
BOOL IsDefaultButton();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli formant znajduje się przycisk domyślny w oknie, w przeciwnym razie od zera.  
  
##  <a name="iswindowenabled"></a>  COleControlSite::IsWindowEnabled  
 Określa, czy włączono kontroli lokacji.  
  
```  
virtual BOOL IsWindowEnabled() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli kontrolka jest włączona, w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Wartość jest pobierana z właściwości podstawowych włączone formantu.  
  
##  <a name="m_biswindowless"></a>  COleControlSite::m_bIsWindowless  
 Określa, czy obiekt jest formantem bez okien.  
  
```  
BOOL m_bIsWindowless;  
```  
  
### <a name="remarks"></a>Uwagi  
 Wartość różną od zera, jeśli kontrolka nie ma żadnego okna, w przeciwnym razie wartość zero.  
  
##  <a name="m_ctlinfo"></a>  COleControlSite::m_ctlInfo  
 Informacje na temat sposobu obsługi danych wprowadzonych z klawiatury przez kontrolkę.  
  
```  
CONTROLINFO m_ctlInfo;  
```  
  
### <a name="remarks"></a>Uwagi  
 Te informacje są przechowywane w [CONTROLINFO](http://msdn.microsoft.com/library/windows/desktop/ms680734) struktury.  
  
##  <a name="m_dweventsink"></a>  COleControlSite::m_dwEventSink  
 Zawiera cookie punkt połączenia z obiektu sink zdarzenia formantu.  
  
```  
DWORD m_dwEventSink;  
```  
  
##  <a name="m_dwmiscstatus"></a>  COleControlSite::m_dwMiscStatus  
 Zawiera różne informacje o kontrolce.  
  
```  
DWORD m_dwMiscStatus;  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)w zestawie Windows SDK.  
  
##  <a name="m_dwpropnotifysink"></a>  COleControlSite::m_dwPropNotifySink  
 Zawiera [ipropertynotifysink —](http://msdn.microsoft.com/library/windows/desktop/ms692638) pliku cookie.  
  
```  
DWORD m_dwPropNotifySink;  
```  
  
##  <a name="m_dwstyle"></a>  COleControlSite::m_dwStyle  
 Zawiera style okna ramowego formantu.  
  
```  
DWORD m_dwStyle;  
```  
  
##  <a name="m_hwnd"></a>  COleControlSite::m_hWnd  
 Zawiera HWND formantu lub wartość NULL, jeśli kontrolka jest bez okien.  
  
```  
HWND m_hWnd;  
```  
  
##  <a name="m_iidevents"></a>  COleControlSite::m_iidEvents  
 Zawiera identyfikator interfejsu interfejs ujścia zdarzeń domyślne formantu.  
  
```  
IID m_iidEvents;  
```  
  
##  <a name="m_nid"></a>  COleControlSite::m_nID  
 Zawiera identyfikator formantu okna dialogowego elementu.  
  
```  
UINT m_nID;  
```  
  
##  <a name="m_pactiveobject"></a>  COleControlSite::m_pActiveObject  
 Zawiera [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) interfejsu formantu.  
  
```  
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;  
```  
  
##  <a name="m_pctrlcont"></a>  COleControlSite::m_pCtrlCont  
 Zawiera kontener formantu (reprezentującej formularza).  
  
```  
COleControlContainer* m_pCtrlCont;  
```  
  
##  <a name="m_pinplaceobject"></a>  COleControlSite::m_pInPlaceObject  
 Zawiera `IOleInPlaceObject` [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) interfejsu formantu.  
  
```  
LPOLEINPLACEOBJECT m_pInPlaceObject;  
```  
  
##  <a name="m_pobject"></a>  COleControlSite::m_pObject  
 Zawiera `IOleObjectInterface` interfejsu formantu.  
  
```  
LPOLEOBJECT m_pObject;  
```  
  
##  <a name="m_pwindowlessobject"></a>  COleControlSite::m_pWindowlessObject  
 Zawiera `IOleInPlaceObjectWindowless` [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304) interfejsu formantu.  
  
```  
IOleInPlaceObjectWindowless* m_pWindowlessObject;  
```  
  
##  <a name="m_pwndctrl"></a>  COleControlSite::m_pWndCtrl  
 Zawiera wskaźnik do `CWnd` obiekt, który reprezentuje sam formant.  
  
```  
CWnd* m_pWndCtrl;  
```  
  
##  <a name="m_rect"></a>  COleControlSite::m_rect  
 Zawiera granice formantu względem okna kontenera.  
  
```  
CRect m_rect;  
```  
  
##  <a name="modifystyle"></a>  COleControlSite::ModifyStyle  
 Modyfikuje style kontrolki.  
  
```  
virtual BOOL ModifyStyle(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *dwRemove*  
 Style do usunięcia z bieżącego Style okna ramowego.  
  
 *dwAdd*  
 Style, które mają zostać dodane z bieżącym Style okna ramowego.  
  
 *nFlags*  
 Okno pozycjonowanie flag. Aby uzyskać listę możliwych wartości, zobacz [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) funkcji w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli style zostaną zmienione, w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Stock formantu właściwość włączone zostaną zmodyfikowane w taki sposób, aby dopasować ustawienie WS_DISABLED. Podstawowe właściwości Styl obramowania formantu zostaną zmodyfikowane w taki sposób, aby dopasować żądany ustawienie WS_BORDER. Innymi stylami są stosowane bezpośrednio do dojścia okna kontrolki, jeśli jest obecna.  
  
 Modyfikuje style okna ramowego formantu. Style, które mają być dodane lub usunięte, może być połączone za pomocą bitowe OR ( &#124; ) — operator. Zobacz [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) funkcji w zestawie Windows SDK dla informacji o stylach dostępnym oknie.  
  
 Jeśli *nFlags* jest różna od zera, `ModifyStyle` wywołuje funkcję Win32 `SetWindowPos`i ponownie rysuje okna, łącząc *nFlags* z czterech następujących flag:  
  
- SWP_NOSIZE zachowuje bieżący rozmiar.  
  
- SWP_NOMOVE zachowuje bieżącej pozycji.  
  
- SWP_NOZORDER zachowuje porządek bieżącego.  
  
- SWP_NOACTIVATE nie uaktywnia okna.  
  
 Aby zmodyfikować w oknie, użytkownika rozszerzone style, wywołania [ModifyStyleEx](#modifystyleex).  
  
##  <a name="modifystyleex"></a>  COleControlSite::ModifyStyleEx  
 Modyfikuje rozszerzone style kontrolki.  
  
```  
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *dwRemove*  
 Rozszerzone style do usunięcia z bieżącego Style okna ramowego.  
  
 *dwAdd*  
 Rozszerzone style do dodania z bieżącym Style okna ramowego.  
  
 *nFlags*  
 Okno pozycjonowanie flag. Aby uzyskać listę możliwych wartości, zobacz [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) funkcji w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli style zostaną zmienione, w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Stock formantu właściwości wyglądu zostaną zmodyfikowane w taki sposób, aby dopasować ustawienie WS_EX_CLIENTEDGE. Wszystkie inne rozszerzone Style okna są stosowane bezpośrednio do dojścia okna kontrolki, jeśli jest obecna.  
  
 Modyfikuje okna rozszerzone style obiektu kontroli lokacji. Style, które mają być dodane lub usunięte, może być połączone za pomocą bitowe OR ( &#124; ) — operator. Zobacz [elementu CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) funkcji w zestawie Windows SDK dla informacji o stylach dostępnym oknie.  
  
 Jeśli *nFlags* jest różna od zera, `ModifyStyleEx` wywołuje funkcję Win32 `SetWindowPos`i ponownie rysuje okna, łącząc *nFlags* z czterech następujących flag:  
  
- SWP_NOSIZE zachowuje bieżący rozmiar.  
  
- SWP_NOMOVE zachowuje bieżącej pozycji.  
  
- SWP_NOZORDER zachowuje porządek bieżącego.  
  
- SWP_NOACTIVATE nie uaktywnia okna.  
  
 Aby zmodyfikować w oknie, użytkownika rozszerzone style, wywołania [ModifyStyle](#modifystyle).  
  
##  <a name="movewindow"></a>  COleControlSite::MoveWindow  
 Zmienia położenie formantu.  
  
```  
virtual void MoveWindow(
    int x,  
    int y,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Stanowisko w lewej części okna.  
  
 *y*  
 Stanowisko w górnej części okna.  
  
 *nWidth*  
 Nowe szerokość okna  
  
 *nHeight*  
 Nową wysokość okna.  
  
##  <a name="quickactivate"></a>  COleControlSite::QuickActivate  
 Szybkie aktywuje kontrolkę zawarte.  
  
```  
virtual BOOL QuickActivate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera Jeżeli lokacji kontrolki została aktywowana, w przeciwnym razie zero.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna być wywoływana tylko wtedy, gdy użytkownik zastępuje procesu tworzenia kontrolki.  
  
 `IPersist*::Load` i `IPersist*::InitNew` metody powinna być wywoływana po wystąpieniu szybkiego aktywacji. Formant należy określić jego połączenia z ujść kontenera podczas szybkiego aktywacji. Połączenia te nie są jednak na żywo do momentu `IPersist*::Load` lub `IPersist*::InitNew` została wywołana.  
  
##  <a name="safesetproperty"></a>  COleControlSite::SafeSetProperty  
 Ustawia właściwości kontrolki określonej przez *dwDispID*.  
  
```  
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Określa identyfikator wysyłania odnaleziono właściwości lub metody, na kontrolce `IDispatch` interfejsu, należy ustawić.  
  
 *vtProp*  
 Określa typ właściwości do ustawienia. Aby uzyskać możliwych wartości, zobacz sekcję Spostrzeżenia, aby [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Pojedynczy parametr typu określonego przez *vtProp*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  W odróżnieniu od `SetProperty` i `SetPropertyV`, w przypadku napotkania błędu (np. próbuje ustawić właściwość nieistniejącej), jest zgłaszany żaden wyjątek.  
  
##  <a name="setdefaultbutton"></a>  COleControlSite::SetDefaultButton  
 Ustawienie dla formantu jako przycisk domyślny.  
  
```  
void SetDefaultButton(BOOL bDefault);
```  
  
### <a name="parameters"></a>Parametry  
 *bPoziom domyślny*  
 Wartość różną od zera, jeśli kontrolka powinna stać się przycisk domyślny; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Kontrolka musi mieć OLEMISC_ACTSLIKEBUTTON stan-bitowego zestawu.  
  
##  <a name="setdlgctrlid"></a>  COleControlSite::SetDlgCtrlID  
 Zmienia wartość Identyfikator elementu okno dialogowe formantu.  
  
```  
virtual int SetDlgCtrlID(int nID);
```  
  
### <a name="parameters"></a>Parametry  
 *nID*  
 Nowa wartość identyfikatora.  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia poprzedniego okna dialogowego elementu identyfikatora oknie. w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setfocus"></a>  COleControlSite::SetFocus  
 Ustawia fokus do formantu.  
  
```  
virtual CWnd* SetFocus();  
virtual CWnd* SetFocus(LPMSG lpmsg);
```  
  
### <a name="parameters"></a>Parametry  
 *lpmsg*  
 Wskaźnik do [struktura MSG](../../mfc/reference/msg-structure1.md). Ta struktura zawiera wyzwolenie wiadomości Windows `SetFocus` żądania dla formantu zawartego w bieżącej witrynie formant.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do okna, który wcześniej był aktywny.  
  
##  <a name="setproperty"></a>  COleControlSite::SetProperty  
 Ustawia właściwości kontrolki określonej przez *dwDispID*.  
  
```  
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Określa identyfikator wysyłania odnaleziono właściwości lub metody, na kontrolce `IDispatch` interfejsu, należy ustawić.  
  
 *vtProp*  
 Określa typ właściwości do ustawienia. Aby uzyskać możliwych wartości, zobacz sekcję Spostrzeżenia, aby [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Pojedynczy parametr typu określonego przez *vtProp*.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `SetProperty` napotka błąd, zostanie zgłoszony wyjątek.  
  
 Typ wyjątku jest określana przez wartość zwracaną próba ustawienia właściwości lub metody. Jeśli wartość zwracana jest `DISP_E_EXCEPTION`, `COleDispatchExcpetion` jest zgłoszenia; w przeciwnym razie `COleException`.  
  
##  <a name="setpropertyv"></a>  COleControlSite::SetPropertyV  
 Ustawia właściwości kontrolki określonej przez *dwDispID*.  
  
```  
virtual void SetPropertyV(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    va_list argList);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Określa identyfikator wysyłania odnaleziono właściwości lub metody, na kontrolce `IDispatch` interfejsu, należy ustawić.  
  
 *vtProp*  
 Określa typ właściwości do ustawienia. Aby uzyskać możliwych wartości, zobacz sekcję Spostrzeżenia, aby [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *Lista_argumentów*  
 Wskaźnik do listy argumentów.  
  
### <a name="remarks"></a>Uwagi  
 Dodatkowe parametry dla metody lub właściwości wywoływanej może być passeed przy użyciu *arg_list* parametru. Jeśli `SetProperty` napotka błąd, zostanie zgłoszony wyjątek.  
  
 Typ wyjątku jest określana przez wartość zwracaną próba ustawienia właściwości lub metody. Jeśli wartość zwracana jest `DISP_E_EXCEPTION`, `COleDispatchExcpetion` jest zgłoszenia; w przeciwnym razie `COleException`.  
  
##  <a name="setwindowpos"></a>  COleControlSite::SetWindowPos  
 Ustawia rozmiar, położenie i porządek kontroli lokacji.  
  
```  
virtual BOOL SetWindowPos(
    const CWnd* pWndInsertAfter,  
    int x,  
    int y,  
    int cx,  
    int cy,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndInsertAfter*  
 Wskaźnik do okna.  
  
 *x*  
 Stanowisko w lewej części okna.  
  
 *y*  
 Stanowisko w górnej części okna.  
  
 *CX*  
 Nowe szerokość okna  
  
 *CY*  
 Nową wysokość okna.  
  
 *nFlags*  
 Określa okna, rozmiar i położenie flag. Aby uzyskać możliwych wartości, zobacz sekcję Spostrzeżenia, aby [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera jeśli to się powiedzie, w przeciwnym razie wartość zero.  
  
##  <a name="setwindowtext"></a>  COleControlSite::SetWindowText  
 Ustawia tekst kontroli lokacji.  
  
```  
virtual void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszString*  
 Wskaźnik na ciąg zakończony znakiem null ma być używany jako nowy tekst tytułu lub formant.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja najpierw próbuje ustawić właściwości podstawowe podpisu. Jeśli właściwości podstawowych podpis nie jest obsługiwany, zamiast tego jest ustawiona właściwość Text.  
  
##  <a name="showwindow"></a>  COleControlSite::ShowWindow  
 Ustawia stan Pokaż okna.  
  
```  
virtual BOOL ShowWindow(int nCmdShow);
```  
  
### <a name="parameters"></a>Parametry  
 *nCmdShow*  
 Określa, jak witryna kontrolki ma być wyświetlana. Musi mieć jedną z następujących wartości:  
  
- SW_HIDE polega na schowaniu to okno i przekazuje aktywacji do innego okna.  
  
- SW_MINIMIZE minimalizuje okna i aktywuje okno najwyższego poziomu, na liście systemu.  
  
- Aktywuje SW_RESTORE i wyświetla okno. Jeśli okno jest zminimalizowane lub zmaksymalizowane, Windows przywraca oryginalny rozmiar i położenie.  
  
- SW_SHOW uaktywnia okno i wyświetla go w jego bieżący rozmiar i położenie.  
  
- SW_SHOWMAXIMIZED uaktywnia okno i wyświetla je jako zmaksymalizowane okno.  
  
- SW_SHOWMINIMIZED uaktywnia okno i wyświetla je jako ikona.  
  
- SW_SHOWMINNOACTIVE Wyświetla okno jako ikona. Okno, które jest obecnie aktywny pozostaje aktywna.  
  
- SW_SHOWNA Wyświetla okno w jego bieżącym stanie. Okno, które jest obecnie aktywny pozostaje aktywna.  
  
- SW_SHOWNOACTIVATE Wyświetla okno w najnowszych rozmiar i położenie. Okno, które jest obecnie aktywny pozostaje aktywna.  
  
- Aktywuje SW_SHOWNORMAL i wyświetla okno. Jeśli okno jest zminimalizowane lub zmaksymalizowane, Windows przywraca oryginalny rozmiar i położenie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli okno było wcześniej widoczne; 0, jeśli wcześniej została ukryta, okna.  
  
## <a name="see-also"></a>Zobacz też  
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)
