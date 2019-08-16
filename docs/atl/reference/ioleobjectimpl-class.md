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
ms.openlocfilehash: ded158b0ec862de5b0d0b23dd4b9edb50ad577ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495729"
---
# <a name="ioleobjectimpl-class"></a>Klasa IOleObjectImpl

Ta klasa implementuje `IUnknown` i jest interfejsem głównym, za pomocą którego kontener komunikuje się z kontrolką.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IOleObjectImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IOleObjectImpl:: Advise](#advise)|Nawiązuje połączenie doradcze z kontrolką.|
|[IOleObjectImpl::Close](#close)|Zmienia stan formantu z uruchamiania na załadowany.|
|[IOleObjectImpl::DoVerb](#doverb)|Instruuje formant, aby wykonał jedną z wyliczonych akcji.|
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Informuje formant, aby odrzucił stan wycofania, który jest konserwowany.|
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Instruuje formant, aby usunął interfejs użytkownika z widoku.|
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Uruchamia formant i instaluje jego okno, ale nie instaluje interfejsu użytkownika kontrolki.|
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Powoduje, że kontrolka jest otwierana w osobnym oknie.|
|[IOleObjectImpl::D oVerbPrimary](#doverbprimary)|Wykonuje określoną akcję po dwukrotnym kliknięciu kontrolki przez użytkownika. Formant definiuje akcję, zazwyczaj w celu aktywowania kontrolki w miejscu.|
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Pokazuje nowo wstawiony formant użytkownikowi.|
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Uaktywnia formant w miejscu i pokazuje interfejs użytkownika kontrolki, taki jak menu i paski narzędzi.|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Wylicza połączenia doradcze kontrolki.|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Wylicza akcje dla kontrolki.|
|[IOleObjectImpl::GetClientSite](#getclientsite)|Pobiera lokację klienta kontrolki.|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Pobiera dane ze schowka. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleObjectImpl::GetExtent](#getextent)|Pobiera zakres obszaru wyświetlania formantu.|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Pobiera stan formantu.|
|[IOleObjectImpl::GetMoniker](#getmoniker)|Pobiera moniker kontrolki. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Pobiera identyfikator klasy kontrolki.|
|[IOleObjectImpl::GetUserType](#getusertype)|Pobiera nazwę typu użytkownika kontrolki.|
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicjuje kontrolkę z wybranych danych. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Sprawdza, czy kontrolka jest aktualna. Implementacja ATL zwraca S_OK.|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) po odrzuconym stanie cofania.|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Wywoływane przez [DoVerbHide](#doverbhide) , gdy kontrolka jest ukryta.|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) po aktywowaniu kontrolki.|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Wywoływane przez [DoVerbOpen](#doverbopen) po otwarciu kontrolki do edycji w osobnym oknie.|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Wywoływane przez [DoVerbShow](#doverbshow) po przeprowadzeniu widoczności kontrolki.|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) po aktywowaniu interfejsu użytkownika kontrolki.|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) przed usunięciem stanu cofania.|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Wywoływane przez [DoVerbHide](#doverbhide) przed ukryciem formantu.|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) przed aktywowaniem kontrolki.|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Wywoływane przez [DoVerbOpen](#doverbopen) przed otwarciem kontrolki do edycji w osobnym oknie.|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Wywoływane przez [DoVerbShow](#doverbshow) przed udostępnieniem formantu.|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) przed aktywowaniem interfejsu użytkownika kontrolki.|
|[IOleObjectImpl::SetClientSite](#setclientsite)|Informuje formant o swojej lokacji klienta w kontenerze.|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Zaleca schemat kolorów dla aplikacji kontrolki, jeśli istnieje. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleObjectImpl::SetExtent](#setextent)|Ustawia zakres obszaru wyświetlania formantu.|
|[IOleObjectImpl::SetHostNames](#sethostnames)|Informuje kontrolkę o nazwie aplikacji kontenera i dokumentu kontenera.|
|[IOleObjectImpl::SetMoniker](#setmoniker)|Informuje formant o tym, jaki jest jego moniker. Implementacja ATL zwraca E_NOTIMPL.|
|[IOleObjectImpl::Unadvise](#unadvise)|Usuwa połączenie doradcze z kontrolką.|
|[IOleObjectImpl:: Update](#update)|Aktualizuje formant. Implementacja ATL zwraca S_OK.|

## <a name="remarks"></a>Uwagi

Interfejs [IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject) jest interfejsem głównym, za pomocą którego kontener komunikuje się z kontrolką. Klasa `IOleObjectImpl` zapewnia domyślną implementację tego interfejsu i implementuje `IUnknown` przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

**Powiązane artykuły** [Samouczek ATL](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

##  <a name="advise"></a>IOleObjectImpl:: Advise

Nawiązuje połączenie doradcze z kontrolką.

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject:: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) w Windows SDK.

##  <a name="close"></a>IOleObjectImpl:: Close

Zmienia stan formantu z uruchamiania na załadowany.

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>Uwagi

Dezaktywuje formant i niszczy okno kontroli, jeśli istnieje. Jeśli element członkowski danych klasy kontrolki [CComControlBase:: m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) ma wartość true, a parametr *DWSAVEOPTION* ma wartość OLECLOSE_SAVEIFDIRTY lub OLECLOSE_PROMPTSAVE, właściwości kontrolki są zapisywane przed zamknięciem.

Wskaźniki przechowywane w elementach członkowskich danych klasy kontroli [CComControlBase:: m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) i [CComControlBase:: m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) zostały wydane, a elementy członkowskie danych [CComControlBase:: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase:: m_ bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)i [CComControlBase:: m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) są ustawione na wartość false.

Zobacz [IOleObject:: Close](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close) w Windows SDK.

##  <a name="doverb"></a>IOleObjectImpl::D oVerb

Instruuje formant, aby wykonał jedną z wyliczonych akcji.

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

W zależności od wartości `iVerb`, jedna z funkcji pomocnika ATL `DoVerb` jest wywoływana w następujący sposób:

|*iVerb* Wartościami|Wywołano funkcję pomocnika DoVerb|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

Zobacz [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) w Windows SDK.

##  <a name="doverbdiscardundo"></a>IOleObjectImpl::D oVerbDiscardUndo

Informuje formant, aby odrzucił stan wycofania, który jest konserwowany.

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
podczas Wskaźnik do prostokąta, do którego ma zostać narysowany formant.

*hwndParent*<br/>
podczas Uchwyt okna zawierającego formant.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

##  <a name="doverbhide"></a>IOleObjectImpl::D oVerbHide

Dezaktywuje i usuwa interfejs użytkownika kontrolki, a następnie ukrywa formant.

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
podczas Wskaźnik do prostokąta, do którego ma zostać narysowany formant.

*hwndParent*<br/>
podczas Uchwyt okna zawierającego formant. Nieużywane w implementacji ATL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

##  <a name="doverbinplaceactivate"></a>IOleObjectImpl::D oVerbInPlaceActivate

Uruchamia formant i instaluje jego okno, ale nie instaluje interfejsu użytkownika kontrolki.

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
podczas Wskaźnik do prostokąta, do którego ma zostać narysowany formant.

*hwndParent*<br/>
podczas Uchwyt okna zawierającego formant. Nieużywane w implementacji ATL.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Uaktywnia formant w miejscu przez wywołanie [CComControlBase:: InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). Chyba że element członkowski `m_bWindowOnly` danych klasy kontroli ma wartość true, `DoVerbInPlaceActivate` najpierw próbuje uaktywnić formant jako kontrolkę bez okna (możliwe tylko wtedy, gdy kontener obsługuje [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)). Jeśli to się nie powiedzie, funkcja próbuje uaktywnić formant z rozszerzonymi funkcjami (możliwe tylko wtedy, gdy kontener obsługuje [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)). Jeśli to się nie powiedzie, funkcja próbuje uaktywnić formant bez rozszerzonych funkcji (możliwe tylko wtedy, gdy kontener obsługuje [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)). W przypadku pomyślnego aktywacji funkcja powiadamia kontener, że formant został aktywowany.

##  <a name="doverbopen"></a>IOleObjectImpl::D oVerbOpen

Powoduje, że kontrolka jest otwierana w osobnym oknie.

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
podczas Wskaźnik do prostokąta, do którego ma zostać narysowany formant.

*hwndParent*<br/>
podczas Uchwyt okna zawierającego formant.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

##  <a name="doverbprimary"></a>IOleObjectImpl::D oVerbPrimary

Definiuje akcję wykonywaną po dwukrotnym kliknięciu kontrolki przez użytkownika.

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
podczas Wskaźnik do prostokąta, do którego ma zostać narysowany formant.

*hwndParent*<br/>
podczas Uchwyt okna zawierającego formant.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Domyślnie ustawione na wyświetlanie stron właściwości. Możesz przesłonić ten element w klasie kontrolki, aby wywołać inne zachowanie w przypadku dwukrotnego kliknięcia; na przykład Odtwórz wideo lub przejdź w miejscu aktywności.

##  <a name="doverbshow"></a>IOleObjectImpl::D oVerbShow

Instruuje kontener, aby formant był widoczny.

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
podczas Wskaźnik do prostokąta, do którego ma zostać narysowany formant.

*hwndParent*<br/>
podczas Uchwyt okna zawierającego formant. Nieużywane w implementacji ATL.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="doverbuiactivate"></a>IOleObjectImpl::D oVerbUIActivate

Aktywuje interfejs użytkownika kontrolki i powiadamia kontener, że jego menu są zastępowane przez menu złożone.

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
podczas Wskaźnik do prostokąta, do którego ma zostać narysowany formant.

*hwndParent*<br/>
podczas Uchwyt okna zawierającego formant. Nieużywane w implementacji ATL.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="enumadvise"></a>IOleObjectImpl::EnumAdvise

Dostarcza Wyliczenie zarejestrowanych połączeń doradczych dla tej kontrolki.

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject:: enumAdvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) w Windows SDK.

##  <a name="enumverbs"></a>IOleObjectImpl::EnumVerbs

Dostarcza Wyliczenie zarejestrowanych akcji (czasowników) dla tej kontrolki przez wywołanie `OleRegEnumVerbs`.

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>Uwagi

Do pliku. RGS projektu można dodać czasowniki. Na przykład zobacz CIRCCTL. RGS w przykładowym [cyklem](../../overview/visual-cpp-samples.md) .

Zobacz [IOleObject:: EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) w Windows SDK.

##  <a name="getclientsite"></a>IOleObjectImpl::GetClientSite

Umieszcza wskaźnik w elemencie członkowskim danych klasy kontrolki [CComControlBase:: m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) do *ppClientSite* i zwiększa liczbę odwołań na wskaźniku.

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject:: GetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite) w Windows SDK.

##  <a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData

Pobiera dane ze schowka.

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject:: GetClipboardData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) w Windows SDK.

##  <a name="getextent"></a>IOleObjectImpl:: getzakres

Pobiera rozmiar wyświetlania uruchomionej kontrolki w jednostkach HIMETRIC (0,01 milimetr na jednostkę).

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Uwagi

Rozmiar jest przechowywany w elemencie członkowskim danych klasy kontrolki [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

Zobacz [IOleObject:: getzakres](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent) w Windows SDK.

##  <a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus

Zwraca wskaźnik do zarejestrowanych informacji o stanie dla kontrolki przez wywołanie `OleRegGetMiscStatus`.

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>Uwagi

Informacje o stanie obejmują zachowania obsługiwane przez kontrolkę i dane prezentacji. Do pliku. RGS projektu można dodać informacje o stanie.

Zobacz [IOleObject:: GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) w Windows SDK.

##  <a name="getmoniker"></a>IOleObjectImpl:: GetMoniker

Pobiera moniker kontrolki.

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject:: GetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker) w Windows SDK.

##  <a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID

Zwraca identyfikator klasy kontrolki.

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject:: GetUserClassID](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid) w Windows SDK.

##  <a name="getusertype"></a>IOleObjectImpl:: GetUserType

Zwraca nazwę typu użytkownika kontrolki przez wywołanie `OleRegGetUserType`.

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>Uwagi

Nazwa typu użytkownika jest używana do wyświetlania w elementach interfejsów użytkownika, takich jak menu i okna dialogowe. W pliku. RGS projektu można zmienić nazwę typu użytkownika.

Zobacz [IOleObject::](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype) GetUserType w Windows SDK.

##  <a name="initfromdata"></a>IOleObjectImpl::InitFromData

Inicjuje kontrolkę z wybranych danych.

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject:: InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) w Windows SDK.

##  <a name="isuptodate"></a>IOleObjectImpl::IsUpToDate

Sprawdza, czy kontrolka jest aktualna.

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject:: IsUpToDate](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate) w Windows SDK.

##  <a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo

Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) po odrzuconym stanie cofania.

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę kodem, który ma zostać wykonany po odrzuconym stanie cofania.

##  <a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide

Wywoływane przez [DoVerbHide](#doverbhide) , gdy kontrolka jest ukryta.

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę kodem, który ma zostać wykonany po ukryciu formantu.

##  <a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate

Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) po aktywowaniu kontrolki.

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę kodem, który ma zostać wykonany po aktywowaniu kontrolki.

##  <a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen

Wywoływane przez [DoVerbOpen](#doverbopen) po otwarciu kontrolki do edycji w osobnym oknie.

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę kodem, który ma zostać wykonany po otwarciu kontrolki do edycji w osobnym oknie.

##  <a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow

Wywoływane przez [DoVerbShow](#doverbshow) po przeprowadzeniu widoczności kontrolki.

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę kodem, który ma zostać wykonany po udostępnieniu kontrolki.

##  <a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate

Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) po aktywowaniu interfejsu użytkownika kontrolki.

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę kodem, który ma zostać wykonany po aktywowaniu interfejsu użytkownika kontrolki.

##  <a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo

Wywoływane przez [DoVerbDiscardUndo](#doverbdiscardundo) przed usunięciem stanu cofania.

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby zapobiec odrzuceniu stanu cofania, Zastąp tę metodę, aby zwrócić błąd HRESULT.

##  <a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide

Wywoływane przez [DoVerbHide](#doverbhide) przed ukryciem formantu.

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby zapobiec ukrywaniu formantu, Przesłoń tę metodę w celu zwrócenia błędu HRESULT.

##  <a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate

Wywoływane przez [DoVerbInPlaceActivate](#doverbinplaceactivate) przed aktywowaniem kontrolki.

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby zapobiec aktywowaniu formantu w miejscu, Przesłoń tę metodę, aby zwrócić błąd HRESULT.

##  <a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen

Wywoływane przez [DoVerbOpen](#doverbopen) przed otwarciem kontrolki do edycji w osobnym oknie.

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby uniemożliwić otwieranie formantu w oddzielnym oknie, Przesłoń tę metodę w celu zwrócenia błędu HRESULT.

##  <a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow

Wywoływane przez [DoVerbShow](#doverbshow) przed udostępnieniem formantu.

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby zapobiec widoczności formantu, Przesłoń tę metodę w celu zwrócenia błędu HRESULT.

##  <a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate

Wywoływane przez [DoVerbUIActivate](#doverbuiactivate) przed aktywowaniem interfejsu użytkownika kontrolki.

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Aby zapobiec aktywacji interfejsu użytkownika kontrolki, Zastąp tę metodę, aby zwrócić błąd HRESULT.

##  <a name="setclientsite"></a>  IOleObjectImpl::SetClientSite

Informuje formant o swojej lokacji klienta w kontenerze.

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>Uwagi

Metoda następnie zwraca S_OK.

Zobacz [IOleObject:: SetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite) w Windows SDK.

##  <a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme

Zaleca schemat kolorów dla aplikacji kontrolki, jeśli istnieje.

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) w Windows SDK.

##  <a name="setextent"></a>IOleObjectImpl:: setzakres

Ustawia zakres obszaru wyświetlania formantu.

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Uwagi

W przeciwnym razie `psizel` przechowujewartośćwskazywanąprzezelementczłonkowskidanychklasyformantuCComControlBase`SetExtent` [:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Ta wartość jest w jednostkach HIMETRIC (0,01 milimetr na jednostkę).

Jeśli element członkowski danych klasy kontrolki [CComControlBase:: m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) ma wartość `SetExtent` true, również przechowuje wartość wskazywaną `psizel` przez element członkowski danych klasy kontroli [CComControlBase:: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).

Jeśli element członkowski danych klasy kontrolki [CComControlBase:: m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) ma wartość `SetExtent` true `SendOnDataChange` , `SendOnViewChange` wywołuje i powiadamia wszystkie ujścia doradców zarejestrowane przez posiadacza powiadomienia o zmianie rozmiaru kontrolki.

Zobacz [IOleObject:: setstop](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent) w Windows SDK.

##  <a name="sethostnames"></a>IOleObjectImpl:: SetHostNames

Informuje kontrolkę o nazwie aplikacji kontenera i dokumentu kontenera.

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject::](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames) SetHostNames w Windows SDK.

##  <a name="setmoniker"></a>IOleObjectImpl:: SetMoniker

Informuje formant o tym, jaki jest jego moniker.

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject:: SetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker) w Windows SDK.

##  <a name="unadvise"></a>IOleObjectImpl:: Unadvise

Usuwa połączenie doradcze przechowywane w składowej `m_spOleAdviseHolder` danych klasy formantu.

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject:: Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) w Windows SDK.

##  <a name="update"></a>IOleObjectImpl:: Update

Aktualizuje formant.

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IOleObject:: Update](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfejsy formantów ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
