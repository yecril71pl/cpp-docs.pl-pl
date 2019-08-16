---
title: Klasa CComControlBase
ms.date: 11/04/2016
f1_keywords:
- CComControlBase
- ATLCTL/ATL::CComControlBase
- ATLCTL/ATL::CComControlBase::AppearanceType
- ATLCTL/ATL::CComControlBase::CComControlBase
- ATLCTL/ATL::CComControlBase::ControlQueryInterface
- ATLCTL/ATL::CComControlBase::DoesVerbActivate
- ATLCTL/ATL::CComControlBase::DoesVerbUIActivate
- ATLCTL/ATL::CComControlBase::DoVerbProperties
- ATLCTL/ATL::CComControlBase::FireViewChange
- ATLCTL/ATL::CComControlBase::GetAmbientAppearance
- ATLCTL/ATL::CComControlBase::GetAmbientAutoClip
- ATLCTL/ATL::CComControlBase::GetAmbientBackColor
- ATLCTL/ATL::CComControlBase::GetAmbientCharSet
- ATLCTL/ATL::CComControlBase::GetAmbientCodePage
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayAsDefault
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayName
- ATLCTL/ATL::CComControlBase::GetAmbientFont
- ATLCTL/ATL::CComControlBase::GetAmbientFontDisp
- ATLCTL/ATL::CComControlBase::GetAmbientForeColor
- ATLCTL/ATL::CComControlBase::GetAmbientLocaleID
- ATLCTL/ATL::CComControlBase::GetAmbientMessageReflect
- ATLCTL/ATL::CComControlBase::GetAmbientPalette
- ATLCTL/ATL::CComControlBase::GetAmbientProperty
- ATLCTL/ATL::CComControlBase::GetAmbientRightToLeft
- ATLCTL/ATL::CComControlBase::GetAmbientScaleUnits
- ATLCTL/ATL::CComControlBase::GetAmbientShowGrabHandles
- ATLCTL/ATL::CComControlBase::GetAmbientShowHatching
- ATLCTL/ATL::CComControlBase::GetAmbientSupportsMnemonics
- ATLCTL/ATL::CComControlBase::GetAmbientTextAlign
- ATLCTL/ATL::CComControlBase::GetAmbientTopToBottom
- ATLCTL/ATL::CComControlBase::GetAmbientUIDead
- ATLCTL/ATL::CComControlBase::GetAmbientUserMode
- ATLCTL/ATL::CComControlBase::GetDirty
- ATLCTL/ATL::CComControlBase::GetZoomInfo
- ATLCTL/ATL::CComControlBase::InPlaceActivate
- ATLCTL/ATL::CComControlBase::InternalGetSite
- ATLCTL/ATL::CComControlBase::OnDraw
- ATLCTL/ATL::CComControlBase::OnDrawAdvanced
- ATLCTL/ATL::CComControlBase::OnKillFocus
- ATLCTL/ATL::CComControlBase::OnMouseActivate
- ATLCTL/ATL::CComControlBase::OnPaint
- ATLCTL/ATL::CComControlBase::OnSetFocus
- ATLCTL/ATL::CComControlBase::PreTranslateAccelerator
- ATLCTL/ATL::CComControlBase::SendOnClose
- ATLCTL/ATL::CComControlBase::SendOnDataChange
- ATLCTL/ATL::CComControlBase::SendOnRename
- ATLCTL/ATL::CComControlBase::SendOnSave
- ATLCTL/ATL::CComControlBase::SendOnViewChange
- ATLCTL/ATL::CComControlBase::SetControlFocus
- ATLCTL/ATL::CComControlBase::SetDirty
- ATLCTL/ATL::CComControlBase::m_bAutoSize
- ATLCTL/ATL::CComControlBase::m_bDrawFromNatural
- ATLCTL/ATL::CComControlBase::m_bDrawGetDataInHimetric
- ATLCTL/ATL::CComControlBase::m_bInPlaceActive
- ATLCTL/ATL::CComControlBase::m_bInPlaceSiteEx
- ATLCTL/ATL::CComControlBase::m_bNegotiatedWnd
- ATLCTL/ATL::CComControlBase::m_bRecomposeOnResize
- ATLCTL/ATL::CComControlBase::m_bRequiresSave
- ATLCTL/ATL::CComControlBase::m_bResizeNatural
- ATLCTL/ATL::CComControlBase::m_bUIActive
- ATLCTL/ATL::CComControlBase::m_bUsingWindowRgn
- ATLCTL/ATL::CComControlBase::m_bWasOnceWindowless
- ATLCTL/ATL::CComControlBase::m_bWindowOnly
- ATLCTL/ATL::CComControlBase::m_bWndLess
- ATLCTL/ATL::CComControlBase::m_hWndCD
- ATLCTL/ATL::CComControlBase::m_nFreezeEvents
- ATLCTL/ATL::CComControlBase::m_rcPos
- ATLCTL/ATL::CComControlBase::m_sizeExtent
- ATLCTL/ATL::CComControlBase::m_sizeNatural
- ATLCTL/ATL::CComControlBase::m_spAdviseSink
- ATLCTL/ATL::CComControlBase::m_spAmbientDispatch
- ATLCTL/ATL::CComControlBase::m_spClientSite
- ATLCTL/ATL::CComControlBase::m_spDataAdviseHolder
- ATLCTL/ATL::CComControlBase::m_spInPlaceSite
- ATLCTL/ATL::CComControlBase::m_spOleAdviseHolder
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
ms.openlocfilehash: 36afd716009848ccd2e2f0ab966f66f573acdfd8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497387"
---
# <a name="ccomcontrolbase-class"></a>Klasa CComControlBase

Ta klasa udostępnia metody tworzenia formantów ATL i zarządzania nimi.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CComControlBase:: Wyglądutype](#appearancetype)|Zastąp, `m_nAppearance` Jeśli właściwość giełdowa nie jest typu **Short**.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|Konstruktor.|
|[CComControlBase::~CComControlBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Pobiera wskaźnik do żądanego interfejsu.|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Sprawdza, czy parametr *iVerb* używany przez `IOleObjectImpl::DoVerb` uaktywnia interfejs użytkownika kontrolki (*iVerb* Equals OLEIVERB_UIACTIVATE), definiuje akcję wykonywaną, gdy użytkownik kliknie dwukrotnie formant (*iVerb* jest równa OLEIVERB_ PODSTAWOWA), wyświetla formant (*iVerb* = OLEIVERB_SHOW) lub aktywuje formant (*iVerb* Equals OLEIVERB_INPLACEACTIVATE).|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Sprawdza, czy parametr *iVerb* używany przez `IOleObjectImpl::DoVerb` powoduje, że interfejs użytkownika kontrolki do aktywacji i zwraca wartość true.|
|[CComControlBase::DoVerbProperties](#doverbproperties)|Wyświetla strony właściwości kontrolki.|
|[CComControlBase::FireViewChange](#fireviewchange)|Wywołaj tę metodę, aby poinformować kontener o konieczności ponownego narysowania kontrolki lub powiadomić zarejestrowane ujścia doradców, że widok kontrolki został zmieniony.|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Pobiera DISPID_AMBIENT_APPEARANCE, bieżące ustawienie wyglądu dla kontrolki: 0 dla płaskich i 1 dla 3W.|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Pobiera DISPID_AMBIENT_AUTOCLIP, flagę wskazującą, czy kontener obsługuje automatyczne przycinanie obszaru wyświetlania formantu.|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Pobiera DISPID_AMBIENT_BACKCOLOR, kolor tła otoczenia dla wszystkich kontrolek, zdefiniowany przez kontener.|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Pobiera DISPID_AMBIENT_CHARSET, otaczający zestaw znaków dla wszystkich kontrolek, zdefiniowany przez kontener.|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Pobiera DISPID_AMBIENT_CODEPAGE, otaczający zestaw znaków dla wszystkich kontrolek, zdefiniowany przez kontener.|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Pobiera DISPID_AMBIENT_DISPLAYASDEFAULT, flagę, która ma wartość TRUE, jeśli kontener oznaczył formant w tej witrynie jako przycisk domyślny i w związku z tym formant przycisku powinien być rysowany z grubszą ramką.|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Pobiera DISPID_AMBIENT_DISPLAYNAME, nazwę kontenera dostarczono do kontrolki.|
|[CComControlBase::GetAmbientFont](#getambientfont)|Pobiera wskaźnik do otaczającego `IFont` interfejsu kontenera.|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Pobiera wskaźnik do otaczającego `IFontDisp` interfejsu do dystrybucji kontenera.|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Pobiera DISPID_AMBIENT_FORECOLOR, kolor pierwszego planu dla wszystkich kontrolek, zdefiniowany przez kontener.|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Pobiera DISPID_AMBIENT_LOCALEID, identyfikator języka używanego przez kontener.|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Pobiera DISPID_AMBIENT_MESSAGEREFLECT, flagę wskazującą, czy kontener chce otrzymywać komunikaty okna (takie jak WM_DRAWITEM) jako zdarzenia.|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Pobiera DISPID_AMBIENT_PALETTE, używany do uzyskania dostępu do HPALETTE kontenera.|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Pobiera właściwość kontenera określoną przez *Identyfikator*.|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Pobiera DISPID_AMBIENT_RIGHTTOLEFT, kierunek, w którym zawartość jest wyświetlana przez kontener.|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Pobiera DISPID_AMBIENT_SCALEUNITS, jednostki otoczenia kontenera (na przykład cale lub centymetry) do wyświetlania etykiet.|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Pobiera DISPID_AMBIENT_SHOWGRABHANDLES, flagę wskazującą, czy kontener umożliwia kontrolce wyświetlanie uchwytów dla siebie, gdy jest aktywny.|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Pobiera DISPID_AMBIENT_SHOWHATCHING, flagę wskazującą, czy kontener pozwala formantowi wyświetlać się z kreskowanym wzorcem, gdy interfejs użytkownika jest aktywny.|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Pobiera DISPID_AMBIENT_SUPPORTSMNEMONICS, flagę wskazującą, czy kontener obsługuje skróty klawiaturowe.|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Pobiera DISPID_AMBIENT_TEXTALIGN, wyrównanie tekstu preferowane przez kontener: 0 w przypadku ogólnego wyrównania (liczby w prawo, tekst z lewej), 1 dla wyrównania po lewej, 2 dla wyrównania Center i 3 do prawej wyrównania.|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Pobiera DISPID_AMBIENT_TOPTOBOTTOM, kierunek, w którym zawartość jest wyświetlana przez kontener.|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Pobiera DISPID_AMBIENT_UIDEAD, flagę wskazującą, czy kontener chce, aby formant odpowiadał na akcje interfejsu użytkownika.|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Pobiera DISPID_AMBIENT_USERMODE, flagę wskazującą, czy kontener jest w trybie uruchomieniowym (TRUE), czy w trybie projektowania (FALSE).|
|[CComControlBase:: getdirty](#getdirty)|Zwraca wartość elementu członkowskiego `m_bRequiresSave`danych.|
|[CComControlBase::GetZoomInfo](#getzoominfo)|Pobiera wartości x i y licznika i mianownik współczynnika powiększenia dla kontrolki aktywowanej do edycji w miejscu.|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Powoduje, że kontrolka przechodzi ze stanu nieaktywności do dowolnego stanu, w którym wskazuje zlecenie w *iVerb* .|
|[CComControlBase::InternalGetSite](#internalgetsite)|Wywołaj tę metodę, aby wykonać zapytanie o lokację kontroli dla wskaźnika do zidentyfikowanego interfejsu.|
|[CComControlBase:: OnDraw](#ondraw)|Zastąp tę metodę, aby narysować kontrolkę.|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|Domyślnie `OnDrawAdvanced` przygotowuje znormalizowany kontekst urządzenia do rysowania, a następnie wywołuje `OnDraw` metodę klasy formantu.|
|[CComControlBase::OnKillFocus](#onkillfocus)|Sprawdza, czy formant jest aktywny i ma prawidłową lokację kontroli, a następnie informuje o tym, że formant utracił fokus.|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Sprawdza, czy interfejs użytkownika znajduje się w trybie użytkownik, a następnie uaktywnia formant.|
|[CComControlBase::OnPaint](#onpaint)|Przygotowuje kontener do malowania, Pobiera obszar klienta kontrolki, a następnie wywołuje `OnDraw` metodę klasy formantu.|
|[CComControlBase::OnSetFocus](#onsetfocus)|Sprawdza, czy formant jest aktywny i ma prawidłową lokację kontroli, a następnie informuje o tym, że formant uzyskał fokus.|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Zastąp tę metodę, aby zapewnić własne programy obsługi akceleratora klawiaturowego.|
|[CComControlBase::SendOnClose](#sendonclose)|Powiadamia wszystkie ujścia doradców zarejestrowane przez posiadacza doradcy, że formant został zamknięty.|
|[CComControlBase::SendOnDataChange](#sendondatachange)|Powiadamia wszystkie ujścia doradców zarejestrowane przez posiadacza doradcy, że dane kontroli uległy zmianie.|
|[CComControlBase::SendOnRename](#sendonrename)|Powiadamia wszystkie ujścia doradcze zarejestrowane przez posiadacza doradcy, że kontrolka ma nowy moniker.|
|[CComControlBase::SendOnSave](#sendonsave)|Powiadamia wszystkie ujścia doradców zarejestrowane przez posiadacza powiadomienia, że formant został zapisany.|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Powiadamia wszystkie zarejestrowane ujścia doradców, że widok kontrolki został zmieniony.|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Ustawia lub usuwa fokus klawiatury do lub z formantu.|
|[CComControlBase::SetDirty](#setdirty)|Ustawia element członkowski `m_bRequiresSave` danych na wartość w *bDirty*.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|Flaga wskazująca, że formant nie może być żadnym innym rozmiarem.|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Flaga oznaczająca `IDataObjectImpl::GetData` , `CComControlBase::GetZoomInfo` że należy ustawić rozmiar formantu od `m_sizeNatural` , a nie `m_sizeExtent`z.|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Flaga oznaczająca `IDataObjectImpl::GetData` , że należy używać jednostek HIMETRIC, a nie pikseli przy rysowaniu.|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Flaga wskazująca, że formant jest aktywny w miejscu.|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Flaga wskazująca, że kontener `IOleInPlaceSiteEx` obsługuje funkcje sterowania interfejsem i OCX96, takie jak kontrolki bez okna i niezawierające migotania.|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Flaga oznaczająca, czy kontrolka została wynegocjowana z kontenerem o obsłudze funkcji kontroli OCX96 (takich jak kontrolki bez okna i nieokienkowe), oraz czy kontrolka jest okienkowa, czy bez okien.|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Flaga wskazująca, że kontrolka chce ponownie złożyć swoją prezentację, gdy kontener zmieni rozmiar wyświetlania formantu.|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Flaga wskazująca, że formant został zmieniony od ostatniego zapisu.|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Flaga wskazująca, że formant chce zmienić rozmiar swojego naturalnego zakresu (nieskalowanego rozmiaru fizycznego), gdy kontener zmienia rozmiar wyświetlania formantu.|
|[CComControlBase::m_bUIActive](#m_buiactive)|Flaga wskazująca, że interfejs użytkownika kontrolki, taki jak menu i paski narzędzi, jest aktywny.|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Flaga wskazująca, że formant korzysta z regionu okna dostarczonego z kontenerem.|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Flaga wskazująca, że kontrolka została bez okien, ale może nie być teraz bez okien.|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Flaga wskazująca, że formant powinien być okienkowy, nawet jeśli kontener obsługuje kontrolki bez okien.|
|[CComControlBase::m_bWndLess](#m_bwndless)|Flaga wskazująca, że formant jest bez okien.|
|[CComControlBase::m_hWndCD](#m_hwndcd)|Zawiera odwołanie do uchwytu okna skojarzonego z kontrolką.|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Liczba zdarzeń zamrożonych w kontenerze (odrzuconych do zaakceptowania zdarzeń) bez interwencji z rozmrożeniem zdarzeń (akceptowanie zdarzeń).|
|[CComControlBase::m_rcPos](#m_rcpos)|Pozycja w pikselach kontrolki wyrażona we współrzędnych kontenera.|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|Zakres formantu w jednostkach HIMETRIC (każda jednostka to 0,01 milimetrów) dla określonego ekranu.|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|Rozmiar fizyczny formantu w jednostkach HIMETRIC (każda jednostka to 0,01 milimetrów).|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Bezpośredni wskaźnik do połączenia Doradczego na kontenerze ( [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)kontenera).|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|Obiekt, który umożliwia pobieranie i Ustawianie właściwości kontenera `IDispatch` za pomocą wskaźnika. `CComDispatchDriver`|
|[CComControlBase::m_spClientSite](#m_spclientsite)|Wskaźnik do lokacji klienta kontrolki w kontenerze.|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Zapewnia standardową metodę utrzymywania połączeń doradczych między obiektami danych i doradzania ujściam.|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Wskaźnik do wskaźnika interfejsu [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)lub IOleInPlaceSiteWindowlessu kontenera [](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) .|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Zapewnia standardową implementację sposobu utrzymywania połączeń doradczych.|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia metody tworzenia formantów ATL i zarządzania nimi. [Klasa CComControl](../../atl/reference/ccomcontrol-class.md) pochodzi od `CComControlBase`. Podczas tworzenia formantu standardowego lub kontrolki DHTML przy użyciu kreatora kontrolki ATL, Kreator automatycznie utworzy klasę z `CComControlBase`.

Aby uzyskać więcej informacji na temat tworzenia kontrolki, zobacz [samouczek ATL](../../atl/active-template-library-atl-tutorial.md). Aby uzyskać więcej informacji na temat Kreatora projektu ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

##  <a name="appearancetype"></a>CComControlBase:: Wyglądutype

Zastąp, `m_nAppearance` Jeśli właściwość giełdowa nie jest typu **Short**.

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Uwagi

Kreator kontrolki ATL dodaje `m_nAppearance` Właściwość Stock typu short. Zastąp `AppearanceType` , jeśli używasz innego typu danych.

##  <a name="ccomcontrolbase"></a>CComControlBase::CComControlBase

Konstruktor.

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Uchwyt do okna skojarzonego z kontrolką.

### <a name="remarks"></a>Uwagi

Inicjuje rozmiar formantu do 5080X5080 jednostek HIMETRIC (2 "X2") i inicjuje `CComControlBase` wartości elementu członkowskiego danych wartością null lub false.

##  <a name="dtor"></a>CComControlBase:: ~ CComControlBase

Destruktor.

```
~CComControlBase();
```

### <a name="remarks"></a>Uwagi

Jeśli kontrolka jest okienkowa, `~CComControlBase` niszczy ją przez wywołanie [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow).

##  <a name="controlqueryinterface"></a>CComControlBase::ControlQueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
Identyfikator GUID żądanego interfejsu.

*ppv*<br/>
Wskaźnik do wskaźnika interfejsu identyfikowanego przez *Identyfikator IID*lub wartość null, jeśli nie można odnaleźć interfejsu.

### <a name="remarks"></a>Uwagi

Obsługuje tylko interfejsy w tabeli mapy COM.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

##  <a name="doesverbactivate"></a>CComControlBase::D oesVerbActivate

Sprawdza, czy parametr *iVerb* używany przez `IOleObjectImpl::DoVerb` uaktywnia interfejs użytkownika kontrolki (*iVerb* Equals OLEIVERB_UIACTIVATE), definiuje akcję wykonywaną, gdy użytkownik kliknie dwukrotnie formant (*iVerb* jest równa OLEIVERB_ PODSTAWOWA), wyświetla formant (*iVerb* = OLEIVERB_SHOW) lub aktywuje formant (*iVerb* Equals OLEIVERB_INPLACEACTIVATE).

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Wartość wskazująca akcję, która ma zostać `DoVerb`wykonana przez.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli *iVerb* jest równe OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW lub OLEIVERB_INPLACEACTIVATE; w przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Można zastąpić tę metodę, aby zdefiniować własne zlecenie aktywacji.

##  <a name="doesverbuiactivate"></a>CComControlBase::D oesVerbUIActivate

Sprawdza, czy parametr *iVerb* używany przez `IOleObjectImpl::DoVerb` powoduje, że interfejs użytkownika kontrolki do aktywacji i zwraca wartość true.

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Wartość wskazująca akcję, która ma zostać `DoVerb`wykonana przez.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli *iVerb* jest równe OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW lub OLEIVERB_INPLACEACTIVATE. W przeciwnym razie metoda zwraca wartość FALSE.

##  <a name="doverbproperties"></a>CComControlBase::D oVerbProperties

Wyświetla strony właściwości kontrolki.

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
Rezerwacj.

*hwndParent*<br/>
Uchwyt okna zawierającego formant.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

##  <a name="fireviewchange"></a>CComControlBase::FireViewChange

Wywołaj tę metodę, aby poinformować kontener o konieczności ponownego narysowania kontrolki lub powiadomić zarejestrowane ujścia doradców, że widok kontrolki został zmieniony.

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli formant jest aktywny (element członkowski danych klasy kontrolki [CComControlBase:: m_bInPlaceActive](#m_binplaceactive) ma wartość true), powiadamia kontener, który ma zostać ponownie narysowany cały formant. Jeśli formant jest nieaktywny, powiadamia o zarejestrowanych ujściach doradców kontrolki (za pomocą elementu członkowskiego danych klasy sterowania [CComControlBase:: m_spAdviseSink](#m_spadvisesink)), że widok kontrolki został zmieniony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

##  <a name="getambientappearance"></a>CComControlBase::GetAmbientAppearance

Pobiera DISPID_AMBIENT_APPEARANCE, bieżące ustawienie wyglądu dla kontrolki: 0 dla płaskich i 1 dla 3W.

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>Parametry

*nAppearance*<br/>
Właściwość DISPID_AMBIENT_APPEARANCE.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

##  <a name="getambientautoclip"></a>  CComControlBase::GetAmbientAutoClip

Pobiera DISPID_AMBIENT_AUTOCLIP, flagę wskazującą, czy kontener obsługuje automatyczne przycinanie obszaru wyświetlania formantu.

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>Parametry

*bAutoClip*<br/>
Właściwość DISPID_AMBIENT_AUTOCLIP.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="getambientbackcolor"></a>CComControlBase::GetAmbientBackColor

Pobiera DISPID_AMBIENT_BACKCOLOR, kolor tła otoczenia dla wszystkich kontrolek, zdefiniowany przez kontener.

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>Parametry

*BackColor*<br/>
Właściwość DISPID_AMBIENT_BACKCOLOR.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet

Pobiera DISPID_AMBIENT_CHARSET, otaczający zestaw znaków dla wszystkich kontrolek, zdefiniowany przez kontener.

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>Parametry

*bstrCharSet*<br/>
Właściwość DISPID_AMBIENT_CHARSET.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="getambientcodepage"></a>CComControlBase::GetAmbientCodePage

Pobiera DISPID_AMBIENT_CODEPAGE, stronę kodową otoczenia dla wszystkich kontrolek, zdefiniowanych przez kontener.

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>Parametry

*ulCodePage*<br/>
Właściwość DISPID_AMBIENT_CODEPAGE.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="getambientdisplayasdefault"></a>CComControlBase::GetAmbientDisplayAsDefault

Pobiera DISPID_AMBIENT_DISPLAYASDEFAULT, flagę, która ma wartość TRUE, jeśli kontener oznaczył formant w tej witrynie jako przycisk domyślny i w związku z tym formant przycisku powinien być rysowany z grubszą ramką.

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*bDisplayAsDefault*<br/>
Właściwość DISPID_AMBIENT_DISPLAYASDEFAULT.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="getambientdisplayname"></a>CComControlBase::GetAmbientDisplayName

Pobiera DISPID_AMBIENT_DISPLAYNAME, nazwę kontenera dostarczono do kontrolki.

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>Parametry

*bstrDisplayName*<br/>
Właściwość DISPID_AMBIENT_DISPLAYNAME.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="getambientfont"></a>CComControlBase::GetAmbientFont

Pobiera wskaźnik do otaczającego `IFont` interfejsu kontenera.

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont*<br/>
Wskaźnik do otaczającego interfejsu [iFont](/windows/win32/api/ocidl/nn-ocidl-ifont) kontenera.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli właściwość ma wartość NULL, wskaźnik ma wartość NULL. Jeśli wskaźnik nie ma wartości NULL, obiekt wywołujący musi zwolnić wskaźnik.

##  <a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp

Pobiera wskaźnik do otaczającego `IFontDisp` interfejsu do dystrybucji kontenera.

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont*<br/>
Wskaźnik do interfejsu wysyłania [IFontDisp](/windows/win32/api/ocidl/nn-ocidl-ifontdisp) otaczającego kontenera.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Jeśli właściwość ma wartość NULL, wskaźnik ma wartość NULL. Jeśli wskaźnik nie ma wartości NULL, obiekt wywołujący musi zwolnić wskaźnik.

##  <a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor

Pobiera DISPID_AMBIENT_FORECOLOR, kolor pierwszego planu dla wszystkich kontrolek, zdefiniowany przez kontener.

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>Parametry

*ForeColor*<br/>
Właściwość DISPID_AMBIENT_FORECOLOR.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID

Pobiera DISPID_AMBIENT_LOCALEID, identyfikator języka używanego przez kontener.

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Właściwość DISPID_AMBIENT_LOCALEID.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Kontrolka może używać tego identyfikatora do dostosowywania interfejsu użytkownika do różnych języków.

##  <a name="getambientmessagereflect"></a>CComControlBase::GetAmbientMessageReflect

Pobiera DISPID_AMBIENT_MESSAGEREFLECT, flagę wskazującą, czy kontener chce otrzymywać komunikaty okna (takie jak `WM_DRAWITEM`) jako zdarzenia.

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>Parametry

*bMessageReflect*<br/>
Właściwość DISPID_AMBIENT_MESSAGEREFLECT.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="getambientpalette"></a>CComControlBase::GetAmbientPalette

Pobiera DISPID_AMBIENT_PALETTE, używany do uzyskania dostępu do HPALETTE kontenera.

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>Parametry

*hPalette*<br/>
Właściwość DISPID_AMBIENT_PALETTE.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="getambientproperty"></a>CComControlBase::GetAmbientProperty

Pobiera właściwość kontenera określoną przez identyfikator *DISPID*.

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>Parametry

*DISPID*<br/>
Identyfikator właściwości kontenera do pobrania.

*var*<br/>
Zmienna do odebrania właściwości.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

ATL udostępnia zestaw funkcji pomocnika do pobierania określonych właściwości, na przykład [CComControlBase:: GetAmbientBackColor](#getambientbackcolor). Jeśli nie ma dostępnej odpowiedniej metody, użyj `GetAmbientProperty`.

##  <a name="getambientrighttoleft"></a>CComControlBase::GetAmbientRightToLeft

Pobiera DISPID_AMBIENT_RIGHTTOLEFT, kierunek, w którym zawartość jest wyświetlana przez kontener.

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>Parametry

*bRightToLeft*<br/>
Właściwość DISPID_AMBIENT_RIGHTTOLEFT. Ustaw wartość TRUE, jeśli zawartość jest wyświetlana od prawej do lewej, FAŁSZ, jeśli jest wyświetlana od lewej do prawej.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="getambientscaleunits"></a>CComControlBase::GetAmbientScaleUnits

Pobiera DISPID_AMBIENT_SCALEUNITS, jednostki otoczenia kontenera (na przykład cale lub centymetry) do wyświetlania etykiet.

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>Parametry

*bstrScaleUnits*<br/>
Właściwość DISPID_AMBIENT_SCALEUNITS.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles

Pobiera DISPID_AMBIENT_SHOWGRABHANDLES, flagę wskazującą, czy kontener umożliwia kontrolce wyświetlanie uchwytów dla siebie, gdy jest aktywny.

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>Parametry

*bShowGrabHandles*<br/>
Właściwość DISPID_AMBIENT_SHOWGRABHANDLES.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching

Pobiera DISPID_AMBIENT_SHOWHATCHING, flagę wskazującą, czy kontener pozwala formantowi wyświetlać się z kreskowanym wzorcem, gdy interfejs użytkownika kontrolki jest aktywny.

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>Parametry

*bShowHatching*<br/>
Właściwość DISPID_AMBIENT_SHOWHATCHING.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientSupportsMnemonics

Pobiera DISPID_AMBIENT_SUPPORTSMNEMONICS, flagę wskazującą, czy kontener obsługuje skróty klawiaturowe.

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>Parametry

*bSupportsMnemonics*<br/>
Właściwość DISPID_AMBIENT_SUPPORTSMNEMONICS.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="getambienttextalign"></a>CComControlBase::GetAmbientTextAlign

Pobiera DISPID_AMBIENT_TEXTALIGN, wyrównanie tekstu preferowane przez kontener: 0 w przypadku ogólnego wyrównania (liczby w prawo, tekst z lewej), 1 dla wyrównania po lewej, 2 dla wyrównania Center i 3 do prawej wyrównania.

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>Parametry

*nTextAlign*<br/>
Właściwość DISPID_AMBIENT_TEXTALIGN.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="getambienttoptobottom"></a>CComControlBase::GetAmbientTopToBottom

Pobiera DISPID_AMBIENT_TOPTOBOTTOM, kierunek, w którym zawartość jest wyświetlana przez kontener.

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>Parametry

*bTopToBottom*<br/>
Właściwość DISPID_AMBIENT_TOPTOBOTTOM. Ustaw wartość TRUE, jeśli tekst jest wyświetlany od góry do dołu, FAŁSZ, jeśli jest wyświetlany od dołu do góry.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="getambientuidead"></a>CComControlBase::GetAmbientUIDead

Pobiera DISPID_AMBIENT_UIDEAD, flagę wskazującą, czy kontener chce, aby formant odpowiadał na akcje interfejsu użytkownika.

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>Parametry

*bUIDead*<br/>
Właściwość DISPID_AMBIENT_UIDEAD.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

W przypadku wartości TRUE formant nie powinien reagować. Ta flaga stosuje się niezależnie od flagi DISPID_AMBIENT_USERMODE. Zobacz [CComControlBase:: GetAmbientUserMode](#getambientusermode).

##  <a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode

Pobiera DISPID_AMBIENT_USERMODE, flagę wskazującą, czy kontener jest w trybie uruchomieniowym (TRUE), czy w trybie projektowania (FALSE).

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>Parametry

*bUserMode*<br/>
Właściwość DISPID_AMBIENT_USERMODE.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

##  <a name="getdirty"></a>CComControlBase:: getdirty

Zwraca wartość elementu członkowskiego `m_bRequiresSave`danych.

```
BOOL GetDirty();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość elementu członkowskiego danych [m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Uwagi

Ta wartość jest ustawiana za pomocą [CComControlBase::](#setdirty)SetDirty.

##  <a name="getzoominfo"></a>CComControlBase::GetZoomInfo

Pobiera wartości x i y licznika i mianownik współczynnika powiększenia dla kontrolki aktywowanej do edycji w miejscu.

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*di*<br/>
Struktura, w której będzie przechowywana wartość licznika i mianownik współczynnika powiększenia. Aby uzyskać więcej informacji, zobacz [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).

### <a name="remarks"></a>Uwagi

Współczynnik powiększenia jest proporcją rozmiaru naturalnego formantu do jego bieżącego zakresu.

##  <a name="inplaceactivate"></a>CComControlBase::InPlaceActivate

Powoduje, że kontrolka przechodzi ze stanu nieaktywności do dowolnego stanu, w którym wskazuje zlecenie w *iVerb* .

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Wartość wskazująca akcję, która ma zostać wykonana przez [IOleObjectImpl::D overb](../../atl/reference/ioleobjectimpl-class.md#doverb).

*prcPosRect*<br/>
Wskaźnik na pozycję kontrolki miejscowej.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Przed aktywacją ta metoda sprawdza, czy formant ma lokację klienta, sprawdza, jaka część kontrolki jest widoczna i pobiera lokalizację kontrolki w oknie nadrzędnym. Po aktywowaniu kontrolki ta metoda aktywuje interfejs użytkownika kontrolki i instruuje kontener, aby formant był widoczny.

Ta metoda pobiera `IOleInPlaceSite`również wskaźnik, `IOleInPlaceSiteEx`lub `IOleInPlaceSiteWindowless` interfejsu dla kontrolki i zapisuje ją w składowej danych klasy kontrolki [CComControlBase:: m_spInPlaceSite](#m_spinplacesite). Elementy członkowskie danych klasy kontrolki [CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase:: m_bWndLess](#m_bwndless), [CComControlBase:: M_bWasOnceWindowless](#m_bwasoncewindowless)i [CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd) są ustawione na wartość true, zgodnie z potrzebami.

##  <a name="internalgetsite"></a>  CComControlBase::InternalGetSite

Wywołaj tę metodę, aby wykonać zapytanie o lokację kontroli dla wskaźnika do zidentyfikowanego interfejsu.

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identyfikator IID wskaźnika interfejsu, który powinien zostać zwrócony w *ppUnkSite*.

*ppUnkSite*<br/>
Adres zmiennej wskaźnika, która odbiera wskaźnik interfejsu żądany w *riid*.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Jeśli lokacja obsługuje interfejs żądany w *riid*, wskaźnik jest zwracany przy użyciu *ppUnkSite*. W przeciwnym razie *ppUnkSite* ma wartość null.

##  <a name="m_bautosize"></a>  CComControlBase::m_bAutoSize

Flaga wskazująca, że formant nie może być żadnym innym rozmiarem.

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Uwagi

Ta flaga jest sprawdzana `IOleObjectImpl::SetExtent` przez i, jeśli ma wartość true, powoduje, że funkcja zwraca wartość E_FAIL.

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

Jeśli dodasz opcję **automatycznego rozmiaru** na karcie [Właściwości](../../atl/reference/stock-properties-atl-control-wizard.md) podstawowe kreatora kontrolki ATL, Kreator automatycznie utworzy ten element członkowski danych w klasie kontrolki, utworzy metody PUT i Get dla właściwości i obsługuje [IPropertyNotifySink ](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)w celu automatycznego powiadamiania kontenera o zmianie właściwości.

##  <a name="m_bdrawfromnatural"></a>  CComControlBase::m_bDrawFromNatural

Flaga oznaczająca `IDataObjectImpl::GetData` , `CComControlBase::GetZoomInfo` że należy ustawić rozmiar formantu od `m_sizeNatural` , a nie `m_sizeExtent`z.

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_bdrawgetdatainhimetric"></a>CComControlBase::m_bDrawGetDataInHimetric

Flaga oznaczająca `IDataObjectImpl::GetData` , że należy używać jednostek HIMETRIC, a nie pikseli przy rysowaniu.

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Uwagi

Każda logiczna jednostka HIMETRIC ma 0,01 milimetrów.

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_binplaceactive"></a>  CComControlBase::m_bInPlaceActive

Flaga wskazująca, że formant jest aktywny w miejscu.

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Uwagi

Oznacza to, że formant jest widoczny, a jego okno (jeśli istnieje) jest widoczne, ale jego menu i paski narzędzi mogą nie być aktywne. `m_bUIActive` Flaga wskazuje, że interfejs użytkownika kontrolki, taki jak menu, jest również aktywny.

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_binplacesiteex"></a>  CComControlBase::m_bInPlaceSiteEx

Flaga wskazująca, że kontener `IOleInPlaceSiteEx` obsługuje funkcje sterowania interfejsem i OCX96, takie jak kontrolki bez okna i niezawierające migotania.

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

Element członkowski `m_spInPlaceSite` danych wskazuje interfejs [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)lub [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) `m_bWndLess` , w zależności od wartości flag i `m_bInPlaceSiteEx` . (Element członkowski `m_bNegotiatedWnd` danych musi mieć wartość true, `m_spInPlaceSite` aby wskaźnik był prawidłowy).

Jeśli `m_bWndLess` ma wartość false `m_bInPlaceSiteEx` `m_spInPlaceSite` i`IOleInPlaceSiteEx` ma wartość true, jest wskaźnikiem interfejsu. Zobacz [m_spInPlaceSite](#m_spinplacesite) , aby uzyskać tabelę przedstawiającą relację między tymi trzema elementami członkowskimi danych.

##  <a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd

Flaga oznaczająca, czy kontrolka została wynegocjowana z kontenerem o obsłudze funkcji kontroli OCX96 (takich jak kontrolki bez okna i nieokienkowe), oraz czy kontrolka jest okienkowa, czy bez okien.

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

Aby wskaźnik był prawidłowy, `m_spInPlaceSite` Flagamusimiećwartośćtrue.`m_bNegotiatedWnd`

##  <a name="m_brecomposeonresize"></a>CComControlBase::m_bRecomposeOnResize

Flaga wskazująca, że kontrolka chce ponownie złożyć swoją prezentację, gdy kontener zmieni rozmiar wyświetlania formantu.

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

Ta flaga jest sprawdzana przez [IOleObjectImpl:: setzakres](../../atl/reference/ioleobjectimpl-class.md#setextent) i, Jeśli true `SetExtent` , powiadamia kontener o zmianach widoku. Jeśli ta flaga jest ustawiona, należy również ustawić bit OLEMISC_RECOMPOSEONRESIZE w wyliczeniu [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) .

##  <a name="m_brequiressave"></a>CComControlBase::m_bRequiresSave

Flaga wskazująca, że formant został zmieniony od ostatniego zapisu.

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Uwagi

Wartość `m_bRequiresSave` można ustawić za pomocą [CComControlBase::](#setdirty) SetDirty i pobranej z [CComControlBase::](#getdirty)getdirty.

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural

Flaga wskazująca, że formant chce zmienić rozmiar swojego naturalnego zakresu (nieskalowanego rozmiaru fizycznego), gdy kontener zmienia rozmiar wyświetlania formantu.

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Uwagi

Ta flaga jest sprawdzana `IOleObjectImpl::SetExtent` przez i, jeśli ma wartość true, rozmiar `SetExtent` przekazane do jest `m_sizeNatural`przypisany do.

Rozmiar przekazanego `SetExtent` elementu jest zawsze przypisany do `m_sizeExtent`, niezależnie od wartości. `m_bResizeNatural`

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_buiactive"></a>  CComControlBase::m_bUIActive

Flaga wskazująca, że interfejs użytkownika kontrolki, taki jak menu i paski narzędzi, jest aktywny.

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Uwagi

`m_bInPlaceActive` Flaga wskazuje, że formant jest aktywny, ale nie jest aktywny.

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn

Flaga wskazująca, że formant korzysta z regionu okna dostarczonego z kontenerem.

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_bwasoncewindowless"></a>  CComControlBase::m_bWasOnceWindowless

Flaga wskazująca, że kontrolka została bez okien, ale może nie być teraz bez okien.

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_bwindowonly"></a>CComControlBase::m_bWindowOnly

Flaga wskazująca, że formant powinien być okienkowy, nawet jeśli kontener obsługuje kontrolki bez okien.

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_bwndless"></a>CComControlBase::m_bWndLess

Flaga wskazująca, że formant jest bez okien.

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

Element `m_spInPlaceSite` członkowski danych wskazuje interfejs [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)lub [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) `m_bWndLess` , w zależności od wartości flag i [CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex) . (Element członkowski danych [CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd) musi mieć wartość true, aby wskaźnik [CComControlBase:: m_spInPlaceSite](#m_spinplacesite) był prawidłowy.)

Jeśli `m_bWndLess` ma wartość true `m_spInPlaceSite` , jest `IOleInPlaceSiteWindowless` wskaźnikiem interfejsu. Zobacz [CComControlBase:: m_spInPlaceSite](#m_spinplacesite) dla tabeli pokazującej pełną relację między tymi elementami członkowskimi danych.

##  <a name="m_hwndcd"></a>CComControlBase::m_hWndCD

Zawiera odwołanie do uchwytu okna skojarzonego z kontrolką.

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents

Liczba zdarzeń zamrożonych w kontenerze (odrzuconych do zaakceptowania zdarzeń) bez interwencji z rozmrożeniem zdarzeń (akceptowanie zdarzeń).

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_rcpos"></a>CComControlBase::m_rcPos

Pozycja w pikselach kontrolki wyrażona we współrzędnych kontenera.

```
RECT m_rcPos;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_sizeextent"></a>CComControlBase::m_sizeExtent

Zakres formantu w jednostkach HIMETRIC (każda jednostka to 0,01 milimetrów) dla określonego ekranu.

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

Ten rozmiar jest skalowany na ekranie. Rozmiar fizyczny kontrolki jest określony w `m_sizeNatural` elemencie członkowskim danych i jest stały.

Możesz skonwertować rozmiar do pikseli przy użyciu funkcji globalnej [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_sizenatural"></a>CComControlBase::m_sizeNatural

Rozmiar fizyczny formantu w jednostkach HIMETRIC (każda jednostka to 0,01 milimetrów).

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

Ten rozmiar jest ustalony, podczas gdy rozmiar `m_sizeExtent` w programie jest skalowany na ekranie.

Możesz skonwertować rozmiar do pikseli przy użyciu funkcji globalnej [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_spadvisesink"></a>  CComControlBase::m_spAdviseSink

Bezpośredni wskaźnik do połączenia Doradczego na kontenerze ( [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)kontenera).

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_spambientdispatch"></a>  CComControlBase::m_spAmbientDispatch

Obiekt, który umożliwia pobieranie i Ustawianie właściwości obiektu `IDispatch` za pomocą wskaźnika. `CComDispatchDriver`

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_spclientsite"></a>  CComControlBase::m_spClientSite

Wskaźnik do lokacji klienta kontrolki w kontenerze.

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

##  <a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder

Zapewnia standardową metodę utrzymywania połączeń doradczych między obiektami danych i doradzania ujściam.

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

Obiekt danych jest formantem, który może przesyłać dane i implementuje [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject), których metody określają format i nośnik transferu danych.

Interfejs `m_spDataAdviseHolder` implementuje metody [IDataObject::D Advise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) i [IDataObject::D](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) nie doradzają metodami do nawiązywania i usuwania połączeń doradczych do kontenera. Kontener kontrolki musi implementować obiekt doradzający przez obsługę interfejsu [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) .

##  <a name="m_spinplacesite"></a>  CComControlBase::m_spInPlaceSite

Wskaźnik do wskaźnika interfejsu [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)lub IOleInPlaceSiteWindowlessu kontenera [](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) .

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

Wskaźnik jest prawidłowy tylko wtedy, gdy flaga m_bNegotiatedWnd ma wartość true. [](#m_bnegotiatedwnd) `m_spInPlaceSite`

W poniższej tabeli przedstawiono sposób, `m_spInPlaceSite` w jaki typ wskaźnika zależy od flag elementu członkowskiego danych [m_bWndLess](#m_bwndless) i [m_bInPlaceSiteEx](#m_binplacesiteex) :

|m_spInPlaceSite Type|m_bWndLess wartość|m_bInPlaceSiteEx wartość|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|OZNACZA|PRAWDA lub FAŁSZ|
|`IOleInPlaceSiteEx`|FAŁSZ|OZNACZA|
|`IOleInPlaceSite`|FAŁSZ|FAŁSZ|

##  <a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder

Zapewnia standardową implementację sposobu utrzymywania połączeń doradczych.

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w klasie formantów, należy zadeklarować go jako element członkowski danych w klasie kontrolki. Klasa kontrolki nie będzie dziedziczyć tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest ona zadeklarowana w Unii w klasie bazowej.

Interfejs `m_spOleAdviseHolder` implementuje metody [IOleObject:: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) i [IOleObject:: Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) do nawiązywania i usuwania połączeń doradczych do kontenera. Kontener kontrolki musi implementować obiekt doradzający przez obsługę interfejsu [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) .

##  <a name="ondraw"></a>CComControlBase:: OnDraw

Zastąp tę metodę, aby narysować kontrolkę.

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*di*<br/>
Odwołanie do struktury [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) , która zawiera informacje o rysunku, takie jak aspekt rysowania, granice kontrolki i czy rysunek jest zoptymalizowany.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Domyślnie `OnDraw` usuwa lub przywraca kontekst urządzenia albo nie robi nic, w zależności od flag ustawionych w [CComControlBase:: OnDrawAdvanced](#ondrawadvanced).

`OnDraw` Metoda jest automatycznie dodawana do klasy formantów podczas tworzenia kontrolki za pomocą Kreatora kontrolki ATL. Domyślny `OnDraw` Kreator rysuje prostokąt z etykietą "ATL 8,0".

### <a name="example"></a>Przykład

Zobacz przykład dla [CComControlBase:: GetAmbientAppearance](#getambientappearance).

##  <a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced

Domyślnie `OnDrawAdvanced` przygotowuje znormalizowany kontekst urządzenia do rysowania, a następnie wywołuje `OnDraw` metodę klasy formantu.

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*di*<br/>
Odwołanie do struktury [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) , która zawiera informacje o rysunku, takie jak aspekt rysowania, granice kontrolki i czy rysunek jest zoptymalizowany.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, jeśli chcesz zaakceptować kontekst urządzenia przekazaną przez kontener bez normalizacji.

Aby uzyskać więcej informacji, zobacz [CComControlBase:: OnDraw](#ondraw) .

##  <a name="onkillfocus"></a>CComControlBase::OnKillFocus

Sprawdza, czy formant jest aktywny i ma prawidłową lokację kontroli, a następnie informuje o tym, że formant utracił fokus.

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Rezerwacj.

*wParam*<br/>
Rezerwacj.

*lParam*<br/>
Rezerwacj.

*bHandled*<br/>
Flaga wskazująca, czy komunikat okna został pomyślnie obsłużony. Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca 1.

##  <a name="onmouseactivate"></a>CComControlBase::OnMouseActivate

Sprawdza, czy interfejs użytkownika znajduje się w trybie użytkownik, a następnie uaktywnia formant.

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Rezerwacj.

*wParam*<br/>
Rezerwacj.

*lParam*<br/>
Rezerwacj.

*bHandled*<br/>
Flaga wskazująca, czy komunikat okna został pomyślnie obsłużony. Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca 1.

##  <a name="onpaint"></a>CComControlBase:: OnPaint

Przygotowuje kontener do malowania, Pobiera obszar klienta kontrolki, a następnie wywołuje `OnDrawAdvanced` metodę klasy formantu.

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Rezerwacj.

*wParam*<br/>
Istniejący używający HDC.

*lParam*<br/>
Rezerwacj.

*lResult*<br/>
Rezerwacj.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca zero.

### <a name="remarks"></a>Uwagi

Jeśli *wParam* nie ma wartości null `OnPaint` , zakłada, że zawiera prawidłowe używający HDC i używa go zamiast [CComControlBase:: m_hWndCD](#m_hwndcd).

##  <a name="onsetfocus"></a>CComControlBase:: funkcji OnSetFocus

Sprawdza, czy formant jest aktywny i ma prawidłową lokację kontroli, a następnie informuje o tym, że formant uzyskał fokus.

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Rezerwacj.

*wParam*<br/>
Rezerwacj.

*lParam*<br/>
Rezerwacj.

*bHandled*<br/>
Flaga wskazująca, czy komunikat okna został pomyślnie obsłużony. Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca 1.

### <a name="remarks"></a>Uwagi

Wysyła powiadomienie do kontenera, w którym formant otrzymał fokus.

##  <a name="pretranslateaccelerator"></a>  CComControlBase::PreTranslateAccelerator

Zastąp tę metodę, aby zapewnić własne programy obsługi akceleratora klawiaturowego.

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Rezerwacj.

*hRet*<br/>
Rezerwacj.

### <a name="return-value"></a>Wartość zwracana

Domyślnie zwraca wartość FALSE.

##  <a name="sendonclose"></a>CComControlBase::SendOnClose

Powiadamia wszystkie ujścia doradców zarejestrowane przez posiadacza doradcy, że formant został zamknięty.

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wysyła powiadomienie, że formant zamknął swoje ujścia doradcy.

##  <a name="sendondatachange"></a>CComControlBase::SendOnDataChange

Powiadamia wszystkie ujścia doradców zarejestrowane przez posiadacza doradcy, że dane kontroli uległy zmianie.

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>Parametry

*advf*<br/>
Zaleca flagi określające sposób wywołania [IAdviseSink:: OnDataChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange) . Wartości pochodzą z wyliczenia [ADVF](/windows/win32/api/objidl/ne-objidl-advf) .

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="sendonrename"></a>CComControlBase::SendOnRename

Powiadamia wszystkie ujścia doradcze zarejestrowane przez posiadacza doradcy, że kontrolka ma nowy moniker.

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Wskaźnik do nowej monikera formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wysyła powiadomienie, że moniker dla kontrolki został zmieniony.

##  <a name="sendonsave"></a>CComControlBase::SendOnSave

Powiadamia wszystkie ujścia doradców zarejestrowane przez posiadacza powiadomienia, że formant został zapisany.

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wysyła powiadomienie, że formant właśnie zapisał swoje dane.

##  <a name="sendonviewchange"></a>CComControlBase::SendOnViewChange

Powiadamia wszystkie zarejestrowane ujścia doradców, że widok kontrolki został zmieniony.

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>Parametry

*dwAspect*<br/>
Aspekt lub widok formantu.

*lindex*<br/>
Część widoku, która zmieniła się. Tylko-1 jest prawidłowy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`SendOnViewChange`wywołuje [IAdviseSink:: OnViewChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange). Jedyną obsługiwaną wartością *Lindex* jest-1, co oznacza, że cały widok jest interesujący.

##  <a name="setcontrolfocus"></a>CComControlBase::SetControlFocus

Ustawia lub usuwa fokus klawiatury do lub z formantu.

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>Parametry

*bGrab*<br/>
W przypadku wartości TRUE ustawia fokus klawiatury dla kontrolki wywołującej. W przypadku wartości FALSE program usuwa fokus klawiatury z kontrolki wywołującej, pod warunkiem, że ma fokus.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, Jeśli kontrolka pomyślnie odbierze fokus; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

W przypadku kontrolki okienkowej wywoływana jest funkcja Windows [](/windows/win32/api/winuser/nf-winuser-setfocus) API SetFocus. W przypadku kontrolki bez okien jest wywoływana funkcja [IOleInPlaceSiteWindowless:: SetFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) . Za pomocą tego wywołania, kontrola bez okien uzyskuje fokus klawiatury i może odpowiadać na komunikaty okna.

##  <a name="setdirty"></a>CComControlBase:: SetDirty

Ustawia element członkowski `m_bRequiresSave` danych na wartość w *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*bDirty*<br/>
Wartość elementu członkowskiego danych [CComControlBase:: m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Uwagi

`SetDirty(TRUE)`powinien zostać wywołany, aby oflagować, że formant został zmieniony od ostatniego zapisu. Wartość `m_bRequiresSave` jest pobierana z [CComControlBase::](#getdirty)getdirty.

## <a name="see-also"></a>Zobacz także

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
