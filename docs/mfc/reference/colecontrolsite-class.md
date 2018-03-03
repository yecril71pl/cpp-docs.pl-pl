---
title: Klasa COleControlSite | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 80541bc777d2c77209812cbee621045b7d6c6507
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|Wiąże domyślną właściwość obsługiwanego formantu ze źródłem danych.|  
|[COleControlSite::BindProperty](#bindproperty)|Wiąże właściwości obsługiwanego formantu ze źródłem danych.|  
|[COleControlSite::CreateControl](#createcontrol)|Tworzy obsługiwanego formantu ActiveX.|  
|[COleControlSite::DestroyControl](#destroycontrol)|Niszczy obsługiwanego formantu.|  
|[COleControlSite::DoVerb](#doverb)|Wykonuje określone zlecenie obsługiwanego formantu.|  
|[COleControlSite::EnableDSC](#enabledsc)|Umożliwia danych sourcing kontroli lokacji.|  
|[COleControlSite::EnableWindow](#enablewindow)|Umożliwia kontroli lokacji.|  
|[COleControlSite::FreezeEvents](#freezeevents)|Określa, czy kontroli lokacji akceptuje zdarzenia.|  
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Pobiera domyślny kod obsługiwanego formantu przycisku.|  
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Pobiera identyfikator formantu.|  
|[COleControlSite::GetEventIID](#geteventiid)|Pobiera identyfikator interfejs zdarzenie dla obsługiwanego formantu.|  
|[COleControlSite::GetExStyle](#getexstyle)|Pobiera rozszerzone style kontroli lokacji.|  
|[COleControlSite::GetProperty](#getproperty)|Pobiera określoną właściwością obsługiwanego formantu.|  
|[COleControlSite::GetStyle](#getstyle)|Pobiera style kontroli lokacji.|  
|[COleControlSite::GetWindowText](#getwindowtext)|Pobiera tekst formantu hostowanej.|  
|[COleControlSite::InvokeHelper](#invokehelper)|Wywoływanie metody określonej obsługiwanego formantu.|  
|[COleControlSite::InvokeHelperV](#invokehelperv)|Wywoływanie metody określonej obsługiwanego formantu z listy zmiennych argumentów.|  
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|Określa, czy formant jest przycisk domyślny w oknie.|  
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|Sprawdza, czy wyświetlany stan kontroli lokacji.|  
|[COleControlSite::ModifyStyle](#modifystyle)|Modyfikuje bieżącego rozszerzone style kontroli lokacji.|  
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Modyfikuje style bieżącego kontroli lokacji.|  
|[COleControlSite::MoveWindow](#movewindow)|Zmienia położenie kontroli lokacji.|  
|[COleControlSite::QuickActivate](#quickactivate)|Szybkie aktywuje obsługiwanego formantu.|  
|[COleControlSite::SafeSetProperty](#safesetproperty)|Ustawia właściwości lub metody kontroli bez generowania wyjątku ryzyko.|  
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Ustawia przycisk domyślny w oknie.|  
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Pobiera identyfikator formantu.|  
|[COleControlSite::SetFocus](#setfocus)|Ustawia fokus kontroli lokacji.|  
|[COleControlSite::SetProperty](#setproperty)|Ustawia określoną właściwością obsługiwanego formantu.|  
|[COleControlSite::SetPropertyV](#setpropertyv)|Ustawia z określoną właściwością obsługiwanego formantu listy zmiennych argumentów.|  
|[COleControlSite::SetWindowPos](#setwindowpos)|Ustawia położenie kontroli lokacji.|  
|[COleControlSite::SetWindowText](#setwindowtext)|Ustawia tekst obsługiwanego formantu.|  
|[COleControlSite::ShowWindow](#showwindow)|Pokazuje lub ukrywa kontroli lokacji.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Pobiera informacje o klawiatury i klawiszy skrótu dla obsługiwanego formantu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Określa, czy formant hostowanej jest formantem bez okien.|  
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Zawiera informacje dotyczące formantu za pomocą klawiatury.|  
|[COleControlSite::m_dwEventSink](#m_dweventsink)|Plik cookie punkt połączenia z formantu.|  
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Różne stany obsługiwanego formantu.|  
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|`IPropertyNotifySink` Plik cookie formantu.|  
|[COleControlSite::m_dwStyle](#m_dwstyle)|Style formantu hostowanej.|  
|[COleControlSite::m_hWnd](#m_hwnd)|Dojście kontroli lokacji.|  
|[COleControlSite::m_iidEvents](#m_iidevents)|Identyfikator interfejsu zdarzenia dla obsługiwanego formantu.|  
|[COleControlSite::m_nID](#m_nid)|Identyfikator formantu hostowanej.|  
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|Wskaźnik do `IOleInPlaceActiveObject` obiektu obsługiwanego formantu.|  
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|Kontener obsługiwanego formantu.|  
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|Wskaźnik do `IOleInPlaceObject` obiektu obsługiwanego formantu.|  
|[COleControlSite::m_pObject](#m_pobject)|Wskaźnik do `IOleObjectInterface` interfejsu formantu.|  
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|Wskaźnik do `IOleInPlaceObjectWindowless` interfejsu formantu.|  
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|Wskaźnik do obiektu okna dla formantu hostowanej.|  
|[COleControlSite::m_rect](#m_rect)|Wymiary kontroli lokacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ta obsługa jest podstawowym elementem używanym za pomocą którego osadzonego formantu ActiveX uzyskuje informacje o lokalizacji i zakresie swojej witryny wyświetlania, jego nazwie interfejs użytkownika, jej otoczeniu właściwości i innych zasobów udostępnianych przez jego kontenera. `COleControlSite`implementuje w pełni [IOleControlSite](http://msdn.microsoft.com/library/windows/desktop/ms688502), [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706), [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), **IBoundObjectSite**, **INotifyDBEvents**, [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md) interfejsów. Ponadto również zaimplementowano interfejs IDispatch (Zapewnianie obsługi do właściwości otaczających i wychwytywanie zdarzeń).  
  
 Aby utworzyć ActiveX sterowania lokacji za pomocą `COleControlSite`, klasa wyprowadzona z `COleControlSite`. W Twojej `CWnd`-przesłonić klasy pochodnej kontenera (na przykład dialogowym) **CWnd::CreateControlSite** funkcji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlSite`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxocc.h  
  
##  <a name="binddefaultproperty"></a>COleControlSite::BindDefaultProperty  
 Wiąże obiekt wywołujący domyślne proste powiązania właściwość, jako oznaczone w bibliotece typów podstawowych kursora, jest definiowana za pomocą właściwości źródła danych, nazwę użytkownika, hasło i SQL kontroli źródła danych.  
  
```  
virtual void BindDefaultProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    LPCTSTR szFieldName,  
    CWnd* pDSCWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Określa **DISPID** właściwości dla formantu powiązanego z danymi, który ma zostać powiązany do kontroli źródła danych.  
  
 `vtProp`  
 Określa typ właściwości powiązać — na przykład `VT_BSTR`, **VT_VARIANT**i tak dalej.  
  
 `szFieldName`  
 Określa nazwę kolumny w kursorze pochodzącymi z kontroli źródła danych, do którego będzie można powiązać właściwości.  
  
 `pDSCWnd`  
 Wskaźnik do `CWnd`-pochodnej obiekt, który obsługuje kontroli źródła danych, do którego będzie można powiązać właściwości.  
  
### <a name="remarks"></a>Uwagi  
 `CWnd` Obiektu, na którym wywołanie tej funkcji musi być formantem powiązane z danymi.  
  
##  <a name="bindproperty"></a>COleControlSite::BindProperty  
 Wiąże obiektu wywołującego proste powiązania właściwość, jako zaznaczone w bibliotece typów podstawowych kursora, jest definiowana za pomocą właściwości źródła danych, nazwę użytkownika, hasło i SQL kontroli źródła danych.  
  
```  
virtual void BindProperty(
    DISPID dwDispId,  
    CWnd* pWndDSC);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispId*  
 Określa **DISPID** właściwości dla formantu powiązanego z danymi, który ma zostać powiązany do kontroli źródła danych.  
  
 `pWndDSC`  
 Wskaźnik do `CWnd`-pochodnej obiekt, który obsługuje kontroli źródła danych, do którego będzie można powiązać właściwości.  
  
### <a name="remarks"></a>Uwagi  
 `CWnd` Obiektu, na którym wywołanie tej funkcji musi być formantem powiązane z danymi.  
  
##  <a name="colecontrolsite"></a>COleControlSite::COleControlSite  
 Tworzy nową `COleControlSite` obiektu.  
  
```  
explicit COleControlSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>Parametry  
 `pCtrlCont`  
 Wskaźnik do formantu kontenera, (reprezentujący okno obsługującego kontroli AtiveX).  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana [COccManager::CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer) funkcji. Aby uzyskać więcej informacji o dostosowywaniu tworzenie kontenerów, zobacz [COccManager::CreateSite](../../mfc/reference/coccmanager-class.md#createsite).  
  
##  <a name="createcontrol"></a>COleControlSite::CreateControl  
 Tworzy formantu ActiveX, obsługiwanych przez `COleControlSite` obiektu.  
  
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
 `pWndCtrl`  
 Wskaźnik do obiekt window reprezentujący formantu.  
  
 `clsid`  
 Identyfikator unikatowy klasy formantu.  
  
 `lpszWindowName`  
 Wskaźnik do tekstu wyświetlanego w formancie. Ustawia wartości właściwości podpisu lub tekst winodw (jeśli istnieje).  
  
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
  
 `ppt`  
 Wskaźnik do **punktu** struktury, która zawiera górnego lewego rogu formantu. Rozmiar formantu jest określana przez wartość *psize*. `ppt` i *psize* wartości są opcjonalne metoda określania rozmiaru i pozycji opf formantu.  
  
 *psize*  
 Wskaźnik do **rozmiar** struktury, która zawiera rozmiar formantu. Lewy górny róg jest określana przez wartość `ppt`. `ppt` i *psize* wartości są opcjonalne metoda określania rozmiaru i pozycji opf formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Tylko podzestaw systemu Windows `dwStyle` flagi są obsługiwane przez `CreateControl`:  
  
- **Ws_visible —** tworzy okna, które jest początkowo widoczne. Wymagane, jeśli formantu ma być widoczna od razu, takich jak zwykłe systemu windows.  
  
- **Ws_disabled —** tworzy okno, które jest początkowo wyłączone. Wyłączone okna nie mogą otrzymywać dane wejściowe użytkownika. Można ustawić, jeśli formant ma właściwość Enabled.  
  
- `WS_BORDER`Tworzy okno z elastycznej linii obramowania. Można ustawić, jeśli formant ma właściwości BorderStyle.  
  
- **Ws_group —** Określa pierwszą kontrolkę grupy formantów. Użytkownik może zmienić fokus klawiatury z jednego formantu w grupie do następnego przy użyciu kluczy kierunku. Wszystkie formanty zdefiniowane z **ws_group —** styl po pierwszą kontrolkę należą do tej samej grupy. Następnego formantu z **ws_group —** styl kończy się grupie i uruchamia następnej grupy.  
  
- **Ws_tabstop —** Określa formant może przyjmować fokus klawiatury, gdy użytkownik naciśnie klawisz TAB. Naciśnięcie klawisza TAB zmienia fokus klawiatury do następnej kontrolki z **ws_tabstop —** stylu.  
  
 Drugi przeciążenie umożliwia tworzenie formantów o rozmiarze domyślnym.  
  
##  <a name="destroycontrol"></a>COleControlSite::DestroyControl  
 Niszczy `COleControlSite` obiektu.  
  
```  
virtual BOOL DestroyControl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli to się powiedzie, w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Po zakończeniu obiekt zostanie zwolniona z pamięci, a wszystkie wskaźniki do obiektu nie są już prawidłowe.  
  
##  <a name="doverb"></a>COleControlSite::DoVerb  
 Wykonuje określone zlecenie.  
  
```  
virtual HRESULT DoVerb(
    LONG nVerb,  
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nVerb`  
 Określa zlecenie do wykonania. Może zawierać jedną z następujących czynności:  
  
|Wartość|Znaczenie|Symbol|  
|-----------|-------------|------------|  
|0|Primary — Zlecenie|`OLEIVERB_PRIMARY`|  
|-1|Zlecenie dodatkowej|(Brak)|  
|1|Wyświetla obiekt do edycji.|`OLEIVERB_SHOW`|  
|-2|Edytuje element w osobnym oknie.|`OLEIVERB_OPEN`|  
|-3|Ukrywa obiektu.|`OLEIVERB_HIDE`|  
|-4|Aktywuje formant w miejscu.|`OLEIVERB_UIACTIVATE`|  
|-5|Aktywuje formant w miejscu, bez dodatkowe elementy interfejsu użytkownika.|**OLEIVERB_INPLACEACTIVATE**|  
|-7|Wyświetl właściwości formantu.|**OLEIVERB_PROPERTIES**|  
  
 `lpMsg`  
 Wskaźnik do wiadomości, który spowodował ten element, aby aktywować.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja bezpośrednio wywołuje za pomocą formantu `IOleObject` interfejsu, aby wykonać określone zlecenie. Jeśli w wyniku tego wywołania funkcji, jest zgłaszany wyjątek `HRESULT` zwrócony kod błędu.  
  
 Aby uzyskać więcej informacji, zobacz [IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) w zestawie Windows SDK.  
  
##  <a name="enabledsc"></a>COleControlSite::EnableDSC  
 Umożliwia danych sourcing kontroli lokacji.  
  
```  
virtual void EnableDSC();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywoływane przez platformę, by włączyć i zainicjuj dane sourcing kontroli lokacji. Przesłonić tę funkcję, aby zapewnić zachowanie niestandardowych.  
  
##  <a name="enablewindow"></a>COleControlSite::EnableWindow  
 Włącza lub wyłącza myszy i klawiatury do kontroli lokacji.  
  
```  
virtual BOOL EnableWindow(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 Określa, czy włączyć lub wyłączyć okna: **TRUE** w przypadku wprowadzania okna do włączenia, w przeciwnym razie **FALSE**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wcześniej była wyłączona okna, w przeciwnym razie wartość 0.  
  
##  <a name="freezeevents"></a>COleControlSite::FreezeEvents  
 Określa, czy kontroli lokacji będzie obsługiwać lub Ignoruj zdarzenia wywoływane z formantu.  
  
```  
void FreezeEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>Parametry  
 `bFreeze`  
 Określa lokacji kontroli chce akceptować zdarzenia. Różna od zera, jeśli formant nie akceptuje zdarzeń; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bFreeze` jest **TRUE**, witrynie formant żądań formant przestanie fring zdarzenia. Jeśli `bFreeze` jest **FALSE**, witrynie formant żądań kontroli, aby kontynuować, wyzwalania zdarzenia.  
  
> [!NOTE]
>  Formant nie jest wymagane do zatrzymania wyzwalania zdarzenia żądanie kontroli lokacji. Można kontynuować uruchamiania, ale wszystkich kolejnych zdarzeń zostaną zignorowane przez kontroli lokacji.  
  
##  <a name="getcontrolinfo"></a>COleControlSite::GetControlInfo  
 Pobiera informacje o klawiszy skrótu klawiatury i zachowanie klawiatury formantu.  
  
```  
void GetControlInfo();
```  
  
### <a name="remarks"></a>Uwagi  
 Informacje są przechowywane w [COleControlSite::m_ctlInfo](#m_ctlinfo).  
  
##  <a name="getdefbtncode"></a>COleControlSite::GetDefBtnCode  
 Określa, czy formant jest domyślny przycisk.  
  
```  
DWORD GetDefBtnCode();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Może to być jedna z następujących wartości:  
  
- **DLGC_DEFPUSHBUTTON** formant jest przycisk domyślny w oknie dialogowym.  
  
- **DLGC_UNDEFPUSHBUTTON** formant nie jest przycisk domyślny w oknie dialogowym.  
  
- **0** formant nie jest przycisk.  
  
##  <a name="getdlgctrlid"></a>COleControlSite::GetDlgCtrlID  
 Pobiera identyfikator formantu.  
  
```  
virtual int GetDlgCtrlID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator elementu okna dialogowego formantu.  
  
##  <a name="geteventiid"></a>COleControlSite::GetEventIID  
 Pobiera wskaźnik do interfejsu zdarzenia domyślne formantu.  
  
```  
BOOL GetEventIID(IID* piid);
```  
  
### <a name="parameters"></a>Parametry  
 `piid`  
 Wskaźnik do identyfikatora interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli to się powiedzie, w przeciwnym razie wartość 0. W przypadku powodzenia `piid` zawiera identyfikator interfejsu dla interfejsu zdarzenia domyślne formantu.  
  
##  <a name="getexstyle"></a>COleControlSite::GetExStyle  
 Pobiera rozszerzone Style okna.  
  
```  
virtual DWORD GetExStyle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Okno kontrolki użytkownika rozszerzone style.  
  
### <a name="remarks"></a>Uwagi  
 Aby pobrać regularne style, wywołania [COleControlSite::GetStyle](#getstyle).  
  
##  <a name="getproperty"></a>COleControlSite::GetProperty  
 Pobiera określony przez właściwość formantu `dwDispID`.  
  
```  
virtual void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Określa identyfikator wysyłania odnaleziono na formantu domyślnych właściwości `IDispatch` interfejsu do pobrania.  
  
 `vtProp`  
 Określa typ właściwości, które mają zostać pobrane. Możliwe wartości w sekcji uwag dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `pvProp`  
 Adres zmiennej, która otrzyma wartość właściwości. Musi on być zgodny z typem określonym przez `vtProp`.  
  
### <a name="remarks"></a>Uwagi  
 Wartość jest zwracana przez `pvProp`.  
  
##  <a name="getstyle"></a>COleControlSite::GetStyle  
 Pobiera style kontroli lokacji.  
  
```  
virtual DWORD GetStyle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Style okna.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać listę możliwych wartości, zobacz [style Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles). Aby pobrać rozszerzone style sterowania lokacji, należy wywołać [COleControlSite::GetExStyle](#getexstyle).  
  
##  <a name="getwindowtext"></a>COleControlSite::GetWindowText  
 Pobiera bieżący tekst formantu.  
  
```  
virtual void GetWindowText(CString& str) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Odwołanie do `CString` obiekt, który zawiera dany tekst formantu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli formant obsługuje właściwości standardowych podpis, ta wartość jest zwracana. Jeśli właściwość standardowych podpis nie jest obsługiwana, jest zwracana wartość właściwości Text.  
  
##  <a name="invokehelper"></a>COleControlSite::InvokeHelper  
 Wywołuje metodę lub określona przez właściwość `dwDispID`, w ramach określonej przez `wFlags`.  
  
```  
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,  
    WORD wFlags,  
    VARTYPE vtRet,  
    void* pvRet,  
    const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Określa identyfikator wysyłania właściwości lub metody, na formantu `IDispatch` interfejs do wywołania.  
  
 `wFlags`  
 Flagi opisujące Kontekst wywołania IDispatch::Invoke. Do ewentualnego `wFlags` wartości, zobacz `IDispatch::Invoke` w zestawie Windows SDK.  
  
 `vtRet`  
 Określa typ zwracanej wartości. Możliwe wartości w sekcji uwag dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `pvRet`  
 Adres zmiennej, która będzie odbierać wartość właściwości ani zwracanej wartości. Musi on być zgodny z typem określonym przez `vtRet`.  
  
 `pbParamInfo`  
 Wskaźnik do zerem ciągu bajtów Określanie typów parametrów po `pbParamInfo`. Możliwe wartości w sekcji uwag dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Zmiennej listy parametrów typów określonych w `pbParamInfo`.  
  
### <a name="remarks"></a>Uwagi  
 `pbParamInfo` Parametr określa typy parametrów przekazanych do metody lub właściwości. Listy zmiennych argumentów jest reprezentowana przez... w deklaracji składni.  
  
 Ta funkcja konwertuje parametry **VARIANTARG** wartości, a następnie wywołuje **IDispatch::Invoke** metody w formancie. Jeśli wywołanie **IDispatch::Invoke** kończy się niepowodzeniem, ta funkcja spowoduje zgłoszenie wyjątku. Jeśli kod stanu zwrócony przez **IDispatch::Invoke** jest `DISP_E_EXCEPTION`, funkcja zwraca **COleDispatchException** obiektu, w przeciwnym razie zgłasza `COleException`.  
  
##  <a name="invokehelperv"></a>COleControlSite::InvokeHelperV  
 Wywołuje metodę lub określona przez właściwość `dwDispID`, w ramach określonej przez `wFlags`.  
  
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
 `dwDispID`  
 Określa identyfikator wysyłania właściwości lub metody, na formantu `IDispatch` interfejs do wywołania.  
  
 `wFlags`  
 Flagi opisujące Kontekst wywołania IDispatch::Invoke.  
  
 `vtRet`  
 Określa typ zwracanej wartości. Możliwe wartości w sekcji uwag dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `pvRet`  
 Adres zmiennej, która będzie odbierać wartość właściwości ani zwracanej wartości. Musi on być zgodny z typem określonym przez `vtRet`.  
  
 `pbParamInfo`  
 Wskaźnik do zerem ciągu bajtów Określanie typów parametrów po `pbParamInfo`. Możliwe wartości w sekcji uwag dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `argList`  
 Wskaźnik do listy zmiennych argumentów.  
  
### <a name="remarks"></a>Uwagi  
 `pbParamInfo` Parametr określa typy parametrów przekazanych do metody lub właściwości. Dodatkowe parametry dla metody lub właściwości wywoływaną mogą zostać przekazane za pomocą *va_list* parametru.  
  
 Zwykle ta funkcja jest wywoływana `COleControlSite::InvokeHelper`.  
  
##  <a name="isdefaultbutton"></a>COleControlSite::IsDefaultButton  
 Określa, czy formant jest przycisk domyślny.  
  
```  
BOOL IsDefaultButton();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli kontrolka znajduje się przycisk domyślny w oknie, w przeciwnym razie wartość zero.  
  
##  <a name="iswindowenabled"></a>COleControlSite::IsWindowEnabled  
 Określa, czy włączono kontroli lokacji.  
  
```  
virtual BOOL IsWindowEnabled() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli formant jest włączony, w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Wartość jest pobierana z właściwości standardowych włączone formantu.  
  
##  <a name="m_biswindowless"></a>COleControlSite::m_bIsWindowless  
 Określa, czy obiekt jest formantem bez okien.  
  
```  
BOOL m_bIsWindowless;  
```  
  
### <a name="remarks"></a>Uwagi  
 Różna od zera, jeśli formant nie ma żadnego okna, w przeciwnym razie wartość zero.  
  
##  <a name="m_ctlinfo"></a>COleControlSite::m_ctlInfo  
 Informacje na temat sposobu obsługi danych wprowadzonych z klawiatury przez formant.  
  
```  
CONTROLINFO m_ctlInfo;  
```  
  
### <a name="remarks"></a>Uwagi  
 Te informacje są przechowywane w [CONTROLINFO](http://msdn.microsoft.com/library/windows/desktop/ms680734) struktury.  
  
##  <a name="m_dweventsink"></a>COleControlSite::m_dwEventSink  
 Zawiera plik cookie punkt połączenia z obiektu sink zdarzenia formantu.  
  
```  
DWORD m_dwEventSink;  
```  
  
##  <a name="m_dwmiscstatus"></a>COleControlSite::m_dwMiscStatus  
 Zawiera dodatkowe informacje dotyczące formantu.  
  
```  
DWORD m_dwMiscStatus;  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)w zestawie Windows SDK.  
  
##  <a name="m_dwpropnotifysink"></a>COleControlSite::m_dwPropNotifySink  
 Zawiera [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) pliku cookie.  
  
```  
DWORD m_dwPropNotifySink;  
```  
  
##  <a name="m_dwstyle"></a>COleControlSite::m_dwStyle  
 Zawiera style okna formantu.  
  
```  
DWORD m_dwStyle;  
```  
  
##  <a name="m_hwnd"></a>COleControlSite::m_hWnd  
 Zawiera `HWND` formantu, lub **NULL** Jeśli formant jest powiązany z oknami.  
  
```  
HWND m_hWnd;  
```  
  
##  <a name="m_iidevents"></a>COleControlSite::m_iidEvents  
 Zawiera identyfikator interfejsu interfejsu obiekt sink zdarzenia domyślne formantu.  
  
```  
IID m_iidEvents;  
```  
  
##  <a name="m_nid"></a>COleControlSite::m_nID  
 Zawiera identyfikator formantu okna dialogowego elementu.  
  
```  
UINT m_nID;  
```  
  
##  <a name="m_pactiveobject"></a>COleControlSite::m_pActiveObject  
 Zawiera [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) interfejsu formantu.  
  
```  
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;  
```  
  
##  <a name="m_pctrlcont"></a>COleControlSite::m_pCtrlCont  
 Zawiera formantu kontenera (formularz reprezentujący).  
  
```  
COleControlContainer* m_pCtrlCont;  
```  
  
##  <a name="m_pinplaceobject"></a>COleControlSite::m_pInPlaceObject  
 Zawiera `IOleInPlaceObject` [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) interfejsu formantu.  
  
```  
LPOLEINPLACEOBJECT m_pInPlaceObject;  
```  
  
##  <a name="m_pobject"></a>COleControlSite::m_pObject  
 Zawiera **IOleObjectInterface** interfejsu formantu.  
  
```  
LPOLEOBJECT m_pObject;  
```  
  
##  <a name="m_pwindowlessobject"></a>COleControlSite::m_pWindowlessObject  
 Zawiera `IOleInPlaceObjectWindowless` [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304) interfejsu formantu.  
  
```  
IOleInPlaceObjectWindowless* m_pWindowlessObject;  
```  
  
##  <a name="m_pwndctrl"></a>COleControlSite::m_pWndCtrl  
 Zawiera wskaźnik do `CWnd` obiekt, który reprezentuje samego formantu.  
  
```  
CWnd* m_pWndCtrl;  
```  
  
##  <a name="m_rect"></a>COleControlSite::m_rect  
 Zawiera granice kontroli względem kontenera okna.  
  
```  
CRect m_rect;  
```  
  
##  <a name="modifystyle"></a>COleControlSite::ModifyStyle  
 Modyfikuje stylów formantu.  
  
```  
virtual BOOL ModifyStyle(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `dwRemove`  
 Style do usunięcia z bieżącego Style okna.  
  
 `dwAdd`  
 Style, które ma zostać dodana z style bieżącego okna.  
  
 `nFlags`  
 Okno pozycjonowanie flagi. Aby uzyskać listę możliwych wartości, zobacz [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) funkcji w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeżeli style są zmieniane, w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Stock formantu Właściwość Enabled zostaną zmodyfikowane i odpowiadają ustawieniom **ws_disabled —**. Właściwości standardowych styl obramowania formantu zostaną zmodyfikowane i odpowiadają ustawieniom żądanego `WS_BORDER`. Wszystkie inne style są stosowane bezpośrednio do uchwytu okna dla formantu, jeśli występuje.  
  
 Modyfikuje style okna formantu. Style, które mają zostać dodane lub usunięte można łączyć przy użyciu wartości bitowe lub (&#124;) — operator. Zobacz [właściwości CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) funkcji w zestawie Windows SDK dla informacji o style dostępnym oknie.  
  
 Jeśli `nFlags` jest różna od zera, `ModifyStyle` wywołania funkcji Win32 `SetWindowPos`i ponownie rysuje okna łącząc `nFlags` z następujących czterech flag:  
  
- `SWP_NOSIZE`Zachowuje bieżący rozmiar.  
  
- `SWP_NOMOVE`Zachowuje bieżące położenie.  
  
- `SWP_NOZORDER`Zachowuje bieżący porządek osi.  
  
- `SWP_NOACTIVATE`Nie aktywować okna.  
  
 Aby zmodyfikować okna na rozszerzone style, wywołania [ModifyStyleEx](#modifystyleex).  
  
##  <a name="modifystyleex"></a>COleControlSite::ModifyStyleEx  
 Modyfikuje rozszerzone style formantu.  
  
```  
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `dwRemove`  
 Rozszerzone style do usunięcia z bieżącego Style okna.  
  
 `dwAdd`  
 Rozszerzone style ma zostać dodana z style bieżącego okna.  
  
 `nFlags`  
 Okno pozycjonowanie flagi. Aby uzyskać listę możliwych wartości, zobacz [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) funkcji w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeżeli style są zmieniane, w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Właściwości standardowych wygląd formantu zostaną zmodyfikowane i odpowiadają ustawieniom **WS_EX_CLIENTEDGE**. Wszystkie inne rozszerzone Style okna są stosowane bezpośrednio do uchwytu okna dla formantu, jeśli występuje.  
  
 Modyfikuje okna rozszerzone style obiektu kontroli lokacji. Style, które mają zostać dodane lub usunięte można łączyć przy użyciu wartości bitowe lub (&#124;) — operator. Zobacz [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) funkcji w zestawie Windows SDK dla informacji o style dostępnym oknie.  
  
 Jeśli `nFlags` jest różna od zera, `ModifyStyleEx` wywołania funkcji Win32 `SetWindowPos`i ponownie rysuje okna łącząc `nFlags` z następujących czterech flag:  
  
- `SWP_NOSIZE`Zachowuje bieżący rozmiar.  
  
- `SWP_NOMOVE`Zachowuje bieżące położenie.  
  
- `SWP_NOZORDER`Zachowuje bieżący porządek osi.  
  
- `SWP_NOACTIVATE`Nie aktywować okna.  
  
 Aby zmodyfikować okna na rozszerzone style, wywołania [ModifyStyle](#modifystyle).  
  
##  <a name="movewindow"></a>COleControlSite::MoveWindow  
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
 Nowa pozycja lewej części okna.  
  
 *y*  
 Nowa pozycja górnej części okna.  
  
 `nWidth`  
 Nową szerokość okna  
  
 `nHeight`  
 Nową wysokość okna.  
  
##  <a name="quickactivate"></a>COleControlSite::QuickActivate  
 Szybkie aktywuje formant zawartych w niej.  
  
```  
virtual BOOL QuickActivate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli uaktywniono sterowania lokacji, w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna być wywoływana tylko wtedy, gdy użytkownik zastępuje procesu tworzenia formantu.  
  
 `IPersist*::Load` i `IPersist*::InitNew` metody powinna być wywoływana po wystąpieniu szybkie aktywacji. Formant należy określić jego połączenia z wychwytywanie kontenera podczas szybkiego aktywacji. Połączenia te nie są jednak na żywo do `IPersist*::Load` lub `IPersist*::InitNew` została wywołana.  
  
##  <a name="safesetproperty"></a>COleControlSite::SafeSetProperty  
 Ustawia właściwość formantu określony przez `dwDispID`.  
  
```  
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Określa identyfikator wysyłania właściwości lub metody, na formantu `IDispatch` interfejsu, należy ustawić wartość.  
  
 `vtProp`  
 Określa typ właściwości do ustawienia. Możliwe wartości w sekcji uwag dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Pojedynczy parametr typu określony przez `vtProp`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  W odróżnieniu od `SetProperty` i `SetPropertyV`, jeśli wystąpił błąd (na przykład próby ustawienia właściwości nieistniejącą), nie jest wyjątek.  
  
##  <a name="setdefaultbutton"></a>COleControlSite::SetDefaultButton  
 Formant jako przycisk domyślny.  
  
```  
void SetDefaultButton(BOOL bDefault);
```  
  
### <a name="parameters"></a>Parametry  
 `bDefault`  
 Różna od zera, jeśli formant powinien być przycisk domyślny; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Kontrolka musi mieć **OLEMISC_ACTSLIKEBUTTON** bitu stanu.  
  
##  <a name="setdlgctrlid"></a>COleControlSite::SetDlgCtrlID  
 Zmienia wartość Identyfikator elementu okna dialogowego formantu.  
  
```  
virtual int SetDlgCtrlID(int nID);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Nowa wartość identyfikatora.  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia poprzedniego okna dialogowego elementu identyfikator okna; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setfocus"></a>COleControlSite::SetFocus  
 Ustawia fokus do formantu.  
  
```  
virtual CWnd* SetFocus();  
virtual CWnd* SetFocus(LPMSG lpmsg);
```  
  
### <a name="parameters"></a>Parametry  
 *lpmsg*  
 Wskaźnik do [struktura MSG](../../mfc/reference/msg-structure1.md). Ta struktura zawiera wyzwalania wiadomości Windows `SetFocus` żądania kontroli zawarte w bieżącej witrynie formant.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do okna, który wcześniej był aktywny.  
  
##  <a name="setproperty"></a>COleControlSite::SetProperty  
 Ustawia właściwość formantu określony przez `dwDispID`.  
  
```  
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Określa identyfikator wysyłania właściwości lub metody, na formantu `IDispatch` interfejsu, należy ustawić wartość.  
  
 `vtProp`  
 Określa typ właściwości do ustawienia. Możliwe wartości w sekcji uwag dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Pojedynczy parametr typu określony przez `vtProp`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `SetProperty` napotka błąd, jest zgłaszany wyjątek.  
  
 Typ wyjątku jest określany przez wartość zwracaną próba ustawienia właściwości lub metody. Jeśli wartość zwracana jest `DISP_E_EXCEPTION`, **COleDispatchExcpetion** zgłoszenia; w przeciwnym razie `COleException`.  
  
##  <a name="setpropertyv"></a>COleControlSite::SetPropertyV  
 Ustawia właściwość formantu określony przez `dwDispID`.  
  
```  
virtual void SetPropertyV(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    va_list argList);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Określa identyfikator wysyłania właściwości lub metody, na formantu `IDispatch` interfejsu, należy ustawić wartość.  
  
 `vtProp`  
 Określa typ właściwości do ustawienia. Możliwe wartości w sekcji uwag dla [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `argList`  
 Wskaźnik do listy argumentów.  
  
### <a name="remarks"></a>Uwagi  
 Dodatkowe parametry dla metody lub właściwości wywoływaną mogą być passeed przy użyciu *arg_list* parametru. Jeśli `SetProperty` napotka błąd, jest zgłaszany wyjątek.  
  
 Typ wyjątku jest określany przez wartość zwracaną próba ustawienia właściwości lub metody. Jeśli wartość zwracana jest `DISP_E_EXCEPTION`, **COleDispatchExcpetion** zgłoszenia; w przeciwnym razie `COleException`.  
  
##  <a name="setwindowpos"></a>COleControlSite::SetWindowPos  
 Ustawia położenie, rozmiar i porządek osi z kontroli lokacji.  
  
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
 `pWndInsertAfter`  
 Wskaźnik do okna.  
  
 *x*  
 Nowa pozycja lewej części okna.  
  
 *y*  
 Nowa pozycja górnej części okna.  
  
 `cx`  
 Nową szerokość okna  
  
 `cy`  
 Nową wysokość okna.  
  
 `nFlags`  
 Określa okno zmiany rozmiaru i pozycjonowania flagi. Możliwe wartości w sekcji uwag dla [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli to się powiedzie, w przeciwnym razie wartość zero.  
  
##  <a name="setwindowtext"></a>COleControlSite::SetWindowText  
 Ustawia tekst kontroli lokacji.  
  
```  
virtual void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszString`  
 Wskaźnik do ciągu zerem służący jako nowy tekst tytułu lub formantu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja najpierw próbuje ustawić właściwości podpisu podstawowego. Jeśli właściwość standardowych podpis nie jest obsługiwana, jest Ustaw zamiast tego właściwość Text.  
  
##  <a name="showwindow"></a>COleControlSite::ShowWindow  
 Ustawia okna Pokaż stan.  
  
```  
virtual BOOL ShowWindow(int nCmdShow);
```  
  
### <a name="parameters"></a>Parametry  
 `nCmdShow`  
 Określa, jak ma być wyświetlana kontroli lokacji. Musi to być jedna z następujących wartości:  
  
- **SW_HIDE** ukrywa okno i przekazuje aktywacji do innego okna.  
  
- **SW_MINIMIZE** minimalizuje okno i aktywuje okno najwyższego poziomu w liście systemu.  
  
- **SW_RESTORE** Activates i wyświetla okno. Jeśli okno jest zminimalizowane lub zmaksymalizowane, Windows przywracania go w jego oryginalny rozmiar i położenie.  
  
- **SW_SHOW** uaktywnia okno i wyświetla je w jego bieżący rozmiar i położenie.  
  
- **SW_SHOWMAXIMIZED** uaktywnia okno i wyświetla je jako okno zmaksymalizowane.  
  
- **SW_SHOWMINIMIZED** uaktywnia okno i wyświetla je w postaci ikony.  
  
- **SW_SHOWMINNOACTIVE** Wyświetla okna w postaci ikony. Okno, który jest obecnie aktywny pozostaje aktywna.  
  
- **SW_SHOWNA** Wyświetla okno w bieżącym stanie. Okno, który jest obecnie aktywny pozostaje aktywna.  
  
- **SW_SHOWNOACTIVATE** Wyświetla okna w najnowszych rozmiar i położenie. Okno, który jest obecnie aktywny pozostaje aktywna.  
  
- **SW_SHOWNORMAL** Activates i wyświetla okno. Jeśli okno jest zminimalizowane lub zmaksymalizowane, Windows przywracania go w jego oryginalny rozmiar i położenie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli okno było widoczne wcześniej; 0, jeśli okno zostało wcześniej ukryte.  
  
## <a name="see-also"></a>Zobacz też  
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)
