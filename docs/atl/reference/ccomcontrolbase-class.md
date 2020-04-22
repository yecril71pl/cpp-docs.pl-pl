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
ms.openlocfilehash: 15cfa205337248181f02e6a1218d49e75bda58e6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748110"
---
# <a name="ccomcontrolbase-class"></a>Klasa CComControlBase

Ta klasa zawiera metody tworzenia formantów ATL i zarządzania nimi.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CComControlBase::Rodzaj wyglądu](#appearancetype)|Zastąpuj, `m_nAppearance` jeśli właściwość akcji nie jest **typu krótki**.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|Konstruktor.|
|[CComControlBase::~CComControlBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Pobiera wskaźnik do żądanego interfejsu.|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Sprawdza, czy parametr *iVerb* używany `IOleObjectImpl::DoVerb` przez który aktywuje interfejs użytkownika formantu (*iVerb* jest OLEIVERB_UIACTIVATE), definiuje akcję podjętą po dwukrotnym kliknięciu formantu (*iVerb* jest równy OLEIVERB_PRIMARY), wyświetla formant (*iVerb* jest równy OLEIVERB_SHOW) lub aktywuje formant (*iVerb* jest równa OLEIVERB_INPLACEACTIVATE).|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Sprawdza, czy parametr *iVerb* używany przez `IOleObjectImpl::DoVerb` powoduje, że interfejs użytkownika formantu, aby aktywować i zwraca wartość TRUE.|
|[CComControlBase::DoVerbProperties](#doverbproperties)|Wyświetla strony właściwości formantu.|
|[CComControlBase::FireViewZmienienie](#fireviewchange)|Wywołanie tej metody, aby poinformować kontenera, aby przerysować formant lub powiadomić zarejestrowane powiadomić sinks, że widok formantu uległ zmianie.|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Pobiera DISPID_AMBIENT_APPEARANCE, bieżące ustawienie wyglądu dla formantu: 0 dla płaskiego i 1 dla 3D.|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Pobiera DISPID_AMBIENT_AUTOCLIP, flagę wskazującą, czy kontener obsługuje automatyczne przycinanie obszaru wyświetlania sterowania.|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Pobiera DISPID_AMBIENT_BACKCOLOR, kolor tła otoczenia dla wszystkich formantów, zdefiniowane przez kontener.|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Pobiera DISPID_AMBIENT_CHARSET, zestaw znaków otoczenia dla wszystkich formantów, zdefiniowane przez kontener.|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Pobiera DISPID_AMBIENT_CODEPAGE, zestaw znaków otoczenia dla wszystkich formantów, zdefiniowane przez kontener.|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Pobiera DISPID_AMBIENT_DISPLAYASDEFAULT, flagę, która ma wartość TRUE, jeśli kontener oznaczył formant w tej witrynie jako przycisk domyślny, a zatem formant przycisku powinien narysować się grubszą ramką.|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Pobiera DISPID_AMBIENT_DISPLAYNAME, nazwę kontenera dostarczył do formantu.|
|[CComControlBase::GetAmbientFont](#getambientfont)|Pobiera wskaźnik do interfejsu otoczenia `IFont` kontenera.|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Pobiera wskaźnik do interfejsu wysyłki `IFontDisp` otoczenia kontenera.|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Pobiera DISPID_AMBIENT_FORECOLOR, otaczający kolor pierwszego planu dla wszystkich formantów, zdefiniowane przez kontener.|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Pobiera DISPID_AMBIENT_LOCALEID, identyfikator języka używanego przez kontener.|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Pobiera DISPID_AMBIENT_MESSAGEREFLECT, flagę wskazującą, czy kontener chce odbierać komunikaty okna (takie jak WM_DRAWITEM) jako zdarzenia.|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Pobiera DISPID_AMBIENT_PALETTE, używane do uzyskiwania dostępu do hpalette kontenera.|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Pobiera właściwość kontenera określoną przez *identyfikator*.|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Pobiera DISPID_AMBIENT_RIGHTTOLEFT, kierunek, w którym zawartość jest wyświetlana przez kontener.|
|[CComControlBase::GetAmbientScaleJednostki](#getambientscaleunits)|Pobiera DISPID_AMBIENT_SCALEUNITS, jednostki otoczenia kontenera (takie jak cale lub centymetry) do etykietowania wyświetlaczy.|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Pobiera DISPID_AMBIENT_SHOWGRABHANDLES, flagę wskazującą, czy kontener umożliwia formantowi wyświetlanie uchwytów chwytania dla siebie, gdy jest aktywny.|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Pobiera DISPID_AMBIENT_SHOWHATCHING, flagę wskazującą, czy kontener umożliwia formantowi wyświetlanie się z kreskowanym wzorkiem, gdy interfejs użytkownika jest aktywny.|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Pobiera DISPID_AMBIENT_SUPPORTSMNEMONICS, flagę wskazującą, czy kontener obsługuje klawiatury mnemoniki.|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Pobiera DISPID_AMBIENT_TEXTALIGN, wyrównanie tekstu preferowane przez kontener: 0 dla wyrównania ogólnego (liczby w prawo, tekst w lewo), 1 dla wyrównania w lewo, 2 dla wyrównania środka i 3 dla wyrównania w prawo.|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Pobiera DISPID_AMBIENT_TOPTOBOTTOM, kierunek, w którym zawartość jest wyświetlana przez kontener.|
|[CComControlBase::GetAmbientUiDead](#getambientuidead)|Pobiera DISPID_AMBIENT_UIDEAD, flagę wskazującą, czy kontener chce, aby formant odpowiadał na akcje interfejsu użytkownika.|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Pobiera DISPID_AMBIENT_USERMODE, flagę wskazującą, czy kontener jest w trybie uruchamiania (PRAWDA) lub w trybie projektowania (FALSE).|
|[CComControlBase::GetDirty](#getdirty)|Zwraca wartość elementu `m_bRequiresSave`członkowskiego danych .|
|[CComControlBase::GetZoomInfo](#getzoominfo)|Pobiera wartości x i y licznika i mianownika współczynnika powiększenia dla formantu aktywowanego do edycji w miejscu.|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Powoduje, że formant do przejścia ze stanu nieaktywnego do dowolnego stanu zlecenie w *iVerb* wskazuje.|
|[CComControlBase::InternalGetSite](#internalgetsite)|Wywołanie tej metody, aby zbadać witrynę formantu dla wskaźnika do zidentyfikowanego interfejsu.|
|[CComControlBase::OnDraw](#ondraw)|Zastąd w tej metodzie należy narysować formant.|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|Domyślnie `OnDrawAdvanced` przygotowuje znormalizowane kontekście urządzenia do rysowania, a następnie wywołuje `OnDraw` metodę klasy sterowania.|
|[CComControlBase::OnKillFocus](#onkillfocus)|Sprawdza, czy formant jest aktywny w miejscu i ma prawidłową lokację formantu, a następnie informuje kontener, że formant utracił fokus.|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Sprawdza, czy interfejs użytkownika jest w trybie użytkownika, a następnie aktywuje formant.|
|[CComControlBase::OnPaint](#onpaint)|Przygotowuje kontener do malowania, pobiera obszar klienta formantu, a `OnDraw` następnie wywołuje metodę klasy control.|
|[CComControlBase::OnSetFocus](#onsetfocus)|Sprawdza, czy formant jest aktywny w miejscu i ma prawidłową lokację formantu, a następnie informuje kontener, który uzyskał fokus.|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Zastąd w tej metodzie należy udostępnić własne programy obsługi akceleratora klawiatury.|
|[CComControlBase::SendOnClose](#sendonclose)|Powiadamia wszystkie zlewozmywaki doradcze zarejestrowane u posiadacza informacji, że kontrola została zamknięta.|
|[CComControlBase::SendOnDataWyłącznik](#sendondatachange)|Powiadamia wszystkie zlewozmywaki doradcze zarejestrowane u posiadacza informacji, że dane kontrolne uległy zmianie.|
|[CComControlBase::SendOnRename](#sendonrename)|Powiadamia wszystkie zlewozmywaki doradcze zarejestrowane u posiadacza informacji, że formant ma nowy moniker.|
|[CComControlBase::SendOnSave](#sendonsave)|Powiadamia wszystkie zlewozmywaki doradcze zarejestrowane u posiadacza informacji, że kontrola została zapisana.|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Powiadamia wszystkie zarejestrowane pochłaniacze doradcze, że widok formantu został zmieniony.|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Ustawia lub usuwa fokus klawiatury do lub z formantu.|
|[CComControlBase::SetDirty](#setdirty)|Ustawia element `m_bRequiresSave` członkowski danych na wartość w *bDirty*.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|Flaga wskazująca, że formant nie może mieć innego rozmiaru.|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Flaga `IDataObjectImpl::GetData` wskazująca, że i `CComControlBase::GetZoomInfo` `m_sizeNatural` należy ustawić `m_sizeExtent`rozmiar sterowania z, a nie z .|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Flaga wskazująca, że `IDataObjectImpl::GetData` podczas rysowania należy używać jednostek HIMETRIC, a nie pikseli.|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Flaga wskazująca, że formant jest aktywny w miejscu.|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Flaga wskazująca, `IOleInPlaceSiteEx` że kontener obsługuje interfejs i funkcje sterowania OCX96, takie jak formanty bez okien i bez migotania.|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Flaga wskazująca, czy formant wynegocjował z kontenerem obsługę funkcji sterowania OCX96 (takich jak formanty bez migotania i bez okien) oraz czy formant jest okienny czy bez okien.|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Flaga wskazująca formant chce ponownie skomponować jego prezentacji, gdy kontener zmienia rozmiar wyświetlania formantu.|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Flaga wskazująca, że formant uległ zmianie od czasu jego ostatniego zapisania.|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Flaga wskazująca formant chce zmienić jego rozmiar naturalny (jego rozmiar fizyczny nieskalowania), gdy kontener zmienia rozmiar wyświetlania formantu.|
|[CComControlBase::m_bUIActive](#m_buiactive)|Flaga wskazująca interfejs użytkownika formantu, takich jak menu i paski narzędzi, jest aktywny.|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Flaga wskazująca, że formant używa regionu okna dostarczonego przez kontener.|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Flaga wskazująca formant został bez okien, ale może lub nie może być teraz bez okien.|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Flaga wskazująca formant powinien być windowed, nawet jeśli kontener obsługuje formantów bez okien.|
|[CComControlBase::m_bWndLess](#m_bwndless)|Flaga wskazująca formant jest bez okien.|
|[CComControlBase::m_hWndCD](#m_hwndcd)|Zawiera odwołanie do dojścia okna skojarzonego z formantem.|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Liczba zamrożonych zdarzeń w kontenerze (odmowa przyjęcia zdarzeń) bez interweniującej odwilży zdarzeń (akceptacja zdarzeń).|
|[CComControlBase::m_rcPos](#m_rcpos)|Położenie w pikselach formantu, wyrażone we współrzędnych kontenera.|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|Zasięg sterowania w jednostkach HIMETRIC (każda jednostka wynosi 0,01 milimetra) dla określonego wyświetlacza.|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|Fizyczny rozmiar formantu w jednostkach HIMETRIC (każda jednostka wynosi 0,01 milimetra).|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Bezpośredni wskaźnik do połączenia doradczego w kontenerze (kontener [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)).|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|Obiekt, `CComDispatchDriver` który umożliwia pobieranie i ustawianie właściwości kontenera za pomocą wskaźnika. `IDispatch`|
|[CComControlBase::m_spClientSite](#m_spclientsite)|Wskaźnik do lokacji klienta formantu w kontenerze.|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Zapewnia standardowy sposób przechowywania połączeń doradczych między obiektami danych i doradzania pochłaniaczom.|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Wskaźnik do kontenera [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaCeSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)lub [IOleInPlaCeSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) wskaźnik interfejsu.|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Zapewnia standardową implementację sposobu utrzymywania połączeń doradczych.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera metody tworzenia formantów ATL i zarządzania nimi. [Klasa CComControl](../../atl/reference/ccomcontrol-class.md) wywodzi się od `CComControlBase`. Podczas tworzenia formantu standardowego lub kontrolki DHTML za pomocą Kreatora `CComControlBase`sterowania ATL kreator automatycznie wyprowadzi klasę z programu .

Aby uzyskać więcej informacji na temat tworzenia formantu, zobacz [samouczek ATL](../../atl/active-template-library-atl-tutorial.md). Aby uzyskać więcej informacji na temat Kreatora projektów ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="ccomcontrolbaseappearancetype"></a><a name="appearancetype"></a>CComControlBase::Rodzaj wyglądu

Zastąpuj, `m_nAppearance` jeśli właściwość akcji nie jest **typu krótki**.

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Uwagi

Kreator sterowania ATL `m_nAppearance` dodaje właściwość magazynu typu krótki. Zastąpuj, `AppearanceType` jeśli używasz innego typu danych.

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="ccomcontrolbase"></a>CComControlBase::CComControlBase

Konstruktor.

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Dojście do okna skojarzone z formantem.

### <a name="remarks"></a>Uwagi

Inicjuje rozmiar formantu do jednostek HIMETRIC 5080X5080 (2"X2") i inicjuje wartości elementu `CComControlBase` członkowskiego danych na wartość NULL lub FALSE.

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="dtor"></a>CComControlBase::~CComControlBase

Destruktor.

```
~CComControlBase();
```

### <a name="remarks"></a>Uwagi

Jeśli formant jest `~CComControlBase` w oknie, niszczy go, wywołując [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow).

## <a name="ccomcontrolbasecontrolqueryinterface"></a><a name="controlqueryinterface"></a>CComControlBase::ControlQueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
Identyfikator GUID żądanego interfejsu.

*Ppv*<br/>
Wskaźnik do wskaźnika interfejsu identyfikowanego przez *iid*lub NULL, jeśli interfejs nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

Obsługuje tylko interfejsy w tabeli mapy COM.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

## <a name="ccomcontrolbasedoesverbactivate"></a><a name="doesverbactivate"></a>CComControlBase::DoesVerbActivate

Sprawdza, czy parametr *iVerb* używany `IOleObjectImpl::DoVerb` przez który aktywuje interfejs użytkownika formantu (*iVerb* jest OLEIVERB_UIACTIVATE), definiuje akcję podjętą po dwukrotnym kliknięciu formantu (*iVerb* jest równy OLEIVERB_PRIMARY), wyświetla formant (*iVerb* jest równy OLEIVERB_SHOW) lub aktywuje formant (*iVerb* jest równa OLEIVERB_INPLACEACTIVATE).

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Wartość wskazująca akcję, która `DoVerb`ma zostać wykonana przez .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli *iVerb* jest równa OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW lub OLEIVERB_INPLACEACTIVATE; w przeciwnym razie zwraca wartość FAŁSZ.

### <a name="remarks"></a>Uwagi

Tę metodę można zastąpić w celu zdefiniowania własnego zlecenia aktywacji.

## <a name="ccomcontrolbasedoesverbuiactivate"></a><a name="doesverbuiactivate"></a>CComControlBase::DoesVerbUIActivate

Sprawdza, czy parametr *iVerb* używany przez `IOleObjectImpl::DoVerb` powoduje, że interfejs użytkownika formantu, aby aktywować i zwraca wartość TRUE.

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Wartość wskazująca akcję, która `DoVerb`ma zostać wykonana przez .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli *iVerb* jest równa OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW lub OLEIVERB_INPLACEACTIVATE. W przeciwnym razie metoda zwraca wartość FAŁSZ.

## <a name="ccomcontrolbasedoverbproperties"></a><a name="doverbproperties"></a>CComControlBase::DoVerbProperties

Wyświetla strony właściwości formantu.

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>Parametry

*chcPosRec*<br/>
Zarezerwowany.

*hwndRodziciela*<br/>
Uchwyt okna zawierającego formant.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

## <a name="ccomcontrolbasefireviewchange"></a><a name="fireviewchange"></a>CComControlBase::FireViewZmienienie

Wywołanie tej metody, aby poinformować kontenera, aby przerysować formant lub powiadomić zarejestrowane powiadomić sinks, że widok formantu uległ zmianie.

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli formant jest aktywny (element członkowski danych klasy kontrolnej [CComControlBase::m_bInPlaceActive](#m_binplaceactive) ma wartość TRUE), powiadamia kontener, który ma zostać ponownie rysowany przez cały formant. Jeśli formant jest nieaktywny, powiadamia zarejestrowanych kontroli sinks (za pośrednictwem elementu danych klasy kontrolnej [CComControlBase::m_spAdviseSink),](#m_spadvisesink)że widok formantu uległ zmianie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

## <a name="ccomcontrolbasegetambientappearance"></a><a name="getambientappearance"></a>CComControlBase::GetAmbientAppearance

Pobiera DISPID_AMBIENT_APPEARANCE, bieżące ustawienie wyglądu dla formantu: 0 dla płaskiego i 1 dla 3D.

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>Parametry

*nPojatrakcja*<br/>
Obiekt DISPID_AMBIENT_APPEARANCE.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

## <a name="ccomcontrolbasegetambientautoclip"></a><a name="getambientautoclip"></a>CComControlBase::GetAmbientAutoClip

Pobiera DISPID_AMBIENT_AUTOCLIP, flagę wskazującą, czy kontener obsługuje automatyczne przycinanie obszaru wyświetlania sterowania.

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>Parametry

*bAutoClip*<br/>
Obiekt DISPID_AMBIENT_AUTOCLIP.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomcontrolbasegetambientbackcolor"></a><a name="getambientbackcolor"></a>CComControlBase::GetAmbientBackColor

Pobiera DISPID_AMBIENT_BACKCOLOR, kolor tła otoczenia dla wszystkich formantów, zdefiniowane przez kontener.

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>Parametry

*Backcolor*<br/>
Obiekt DISPID_AMBIENT_BACKCOLOR.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomcontrolbasegetambientcharset"></a><a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet

Pobiera DISPID_AMBIENT_CHARSET, zestaw znaków otoczenia dla wszystkich formantów, zdefiniowane przez kontener.

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>Parametry

*zestaw bstrCharSet*<br/>
Obiekt DISPID_AMBIENT_CHARSET.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="ccomcontrolbasegetambientcodepage"></a><a name="getambientcodepage"></a>CComControlBase::GetAmbientCodePage

Pobiera DISPID_AMBIENT_CODEPAGE, otaczającej strony kodowej dla wszystkich formantów, zdefiniowane przez kontener.

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>Parametry

*strona ulCodePage*<br/>
Obiekt DISPID_AMBIENT_CODEPAGE.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="ccomcontrolbasegetambientdisplayasdefault"></a><a name="getambientdisplayasdefault"></a>CComControlBase::GetAmbientDisplayAsDefault

Pobiera DISPID_AMBIENT_DISPLAYASDEFAULT, flagę, która ma wartość TRUE, jeśli kontener oznaczył formant w tej witrynie jako przycisk domyślny, a zatem formant przycisku powinien narysować się grubszą ramką.

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*bDisplayAsDefault*<br/>
Obiekt DISPID_AMBIENT_DISPLAYASDEFAULT.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomcontrolbasegetambientdisplayname"></a><a name="getambientdisplayname"></a>CComControlBase::GetAmbientDisplayName

Pobiera DISPID_AMBIENT_DISPLAYNAME, nazwę kontenera dostarczył do formantu.

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>Parametry

*nazwa bstrDisplayName*<br/>
Obiekt DISPID_AMBIENT_DISPLAYNAME.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomcontrolbasegetambientfont"></a><a name="getambientfont"></a>CComControlBase::GetAmbientFont

Pobiera wskaźnik do interfejsu otoczenia `IFont` kontenera.

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont (polski)*<br/>
Wskaźnik do otaczającego interfejsu [IFont](/windows/win32/api/ocidl/nn-ocidl-ifont) kontenera.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli właściwość ma wartość NULL, wskaźnik ma wartość NULL. Jeśli wskaźnik nie jest null, wywołujący musi zwolnić wskaźnik.

## <a name="ccomcontrolbasegetambientfontdisp"></a><a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp

Pobiera wskaźnik do interfejsu wysyłki `IFontDisp` otoczenia kontenera.

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont (polski)*<br/>
Wskaźnik do otaczającego interfejsu wysyłki [IFontDisp](/windows/win32/api/ocidl/nn-ocidl-ifontdisp) kontenera.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Jeśli właściwość ma wartość NULL, wskaźnik ma wartość NULL. Jeśli wskaźnik nie jest null, wywołujący musi zwolnić wskaźnik.

## <a name="ccomcontrolbasegetambientforecolor"></a><a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor

Pobiera DISPID_AMBIENT_FORECOLOR, otaczający kolor pierwszego planu dla wszystkich formantów, zdefiniowane przez kontener.

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>Parametry

*Forecolor*<br/>
Obiekt DISPID_AMBIENT_FORECOLOR.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomcontrolbasegetambientlocaleid"></a><a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID

Pobiera DISPID_AMBIENT_LOCALEID, identyfikator języka używanego przez kontener.

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Obiekt DISPID_AMBIENT_LOCALEID.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Formant może użyć tego identyfikatora, aby dostosować swój interfejs użytkownika do różnych języków.

## <a name="ccomcontrolbasegetambientmessagereflect"></a><a name="getambientmessagereflect"></a>CComControlBase::GetAmbientMessageReflect

Pobiera DISPID_AMBIENT_MESSAGEREFLECT, flagę wskazującą, czy kontener chce odbierać komunikaty okna (na `WM_DRAWITEM`przykład) jako zdarzenia.

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>Parametry

*bMessageReflect*<br/>
Obiekt DISPID_AMBIENT_MESSAGEREFLECT.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomcontrolbasegetambientpalette"></a><a name="getambientpalette"></a>CComControlBase::GetAmbientPalette

Pobiera DISPID_AMBIENT_PALETTE, używane do uzyskiwania dostępu do hpalette kontenera.

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>Parametry

*hPalette (paleta hpalette)*<br/>
Obiekt DISPID_AMBIENT_PALETTE.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomcontrolbasegetambientproperty"></a><a name="getambientproperty"></a>CComControlBase::GetAmbientProperty

Pobiera właściwość kontenera określoną przez *dispid*.

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
Identyfikator właściwości kontenera do pobrania.

*var*<br/>
Zmienna, aby otrzymać właściwość.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

ATL dostarczył zestaw funkcji pomocnika do pobierania określonych właściwości, na przykład [CComControlBase::GetAmbientBackColor](#getambientbackcolor). Jeśli nie ma dostępnej `GetAmbientProperty`odpowiedniej metody, należy użyć .

## <a name="ccomcontrolbasegetambientrighttoleft"></a><a name="getambientrighttoleft"></a>CComControlBase::GetAmbientRightToLeft

Pobiera DISPID_AMBIENT_RIGHTTOLEFT, kierunek, w którym zawartość jest wyświetlana przez kontener.

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>Parametry

*bRightToDodzierka*<br/>
Obiekt DISPID_AMBIENT_RIGHTTOLEFT. Ustaw wartość PRAWDA, jeśli zawartość jest wyświetlana od prawej do lewej, FALSE, jeśli jest wyświetlana od lewej do prawej.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="ccomcontrolbasegetambientscaleunits"></a><a name="getambientscaleunits"></a>CComControlBase::GetAmbientScaleJednostki

Pobiera DISPID_AMBIENT_SCALEUNITS, jednostki otoczenia kontenera (takie jak cale lub centymetry) do etykietowania wyświetlaczy.

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>Parametry

*jednostki bstrScaleunits*<br/>
Obiekt DISPID_AMBIENT_SCALEUNITS.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomcontrolbasegetambientshowgrabhandles"></a><a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles

Pobiera DISPID_AMBIENT_SHOWGRABHANDLES, flagę wskazującą, czy kontener umożliwia formantowi wyświetlanie uchwytów chwytania dla siebie, gdy jest aktywny.

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>Parametry

*bShowGrabHandles*<br/>
Obiekt DISPID_AMBIENT_SHOWGRABHANDLES.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomcontrolbasegetambientshowhatching"></a><a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching

Pobiera DISPID_AMBIENT_SHOWHATCHING, flagę wskazującą, czy kontener umożliwia formantowi wyświetlanie się z kreskowanym wzorkiem, gdy interfejs użytkownika formantu jest aktywny.

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>Parametry

*bShowHatching*<br/>
Obiekt DISPID_AMBIENT_SHOWHATCHING.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomcontrolbasegetambientsupportsmnemonics"></a><a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientSupportsMnemonics

Pobiera DISPID_AMBIENT_SUPPORTSMNEMONICS, flagę wskazującą, czy kontener obsługuje klawiatury mnemoniki.

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>Parametry

*bSupportsMnemonics*<br/>
Obiekt DISPID_AMBIENT_SUPPORTSMNEMONICS.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomcontrolbasegetambienttextalign"></a><a name="getambienttextalign"></a>CComControlBase::GetAmbientTextAlign

Pobiera DISPID_AMBIENT_TEXTALIGN, wyrównanie tekstu preferowane przez kontener: 0 dla wyrównania ogólnego (liczby w prawo, tekst w lewo), 1 dla wyrównania w lewo, 2 dla wyrównania środka i 3 dla wyrównania w prawo.

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>Parametry

*nTeksalnie*<br/>
Obiekt DISPID_AMBIENT_TEXTALIGN.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomcontrolbasegetambienttoptobottom"></a><a name="getambienttoptobottom"></a>CComControlBase::GetAmbientTopToBottom

Pobiera DISPID_AMBIENT_TOPTOBOTTOM, kierunek, w którym zawartość jest wyświetlana przez kontener.

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>Parametry

*bTopToBottom*<br/>
Obiekt DISPID_AMBIENT_TOPTOBOTTOM. Ustaw wartość PRAWDA, jeśli tekst jest wyświetlany od góry do dołu, FALSE, jeśli jest wyświetlany od dołu do góry.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="ccomcontrolbasegetambientuidead"></a><a name="getambientuidead"></a>CComControlBase::GetAmbientUiDead

Pobiera DISPID_AMBIENT_UIDEAD, flagę wskazującą, czy kontener chce, aby formant odpowiadał na akcje interfejsu użytkownika.

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>Parametry

*bUIDead*<br/>
Obiekt DISPID_AMBIENT_UIDEAD.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli true, formant nie powinien odpowiadać. Ta flaga ma zastosowanie niezależnie od flagi DISPID_AMBIENT_USERMODE. Zobacz [CComControlBase::GetAmbientUserMode](#getambientusermode).

## <a name="ccomcontrolbasegetambientusermode"></a><a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode

Pobiera DISPID_AMBIENT_USERMODE, flagę wskazującą, czy kontener jest w trybie uruchamiania (PRAWDA) lub w trybie projektowania (FALSE).

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>Parametry

*BMode dla typuuser*<br/>
Obiekt DISPID_AMBIENT_USERMODE.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomcontrolbasegetdirty"></a><a name="getdirty"></a>CComControlBase::GetDirty

Zwraca wartość elementu `m_bRequiresSave`członkowskiego danych .

```
BOOL GetDirty();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość m_bRequiresSave [elementu](#m_brequiressave)członkowskiego danych .

### <a name="remarks"></a>Uwagi

Ta wartość jest ustawiana przy użyciu [CComControlBase::SetDirty](#setdirty).

## <a name="ccomcontrolbasegetzoominfo"></a><a name="getzoominfo"></a>CComControlBase::GetZoomInfo

Pobiera wartości x i y licznika i mianownika współczynnika powiększenia dla formantu aktywowanego do edycji w miejscu.

```cpp
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*Di*<br/>
Struktura, która będzie zawierać licznik i mianownik współczynnika powiększenia. Aby uzyskać więcej informacji, zobacz [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).

### <a name="remarks"></a>Uwagi

Współczynnik powiększenia jest proporcją naturalnego rozmiaru formantu do jego aktualnego zasięgu.

## <a name="ccomcontrolbaseinplaceactivate"></a><a name="inplaceactivate"></a>CComControlBase::InPlaceActivate

Powoduje, że formant do przejścia ze stanu nieaktywnego do dowolnego stanu zlecenie w *iVerb* wskazuje.

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Wartość wskazująca akcję, która ma być wykonana przez [IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb).

*chrl.ekcPosRect*<br/>
Wskaźnik do położenia formantu w miejscu.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Przed aktywacją ta metoda sprawdza, czy formant ma lokację klienta, sprawdza, ile formantu jest widoczny i pobiera lokalizację formantu w oknie nadrzędnym. Po aktywowaniu formantu ta metoda aktywuje interfejs użytkownika formantu i informuje kontener, aby formant był widoczny.

Ta metoda pobiera `IOleInPlaceSite`również `IOleInPlaceSiteEx`wskaźnik `IOleInPlaceSiteWindowless` , lub interfejsu dla formantu i przechowuje go w elementów członkowskich danych klasy kontrolnej [CComControlBase::m_spInPlaceSite](#m_spinplacesite). Elementy członkowskie danych klasy kontrolnej [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase::m_bWndLess](#m_bwndless), [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)i [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) są ustawione na true odpowiednio.

## <a name="ccomcontrolbaseinternalgetsite"></a><a name="internalgetsite"></a>CComControlBase::InternalGetSite

Wywołanie tej metody, aby zbadać witrynę formantu dla wskaźnika do zidentyfikowanego interfejsu.

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>Parametry

*Riid*<br/>
Identyfikator wskaźnika interfejsu, który powinien zostać zwrócony w *ppUnkSite*.

*ppUnkSite (polski)*<br/>
Adres zmiennej wskaźnika odbierając wskaźnik interfejsu żądany w *riid*.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Jeśli witryna obsługuje interfejs wymagany w *riid,* wskaźnik jest zwracany za pomocą *ppUnkSite*. W przeciwnym razie *ppUnkSite* jest ustawiona na NULL.

## <a name="ccomcontrolbasem_bautosize"></a><a name="m_bautosize"></a>CComControlBase::m_bAutoSize

Flaga wskazująca, że formant nie może mieć innego rozmiaru.

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Uwagi

Ta flaga jest `IOleObjectImpl::SetExtent` sprawdzana przez i, jeśli TRUE, powoduje, że funkcja zwraca E_FAIL.

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

Jeśli dodasz opcję **Automatyczny rozmiar** na karcie [Właściwości zapasów](../../atl/reference/stock-properties-atl-control-wizard.md) Kreatora sterowania ATL, kreator automatycznie utworzy ten element członkowski danych w klasie formantu, utworzy metody put and get dla właściwości i obsługuje [funkcję IPropertyNotifySink,](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) aby automatycznie powiadamiać kontener o zmianie właściwości.

## <a name="ccomcontrolbasem_bdrawfromnatural"></a><a name="m_bdrawfromnatural"></a>CComControlBase::m_bDrawFromNatural

Flaga `IDataObjectImpl::GetData` wskazująca, że i `CComControlBase::GetZoomInfo` `m_sizeNatural` należy ustawić `m_sizeExtent`rozmiar sterowania z, a nie z .

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_bdrawgetdatainhimetric"></a><a name="m_bdrawgetdatainhimetric"></a>CComControlBase::m_bDrawGetDataInHimetric

Flaga wskazująca, że `IDataObjectImpl::GetData` podczas rysowania należy używać jednostek HIMETRIC, a nie pikseli.

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Uwagi

Każda logiczna jednostka HIMETRIC ma 0,01 milimetra.

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_binplaceactive"></a><a name="m_binplaceactive"></a>CComControlBase::m_bInPlaceActive

Flaga wskazująca, że formant jest aktywny w miejscu.

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Uwagi

Oznacza to, że formant jest widoczny, a jego okno, jeśli istnieje, jest widoczne, ale jego menu i paski narzędzi mogą nie być aktywne. Flaga `m_bUIActive` wskazuje, że interfejs użytkownika formantu, takich jak menu, jest również aktywny.

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_binplacesiteex"></a><a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx

Flaga wskazująca, `IOleInPlaceSiteEx` że kontener obsługuje interfejs i funkcje sterowania OCX96, takie jak formanty bez okien i bez migotania.

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

Element `m_spInPlaceSite` członkowski danych wskazuje interfejs [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaCeSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)lub [IOleInPlaCeSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) interfejs, w zależności od wartości `m_bWndLess` i `m_bInPlaceSiteEx` flagi. (Element członkowski `m_bNegotiatedWnd` danych musi `m_spInPlaceSite` mieć wartość TRUE, aby wskaźnik był prawidłowy).

Jeśli `m_bWndLess` jest `m_bInPlaceSiteEx` false i `m_spInPlaceSite` jest `IOleInPlaceSiteEx` true, jest wskaźnikiem interfejsu. Zobacz [m_spInPlaceSite](#m_spinplacesite) dla tabeli przedstawiającej relację między tymi trzema członkami danych.

## <a name="ccomcontrolbasem_bnegotiatedwnd"></a><a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd

Flaga wskazująca, czy formant wynegocjował z kontenerem obsługę funkcji sterowania OCX96 (takich jak formanty bez migotania i bez okien) oraz czy formant jest okienny czy bez okien.

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

Flaga `m_bNegotiatedWnd` musi być `m_spInPlaceSite` true dla wskaźnika, aby być prawidłowe.

## <a name="ccomcontrolbasem_brecomposeonresize"></a><a name="m_brecomposeonresize"></a>CComControlBase::m_bRecomposeOnResize

Flaga wskazująca formant chce ponownie skomponować jego prezentacji, gdy kontener zmienia rozmiar wyświetlania formantu.

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

Ta flaga jest sprawdzana przez [IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) i, jeśli TRUE, `SetExtent` powiadamia o zmianie kontenera widoku. Jeśli ta flaga jest ustawiona, należy również ustawić bit OLEMISC_RECOMPOSEONRESIZE w wyliczeniu [OLEMISC.](/windows/win32/api/oleidl/ne-oleidl-olemisc)

## <a name="ccomcontrolbasem_brequiressave"></a><a name="m_brequiressave"></a>CComControlBase::m_bRequiresSave

Flaga wskazująca, że formant uległ zmianie od czasu jego ostatniego zapisania.

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Uwagi

Wartość `m_bRequiresSave` można ustawić za pomocą [CComControlBase::SetDirty](#setdirty) i pobrać z [CComControlBase::GetDirty](#getdirty).

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_bresizenatural"></a><a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural

Flaga wskazująca formant chce zmienić jego rozmiar naturalny (jego rozmiar fizyczny nieskalowania), gdy kontener zmienia rozmiar wyświetlania formantu.

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Uwagi

Ta flaga jest `IOleObjectImpl::SetExtent` sprawdzana przez i, `SetExtent` jeśli TRUE, `m_sizeNatural`rozmiar przekazywany jest przypisany do .

Rozmiar przekazywany jest `SetExtent` zawsze `m_sizeExtent`przypisany do , `m_bResizeNatural`niezależnie od wartości .

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_buiactive"></a><a name="m_buiactive"></a>CComControlBase::m_bUIActive

Flaga wskazująca interfejs użytkownika formantu, takich jak menu i paski narzędzi, jest aktywny.

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Uwagi

Flaga `m_bInPlaceActive` wskazuje, że formant jest aktywny, ale nie, że jego interfejs użytkownika jest aktywny.

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_busingwindowrgn"></a><a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn

Flaga wskazująca, że formant używa regionu okna dostarczonego przez kontener.

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_bwasoncewindowless"></a><a name="m_bwasoncewindowless"></a>CComControlBase::m_bWasOnceWindowless

Flaga wskazująca formant został bez okien, ale może lub nie może być teraz bez okien.

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_bwindowonly"></a><a name="m_bwindowonly"></a>CComControlBase::m_bWindowOnly

Flaga wskazująca formant powinien być windowed, nawet jeśli kontener obsługuje formantów bez okien.

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_bwndless"></a><a name="m_bwndless"></a>CComControlBase::m_bWndLess

Flaga wskazująca formant jest bez okien.

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

Element `m_spInPlaceSite` członkowski danych wskazuje interfejs [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaCeSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)lub [IOleInPlaCeSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) interfejs, w zależności od wartości `m_bWndLess` i [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex) flagi. (Element członkowski danych [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) musi być true dla [CComControlBase::m_spInPlaceSite](#m_spinplacesite) wskaźnik jest prawidłowy.)

Jeśli `m_bWndLess` jest `m_spInPlaceSite` true, `IOleInPlaceSiteWindowless` jest wskaźnikiem interfejsu. Zobacz [CComControlBase::m_spInPlaceSite](#m_spinplacesite) dla tabeli przedstawiającej pełną relację między tymi członkami danych.

## <a name="ccomcontrolbasem_hwndcd"></a><a name="m_hwndcd"></a>CComControlBase::m_hWndCD

Zawiera odwołanie do dojścia okna skojarzonego z formantem.

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_nfreezeevents"></a><a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents

Liczba zamrożonych zdarzeń w kontenerze (odmowa przyjęcia zdarzeń) bez interweniującej odwilży zdarzeń (akceptacja zdarzeń).

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_rcpos"></a><a name="m_rcpos"></a>CComControlBase::m_rcPos

Położenie w pikselach formantu, wyrażone we współrzędnych kontenera.

```
RECT m_rcPos;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_sizeextent"></a><a name="m_sizeextent"></a>CComControlBase::m_sizeExtent

Zasięg sterowania w jednostkach HIMETRIC (każda jednostka wynosi 0,01 milimetra) dla określonego wyświetlacza.

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

Ten rozmiar jest skalowany przez wyświetlacz. Rozmiar fizyczny formantu jest `m_sizeNatural` określony w elementów członkowskich danych i jest stały.

Rozmiar można przekonwertować na piksele za pomocą funkcji globalnej [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

## <a name="ccomcontrolbasem_sizenatural"></a><a name="m_sizenatural"></a>CComControlBase::m_sizeNatural

Fizyczny rozmiar formantu w jednostkach HIMETRIC (każda jednostka wynosi 0,01 milimetra).

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

Ten rozmiar jest stały, `m_sizeExtent` podczas gdy rozmiar w jest skalowany przez wyświetlacz.

Rozmiar można przekonwertować na piksele za pomocą funkcji globalnej [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

## <a name="ccomcontrolbasem_spadvisesink"></a><a name="m_spadvisesink"></a>CComControlBase::m_spAdviseSink

Bezpośredni wskaźnik do połączenia doradczego w kontenerze (kontener [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)).

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_spambientdispatch"></a><a name="m_spambientdispatch"></a>CComControlBase::m_spAmbientDispatch

Obiekt, `CComDispatchDriver` który umożliwia pobieranie i ustawianie właściwości obiektu `IDispatch` za pomocą wskaźnika.

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_spclientsite"></a><a name="m_spclientsite"></a>CComControlBase::m_spClientSite

Wskaźnik do lokacji klienta formantu w kontenerze.

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

## <a name="ccomcontrolbasem_spdataadviseholder"></a><a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder

Zapewnia standardowy sposób przechowywania połączeń doradczych między obiektami danych i doradzania pochłaniaczom.

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

Obiekt danych jest formantem, który może przesyłać dane i implementuje [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject), którego metody określają format i nośnik transferu danych.

Interfejs `m_spDataAdviseHolder` implementuje [metody IDataObject::DAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) i [IDataObject::DUnadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) w celu ustanowienia i usunięcia połączeń doradczych z kontenerem. Kontener formantu musi implementować zlewdorawiadczy przez obsługę interfejsu [IAdviseSink.](/windows/win32/api/objidl/nn-objidl-iadvisesink)

## <a name="ccomcontrolbasem_spinplacesite"></a><a name="m_spinplacesite"></a>CComControlBase::m_spInPlaceSite

Wskaźnik do kontenera [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaCeSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)lub [IOleInPlaCeSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) wskaźnik interfejsu.

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

Wskaźnik `m_spInPlaceSite` jest prawidłowy tylko wtedy, gdy flaga [m_bNegotiatedWnd](#m_bnegotiatedwnd) ma wartość PRAWDA.

W poniższej tabeli pokazano, jak typ wskaźnika `m_spInPlaceSite` zależy od flagi [m_bWndLess](#m_bwndless) i [m_bInPlaceSiteEx](#m_binplacesiteex) elementów członkowskich danych:

|Typ m_spInPlaceSite|Wartość m_bWndLess|Wartość m_bInPlaceSiteEx|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|Prawda|PRAWDA lub FAŁSZ|
|`IOleInPlaceSiteEx`|FAŁSZ|Prawda|
|`IOleInPlaceSite`|FAŁSZ|FAŁSZ|

## <a name="ccomcontrolbasem_spoleadviseholder"></a><a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder

Zapewnia standardową implementację sposobu utrzymywania połączeń doradczych.

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć tego elementu członkowskiego danych w klasie formantu, należy zadeklarować go jako element członkowski danych w klasie kontroli. Klasa formantu nie odziedziczy tego elementu członkowskiego danych z klasy podstawowej, ponieważ jest zadeklarowany w ramach unii w klasie podstawowej.

Interfejs `m_spOleAdviseHolder` implementuje [IOleObject::Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) i [IOleObject::Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) metody do ustanawiania i usuwania połączeń doradczych do kontenera. Kontener formantu musi implementować zlewdorawiadczy przez obsługę interfejsu [IAdviseSink.](/windows/win32/api/objidl/nn-objidl-iadvisesink)

## <a name="ccomcontrolbaseondraw"></a><a name="ondraw"></a>CComControlBase::OnDraw

Zastąd w tej metodzie należy narysować formant.

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*Di*<br/>
Odwołanie do [struktury ATL_DRAWINFO,](../../atl/reference/atl-drawinfo-structure.md) która zawiera informacje o rysunku, takie jak aspekt rysowania, granice formantu i to, czy rysunek jest zoptymalizowany, czy nie.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Domyślnie `OnDraw` usuwa lub przywraca kontekst urządzenia lub nic nie robi, w zależności od flag ustawionych w [CComControlBase::OnDrawAdvanced](#ondrawadvanced).

Metoda `OnDraw` jest automatycznie dodawana do klasy sterowania podczas tworzenia formantu za pomocą Kreatora sterowania ATL. Domyślnie `OnDraw` kreator rysuje prostokąt z etykietą "ATL 8.0".

### <a name="example"></a>Przykład

Zobacz przykład [CComControlBase::GetAmbientAppearance](#getambientappearance).

## <a name="ccomcontrolbaseondrawadvanced"></a><a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced

Domyślnie `OnDrawAdvanced` przygotowuje znormalizowane kontekście urządzenia do rysowania, a następnie wywołuje `OnDraw` metodę klasy sterowania.

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*Di*<br/>
Odwołanie do [struktury ATL_DRAWINFO,](../../atl/reference/atl-drawinfo-structure.md) która zawiera informacje o rysunku, takie jak aspekt rysowania, granice formantu i to, czy rysunek jest zoptymalizowany, czy nie.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zastąpuj tę metodę, jeśli chcesz zaakceptować kontekst urządzenia przekazany przez kontener bez jego normalizacji.

Zobacz [CComControlBase::OnDraw aby](#ondraw) uzyskać więcej informacji.

## <a name="ccomcontrolbaseonkillfocus"></a><a name="onkillfocus"></a>CComControlBase::OnKillFocus

Sprawdza, czy formant jest aktywny w miejscu i ma prawidłową lokację formantu, a następnie informuje kontener, że formant utracił fokus.

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*Nmsg*<br/>
Zarezerwowany.

*Wparam*<br/>
Zarezerwowany.

*Lparam*<br/>
Zarezerwowany.

*bHandled (Obj.*<br/>
Flaga wskazująca, czy komunikat okna został pomyślnie obsłużona. Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca 1.

## <a name="ccomcontrolbaseonmouseactivate"></a><a name="onmouseactivate"></a>CComControlBase::OnMouseActivate

Sprawdza, czy interfejs użytkownika jest w trybie użytkownika, a następnie aktywuje formant.

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*Nmsg*<br/>
Zarezerwowany.

*Wparam*<br/>
Zarezerwowany.

*Lparam*<br/>
Zarezerwowany.

*bHandled (Obj.*<br/>
Flaga wskazująca, czy komunikat okna został pomyślnie obsłużona. Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca 1.

## <a name="ccomcontrolbaseonpaint"></a><a name="onpaint"></a>CComControlBase::OnPaint

Przygotowuje kontener do malowania, pobiera obszar klienta formantu, a `OnDrawAdvanced` następnie wywołuje metodę klasy control.

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>Parametry

*Nmsg*<br/>
Zarezerwowany.

*Wparam*<br/>
Istniejący HDC.

*Lparam*<br/>
Zarezerwowany.

*lWyskuj*<br/>
Zarezerwowany.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca zero.

### <a name="remarks"></a>Uwagi

Jeśli *wParam* nie `OnPaint` ma wartości NULL, zakłada, że zawiera prawidłowy kontroler HDC i używa go zamiast [CComControlBase::m_hWndCD](#m_hwndcd).

## <a name="ccomcontrolbaseonsetfocus"></a><a name="onsetfocus"></a>CComControlBase::OnSetFocus

Sprawdza, czy formant jest aktywny w miejscu i ma prawidłową lokację formantu, a następnie informuje kontener, który uzyskał fokus.

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*Nmsg*<br/>
Zarezerwowany.

*Wparam*<br/>
Zarezerwowany.

*Lparam*<br/>
Zarezerwowany.

*bHandled (Obj.*<br/>
Flaga wskazująca, czy komunikat okna został pomyślnie obsłużona. Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca 1.

### <a name="remarks"></a>Uwagi

Wysyła powiadomienie do kontenera, który otrzymał fokus.

## <a name="ccomcontrolbasepretranslateaccelerator"></a><a name="pretranslateaccelerator"></a>CComControlBase::PreTranslateAccelerator

Zastąd w tej metodzie należy udostępnić własne programy obsługi akceleratora klawiatury.

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Zarezerwowany.

*hRet ( hRet )*<br/>
Zarezerwowany.

### <a name="return-value"></a>Wartość zwracana

Domyślnie zwraca WARTOŚĆ FAŁSZ.

## <a name="ccomcontrolbasesendonclose"></a><a name="sendonclose"></a>CComControlBase::SendOnClose

Powiadamia wszystkie zlewozmywaki doradcze zarejestrowane u posiadacza informacji, że kontrola została zamknięta.

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wysyła powiadomienie, że formant zamknął swoje ujścia doradcze.

## <a name="ccomcontrolbasesendondatachange"></a><a name="sendondatachange"></a>CComControlBase::SendOnDataWyłącznik

Powiadamia wszystkie zlewozmywaki doradcze zarejestrowane u posiadacza informacji, że dane kontrolne uległy zmianie.

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>Parametry

*advf ( advf )*<br/>
Doradza flagi, które określają, jak [wywołanie IAdviseSink::OnDataChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange) jest. Wartości pochodzą z wyliczenia [ADVF.](/windows/win32/api/objidl/ne-objidl-advf)

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="ccomcontrolbasesendonrename"></a><a name="sendonrename"></a>CComControlBase::SendOnRename

Powiadamia wszystkie zlewozmywaki doradcze zarejestrowane u posiadacza informacji, że formant ma nowy moniker.

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>Parametry

*Pmk*<br/>
Wskaźnik do nowego moniker formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wysyła powiadomienie, że moniker formantu został zmieniony.

## <a name="ccomcontrolbasesendonsave"></a><a name="sendonsave"></a>CComControlBase::SendOnSave

Powiadamia wszystkie zlewozmywaki doradcze zarejestrowane u posiadacza informacji, że kontrola została zapisana.

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wysyła powiadomienie, że formant właśnie zapisał swoje dane.

## <a name="ccomcontrolbasesendonviewchange"></a><a name="sendonviewchange"></a>CComControlBase::SendOnViewChange

Powiadamia wszystkie zarejestrowane pochłaniacze doradcze, że widok formantu został zmieniony.

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>Parametry

*dwAspect*<br/>
Aspekt lub widok formantu.

*Lindex*<br/>
Część widoku, która uległa zmianie. Tylko -1 jest ważny.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

`SendOnViewChange`wywołuje [IAdviseSink::OnViewChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange). Jedyną wartością *lindex* obecnie obsługiwane jest -1, co wskazuje, że cały widok jest interesujące.

## <a name="ccomcontrolbasesetcontrolfocus"></a><a name="setcontrolfocus"></a>CComControlBase::SetControlFocus

Ustawia lub usuwa fokus klawiatury do lub z formantu.

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>Parametry

*bGrab*<br/>
Jeśli true, ustawia fokus klawiatury do kontroli połączeń. Jeśli FALSE, usuwa fokus klawiatury z kontroli połączeń, pod warunkiem, że ma fokus.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli formant pomyślnie odbiera fokus; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

W przypadku formantu okienkowego wywoływana jest funkcja [SetFocus](/windows/win32/api/winuser/nf-winuser-setfocus) interfejsu API systemu Windows. Dla formantu bez [okien, IOleInPlaCeSiteWindowless::SetFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) jest wywoływana. Za pomocą tego wywołania formant bez okien uzyskuje fokus klawiatury i może odpowiadać na komunikaty okna.

## <a name="ccomcontrolbasesetdirty"></a><a name="setdirty"></a>CComControlBase::SetDirty

Ustawia element `m_bRequiresSave` członkowski danych na wartość w *bDirty*.

```cpp
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*bDirty*<br/>
Wartość elementu członkowskiego danych [CComControlBase::m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Uwagi

`SetDirty(TRUE)`należy wywołać do flagi, że formant został zmieniony od czasu ostatniego zapisu. Wartość `m_bRequiresSave` jest pobierana z [CComControlBase::GetDirty](#getdirty).

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
