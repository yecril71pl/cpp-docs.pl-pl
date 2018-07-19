---
title: Klasa IOleObjectImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aec4de071df8dcca960a0f1cb802375e5553ceb3
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880307"
---
# <a name="ioleobjectimpl-class"></a>Klasa IOleObjectImpl
Ta klasa implementuje `IUnknown` i jest główną interfejs, za pomocą którego kontener komunikuje się za pomocą kontrolki.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IOleObjectImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IOleObjectImpl::Advise](#advise)|Ustanawia połączenie doradztwa technicznego dotyczącego za pomocą kontrolki.|  
|[IOleObjectImpl::Close](#close)|Zmienia stan formantu uruchamianie załadowane.|  
|[IOleObjectImpl::DoVerb](#doverb)|Informuje kontroli, wykonaj jedną z jego akcje wyliczany.|  
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Informuje formant aby odrzucić wszystkie stany cofania, których obsługi.|  
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Informuje formant Aby usunąć jego interfejs użytkownika z widoku.|  
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Zawsze uruchamiany i instaluje okna, ale nie można zainstalować kontrolki interfejsu użytkownika.|  
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Powoduje, że formantu ma być edytowany otwarte w oddzielnym oknie.|  
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Wykonuje określoną akcję, gdy użytkownik kliknie dwukrotnie formant. Formant definiuje akcję, zazwyczaj w celu aktywowania kontroli w miejscu.|  
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Pokazuje formant nowo wstawionej użytkownikowi.|  
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Aktywuje formant w miejscu i pokazuje kontrolki interfejsu użytkownika, takich jak menu i paski narzędzi.|  
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Wylicza formantu porad dotyczących połączenia.|  
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Wylicza operacje dla formantu.|  
|[IOleObjectImpl::GetClientSite](#getclientsite)|Pobiera formantu lokacji klienta.|  
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Pobiera dane ze Schowka. Implementacja biblioteki ATL zwraca E_NOTIMPL.|  
|[IOleObjectImpl::GetExtent](#getextent)|Pobiera zakres obszaru wyświetlania kontrolki.|  
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Pobiera stan kontrolki.|  
|[IOleObjectImpl::GetMoniker](#getmoniker)|Pobiera moniker formantu. Implementacja biblioteki ATL zwraca E_NOTIMPL.|  
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Pobiera identyfikator klasy formantu.|  
|[IOleObjectImpl::GetUserType](#getusertype)|Pobiera nazwę użytkownika — typ formantu.|  
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicjuje formantu z wybranych danych. Implementacja biblioteki ATL zwraca E_NOTIMPL.|  
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Sprawdza, czy kontrolka jest aktualny. Implementacja biblioteki ATL, zwraca wartość S_OK.|  
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) po poprzedni stan jest odrzucany.|  
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Wywoływane przez [DoVerbHide](#doverbhide) po formantu jest ukryta.|  
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) po aktywowaniu kontrolki w miejscu.|  
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Wywoływane przez [DoVerbOpen](#doverbopen) po otwarciu formantu do edycji w osobnym oknie.|  
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Wywoływane przez [DoVerbShow](#doverbshow) po kontrolki widoczne.|  
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) po aktywowaniu kontrolki interfejsu użytkownika.|  
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) przed cofania stanu jest odrzucany.|  
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Wywoływane przez [DoVerbHide](#doverbhide) przed formantu jest ukryta.|  
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) zanim kontrolka jest aktywowany w miejscu.|  
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Wywoływane przez [DoVerbOpen](#doverbopen) przed formant został otwarty do edycji w osobnym oknie.|  
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Wywoływane przez [DoVerbShow](#doverbshow) przed kontrolki stało się widoczne.|  
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) przed interfejsu użytkownika formantu został aktywowany.|  
|[IOleObjectImpl::SetClientSite](#setclientsite)|Informuje formantu o swojej lokacji klienta w kontenerze.|  
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Zaleca schemat kolorów kontroli aplikacji, jeśli istnieje. Implementacja biblioteki ATL zwraca E_NOTIMPL.|  
|[IOleObjectImpl::SetExtent](#setextent)|Ustawia maksymalny zakres obszaru wyświetlania kontrolki.|  
|[IOleObjectImpl::SetHostNames](#sethostnames)|Informuje kontrolki nazwy aplikacji kontenera i dokumentu kontenera.|  
|[IOleObjectImpl::SetMoniker](#setmoniker)|Informuje o tym formant jest jego nazwie. Implementacja biblioteki ATL zwraca E_NOTIMPL.|  
|[IOleObjectImpl::Unadvise](#unadvise)|Usuwa doradztwa technicznego dotyczącego połączenia za pomocą kontrolki.|  
|[IOleObjectImpl::Update](#update)|Aktualizuje formantu. Implementacja biblioteki ATL, zwraca wartość S_OK.|  
  
## <a name="remarks"></a>Uwagi  
 [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709) interfejs jest interfejsem podmiotu zabezpieczeń za pomocą którego kontener komunikuje się za pomocą kontrolki. Klasa `IOleObjectImpl` udostępnia domyślną implementację tego interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.  
  
 **Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IOleObject`  
  
 `IOleObjectImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="advise"></a>  IOleObjectImpl::Advise  
 Ustanawia połączenie doradztwa technicznego dotyczącego za pomocą kontrolki.  
  
```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573) w Windows SDK.  
  
##  <a name="close"></a>  IOleObjectImpl::Close  
 Zmienia stan formantu uruchamianie załadowane.  
  
```
STDMETHOD(Close)(DWORD dwSaveOption);
```  
  
### <a name="remarks"></a>Uwagi  
 Dezaktywuje kontrolki i niszczy okno kontrolki, jeśli taki istnieje. Jeśli dane składowej klasy kontrolki [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) ma wartość TRUE i *dwSaveOption* parametr to OLECLOSE_SAVEIFDIRTY lub OLECLOSE_PROMPTSAVE, są właściwości kontrolki zapisane przed zamknięciem.  
  
 Wskaźniki przechowywanych w składowe danych klasy kontrolki [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) i [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) zostaną zwolnione i elementy członkowskie danych [CComControlBase:: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless), i [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) są ustawione na wartość FALSE.  
  
 Zobacz [IOleObject::Close](http://msdn.microsoft.com/library/windows/desktop/ms683922) w Windows SDK.  
  
##  <a name="doverb"></a>  IOleObjectImpl::DoVerb  
 Informuje kontroli, wykonaj jedną z jego akcje wyliczany.  
  
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
 W zależności od wartości `iVerb`, jeden z ATL `DoVerb` funkcji pomocniczych jest wywoływana w następujący sposób:  
  
|*iVerb* wartość|Wywołana funkcja pomocnika DoVerb|  
|-------------------|-----------------------------------|  
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|  
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|  
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|  
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|  
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|  
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|  
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|  
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|  
  
 Zobacz [IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) w Windows SDK.  
  
##  <a name="doverbdiscardundo"></a>  IOleObjectImpl::DoVerbDiscardUndo  
 Informuje formant aby odrzucić wszystkie stany cofania, których obsługi.  
  
```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 *prcPosRec*  
 [in] Wskaźnik do prostokąta kontenera chce, aby formant Aby rysować na.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego kontrolkę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
##  <a name="doverbhide"></a>  IOleObjectImpl::DoVerbHide  
 Dezaktywuje usuwa kontrolki interfejsu użytkownika i ukrywa formantu.  
  
```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 *prcPosRec*  
 [in] Wskaźnik do prostokąta kontenera chce, aby formant Aby rysować na.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego kontrolkę. Nie są używane w celu wykonania ATL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
##  <a name="doverbinplaceactivate"></a>  IOleObjectImpl::DoVerbInPlaceActivate  
 Zawsze uruchamiany i instaluje okna, ale nie można zainstalować kontrolki interfejsu użytkownika.  
  
```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 *prcPosRec*  
 [in] Wskaźnik do prostokąta kontenera chce, aby formant Aby rysować na.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego kontrolkę. Nie są używane w celu wykonania ATL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jedna z wartości HRESULT standardowych.  
  
### <a name="remarks"></a>Uwagi  
 Aktywuje kontrolkę w miejscu, wywołując [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). Chyba że element członkowski danych Twojej klasy kontrolki `m_bWindowOnly` ma wartość PRAWDA, `DoVerbInPlaceActivate` najpierw umożliwia przeprowadzenie próby aktywacji formantu kontrolce (możliwe tylko wtedy, gdy kontener obsługuje [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300)). W przypadku niepowodzenia funkcja umożliwia przeprowadzenie próby aktywacji kontrolki z rozszerzonych funkcji (możliwe tylko wtedy, gdy kontener obsługuje [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)). W przypadku niepowodzenia funkcja umożliwia przeprowadzenie próby aktywacji kontrolki z nie rozszerzonych funkcji (możliwe tylko wtedy, gdy kontener obsługuje [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)). Jeśli aktywacja zakończy się powodzeniem, funkcja powiadamia kontener formantu został aktywowany.  
  
##  <a name="doverbopen"></a>  IOleObjectImpl::DoVerbOpen  
 Powoduje, że formantu ma być edytowany otwarte w oddzielnym oknie.  
  
```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 *prcPosRec*  
 [in] Wskaźnik do prostokąta kontenera chce, aby formant Aby rysować na.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego kontrolkę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
##  <a name="doverbprimary"></a>  IOleObjectImpl::DoVerbPrimary  
 Określa akcję podejmowaną po dwukrotnym kliknięciu formantu.  
  
```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```  
  
### <a name="parameters"></a>Parametry  
 *prcPosRec*  
 [in] Wskaźnik do prostokąta kontenera chce, aby formant Aby rysować na.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego kontrolkę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jedna z wartości HRESULT standardowych.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ustawiony na wyświetlanie strony właściwości. Możesz przesłonić to w klasie kontrolki do wywołania różne zachowanie po dwukrotnym kliknięciu; na przykład odtworzyć wideo lub przejdź aktywny w miejscu.  
  
##  <a name="doverbshow"></a>  IOleObjectImpl::DoVerbShow  
 Informuje o tym kontenerze, aby formant stał się widoczny.  
  
```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 *prcPosRec*  
 [in] Wskaźnik do prostokąta kontenera chce, aby formant Aby rysować na.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego kontrolkę. Nie są używane w celu wykonania ATL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jedna z wartości HRESULT standardowych.  
  
##  <a name="doverbuiactivate"></a>  IOleObjectImpl::DoVerbUIActivate  
 Aktywuje kontrolki interfejsu użytkownika i powiadamia kontenera, że jego menu są zastępowane przez złożone menu.  
  
```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 *prcPosRec*  
 [in] Wskaźnik do prostokąta kontenera chce, aby formant Aby rysować na.  
  
 *hwndParent*  
 [in] Uchwyt okna zawierającego kontrolkę. Nie są używane w celu wykonania ATL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jedna z wartości HRESULT standardowych.  
  
##  <a name="enumadvise"></a>  IOleObjectImpl::EnumAdvise  
 Dostarcza wyliczenie zarejestrowanych porad dotyczących połączeń dla tego formantu.  
  
```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::EnumAdvise](http://msdn.microsoft.com/library/windows/desktop/ms682355) w Windows SDK.  
  
##  <a name="enumverbs"></a>  IOleObjectImpl::EnumVerbs  
 Dostarcza wyliczenie zarejestrowanych działań (poleceń) dla tego formantu przez wywołanie metody `OleRegEnumVerbs`.  
  
```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```  
  
### <a name="remarks"></a>Uwagi  
 Zlecenia można dodać do pliku .rgs Twojego projektu. Na przykład zobacz CIRCCTL. RGS w [OK](../../visual-cpp-samples.md) próbki.  
  
 Zobacz [IOleObject::EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781) w Windows SDK.  
  
##  <a name="getclientsite"></a>  IOleObjectImpl::GetClientSite  
 Umieszcza wskaźnik w składowa danych klasy kontrolki [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) do *ppClientSite* i zwiększa liczbę odwołań wskaźnika.  
  
```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::GetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms692603) w Windows SDK.  
  
##  <a name="getclipboarddata"></a>  IOleObjectImpl::GetClipboardData  
 Pobiera dane ze Schowka.  
  
```
STDMETHOD(GetClipboardData)(    
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca E_NOTIMPL.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/ms682288) w Windows SDK.  
  
##  <a name="getextent"></a>  IOleObjectImpl::GetExtent  
 Pobiera rozmiar wyświetlania kontrolkę uruchomionej w jednostkach HIMETRIC (0,01 milimetra na jednostkę).  
  
```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar jest przechowywany w składowa danych klasy kontrolki [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).  
  
 Zobacz [IOleObject::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms692325) w Windows SDK.  
  
##  <a name="getmiscstatus"></a>  IOleObjectImpl::GetMiscStatus  
 Zwraca wskaźnik do informacji o stanie zarejestrowane dla formantu przez wywołanie metody `OleRegGetMiscStatus`.  
  
```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>Uwagi  
 Informacje o stanie zawiera mechanizm zachowań. obsługiwane przez kontrolę i prezentację danych. Informacje o stanie można dodać do pliku .rgs Twojego projektu.  
  
 Zobacz [IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521) w Windows SDK.  
  
##  <a name="getmoniker"></a>  IOleObjectImpl::GetMoniker  
 Pobiera moniker formantu.  
  
```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca E_NOTIMPL.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::GetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms686576) w Windows SDK.  
  
##  <a name="getuserclassid"></a>  IOleObjectImpl::GetUserClassID  
 Zwraca identyfikator klasy formantu.  
  
```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::GetUserClassID](http://msdn.microsoft.com/library/windows/desktop/ms682313) w Windows SDK.  
  
##  <a name="getusertype"></a>  IOleObjectImpl::GetUserType  
 Zwraca nazwę użytkownika — typ formantu przez wywołanie metody `OleRegGetUserType`.  
  
```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```  
  
### <a name="remarks"></a>Uwagi  
 Nazwa typu użytkownika jest używana do wyświetlania w elementach interfejsu użytkownika, takie jak menu i okien dialogowych. Możesz zmienić nazwę typu użytkownika w pliku .rgs projektu.  
  
 Zobacz [IOleObject::GetUserType](http://msdn.microsoft.com/library/windows/desktop/ms688643) w Windows SDK.  
  
##  <a name="initfromdata"></a>  IOleObjectImpl::InitFromData  
 Inicjuje formantu z wybranych danych.  
  
```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca E_NOTIMPL.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) w Windows SDK.  
  
##  <a name="isuptodate"></a>  IOleObjectImpl::IsUpToDate  
 Sprawdza, czy kontrolka jest aktualny.  
  
```
STDMETHOD(IsUpToDate)(void);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::IsUpToDate](http://msdn.microsoft.com/library/windows/desktop/ms686624) w Windows SDK.  
  
##  <a name="onpostverbdiscardundo"></a>  IOleObjectImpl::OnPostVerbDiscardUndo  
 Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) po poprzedni stan jest odrzucany.  
  
```
HRESULT OnPostVerbDiscardUndo();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej metody za pomocą kodu, który ma być wykonany po poprzedni stan jest odrzucany.  
  
##  <a name="onpostverbhide"></a>  IOleObjectImpl::OnPostVerbHide  
 Wywoływane przez [DoVerbHide](#doverbhide) po formantu jest ukryta.  
  
```
HRESULT OnPostVerbHide();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej metody za pomocą kodu, który ma być wykonany po formantu jest ukryta.  
  
##  <a name="onpostverbinplaceactivate"></a>  IOleObjectImpl::OnPostVerbInPlaceActivate  
 Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) po aktywowaniu kontrolki w miejscu.  
  
```
HRESULT OnPostVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej metody za pomocą kodu, który ma być wykonywane po aktywowaniu kontrolki w miejscu.  
  
##  <a name="onpostverbopen"></a>  IOleObjectImpl::OnPostVerbOpen  
 Wywoływane przez [DoVerbOpen](#doverbopen) po otwarciu formantu do edycji w osobnym oknie.  
  
```
HRESULT OnPostVerbOpen();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, przy użyciu kodu, który ma zostać wykonane po otwarciu formantu do edycji w osobnym oknie.  
  
##  <a name="onpostverbshow"></a>  IOleObjectImpl::OnPostVerbShow  
 Wywoływane przez [DoVerbShow](#doverbshow) po kontrolki widoczne.  
  
```
HRESULT OnPostVerbShow();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, przy użyciu kodu, który ma zostać wykonane po kontrolki stało się widoczne.  
  
##  <a name="onpostverbuiactivate"></a>  IOleObjectImpl::OnPostVerbUIActivate  
 Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) po aktywowaniu kontrolki interfejsu użytkownika.  
  
```
HRESULT OnPostVerbUIActivate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, przy użyciu kodu, który ma być wykonywane po aktywowaniu kontrolki interfejsu użytkownika.  
  
##  <a name="onpreverbdiscardundo"></a>  IOleObjectImpl::OnPreVerbDiscardUndo  
 Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) przed cofania stanu jest odrzucany.  
  
```
HRESULT OnPreVerbDiscardUndo();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Aby zapobiec sytuacji, w której poprzedni stan zostanie odrzucony, przesłonić tę metodę, aby zwrócić błąd HRESULT.  
  
##  <a name="onpreverbhide"></a>  IOleObjectImpl::OnPreVerbHide  
 Wywoływane przez [DoVerbHide](#doverbhide) przed formantu jest ukryta.  
  
```
HRESULT OnPreVerbHide();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Aby zapobiec sytuacji, w której formantu jest ukryta, zastąpienie tej metody zwraca błąd HRESULT.  
  
##  <a name="onpreverbinplaceactivate"></a>  IOleObjectImpl::OnPreVerbInPlaceActivate  
 Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) zanim kontrolka jest aktywowany w miejscu.  
  
```
HRESULT OnPreVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Aby zapobiec sytuacji, w której formant aktywowany w miejscu, należy przesłonić tę metodę, zostać zwrócony błąd HRESULT.  
  
##  <a name="onpreverbopen"></a>  IOleObjectImpl::OnPreVerbOpen  
 Wywoływane przez [DoVerbOpen](#doverbopen) przed formant został otwarty do edycji w osobnym oknie.  
  
```
HRESULT OnPreVerbOpen();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Aby zapobiec sytuacji, w której formant jest otwarty do edycji w osobnym oknie, zastąpienie tej metody zwraca błąd HRESULT.  
  
##  <a name="onpreverbshow"></a>  IOleObjectImpl::OnPreVerbShow  
 Wywoływane przez [DoVerbShow](#doverbshow) przed kontrolki stało się widoczne.  
  
```
HRESULT OnPreVerbShow();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Aby zapobiec sytuacji, w której formant jest widoczny, przesłonić tę metodę, aby zwrócić błąd HRESULT.  
  
##  <a name="onpreverbuiactivate"></a>  IOleObjectImpl::OnPreVerbUIActivate  
 Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) przed interfejsu użytkownika formantu został aktywowany.  
  
```
HRESULT OnPreVerbUIActivate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Aby zapobiec aktywowanego kontrolki interfejsu użytkownika, należy przesłonić tę metodę, zostać zwrócony błąd HRESULT.  
  
##  <a name="setclientsite"></a>  IOleObjectImpl::SetClientSite  
 Informuje formantu o swojej lokacji klienta w kontenerze.  
  
```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```  
  
### <a name="remarks"></a>Uwagi  
 Następnie metoda zwraca S_OK.  
  
 Zobacz [IOleObject::SetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms684013) w Windows SDK.  
  
##  <a name="setcolorscheme"></a>  IOleObjectImpl::SetColorScheme  
 Zaleca schemat kolorów kontroli aplikacji, jeśli istnieje.  
  
```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca E_NOTIMPL.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) w Windows SDK.  
  
##  <a name="setextent"></a>  IOleObjectImpl::SetExtent  
 Ustawia maksymalny zakres obszaru wyświetlania kontrolki.  
  
```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>Uwagi  
 W przeciwnym razie `SetExtent` przechowuje wartość wskazywana przez `psizel` w składowa danych klasy kontrolki [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Ta wartość jest w jednostkach HIMETRIC (0,01 milimetra na jednostkę).  
  
 Jeśli dane składowej klasy kontrolki [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) ma wartość PRAWDA, `SetExtent` przechowuje wartość wskazywana przez `psizel` w składowa danych klasy kontrolki [CComControlBase::m_sizeNatural ](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).  
  
 Jeśli dane składowej klasy kontrolki [CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) ma wartość PRAWDA, `SetExtent` wywołania `SendOnDataChange` i `SendOnViewChange` powiadomić wszystkich doradztwa ujść zarejestrowany właściciel Porada, który ma rozmiar kontrolki zmienione.  
  
 Zobacz [IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330) w Windows SDK.  
  
##  <a name="sethostnames"></a>  IOleObjectImpl::SetHostNames  
 Informuje kontrolki nazwy aplikacji kontenera i dokumentu kontenera.  
  
```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::SetHostNames](http://msdn.microsoft.com/library/windows/desktop/ms680642) w Windows SDK.  
  
##  <a name="setmoniker"></a>  IOleObjectImpl::SetMoniker  
 Informuje o tym formant jest jego nazwie.  
  
```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca E_NOTIMPL.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::SetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679671) w Windows SDK.  
  
##  <a name="unadvise"></a>  IOleObjectImpl::Unadvise  
 Usuwa doradztwa technicznego dotyczącego połączenia przechowywana w klasie kontrolki `m_spOleAdviseHolder` element członkowski danych.  
  
```
STDMETHOD(Unadvise)(DWORD dwConnection);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749) w Windows SDK.  
  
##  <a name="update"></a>  IOleObjectImpl::Update  
 Aktualizuje formantu.  
  
```
STDMETHOD(Update)(void);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IOleObject::Update](http://msdn.microsoft.com/library/windows/desktop/ms679699) w Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Interfejsy kontrolki ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
