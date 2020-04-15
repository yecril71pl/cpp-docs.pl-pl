---
title: Klasa IOleObjectImpl
ms.date: 11/04/2016
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
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
ms.openlocfilehash: 86d82aea2e92eb99903284abe4ac03478369616c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326522"
---
# <a name="ioleobjectimpl-class"></a>Klasa IOleObjectImpl

Ta klasa `IUnknown` implementuje i jest głównym interfejsem, za pośrednictwem którego kontener komunikuje się z formantem.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IOleObjectImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IOleObjectImpl::Doradzić](#advise)|Ustanawia połączenie doradcze z formantem.|
|[IOleObjectImpl::Zamknij](#close)|Zmienia stan sterowania z uruchomionego na załadowany.|
|[IOleObjectImpl::DoVerb](#doverb)|Informuje formant, aby wykonać jedną z jego wyliczonych akcji.|
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Informuje formant, aby odrzucić każdy stan cofania, który utrzymuje.|
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Informuje formant, aby usunąć jego interfejs użytkownika z widoku.|
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Uruchamia formant i instaluje jego okno, ale nie instaluje interfejsu użytkownika formantu.|
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Powoduje, że formant ma być otwarty edytowany w osobnym oknie.|
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Wykonuje określoną akcję, gdy użytkownik kliknie dwukrotnie formant. Formant definiuje akcję, zwykle, aby aktywować formant w miejscu.|
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Pokazuje nowo wstawiony formant dla użytkownika.|
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Aktywuje formant w miejscu i pokazuje interfejs użytkownika formantu, takich jak menu i paski narzędzi.|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Wylicza połączenia doradcze formantu.|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Wylicza akcje dla formantu.|
|[IOleObjectImpl::GetClientSite](#getclientsite)|Pobiera lokację klienta formantu.|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Pobiera dane ze Schowka. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleObjectImpl::GetExtent](#getextent)|Pobiera zasięg obszaru wyświetlania formantu.|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Pobiera stan formantu.|
|[IOleObjectImpl::GetMoniker](#getmoniker)|Pobiera moniker formantu. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Pobiera identyfikator klasy formantu.|
|[IOleObjectImpl::GetUserType](#getusertype)|Pobiera nazwę typu użytkownika formantu.|
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicjuje formant z wybranych danych. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Sprawdza, czy kontrola jest aktualna. Implementacja ATL zwraca S_OK.|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) po odrzuceniu stanu cofania.|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Wywoływane przez [DoVerbHide](#doverbhide) po formancie jest ukryty.|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) po włączeniu formantu w miejscu.|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Wywoływane przez [DoVerbOpen](#doverbopen) po otwarciu formantu do edycji w osobnym oknie.|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Wywoływane przez [DoVerbShow](#doverbshow) po kontroli został widoczny.|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) po aktywacji interfejsu użytkownika formantu.|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) przed odrzuceniem stanu cofania.|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Wywoływane przez [DoVerbHide](#doverbhide) przed formant jest ukryty.|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) przed aktywowaniem formantu w miejscu.|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Wywoływane przez [DoVerbOpen](#doverbopen) przed otwarciem formantu do edycji w osobnym oknie.|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Wywoływane przez [DoVerbShow](#doverbshow) przed formant został widoczna.|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) przed interfejsem użytkownika formantu został aktywowany.|
|[IOleObjectImpl::SetClientSite](#setclientsite)|Informuje formant o swojej lokacji klienta w kontenerze.|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Zaleca schemat kolorów do aplikacji formantu, jeśli istnieje. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleObjectImpl::SetExtent](#setextent)|Ustawia zasięg obszaru wyświetlania formantu.|
|[IOleObjectImpl::SetHostNames](#sethostnames)|Informuje formantu nazwy aplikacji kontenera i dokumentu kontenera.|
|[IOleObjectImpl::SetMoniker](#setmoniker)|Informuje formant, co jest jego moniker. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleObjectImpl::Unadvise](#unadvise)|Usuwa połączenie doradcze z formantem.|
|[IOleObjectImpl::Aktualizacja](#update)|Aktualizuje formant. Implementacja ATL zwraca S_OK.|

## <a name="remarks"></a>Uwagi

Interfejs [IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject) jest interfejsem głównym, za pośrednictwem którego kontener komunikuje się z formantem. Klasa `IOleObjectImpl` zapewnia domyślną implementację tego `IUnknown` interfejsu i implementuje przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="ioleobjectimpladvise"></a><a name="advise"></a>IOleObjectImpl::Doradzić

Ustanawia połączenie doradcze z formantem.

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject::Doradzić](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) w windows SDK.

## <a name="ioleobjectimplclose"></a><a name="close"></a>IOleObjectImpl::Zamknij

Zmienia stan sterowania z uruchomionego na załadowany.

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>Uwagi

Dezaktywuje formant i niszczy okno formantu, jeśli istnieje. Jeśli element członkowski danych klasy kontrolnej [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) ma wartość TRUE, a parametr *dwSaveOption* jest OLECLOSE_SAVEIFDIRTY lub OLECLOSE_PROMPTSAVE, właściwości formantu są zapisywane przed zamknięciem.

Wskaźniki przechowywane w grupach kontrolnych elementów członkowskich danych [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) i [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) są zwalniane, a elementy członkowskie danych [CComControlBase::m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)i [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) są ustawione na FALSE.

Zobacz [IOleObject::Zamknij](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close) w windows SDK.

## <a name="ioleobjectimpldoverb"></a><a name="doverb"></a>IOleObjectImpl::DoVerb

Informuje formant, aby wykonać jedną z jego wyliczonych akcji.

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

W zależności od `iVerb`wartości , jedna `DoVerb` z funkcji pomocnika ATL jest wywoływana w następujący sposób:

|*iVerb* Wartość|Funkcja pomocnika DoVerb o nazwie|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide (DoVerbHide)](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceAktywnie](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary (DoVerbPrimary)](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow (DoVerbShow)](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIAktywuj](#doverbuiactivate)|

Zobacz [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) w windows SDK.

## <a name="ioleobjectimpldoverbdiscardundo"></a><a name="doverbdiscardundo"></a>IOleObjectImpl::DoVerbDiscardUndo

Informuje formant, aby odrzucić każdy stan cofania, który utrzymuje.

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*chcPosRec*<br/>
[w] Wskaźnik do prostokąta kontenera chce formantu, aby wyciągnąć do.

*hwndRodziciela*<br/>
[w] Uchwyt okna zawierającego formant.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

## <a name="ioleobjectimpldoverbhide"></a><a name="doverbhide"></a>IOleObjectImpl::DoVerbHide

Dezaktywuje i usuwa interfejs użytkownika formantu i ukrywa formant.

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*chcPosRec*<br/>
[w] Wskaźnik do prostokąta kontenera chce formantu, aby wyciągnąć do.

*hwndRodziciela*<br/>
[w] Uchwyt okna zawierającego formant. Nie jest używany w implementacji ATL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

## <a name="ioleobjectimpldoverbinplaceactivate"></a><a name="doverbinplaceactivate"></a>IOleObjectImpl::DoVerbInPlaceActivate

Uruchamia formant i instaluje jego okno, ale nie instaluje interfejsu użytkownika formantu.

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*chcPosRec*<br/>
[w] Wskaźnik do prostokąta kontenera chce formantu, aby wyciągnąć do.

*hwndRodziciela*<br/>
[w] Uchwyt okna zawierającego formant. Nie jest używany w implementacji ATL.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Aktywuje formant w miejscu, wywołując [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). O ile element członkowski `m_bWindowOnly` danych `DoVerbInPlaceActivate` klasy kontrolnej nie ma właściwości PRAWDA, najpierw próbuje aktywować formant jako formant bez okien (możliwe tylko wtedy, gdy kontener obsługuje [IOleInPlaCeSiteWindowless).](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) Jeśli to się nie powiedzie, funkcja próbuje aktywować formant za pomocą rozszerzonych funkcji (możliwe tylko wtedy, gdy kontener obsługuje [IOleInPlaCeSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)). Jeśli to się nie powiedzie, funkcja próbuje aktywować formant bez rozszerzonych funkcji (możliwe tylko wtedy, gdy kontener obsługuje [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)). Jeśli aktywacja zakończy się pomyślnie, funkcja powiadamia kontener, który został aktywowany.

## <a name="ioleobjectimpldoverbopen"></a><a name="doverbopen"></a>IOleObjectImpl::DoVerbOpen

Powoduje, że formant ma być otwarty edytowany w osobnym oknie.

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*chcPosRec*<br/>
[w] Wskaźnik do prostokąta kontenera chce formantu, aby wyciągnąć do.

*hwndRodziciela*<br/>
[w] Uchwyt okna zawierającego formant.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

## <a name="ioleobjectimpldoverbprimary"></a><a name="doverbprimary"></a>IOleObjectImpl::DoVerbPrimary

Definiuje akcję podjętą po dwukrotnym kliknięciu formantu przez użytkownika.

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>Parametry

*chcPosRec*<br/>
[w] Wskaźnik do prostokąta kontenera chce formantu, aby wyciągnąć do.

*hwndRodziciela*<br/>
[w] Uchwyt okna zawierającego formant.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Domyślnie ustawiono wyświetlanie stron właściwości. Można zastąpić to w klasie formantu, aby wywołać inne zachowanie po dwukrotnym kliknięciu; na przykład odtwórz film lub bądź aktywny w miejscu.

## <a name="ioleobjectimpldoverbshow"></a><a name="doverbshow"></a>IOleObjectImpl::DoVerbShow

Informuje kontener, aby formant był widoczny.

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*chcPosRec*<br/>
[w] Wskaźnik do prostokąta kontenera chce formantu, aby wyciągnąć do.

*hwndRodziciela*<br/>
[w] Uchwyt okna zawierającego formant. Nie jest używany w implementacji ATL.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ioleobjectimpldoverbuiactivate"></a><a name="doverbuiactivate"></a>IOleObjectImpl::DoVerbUIActivate

Aktywuje interfejs użytkownika formantu i powiadamia kontener, że jego menu są zastępowane przez menu złożone.

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*chcPosRec*<br/>
[w] Wskaźnik do prostokąta kontenera chce formantu, aby wyciągnąć do.

*hwndRodziciela*<br/>
[w] Uchwyt okna zawierającego formant. Nie jest używany w implementacji ATL.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ioleobjectimplenumadvise"></a><a name="enumadvise"></a>IOleObjectImpl::EnumAdvise

Dostarcza wyliczenie zarejestrowanych połączeń doradczych dla tego formantu.

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject::EnumAdvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) w windows SDK.

## <a name="ioleobjectimplenumverbs"></a><a name="enumverbs"></a>IOleObjectImpl::EnumVerbs

Dostarcza wyliczenie zarejestrowanych akcji (czasowników) dla `OleRegEnumVerbs`tej kontroli, wywołując .

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>Uwagi

Zlecenia można dodawać do pliku .rgs projektu. Na przykład zobacz CIRCCTL. rgs w próbce [CIRC.](../../overview/visual-cpp-samples.md)

Zobacz [IOleObject::EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) w windows SDK.

## <a name="ioleobjectimplgetclientsite"></a><a name="getclientsite"></a>IOleObjectImpl::GetClientSite

Umieszcza wskaźnik w elementów członkowskich danych klasy kontrolnej [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) w *ppClientSite* i zwiększa liczbę odwołań na wskaźniku.

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject::GetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite) w windows SDK.

## <a name="ioleobjectimplgetclipboarddata"></a><a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData

Pobiera dane ze Schowka.

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject::GetClipboardData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) w windows SDK.

## <a name="ioleobjectimplgetextent"></a><a name="getextent"></a>IOleObjectImpl::GetExtent

Pobiera rozmiar wyświetlania formantu bieżącego w jednostkach HIMETRIC (0,01 milimetra na jednostkę).

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Uwagi

Rozmiar jest przechowywany w elementów członkowskich danych klasy kontrolnej [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

Zobacz [IOleObject::GetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent) w windows SDK.

## <a name="ioleobjectimplgetmiscstatus"></a><a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus

Zwraca wskaźnik do zarejestrowanych informacji o `OleRegGetMiscStatus`stanie formantu przez wywołanie .

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>Uwagi

Informacje o stanie obejmują zachowania obsługiwane przez dane kontroli i prezentacji. Informacje o stanie można dodać do pliku .rgs projektu.

Zobacz [IOleObject::GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) w zestawie Windows SDK.

## <a name="ioleobjectimplgetmoniker"></a><a name="getmoniker"></a>IOleObjectImpl::GetMoniker

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

Zobacz [IOleObject::GetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker) w windows SDK.

## <a name="ioleobjectimplgetuserclassid"></a><a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID

Zwraca identyfikator klasy formantu.

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject::GetUserClassID](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid) w windows SDK.

## <a name="ioleobjectimplgetusertype"></a><a name="getusertype"></a>IOleObjectImpl::GetUserType

Zwraca nazwę typu użytkownika formantu `OleRegGetUserType`przez wywołanie .

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>Uwagi

Nazwa typu użytkownika jest używana do wyświetlania w interfejsach użytkownika elementów, takich jak menu i okna dialogowe. Nazwę typu użytkownika można zmienić w pliku .rgs projektu.

Zobacz [IOleObject::GetUserType](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype) w windows SDK.

## <a name="ioleobjectimplinitfromdata"></a><a name="initfromdata"></a>IOleObjectImpl::InitFromData

Inicjuje formant z wybranych danych.

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject::InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) w windows SDK.

## <a name="ioleobjectimplisuptodate"></a><a name="isuptodate"></a>IOleObjectImpl::IsUpToDate

Sprawdza, czy kontrola jest aktualna.

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject::IsUpToDate](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate) w zestawie Windows SDK.

## <a name="ioleobjectimplonpostverbdiscardundo"></a><a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo

Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) po odrzuceniu stanu cofania.

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę kodem, który ma zostać wykonany po odrzuceniu stanu cofania.

## <a name="ioleobjectimplonpostverbhide"></a><a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide

Wywoływane przez [DoVerbHide](#doverbhide) po formancie jest ukryty.

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę kodem, który ma zostać wykonany po ukryciu formantu.

## <a name="ioleobjectimplonpostverbinplaceactivate"></a><a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate

Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) po włączeniu formantu w miejscu.

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę kodem, który ma zostać wykonany po aktywowaniu formantu na miejscu.

## <a name="ioleobjectimplonpostverbopen"></a><a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen

Wywoływane przez [DoVerbOpen](#doverbopen) po otwarciu formantu do edycji w osobnym oknie.

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę kodem, który ma zostać wykonany po otwarciu formantu do edycji w osobnym oknie.

## <a name="ioleobjectimplonpostverbshow"></a><a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow

Wywoływane przez [DoVerbShow](#doverbshow) po kontroli został widoczny.

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę kodem, który ma zostać wykonany po udostępnieniu formantu.

## <a name="ioleobjectimplonpostverbuiactivate"></a><a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate

Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) po aktywacji interfejsu użytkownika formantu.

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę kodem, który ma zostać wykonany po uaktywnieniu interfejsu użytkownika formantu.

## <a name="ioleobjectimplonpreverbdiscardundo"></a><a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo

Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) przed odrzuceniem stanu cofania.

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby zapobiec odrzucaniu stanu cofania, należy zastąpić tę metodę, aby zwrócić błąd HRESULT.

## <a name="ioleobjectimplonpreverbhide"></a><a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide

Wywoływane przez [DoVerbHide](#doverbhide) przed formant jest ukryty.

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby zapobiec ukryciu formantu, należy zastąpić tę metodę, aby zwrócić błąd HRESULT.

## <a name="ioleobjectimplonpreverbinplaceactivate"></a><a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate

Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) przed aktywowaniem formantu w miejscu.

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby zapobiec aktywowaniu formantu w miejscu, należy zastąpić tę metodę, aby zwrócić błąd HRESULT.

## <a name="ioleobjectimplonpreverbopen"></a><a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen

Wywoływane przez [DoVerbOpen](#doverbopen) przed otwarciem formantu do edycji w osobnym oknie.

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby zapobiec otwarciu formantu do edycji w osobnym oknie, należy zastąpić tę metodę, aby zwrócić błąd HRESULT.

## <a name="ioleobjectimplonpreverbshow"></a><a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow

Wywoływane przez [DoVerbShow](#doverbshow) przed formant został widoczna.

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby zapobiec kontroli są widoczne, należy zastąpić tę metodę, aby zwrócić błąd HRESULT.

## <a name="ioleobjectimplonpreverbuiactivate"></a><a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate

Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) przed interfejsem użytkownika formantu został aktywowany.

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby zapobiec aktywowaniu interfejsu użytkownika formantu, należy zastąpić tę metodę, aby zwrócić błąd HRESULT.

## <a name="ioleobjectimplsetclientsite"></a><a name="setclientsite"></a>IOleObjectImpl::SetClientSite

Informuje formant o swojej lokacji klienta w kontenerze.

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>Uwagi

Następnie metoda zwraca S_OK.

Zobacz [IOleObject::SetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite) w zestawie Windows SDK.

## <a name="ioleobjectimplsetcolorscheme"></a><a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme

Zaleca schemat kolorów do aplikacji formantu, jeśli istnieje.

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject::SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) w zestawie Windows SDK.

## <a name="ioleobjectimplsetextent"></a><a name="setextent"></a>IOleObjectImpl::SetExtent

Ustawia zasięg obszaru wyświetlania formantu.

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Uwagi

W `SetExtent` przeciwnym razie przechowuje `psizel` wartość wskazywuj w elementów członkowskich klasy kontrolnej [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Wartość ta jest w jednostkach HIMETRIC (0,01 milimetra na jednostkę).

Jeśli element członkowski danych klasy kontrolnej [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) ma wartość PRAWDA, `SetExtent` przechowuje również wartość wskazywową przez `psizel` w elementów członkowskich danych klasy kontrolnej [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).

Jeśli element członkowski danych klasy kontrolnej [CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) jest true, `SetExtent` wywołania `SendOnDataChange` i `SendOnViewChange` powiadomić wszystkie pochłaniacze doradcze zarejestrowane z posiadaczem poinformować, że rozmiar formantu uległ zmianie.

Zobacz [IOleObject::SetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent) w zestawie Windows SDK.

## <a name="ioleobjectimplsethostnames"></a><a name="sethostnames"></a>IOleObjectImpl::SetHostNames

Informuje formantu nazwy aplikacji kontenera i dokumentu kontenera.

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject::SetHostNames](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames) w zestawie Windows SDK.

## <a name="ioleobjectimplsetmoniker"></a><a name="setmoniker"></a>IOleObjectImpl::SetMoniker

Informuje formant, co jest jego moniker.

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject::SetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker) w zestawie Windows SDK.

## <a name="ioleobjectimplunadvise"></a><a name="unadvise"></a>IOleObjectImpl::Unadvise

Usuwa połączenie doradcze przechowywane w elementów `m_spOleAdviseHolder` członkowskich danych klasy kontrolnej.

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject::Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) w windows SDK.

## <a name="ioleobjectimplupdate"></a><a name="update"></a>IOleObjectImpl::Aktualizacja

Aktualizuje formant.

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject::Update](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfejsy sterowania ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
