---
title: Klasa IOleObjectImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl::Advise
- ATLCTL/ATL::IOleObjectImpl::Close
- ATLCTL/ATL::IOleObjectImpl::DoVerb
- ATLCTL/ATL::IOleObjectImpl::DoVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::DoVerbHide
- ATLCTL/ATL::IOleObjectImpl::DoVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::DoVerbOpen
- ATLCTL/ATL::IOleObjectImpl::DoVerbPrimary
- ATLCTL/ATL::IOleObjectImpl::DoVerbShow
- ATLCTL/ATL::IOleObjectImpl::DoVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::EnumAdvise
- ATLCTL/ATL::IOleObjectImpl::EnumVerbs
- ATLCTL/ATL::IOleObjectImpl::GetClientSite
- ATLCTL/ATL::IOleObjectImpl::GetClipboardData
- ATLCTL/ATL::IOleObjectImpl::GetExtent
- ATLCTL/ATL::IOleObjectImpl::GetMiscStatus
- ATLCTL/ATL::IOleObjectImpl::GetMoniker
- ATLCTL/ATL::IOleObjectImpl::GetUserClassID
- ATLCTL/ATL::IOleObjectImpl::GetUserType
- ATLCTL/ATL::IOleObjectImpl::InitFromData
- ATLCTL/ATL::IOleObjectImpl::IsUpToDate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::SetClientSite
- ATLCTL/ATL::IOleObjectImpl::SetColorScheme
- ATLCTL/ATL::IOleObjectImpl::SetExtent
- ATLCTL/ATL::IOleObjectImpl::SetHostNames
- ATLCTL/ATL::IOleObjectImpl::SetMoniker
- ATLCTL/ATL::IOleObjectImpl::Unadvise
- ATLCTL/ATL::IOleObjectImpl::Update
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f710953a32ccb32c63742ab28e84818f3a330336
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ioleobjectimpl-class"></a>Klasa IOleObjectImpl
Ta klasa implementuje **IUnknown** i jest główną interfejs, za pomocą którego kontener komunikuje się za pomocą formantu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IOleObjectImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IOleObjectImpl::Advise](#advise)|Ustanawia połączenie advisory z formantem.|  
|[IOleObjectImpl::Close](#close)|Zmienia stan formantu uruchomienie załadowany.|  
|[IOleObjectImpl::DoVerb](#doverb)|Określa, że formant wykonanie jednej z jego wyliczany akcji.|  
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Określa, że formant, aby odrzucić wszystkie stany cofania, których obsługi.|  
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Określa, że formant Usuń interfejs użytkownika z widoku.|  
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Uruchamia formantu i instaluje okna, ale nie można zainstalować formantu interfejsu użytkownika.|  
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Powoduje, że formant można edytowane otwarty w osobnym oknie.|  
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Wykonuje określoną akcję, gdy użytkownik kliknie dwukrotnie formantu. Formant definiuje akcji, zazwyczaj w celu aktywowania formantu w miejscu.|  
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Pokazuje nowo wstawionej kontroli dla użytkownika.|  
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Aktywuje formant w miejscu i pokazuje formantu interfejsu użytkownika, takich jak menu i pasków narzędzi.|  
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Wylicza połączeń advisory formantu.|  
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Wylicza akcje dla formantu.|  
|[IOleObjectImpl::GetClientSite](#getclientsite)|Pobiera formantu lokacji klienta.|  
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Pobiera dane ze Schowka. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::GetExtent](#getextent)|Pobiera zakres obszar wyświetlania formantu.|  
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Pobiera stan formantu.|  
|[IOleObjectImpl::GetMoniker](#getmoniker)|Pobiera moniker formantu. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Pobiera identyfikator klasy formantu.|  
|[IOleObjectImpl::GetUserType](#getusertype)|Pobiera nazwę użytkownika — typ formantu.|  
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicjuje formantu z wybranych danych. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Sprawdza, czy formant jest aktualny. Zwraca implementację ATL `S_OK`.|  
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) po poprzedni stan zostaną odrzucone.|  
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Wywoływane przez [DoVerbHide](#doverbhide) po formant jest ukryty.|  
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) po aktywowaniu formantu w miejscu.|  
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Wywoływane przez [DoVerbOpen](#doverbopen) po formant został otwarty do edycji w osobnym oknie.|  
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Wywoływane przez [DoVerbShow](#doverbshow) po formantu widoczne.|  
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) po uaktywnieniu formantu interfejsu użytkownika.|  
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) przed cofnięcie stanu zostaną odrzucone.|  
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Wywoływane przez [DoVerbHide](#doverbhide) zanim formant jest ukryty.|  
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) aktywowania formantu w miejscu.|  
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Wywoływane przez [DoVerbOpen](#doverbopen) zanim formant został otwarty do edycji w osobnym oknie.|  
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Wywoływane przez [DoVerbShow](#doverbshow) przed formantu stało się widoczne.|  
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) przed formantu interfejsu użytkownika został aktywowany.|  
|[IOleObjectImpl::SetClientSite](#setclientsite)|Określa, że formant o jego lokacji klienta w kontenerze.|  
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Zaleca schemat kolorów aplikacji formantu, jeśli istnieje. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::SetExtent](#setextent)|Ustawia zakres obszar wyświetlania formantu.|  
|[IOleObjectImpl::SetHostNames](#sethostnames)|Określa, że kontrolka nazwy aplikacji kontenera i kontenerem.|  
|[IOleObjectImpl::SetMoniker](#setmoniker)|Określa, że formant jest jego nazwie. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::Unadvise](#unadvise)|Usuwa advisory połączenia za pomocą formantu.|  
|[IOleObjectImpl::Update](#update)|Aktualizuje formantu. Zwraca implementację ATL `S_OK`.|  
  
## <a name="remarks"></a>Uwagi  
 [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709) interfejs jest interfejsem podmiotu zabezpieczeń, za pomocą którego kontener komunikuje się za pomocą formantu. Klasa `IOleObjectImpl` udostępnia domyślną implementację tego interfejsu i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IOleObject`  
  
 `IOleObjectImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="advise"></a>IOleObjectImpl::Advise  
 Ustanawia połączenie advisory z formantem.  
  
```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573) w systemie Windows SDK.  
  
##  <a name="close"></a>IOleObjectImpl::Close  
 Zmienia stan formantu uruchomienie załadowany.  
  
```
STDMETHOD(Close)(DWORD dwSaveOption);
```  
  
### <a name="remarks"></a>Uwagi  
 Dezaktywuje formantu i niszczy okno kontrolki, jeśli istnieje. Jeśli element członkowski danych klasy formantu [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) jest **TRUE** i `dwSaveOption` parametru jest `OLECLOSE_SAVEIFDIRTY` lub `OLECLOSE_PROMPTSAVE`, właściwości są zapisywane. przed zamknięciem.  
  
 Wskaźniki przechowywać w formacie elementy członkowskie danych klasy formantu [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) i [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) są wydawane i elementy członkowskie danych [CComControlBase:: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless), i [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) ustawiono **FALSE**.  
  
 Zobacz [IOleObject::Close](http://msdn.microsoft.com/library/windows/desktop/ms683922) w systemie Windows SDK.  
  
##  <a name="doverb"></a>IOleObjectImpl::DoVerb  
 Określa, że formant wykonanie jednej z jego wyliczany akcji.  
  
```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```  
  
### <a name="remarks"></a>Uwagi  
 W zależności od wartości `iVerb`, jeden ATL `DoVerb` funkcji pomocnika jest wywoływana w następujący sposób:  
  
|*iVerb* wartości|Funkcja pomocnika DoVerb o nazwie|  
|-------------------|-----------------------------------|  
|**OLEIVERB_DISCARDUNDOSTATE**|[DoVerbDiscardUndo](#doverbdiscardundo)|  
|`OLEIVERB_HIDE`|[DoVerbHide](#doverbhide)|  
|**OLEIVERB_INPLACEACTIVATE**|[DoVerbInPlaceActivate](#doverbinplaceactivate)|  
|`OLEIVERB_OPEN`|[DoVerbOpen](#doverbopen)|  
|`OLEIVERB_PRIMARY`|[DoVerbPrimary](#doverbprimary)|  
|**OLEIVERB_PROPERTIES**|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|  
|`OLEIVERB_SHOW`|[DoVerbShow](#doverbshow)|  
|`OLEIVERB_UIACTIVATE`|[DoVerbUIActivate](#doverbuiactivate)|  
  
 Zobacz [IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) w systemie Windows SDK.  
  
##  <a name="doverbdiscardundo"></a>IOleObjectImpl::DoVerbDiscardUndo  
 Określa, że formant, aby odrzucić wszystkie stany cofania, których obsługi.  
  
```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [in] Wskaźnik do prostokąta kontenera chce formantu do rysowania do.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego ten formant.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
##  <a name="doverbhide"></a>IOleObjectImpl::DoVerbHide  
 Dezaktywuje usuwa formantu interfejsu użytkownika i ukrywa formantu.  
  
```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [in] Wskaźnik do prostokąta kontenera chce formantu do rysowania do.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego ten formant. Nie są używane w celu wykonania ATL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
##  <a name="doverbinplaceactivate"></a>IOleObjectImpl::DoVerbInPlaceActivate  
 Uruchamia formantu i instaluje okna, ale nie można zainstalować formantu interfejsu użytkownika.  
  
```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [in] Wskaźnik do prostokąta kontenera chce formantu do rysowania do.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego ten formant. Nie są używane w celu wykonania ATL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
### <a name="remarks"></a>Uwagi  
 Aktywuje formant w miejscu, wywołując [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). Jeśli element członkowski danych klasy formantu `m_bWindowOnly` jest **TRUE**, `DoVerbInPlaceActivate` najpierw próbuje aktywować formant jako formantem bez okien (możliwe tylko wtedy, gdy kontener obsługuje [IOleInPlaceSiteWindowless ](http://msdn.microsoft.com/library/windows/desktop/ms682300)). W przypadku niepowodzenia funkcji umożliwia przeprowadzenie próby aktywacji formantu o rozszerzonych funkcji (możliwe tylko wtedy, gdy kontener obsługuje [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)). W przypadku niepowodzenia funkcji umożliwia przeprowadzenie próby aktywacji kontrolki z nie rozszerzonych funkcji (możliwe tylko wtedy, gdy kontener obsługuje [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)). Jeśli aktywacja zakończy się powodzeniem, funkcja powiadamia kontenera formant został aktywowany.  
  
##  <a name="doverbopen"></a>IOleObjectImpl::DoVerbOpen  
 Powoduje, że formant można edytowane otwarty w osobnym oknie.  
  
```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [in] Wskaźnik do prostokąta kontenera chce formantu do rysowania do.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego ten formant.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
##  <a name="doverbprimary"></a>IOleObjectImpl::DoVerbPrimary  
 Określa akcję wykonywaną, gdy użytkownik kliknie dwukrotnie formantu.  
  
```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [in] Wskaźnik do prostokąta kontenera chce formantu do rysowania do.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego ten formant.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie do wyświetlenia strony właściwości. Można zmienić w Twojej klasy kontrolki do wywołania, inaczej po dwukrotnym kliknięciu; na przykład odtwarzanie wideo lub przejdź aktywny w miejscu.  
  
##  <a name="doverbshow"></a>IOleObjectImpl::DoVerbShow  
 Określa, że kontener, aby uwidocznić formantu.  
  
```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [in] Wskaźnik do prostokąta kontenera chce formantu do rysowania do.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego ten formant. Nie są używane w celu wykonania ATL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
##  <a name="doverbuiactivate"></a>IOleObjectImpl::DoVerbUIActivate  
 Aktywuje formantu interfejsu użytkownika i powiadamia kontener o tym, że jego menu są zastępowane przez złożone menu.  
  
```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [in] Wskaźnik do prostokąta kontenera chce formantu do rysowania do.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego ten formant. Nie są używane w celu wykonania ATL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
##  <a name="enumadvise"></a>IOleObjectImpl::EnumAdvise  
 Dostarcza wyliczenie zarejestrowanych advisory połączeń dla tego formantu.  
  
```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::EnumAdvise](http://msdn.microsoft.com/library/windows/desktop/ms682355) w systemie Windows SDK.  
  
##  <a name="enumverbs"></a>IOleObjectImpl::EnumVerbs  
 Dostarcza wyliczenie zarejestrowanych działań (poleceń) dla tego formantu, wywołując **OleRegEnumVerbs**.  
  
```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```  
  
### <a name="remarks"></a>Uwagi  
 Zlecenia można dodać do pliku .rgs projektu. Na przykład zobacz CIRCCTL. RGS w [OK](../../visual-cpp-samples.md) próbki.  
  
 Zobacz [IOleObject::EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781) w systemie Windows SDK.  
  
##  <a name="getclientsite"></a>IOleObjectImpl::GetClientSite  
 Umieszcza kursor w element członkowski danych klasy formantu [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) do *ppClientSite* i zwiększa liczbę odwołanie wskaźnika.  
  
```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::GetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms692603) w systemie Windows SDK.  
  
##  <a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData  
 Pobiera dane ze Schowka.  
  
```
STDMETHOD(GetClipboardData)(    
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/ms682288) w systemie Windows SDK.  
  
##  <a name="getextent"></a>IOleObjectImpl::GetExtent  
 Pobiera rozmiar wyświetlania formantu uruchomionej w jednostkach HIMETRIC (0,01 milimetra na jednostkę).  
  
```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar jest przechowywany w element członkowski danych klasy formantu [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).  
  
 Zobacz [IOleObject::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms692325) w systemie Windows SDK.  
  
##  <a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus  
 Zwraca wskaźnik do informacji o stanie zastrzeżonymi formantu przez wywołanie metody **OleRegGetMiscStatus**.  
  
```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>Uwagi  
 Informacje o stanie obejmuje zachowania obsługiwane przez formant i prezentacji danych. Informacje o stanie można dodać do pliku .rgs projektu.  
  
 Zobacz [IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521) w systemie Windows SDK.  
  
##  <a name="getmoniker"></a>IOleObjectImpl::GetMoniker  
 Pobiera moniker formantu.  
  
```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::GetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms686576) w systemie Windows SDK.  
  
##  <a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID  
 Zwraca identyfikator klasy formantu.  
  
```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::GetUserClassID](http://msdn.microsoft.com/library/windows/desktop/ms682313) w systemie Windows SDK.  
  
##  <a name="getusertype"></a>IOleObjectImpl::GetUserType  
 Zwraca nazwę użytkownika — typ formantu przez wywołanie metody **OleRegGetUserType**.  
  
```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```  
  
### <a name="remarks"></a>Uwagi  
 Nazwa typu użytkownika jest używana do wyświetlania na interfejsy użytkownika elementów, takich jak menu i okien dialogowych. Można zmienić nazwy typu użytkownika w pliku .rgs projektu.  
  
 Zobacz [IOleObject::GetUserType](http://msdn.microsoft.com/library/windows/desktop/ms688643) w systemie Windows SDK.  
  
##  <a name="initfromdata"></a>IOleObjectImpl::InitFromData  
 Inicjuje formantu z wybranych danych.  
  
```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) w systemie Windows SDK.  
  
##  <a name="isuptodate"></a>IOleObjectImpl::IsUpToDate  
 Sprawdza, czy formant jest aktualny.  
  
```
STDMETHOD(IsUpToDate)(void);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::IsUpToDate](http://msdn.microsoft.com/library/windows/desktop/ms686624) w systemie Windows SDK.  
  
##  <a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo  
 Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) po poprzedni stan zostaną odrzucone.  
  
```
HRESULT OnPostVerbDiscardUndo();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej metody za pomocą kodu, który ma być wykonywane po poprzedni stan zostaną odrzucone.  
  
##  <a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide  
 Wywoływane przez [DoVerbHide](#doverbhide) po formant jest ukryty.  
  
```
HRESULT OnPostVerbHide();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej metody za pomocą kodu, który ma być wykonywane po formant jest ukryty.  
  
##  <a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate  
 Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) po aktywowaniu formantu w miejscu.  
  
```
HRESULT OnPostVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej metody za pomocą kodu, który ma być wykonywane po uaktywnieniu formantu w miejscu.  
  
##  <a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen  
 Wywoływane przez [DoVerbOpen](#doverbopen) po formant został otwarty do edycji w osobnym oknie.  
  
```
HRESULT OnPostVerbOpen();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę z kodem, który ma zostać wykonana po formant został otwarty do edycji w osobnym oknie.  
  
##  <a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow  
 Wywoływane przez [DoVerbShow](#doverbshow) po formantu widoczne.  
  
```
HRESULT OnPostVerbShow();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę z kodem, który ma być wykonywane po formantu widoczne.  
  
##  <a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate  
 Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) po uaktywnieniu formantu interfejsu użytkownika.  
  
```
HRESULT OnPostVerbUIActivate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę z kodem, który ma zostać wykonana po uaktywnieniu formantu interfejsu użytkownika.  
  
##  <a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo  
 Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) przed cofnięcie stanu zostaną odrzucone.  
  
```
HRESULT OnPreVerbDiscardUndo();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Aby zapobiec poprzedni stan zostanie odrzucony, należy przesłonić tę metodę do zwrócony błąd HRESULT.  
  
##  <a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide  
 Wywoływane przez [DoVerbHide](#doverbhide) zanim formant jest ukryty.  
  
```
HRESULT OnPreVerbHide();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Aby zapobiec ukrywane formantu, należy przesłonić tę metodę do zwrócony błąd HRESULT.  
  
##  <a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate  
 Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) aktywowania formantu w miejscu.  
  
```
HRESULT OnPreVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Aby zapobiec formantu aktywowana w miejscu, należy przesłonić tę metodę do zwrócony błąd HRESULT.  
  
##  <a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen  
 Wywoływane przez [DoVerbOpen](#doverbopen) zanim formant został otwarty do edycji w osobnym oknie.  
  
```
HRESULT OnPreVerbOpen();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Aby zapobiec formantu jest otwarty do edycji w osobnym oknie, należy przesłonić tę metodę do zwrócony błąd HRESULT.  
  
##  <a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow  
 Wywoływane przez [DoVerbShow](#doverbshow) przed formantu stało się widoczne.  
  
```
HRESULT OnPreVerbShow();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Aby zapobiec formantu jest widoczne, należy przesłonić tę metodę do zwrócony błąd HRESULT.  
  
##  <a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate  
 Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) przed formantu interfejsu użytkownika został aktywowany.  
  
```
HRESULT OnPreVerbUIActivate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Aby zapobiec aktywowane formantu interfejsu użytkownika, należy przesłonić tę metodę do zwrócony błąd HRESULT.  
  
##  <a name="setclientsite"></a>IOleObjectImpl::SetClientSite  
 Określa, że formant o jego lokacji klienta w kontenerze.  
  
```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```  
  
### <a name="remarks"></a>Uwagi  
 Następnie metoda zwraca `S_OK`.  
  
 Zobacz [IOleObject::SetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms684013) w systemie Windows SDK.  
  
##  <a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme  
 Zaleca schemat kolorów aplikacji formantu, jeśli istnieje.  
  
```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) w systemie Windows SDK.  
  
##  <a name="setextent"></a>IOleObjectImpl::SetExtent  
 Ustawia zakres obszar wyświetlania formantu.  
  
```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>Uwagi  
 W przeciwnym razie `SetExtent` przechowuje wartość wskazywana przez `psizel` w element członkowski danych klasy formantu [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Ta wartość jest wyrażona w jednostkach HIMETRIC (0,01 milimetra na jednostkę).  
  
 Jeśli element członkowski danych klasy formantu [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) jest **TRUE**, `SetExtent` przechowuje także wartość wskazywana przez `psizel` w element członkowski danych klasy formantu [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).  
  
 Jeśli element członkowski danych klasy formantu [CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) jest **TRUE**, `SetExtent` wywołania `SendOnDataChange` i `SendOnViewChange` powiadomiono wszystkich wychwytywanie advisory zarejestrowany Zalecamy symbol zastępczy, że został zmieniony rozmiar formantu.  
  
 Zobacz [IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330) w systemie Windows SDK.  
  
##  <a name="sethostnames"></a>IOleObjectImpl::SetHostNames  
 Określa, że kontrolka nazwy aplikacji kontenera i kontenerem.  
  
```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::SetHostNames](http://msdn.microsoft.com/library/windows/desktop/ms680642) w systemie Windows SDK.  
  
##  <a name="setmoniker"></a>IOleObjectImpl::SetMoniker  
 Określa, że formant jest jego nazwie.  
  
```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::SetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679671) w systemie Windows SDK.  
  
##  <a name="unadvise"></a>IOleObjectImpl::Unadvise  
 Usuwa advisory połączenia, przechowywane w klasy formantu `m_spOleAdviseHolder` element członkowski danych.  
  
```
STDMETHOD(Unadvise)(DWORD dwConnection);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749) w systemie Windows SDK.  
  
##  <a name="update"></a>IOleObjectImpl::Update  
 Aktualizuje formantu.  
  
```
STDMETHOD(Update)(void);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::Update](http://msdn.microsoft.com/library/windows/desktop/ms679699) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Interfejsy formantów ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Przegląd klas](../../atl/atl-class-overview.md)
