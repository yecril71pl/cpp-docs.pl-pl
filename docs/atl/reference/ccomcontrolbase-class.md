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
ms.openlocfilehash: fa7562f49834bf71da6bd095aec19360a43f1538
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447960"
---
# <a name="ccomcontrolbase-class"></a>Klasa CComControlBase

Ta klasa dostarcza metody do tworzenia i zarządzania formantami ATL.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|Zastąpić, jeśli Twoja `m_nAppearance` właściwości podstawowych, nie jest typu **krótki**.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|Konstruktor.|
|[CComControlBase:: ~ CComControlBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Pobiera wskaźnik do żądanego interfejsu.|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Sprawdza, czy *iVerb* parametr używany przez `IOleObjectImpl::DoVerb` albo aktywuje kontrolki interfejsu użytkownika (*iVerb* jest równa OLEIVERB_UIACTIVATE), określa akcję wykonywaną, gdy użytkownik kliknie dwukrotnie kontrolki (*iVerb* jest równa OLEIVERB_PRIMARY), wyświetla kontrolkę (*iVerb* jest równa OLEIVERB_SHOW), lub aktywuje kontrolkę (*iVerb* jest równe OLEIVERB _INPLACEACTIVATE).|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Sprawdza, czy *iVerb* parametr używany przez `IOleObjectImpl::DoVerb` powoduje, że kontrolki interfejsu użytkownika, aby aktywować i zwraca wartość TRUE.|
|[CComControlBase::DoVerbProperties](#doverbproperties)|Wyświetla strony właściwości formantu.|
|[CComControlBase::FireViewChange](#fireviewchange)|Wywołanie tej metody, kontener, by narysować ponownie kontrolki lub powiadomić ujść Porada zarejestrowanych, które kontrolki widok został zmieniony.|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Pobiera DISPID_AMBIENT_APPEARANCE, wygląd bieżące ustawienie dla formantu: 0, dla płaskiej i 1 dla 3D.|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Pobiera DISPID_AMBIENT_AUTOCLIP, flagę wskazującą, czy kontener obsługuje automatyczne wycinka obszaru wyświetlania kontrolki.|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Pobiera DISPID_AMBIENT_BACKCOLOR, kolor tła otoczenia dla wszystkich kontrolek, zdefiniowane przez kontener.|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Pobiera DISPID_AMBIENT_CHARSET, otoczenia zestaw znaków dla wszystkich kontrolek, zdefiniowane przez kontener.|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Pobiera DISPID_AMBIENT_CODEPAGE, otoczenia zestaw znaków dla wszystkich kontrolek, zdefiniowane przez kontener.|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Pobiera DISPID_AMBIENT_DISPLAYASDEFAULT, Flaga, która ma wartość TRUE, jeśli kontener są oznaczone kontroli w tej lokacji jako przycisk domyślny, a w związku z tym kontrolki przycisku powinien być rysowany od samego grubszy ramki.|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Pobiera DISPID_AMBIENT_DISPLAYNAME, nazwa kontenera jest dostarczane do formantu.|
|[CComControlBase::GetAmbientFont](#getambientfont)|Pobiera wskaźnik do kontenera jego otoczenia `IFont` interfejsu.|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Pobiera wskaźnik do kontenera jego otoczenia `IFontDisp` interfejs ekspedycji.|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Pobiera DISPID_AMBIENT_FORECOLOR, kolor otoczenia pierwszego planu dla wszystkich kontrolek, zdefiniowane przez kontener.|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Pobiera DISPID_AMBIENT_LOCALEID, identyfikator języka używanego przez kontener.|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Pobiera DISPID_AMBIENT_MESSAGEREFLECT, flagę wskazującą, czy chce odbierać komunikaty okna (np. WM_DRAWITEM) jako zdarzenia kontenera.|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Pobiera DISPID_AMBIENT_PALETTE, umożliwiający dostęp do HPALETTE kontenera.|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Pobiera właściwości kontenera określonej przez *identyfikator*.|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Pobiera DISPID_AMBIENT_RIGHTTOLEFT, kierunek, w którym zawartość jest wyświetlana przez kontener.|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Pobiera DISPID_AMBIENT_SCALEUNITS, jednostki otoczenia kontenera (takich jak cale lub cm) Wyświetla etykietowania.|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Pobiera DISPID_AMBIENT_SHOWGRABHANDLES, flagę wskazującą, czy kontener zezwala na formant, aby wyświetlić położenie uchwytów dla siebie, gdy jest ona aktywna.|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Pobiera DISPID_AMBIENT_SHOWHATCHING, flagę wskazującą, czy kontener zezwala na formant, aby wyświetlić sam wzorem kreskowanym, gdy interfejs użytkownika jest aktywny.|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Pobiera DISPID_AMBIENT_SUPPORTSMNEMONICS, flagę wskazującą, czy kontener obsługuje klawiszy skrótu klawiatury.|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Pobiera DISPID_AMBIENT_TEXTALIGN, wyrównanie tekstu preferowane przez kontener: 0 dla Wyrównanie ogólne (numery lewej po prawej stronie tekstu), 1 dla wyrównanie do lewej, 2-wyrównanie do środka i 3-wyrównanie do prawej.|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Pobiera DISPID_AMBIENT_TOPTOBOTTOM, kierunek, w którym zawartość jest wyświetlana przez kontener.|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Pobiera DISPID_AMBIENT_UIDEAD, flagę wskazującą, czy kontener wymagane formant aby reagować na działania interfejsu użytkownika.|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Pobiera DISPID_AMBIENT_USERMODE, flagę wskazującą, czy kontener jest w trybie wykonywania (PRAWDA) lub tryb projektowania (FALSE).|
|[CComControlBase::GetDirty](#getdirty)|Zwraca wartość element członkowski danych `m_bRequiresSave`.|
|[CComControlBase::GetZoomInfo](#getzoominfo)|Pobiera x i y wartości licznik i mianownik współczynnika powiększenia dla formantu aktywowana dla w miejscu do edycji.|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Powoduje, że formant przejście ze stanu braku aktywności do stanu niezależnie od czasownika w *iVerb* wskazuje.|
|[CComControlBase::InternalGetSite](#internalgetsite)|Wywołaj tę metodę do wykonywania zapytań w witrynie kontroli dla wskaźnika do interfejsie zidentyfikowany.|
|[CComControlBase::OnDraw](#ondraw)|Zastępuje tę metodę, aby narysować swoją kontrolkę.|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|Wartość domyślna `OnDrawAdvanced` przygotowuje znormalizowany kontekst urządzenia do rysowania, a następnie wywołuje Twojej klasy kontrolki `OnDraw` metody.|
|[CComControlBase::OnKillFocus](#onkillfocus)|Sprawdza, czy formant jest aktywny w miejscu i ma prawidłową kontroli lokacji, a następnie kontenera informuje, że kontrolka utraciła fokus.|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Sprawdza, czy interfejs użytkownika działa w trybie użytkownika, a następnie aktywuje kontrolkę.|
|[CComControlBase::OnPaint](#onpaint)|Przygotowuje obraz kontenera, pobiera obszaru klienckiego kontrolki, a następnie wywołuje Twojej klasy kontrolki `OnDraw` metody.|
|[CComControlBase::OnSetFocus](#onsetfocus)|Sprawdza, czy formant jest aktywny w miejscu i ma prawidłową kontroli lokacji, a następnie informuje kontenera kontrolki zyskało fokus.|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Przesłonić tę metodę, aby podać własne programy obsługi akceleratora.|
|[CComControlBase::SendOnClose](#sendonclose)|Powiadamia o wszystkich doradztwa ujść zarejestrowany właściciel Porada formant został zamknięty.|
|[CComControlBase::SendOnDataChange](#sendondatachange)|Powiadamia o wszystkich doradztwa ujść zarejestrowany właściciel Porada, które uległy zmianie danych formantu.|
|[CComControlBase::SendOnRename](#sendonrename)|Powiadamia wszystkie doradztwa ujść zarejestrowane w usłudze posiadacza Porada kontrolkę nowego krótkiej nazwy.|
|[CComControlBase::SendOnSave](#sendonsave)|Powiadamia o wszystkich doradztwa ujść zarejestrowane w usłudze posiadacza Porada, który formant został zapisany.|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Powiadamia wszystkie zarejestrowane doradztwa technicznego dotyczącego ujścia, które kontrolki widok został zmieniony.|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Ustawia lub usuwa fokus klawiatury do lub z formantu.|
|[CComControlBase::SetDirty](#setdirty)|Ustawia element członkowski danych `m_bRequiresSave` wartość *bDirty*.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|Flaga wskazująca, że kontrolka nie może być dowolnym rozmiarze.|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Flaga wskazująca, że `IDataObjectImpl::GetData` i `CComControlBase::GetZoomInfo` należy ustawić rozmiaru kontrolki `m_sizeNatural` , a nie z `m_sizeExtent`.|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Flaga wskazująca, że `IDataObjectImpl::GetData` należy używać jednostkach HIMETRIC i nie pikseli, podczas rysowania.|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Flaga oznaczająca, czy kontrolka jest aktywny w miejscu.|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Flaga oznaczająca, który obsługuje kontenera `IOleInPlaceSiteEx` interfejsu i OCX96 kontrolować funkcje, takie jak kontrolek bez okien i pozbawionej migotania.|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Flaga oznaczająca, czy formant ma negocjowane z kontenerem o obsługę funkcji kontroli OCX96 (takich jak formanty pozbawionej migotania i bez okien) i tego, czy kontrolka jest okna lub bez okien.|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Flaga wskazująca, że kontrolka chce przeskładać jego prezentacji, gdy kontener zmieni rozmiar wyświetlania kontrolki.|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Flaga wskazująca, że formant został zmieniony od ostatniego zapisu.|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Flaga wskazująca, formant chce, aby zmienić rozmiar jego naturalne rozszerzenie (jego nieskalowanego rozmiar fizyczny) podczas kontenera zmienia rozmiar wyświetlania kontrolki.|
|[CComControlBase::m_bUIActive](#m_buiactive)|Flaga wskazująca, kontrolki interfejsu użytkownika, takie jak menu i paski narzędzi, jest aktywny.|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Flaga wskazująca, że kontrolka używa regionu okna dostarczone przez kontener.|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Flaga oznaczająca, kontrolka została niepowiązanej z oknami, ale może lub nie jest niepowiązanej z oknami teraz.|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Flaga wskazująca, że formant powinien być okna, nawet wtedy, gdy kontener obsługuje kontrolek bez okien.|
|[CComControlBase::m_bWndLess](#m_bwndless)|Flaga wskazująca, że kontrolka ma bez okien.|
|[CComControlBase::m_hWndCD](#m_hwndcd)|Zawiera odwołanie do uchwyt okna skojarzonego z kontrolką.|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Liczbę razy kontenera ma zamrożone zdarzenia (odmówił Akceptuj zdarzenia) bez pośredniczące Odblokuj zdarzenia (akceptacji zdarzenia).|
|[CComControlBase::m_rcPos](#m_rcpos)|Pozycja w pikselach kontrolki, wyrażona w układzie współrzędnych kontenera.|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|Zakres kontroli w jednostkach HIMETRIC (każda jednostka to 0,01 milimetry) do wyświetlenia określonej.|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|Fizyczny rozmiar formantu w jednostkach HIMETRIC (każda jednostka to 0,01 milimetry).|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Bezpośredni wskaźnik do doradztwa technicznego dotyczącego połączenia w kontenerze (kontenera [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)).|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|A `CComDispatchDriver` obiekt, który pozwala pobierać i ustawiać właściwości kontenera za pomocą `IDispatch` wskaźnika.|
|[CComControlBase::m_spClientSite](#m_spclientsite)|Wskaźnik do lokacji klienta formantu w kontenerze.|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Zapewnia to standard sposoby przechowywania doradztwa technicznego dotyczącego połączenia między obiekty danych i zaleca ujścia.|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Wskaźnik do kontenera [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex), lub [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless) wskaźnika interfejsu.|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Udostępnia standardowej implementacji sposób przechowywania porad dotyczących połączenia.|

## <a name="remarks"></a>Uwagi

Ta klasa dostarcza metody do tworzenia i zarządzania formantami ATL. [Klasa CComControl](../../atl/reference/ccomcontrol-class.md) pochodzi od klasy `CComControlBase`. Po utworzeniu kontrolki formantu standardowego lub DHTML przy użyciu kreator kontrolki ATL, Kreator automatycznie, z której pochodzą z klasy `CComControlBase`.

Aby uzyskać więcej informacji na temat tworzenia kontrolki zobacz [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md). Aby uzyskać więcej informacji na temat Kreator projektów ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="appearancetype"></a>  CComControlBase::AppearanceType

Zastąpić, jeśli Twoja `m_nAppearance` właściwości podstawowych, nie jest typu **krótki**.

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Uwagi

Kreator kontrolki ATL, dodaje `m_nAppearance` właściwość typu krótki magazynu. Zastąp `AppearanceType` Jeśli używasz innego typu danych.

##  <a name="ccomcontrolbase"></a>  CComControlBase::CComControlBase

Konstruktor.

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Dojście do okna skojarzonego z kontrolką.

### <a name="remarks"></a>Uwagi

Inicjuje rozmiaru kontrolki na jednostkach HIMETRIC 5080 X 5080 (2 "X 2") i inicjuje `CComControlBase` wartości elementów członkowskich danych na wartość NULL lub wartość FALSE.

##  <a name="dtor"></a>  CComControlBase:: ~ CComControlBase

Destruktor.

```
~CComControlBase();
```

### <a name="remarks"></a>Uwagi

Jeśli kontrolka jest okna, `~CComControlBase` niszczy go przez wywołanie metody [destroywindow —](/windows/desktop/api/winuser/nf-winuser-destroywindow).

##  <a name="controlqueryinterface"></a>  CComControlBase::ControlQueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
Identyfikator GUID interfejsu żądanej.

*ppv*<br/>
Wskaźnik do wskaźnika interfejsu identyfikowane przez *iid*, lub wartość NULL, jeśli nie można odnaleźć interfejsu.

### <a name="remarks"></a>Uwagi

obsługuje tylko interfejsów COM tabeli mapy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

##  <a name="doesverbactivate"></a>  CComControlBase::DoesVerbActivate

Sprawdza, czy *iVerb* parametr używany przez `IOleObjectImpl::DoVerb` albo aktywuje kontrolki interfejsu użytkownika (*iVerb* jest równa OLEIVERB_UIACTIVATE), określa akcję wykonywaną, gdy użytkownik kliknie dwukrotnie kontrolki (*iVerb* jest równa OLEIVERB_PRIMARY), wyświetla kontrolkę (*iVerb* jest równa OLEIVERB_SHOW), lub aktywuje kontrolkę (*iVerb* jest równe OLEIVERB _INPLACEACTIVATE).

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Wartość wskazująca, Akcja do wykonania przez `DoVerb`.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli *iVerb* jest równa OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW lub OLEIVERB_INPLACEACTIVATE; w przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Można zastąpić tę metodę, aby zdefiniować własne zlecenie aktywacji.

##  <a name="doesverbuiactivate"></a>  CComControlBase::DoesVerbUIActivate

Sprawdza, czy *iVerb* parametr używany przez `IOleObjectImpl::DoVerb` powoduje, że kontrolki interfejsu użytkownika, aby aktywować i zwraca wartość TRUE.

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Wartość wskazująca, Akcja do wykonania przez `DoVerb`.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli *iVerb* jest równa OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW lub OLEIVERB_INPLACEACTIVATE. W przeciwnym razie metoda zwraca wartość FALSE.

##  <a name="doverbproperties"></a>  CComControlBase::DoVerbProperties

Wyświetla strony właściwości formantu.

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
Zastrzeżone.

*hwndParent*<br/>
Uchwyt okna zawierającego kontrolkę.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

##  <a name="fireviewchange"></a>  CComControlBase::FireViewChange

Wywołanie tej metody, kontener, by narysować ponownie kontrolki lub powiadomić ujść Porada zarejestrowanych, które kontrolki widok został zmieniony.

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Jeśli kontrolka jest aktywny (składowa danych klasy kontrolki [CComControlBase::m_bInPlaceActive](#m_binplaceactive) ma wartość TRUE), powiadomi kontenera chcesz odświeżyć całą kontrolkę. Jeśli kontrolka jest nieaktywny, powiadamia zarejestrowane kontrolki poinstruuj ujść (za pośrednictwem składowa danych klasy kontrolki [CComControlBase::m_spAdviseSink](#m_spadvisesink)), kontrolki widok został zmieniony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

##  <a name="getambientappearance"></a>  CComControlBase::GetAmbientAppearance

Pobiera DISPID_AMBIENT_APPEARANCE, wygląd bieżące ustawienie dla formantu: 0, dla płaskiej i 1 dla 3D.

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>Parametry

*nAppearance*<br/>
Właściwość DISPID_AMBIENT_APPEARANCE.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

##  <a name="getambientautoclip"></a>  CComControlBase::GetAmbientAutoClip

Pobiera DISPID_AMBIENT_AUTOCLIP, flagę wskazującą, czy kontener obsługuje automatyczne wycinka obszaru wyświetlania kontrolki.

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>Parametry

*bAutoClip*<br/>
Właściwość DISPID_AMBIENT_AUTOCLIP.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="getambientbackcolor"></a>  CComControlBase::GetAmbientBackColor

Pobiera DISPID_AMBIENT_BACKCOLOR, kolor tła otoczenia dla wszystkich kontrolek, zdefiniowane przez kontener.

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>Parametry

*Kolor tła*<br/>
Właściwość DISPID_AMBIENT_BACKCOLOR.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="getambientcharset"></a>  CComControlBase::GetAmbientCharSet

Pobiera DISPID_AMBIENT_CHARSET, otoczenia zestaw znaków dla wszystkich kontrolek, zdefiniowane przez kontener.

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>Parametry

*bstrCharSet*<br/>
Właściwość DISPID_AMBIENT_CHARSET.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="getambientcodepage"></a>  CComControlBase::GetAmbientCodePage

Pobiera DISPID_AMBIENT_CODEPAGE, stronę kodową otoczenia, dla wszystkich kontrolek, zdefiniowane przez kontener.

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>Parametry

*ulCodePage*<br/>
Właściwość DISPID_AMBIENT_CODEPAGE.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="getambientdisplayasdefault"></a>  CComControlBase::GetAmbientDisplayAsDefault

Pobiera DISPID_AMBIENT_DISPLAYASDEFAULT, Flaga, która ma wartość TRUE, jeśli kontener są oznaczone kontroli w tej lokacji jako przycisk domyślny, a w związku z tym kontrolki przycisku powinien być rysowany od samego grubszy ramki.

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*bDisplayAsDefault*<br/>
Właściwość DISPID_AMBIENT_DISPLAYASDEFAULT.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="getambientdisplayname"></a>  CComControlBase::GetAmbientDisplayName

Pobiera DISPID_AMBIENT_DISPLAYNAME, nazwa kontenera jest dostarczane do formantu.

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>Parametry

*bstrDisplayName*<br/>
Właściwość DISPID_AMBIENT_DISPLAYNAME.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="getambientfont"></a>  CComControlBase::GetAmbientFont

Pobiera wskaźnik do kontenera jego otoczenia `IFont` interfejsu.

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont*<br/>
Wskaźnik do kontenera jego otoczenia [IFont](/windows/desktop/api/ocidl/nn-ocidl-ifont) interfejsu.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Jeśli właściwość ma wartość NULL, wskaźnik jest pusty. Jeżeli wskaźnik nie jest NULL, obiekt wywołujący musi zwolnić wskaźnika.

##  <a name="getambientfontdisp"></a>  CComControlBase::GetAmbientFontDisp

Pobiera wskaźnik do kontenera jego otoczenia `IFontDisp` interfejs ekspedycji.

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont*<br/>
Wskaźnik do kontenera jego otoczenia [IFontDisp](https://msdn.microsoft.com/library/windows/desktop/ms692695) interfejs ekspedycji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Jeśli właściwość ma wartość NULL, wskaźnik jest pusty. Jeżeli wskaźnik nie jest NULL, obiekt wywołujący musi zwolnić wskaźnika.

##  <a name="getambientforecolor"></a>  CComControlBase::GetAmbientForeColor

Pobiera DISPID_AMBIENT_FORECOLOR, kolor otoczenia pierwszego planu dla wszystkich kontrolek, zdefiniowane przez kontener.

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>Parametry

*ForeColor*<br/>
Właściwość DISPID_AMBIENT_FORECOLOR.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="getambientlocaleid"></a>  CComControlBase::GetAmbientLocaleID

Pobiera DISPID_AMBIENT_LOCALEID, identyfikator języka używanego przez kontener.

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Właściwość DISPID_AMBIENT_LOCALEID.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Formant może użyć tego identyfikatora można dostosować interfejs użytkownika w różnych językach.

##  <a name="getambientmessagereflect"></a>  CComControlBase::GetAmbientMessageReflect

Pobiera DISPID_AMBIENT_MESSAGEREFLECT, flagę wskazującą, czy chce odbierać komunikaty w oknie kontenera (takie jak `WM_DRAWITEM`) jako zdarzenia.

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>Parametry

*bMessageReflect*<br/>
Właściwość DISPID_AMBIENT_MESSAGEREFLECT.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="getambientpalette"></a>  CComControlBase::GetAmbientPalette

Pobiera DISPID_AMBIENT_PALETTE, umożliwiający dostęp do HPALETTE kontenera.

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>Parametry

*hPalette*<br/>
Właściwość DISPID_AMBIENT_PALETTE.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="getambientproperty"></a>  CComControlBase::GetAmbientProperty

Pobiera właściwości kontenera określonej przez *dispid*.

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>Parametry

*identyfikator DISPID*<br/>
Identyfikator właściwości kontenera, które mają zostać pobrane.

*var*<br/>
Zmiennej, aby otrzymać właściwości.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

ATL udostępnia zestaw funkcji pomocnika do pobrania określonych właściwości, na przykład [CComControlBase::GetAmbientBackColor](#getambientbackcolor). Jeśli jest dostępne nie odpowiedniej metody, użyj `GetAmbientProperty`.

##  <a name="getambientrighttoleft"></a>  CComControlBase::GetAmbientRightToLeft

Pobiera DISPID_AMBIENT_RIGHTTOLEFT, kierunek, w którym zawartość jest wyświetlana przez kontener.

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>Parametry

*bRightToLeft*<br/>
Właściwość DISPID_AMBIENT_RIGHTTOLEFT. Ustaw wartość TRUE, jeśli zawartość jest wyświetlana od prawej do lewej, wartość FALSE, jeśli jest wyświetlany po lewej do prawej.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="getambientscaleunits"></a>  CComControlBase::GetAmbientScaleUnits

Pobiera DISPID_AMBIENT_SCALEUNITS, jednostki otoczenia kontenera (takich jak cale lub cm) Wyświetla etykietowania.

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>Parametry

*bstrScaleUnits*<br/>
Właściwość DISPID_AMBIENT_SCALEUNITS.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="getambientshowgrabhandles"></a>  CComControlBase::GetAmbientShowGrabHandles

Pobiera DISPID_AMBIENT_SHOWGRABHANDLES, flagę wskazującą, czy kontener zezwala na formant, aby wyświetlić położenie uchwytów dla siebie, gdy jest ona aktywna.

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>Parametry

*bShowGrabHandles*<br/>
Właściwość DISPID_AMBIENT_SHOWGRABHANDLES.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="getambientshowhatching"></a>  CComControlBase::GetAmbientShowHatching

Pobiera DISPID_AMBIENT_SHOWHATCHING, flagę wskazującą, czy kontener zezwala na formant, aby wyświetlić sam wzorem kreskowanym, gdy kontrolka interfejsu użytkownika jest aktywny.

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>Parametry

*bShowHatching*<br/>
Właściwość DISPID_AMBIENT_SHOWHATCHING.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="getambientsupportsmnemonics"></a>  CComControlBase::GetAmbientSupportsMnemonics

Pobiera DISPID_AMBIENT_SUPPORTSMNEMONICS, flagę wskazującą, czy kontener obsługuje klawiszy skrótu klawiatury.

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>Parametry

*bSupportsMnemonics*<br/>
Właściwość DISPID_AMBIENT_SUPPORTSMNEMONICS.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="getambienttextalign"></a>  CComControlBase::GetAmbientTextAlign

Pobiera DISPID_AMBIENT_TEXTALIGN, wyrównanie tekstu preferowane przez kontener: 0 dla Wyrównanie ogólne (numery lewej po prawej stronie tekstu), 1 dla wyrównanie do lewej, 2-wyrównanie do środka i 3-wyrównanie do prawej.

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>Parametry

*nTextAlign*<br/>
Właściwość DISPID_AMBIENT_TEXTALIGN.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="getambienttoptobottom"></a>  CComControlBase::GetAmbientTopToBottom

Pobiera DISPID_AMBIENT_TOPTOBOTTOM, kierunek, w którym zawartość jest wyświetlana przez kontener.

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>Parametry

*bTopToBottom*<br/>
Właściwość DISPID_AMBIENT_TOPTOBOTTOM. Ustaw na wartość TRUE, jeśli tekst jest wyświetlany, od góry do dołu, FALSE, jeśli jest wyświetlana dołu do góry.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="getambientuidead"></a>  CComControlBase::GetAmbientUIDead

Pobiera DISPID_AMBIENT_UIDEAD, flagę wskazującą, czy kontener wymagane formant aby reagować na działania interfejsu użytkownika.

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>Parametry

*bUIDead*<br/>
Właściwość DISPID_AMBIENT_UIDEAD.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

W przypadku opcji TRUE formantu nie powinny odpowiadać. Ta flaga ma zastosowanie niezależnie od tego, Flaga DISPID_AMBIENT_USERMODE. Zobacz [CComControlBase::GetAmbientUserMode](#getambientusermode).

##  <a name="getambientusermode"></a>  CComControlBase::GetAmbientUserMode

Pobiera DISPID_AMBIENT_USERMODE, flagę wskazującą, czy kontener jest w trybie wykonywania (PRAWDA) lub tryb projektowania (FALSE).

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>Parametry

*bUserMode*<br/>
Właściwość DISPID_AMBIENT_USERMODE.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="getdirty"></a>  CComControlBase::GetDirty

Zwraca wartość element członkowski danych `m_bRequiresSave`.

```
BOOL GetDirty();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość element członkowski danych [m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Uwagi

Ta wartość jest ustawiana za pomocą [CComControlBase::SetDirty](#setdirty).

##  <a name="getzoominfo"></a>  CComControlBase::GetZoomInfo

Pobiera x i y wartości licznik i mianownik współczynnika powiększenia dla formantu aktywowana dla w miejscu do edycji.

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*di*<br/>
Struktura, w którym będą przechowywane współczynnika powiększenia licznik i mianownik. Aby uzyskać więcej informacji, zobacz [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).

### <a name="remarks"></a>Uwagi

Współczynnika powiększenia jest część formantu rozmiar fizyczne w jej bieżącym stopniu.

##  <a name="inplaceactivate"></a>  CComControlBase::InPlaceActivate

Powoduje, że formant przejście ze stanu braku aktywności do stanu niezależnie od czasownika w *iVerb* wskazuje.

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Wartość wskazująca, Akcja do wykonania przez [IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb).

*prcPosRect*<br/>
Wskaźnik do położenia kontrolki w miejscu.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Przed aktywację ta metoda sprawdza, czy formant ma lokacji klienta, sprawdza, ile kontrolki jest widoczny, a następnie pobiera lokalizacji formantu w oknie nadrzędnym. Po aktywowaniu kontrolki, ta metoda aktywuje kontrolki interfejsu użytkownika i informuje kontenera, aby formant stał się widoczny.

Ta metoda umożliwia również pobranie `IOleInPlaceSite`, `IOleInPlaceSiteEx`, lub `IOleInPlaceSiteWindowless` wskaźnika interfejsu dla kontrolki i zapisuje go w klasie kontrolki element członkowski danych [CComControlBase::m_spInPlaceSite](#m_spinplacesite). Elementy członkowskie danych klasy kontrolki [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase::m_bWndLess](#m_bwndless), [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)i [ CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) są ustawione na wartość true, odpowiednio.

##  <a name="internalgetsite"></a>  CComControlBase::InternalGetSite

Wywołaj tę metodę do wykonywania zapytań w witrynie kontroli dla wskaźnika do interfejsie zidentyfikowany.

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>Parametry

*Parametr riid*<br/>
IID wskaźnika interfejsu, który ma zostać zwrócony w *ppUnkSite*.

*ppUnkSite*<br/>
Adres zmiennej wskaźnika, który otrzymuje wskaźnik interfejsu w *riid*.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Jeśli lokacja obsługuje interfejs żądany podczas *riid*, wskaźnik jest zwracany przez *ppUnkSite*. W przeciwnym razie *ppUnkSite* ma wartość NULL.

##  <a name="m_bautosize"></a>  CComControlBase::m_bAutoSize

Flaga wskazująca, że kontrolka nie może być dowolnym rozmiarze.

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Uwagi

Ta flaga jest sprawdzana przez `IOleObjectImpl::SetExtent` i w przypadku wartości TRUE powoduje, że funkcja zwracać E_FAIL.

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

Jeśli dodasz **automatyczna zmiana rozmiaru** opcja [właściwości podstawowe](../../atl/reference/stock-properties-atl-control-wizard.md) kartę Kreator kontrolki ATL, Kreator automatycznie utworzy ten element członkowski danych w klasie kontrolki wraz z przesyłania i pobieranie metod dla właściwości i obsługuje [ipropertynotifysink —](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) automatycznie powiadamiać kontenera, gdy właściwość.

##  <a name="m_bdrawfromnatural"></a>  CComControlBase::m_bDrawFromNatural

Flaga wskazująca, że `IDataObjectImpl::GetData` i `CComControlBase::GetZoomInfo` należy ustawić rozmiaru kontrolki `m_sizeNatural` , a nie z `m_sizeExtent`.

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_bdrawgetdatainhimetric"></a>  CComControlBase::m_bDrawGetDataInHimetric

Flaga wskazująca, że `IDataObjectImpl::GetData` należy używać jednostkach HIMETRIC i nie pikseli, podczas rysowania.

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Uwagi

Każdej jednostki logicznej HIMETRIC to 0,01 milimetra.

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_binplaceactive"></a>  CComControlBase::m_bInPlaceActive

Flaga oznaczająca, czy kontrolka jest aktywny w miejscu.

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Uwagi

To oznacza, że kontrolka jest widoczna i jego okna, jest widoczny, ale jego menu i pasków zadań nie może być aktywne. `m_bUIActive` Flaga wskazuje kontrolki interfejsu użytkownika, takich jak menu, również jest aktywny.

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_binplacesiteex"></a>  CComControlBase::m_bInPlaceSiteEx

Flaga oznaczająca, który obsługuje kontenera `IOleInPlaceSiteEx` interfejsu i OCX96 kontrolować funkcje, takie jak kontrolek bez okien i pozbawionej migotania.

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

Element członkowski danych `m_spInPlaceSite` wskazuje [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex), lub [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless) interfejsu, w zależności od wartości `m_bWndLess` i `m_bInPlaceSiteEx` flag. (Element członkowski danych `m_bNegotiatedWnd` musi mieć wartość PRAWDA dla `m_spInPlaceSite` wskaźnika ważności.)

Jeśli `m_bWndLess` ma wartość FAŁSZ i `m_bInPlaceSiteEx` ma wartość PRAWDA, `m_spInPlaceSite` jest `IOleInPlaceSiteEx` wskaźnika interfejsu. Zobacz [m_spInPlaceSite](#m_spinplacesite) przedstawiający relację między te elementy członkowskie trzech danych tabeli.

##  <a name="m_bnegotiatedwnd"></a>  CComControlBase::m_bNegotiatedWnd

Flaga oznaczająca, czy formant ma negocjowane z kontenerem o obsługę funkcji kontroli OCX96 (takich jak formanty pozbawionej migotania i bez okien) i tego, czy kontrolka jest okna lub bez okien.

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

`m_bNegotiatedWnd` Flagi musi mieć wartość PRAWDA dla `m_spInPlaceSite` wskaźnika ważności.

##  <a name="m_brecomposeonresize"></a>  CComControlBase::m_bRecomposeOnResize

Flaga wskazująca, że kontrolka chce przeskładać jego prezentacji, gdy kontener zmieni rozmiar wyświetlania kontrolki.

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

Ta flaga jest sprawdzana przez [IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) i, w przypadku opcji TRUE `SetExtent` powiadamia kontenera przeglądanie zmian. Jeśli ta flaga jest ustawiona, OLEMISC_RECOMPOSEONRESIZE bit w [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) również musi mieć wartość wyliczenia.

##  <a name="m_brequiressave"></a>  CComControlBase::m_bRequiresSave

Flaga wskazująca, że formant został zmieniony od ostatniego zapisu.

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Uwagi

Wartość `m_bRequiresSave` można ustawić za pomocą [CComControlBase::SetDirty](#setdirty) i pobrane z [CComControlBase::GetDirty](#getdirty).

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_bresizenatural"></a>  CComControlBase::m_bResizeNatural

Flaga wskazująca, formant chce, aby zmienić rozmiar jego naturalne rozszerzenie (jego nieskalowanego rozmiar fizyczny) podczas kontenera zmienia rozmiar wyświetlania kontrolki.

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Uwagi

Ta flaga jest sprawdzana przez `IOleObjectImpl::SetExtent` i, jeśli ma wartość TRUE, rozmiar przekazanego do `SetExtent` jest przypisany do `m_sizeNatural`.

Rozmiar przekazanego do `SetExtent` jest zawsze przypisywana do `m_sizeExtent`, niezależnie od tego, wartości `m_bResizeNatural`.

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_buiactive"></a>  CComControlBase::m_bUIActive

Flaga wskazująca, kontrolki interfejsu użytkownika, takie jak menu i paski narzędzi, jest aktywny.

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Uwagi

`m_bInPlaceActive` Flaga wskazuje, czy kontrolka jest aktywna, ale nie to interfejs użytkownika jest aktywny.

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_busingwindowrgn"></a>  CComControlBase::m_bUsingWindowRgn

Flaga wskazująca, że kontrolka używa regionu okna dostarczone przez kontener.

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_bwasoncewindowless"></a>  CComControlBase::m_bWasOnceWindowless

Flaga oznaczająca, kontrolka została niepowiązanej z oknami, ale może lub nie jest niepowiązanej z oknami teraz.

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_bwindowonly"></a>  CComControlBase::m_bWindowOnly

Flaga wskazująca, że formant powinien być okna, nawet wtedy, gdy kontener obsługuje kontrolek bez okien.

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_bwndless"></a>  CComControlBase::m_bWndLess

Flaga wskazująca, że kontrolka ma bez okien.

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

Element członkowski danych `m_spInPlaceSite` wskazuje [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex), lub [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless) interfejsu, w zależności od wartości `m_bWndLess` i [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex) flag. (Element członkowski danych [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) musi mieć wartość PRAWDA dla [CComControlBase::m_spInPlaceSite](#m_spinplacesite) wskaźnika ważności.)

Jeśli `m_bWndLess` ma wartość PRAWDA, `m_spInPlaceSite` jest `IOleInPlaceSiteWindowless` wskaźnika interfejsu. Zobacz [CComControlBase::m_spInPlaceSite](#m_spinplacesite) przedstawiający pełną relację między te elementy członkowskie danych tabeli.

##  <a name="m_hwndcd"></a>  CComControlBase::m_hWndCD

Zawiera odwołanie do uchwyt okna skojarzonego z kontrolką.

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_nfreezeevents"></a>  CComControlBase::m_nFreezeEvents

Liczbę razy kontenera ma zamrożone zdarzenia (odmówił Akceptuj zdarzenia) bez pośredniczące Odblokuj zdarzenia (akceptacji zdarzenia).

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_rcpos"></a>  CComControlBase::m_rcPos

Pozycja w pikselach kontrolki, wyrażona w układzie współrzędnych kontenera.

```
RECT m_rcPos;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_sizeextent"></a>  CComControlBase::m_sizeExtent

Zakres kontroli w jednostkach HIMETRIC (każda jednostka to 0,01 milimetry) do wyświetlenia określonej.

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

Ten rozmiar jest skalowana przez wyświetlanie. Kontrolki rozmiar fizyczny jest określona w `m_sizeNatural` element członkowski danych i zostanie rozwiązany.

Rozmiar można przekonwertować na piksele funkcja globalna [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_sizenatural"></a>  CComControlBase::m_sizeNatural

Fizyczny rozmiar formantu w jednostkach HIMETRIC (każda jednostka to 0,01 milimetry).

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

Ten rozmiar jest stała i podczas rozmiar w `m_sizeExtent` skalowania przez wyświetlanie.

Rozmiar można przekonwertować na piksele funkcja globalna [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_spadvisesink"></a>  CComControlBase::m_spAdviseSink

Bezpośredni wskaźnik do doradztwa technicznego dotyczącego połączenia w kontenerze (kontenera [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)).

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_spambientdispatch"></a>  CComControlBase::m_spAmbientDispatch

A `CComDispatchDriver` obiekt, który pozwala pobierać i ustawiać właściwości obiektu za pomocą `IDispatch` wskaźnika.

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_spclientsite"></a>  CComControlBase::m_spClientSite

Wskaźnik do lokacji klienta formantu w kontenerze.

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

##  <a name="m_spdataadviseholder"></a>  CComControlBase::m_spDataAdviseHolder

Zapewnia to standard sposoby przechowywania doradztwa technicznego dotyczącego połączenia między obiekty danych i zaleca ujścia.

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

Obiekt danych jest kontrolki, które mogą przesyłać dane i który implementuje [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject), której metody określać średni format i transfer danych.

Interfejs `m_spDataAdviseHolder` implementuje [IDataObject::DAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dadvise) i [IDataObject::DUnadvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dunadvise) metody do ustalenia i usuwania doradztwa technicznego dotyczącego połączenia z kontenerem. Kontener formantu musi implementować ujścia Porada dzięki obsłudze [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) interfejsu.

##  <a name="m_spinplacesite"></a>  CComControlBase::m_spInPlaceSite

Wskaźnik do kontenera [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex), lub [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless) wskaźnika interfejsu.

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

`m_spInPlaceSite` Wskaźnik jest prawidłowy tylko wtedy, gdy [m_bNegotiatedWnd](#m_bnegotiatedwnd) flaga ma wartość TRUE.

W poniższej tabeli przedstawiono sposób, w jaki `m_spInPlaceSite` zależy od typu wskaźnika [m_bWndLess](#m_bwndless) i [m_bInPlaceSiteEx](#m_binplacesiteex) flagi element członkowski danych:

|m_spInPlaceSite typu|m_bWndLess wartość|m_bInPlaceSiteEx wartość|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|WARTOŚĆ TRUE|Wartość PRAWDA lub FAŁSZ|
|`IOleInPlaceSiteEx`|FAŁSZ|WARTOŚĆ TRUE|
|`IOleInPlaceSite`|FAŁSZ|FAŁSZ|

##  <a name="m_spoleadviseholder"></a>  CComControlBase::m_spOleAdviseHolder

Udostępnia standardowej implementacji sposób przechowywania porad dotyczących połączenia.

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych, w ramach klasy kontrolki, należy zadeklarować ją jako element członkowski danych w klasie kontrolki. Klasy kontrolki nie dziedziczy ten element członkowski danych z klasy bazowej, ponieważ jest ona zadeklarowana w obrębie Unii w klasie bazowej.

Interfejs `m_spOleAdviseHolder` implementuje [IOleObject::Advise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-advise) i [IOleObject::Unadvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-unadvise) metody do ustalenia i usuwania doradztwa technicznego dotyczącego połączenia z kontenerem. Kontener formantu musi implementować ujścia Porada dzięki obsłudze [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) interfejsu.

##  <a name="ondraw"></a>  CComControlBase::OnDraw

Zastępuje tę metodę, aby narysować swoją kontrolkę.

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*di*<br/>
Odwołanie do [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) strukturę, która zawiera rysowania informacje, takie jak aspekt rysowania, granice formantu i czy rysunek jest zoptymalizowany, czy nie.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Wartość domyślna `OnDraw` usuwa przywraca kontekstu urządzenia lub nie działa, w zależności od flag ustawionych w [CComControlBase::OnDrawAdvanced](#ondrawadvanced).

`OnDraw` Metody jest automatycznie dodawany do klasy kontrolki, po utworzeniu kontrolki za pomocą Kreatora formantu biblioteki ATL. Domyślne kreatora `OnDraw` rysuje prostokąt z etykietą "ATL 8.0".

### <a name="example"></a>Przykład

Zobacz przykład [CComControlBase::GetAmbientAppearance](#getambientappearance).

##  <a name="ondrawadvanced"></a>  CComControlBase::OnDrawAdvanced

Wartość domyślna `OnDrawAdvanced` przygotowuje znormalizowany kontekst urządzenia do rysowania, a następnie wywołuje Twojej klasy kontrolki `OnDraw` metody.

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*di*<br/>
Odwołanie do [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) strukturę, która zawiera rysowania informacje, takie jak aspekt rysowania, granice formantu i czy rysunek jest zoptymalizowany, czy nie.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Przesłania tę metodę, jeśli chcesz zaakceptować kontekst urządzenia przekazany przez kontener bez jego normalizacji.

Zobacz [CComControlBase::OnDraw](#ondraw) Aby uzyskać więcej informacji.

##  <a name="onkillfocus"></a>  CComControlBase::OnKillFocus

Sprawdza, czy formant jest aktywny w miejscu i ma prawidłową kontroli lokacji, a następnie kontenera informuje, że kontrolka utraciła fokus.

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Zastrzeżone.

*wParam*<br/>
Zastrzeżone.

*lParam*<br/>
Zastrzeżone.

*bHandled*<br/>
Flaga wskazująca, czy komunikatów okien został pomyślnie obsłużony. Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość 1.

##  <a name="onmouseactivate"></a>  CComControlBase::OnMouseActivate

Sprawdza, czy interfejs użytkownika działa w trybie użytkownika, a następnie aktywuje kontrolkę.

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Zastrzeżone.

*wParam*<br/>
Zastrzeżone.

*lParam*<br/>
Zastrzeżone.

*bHandled*<br/>
Flaga wskazująca, czy komunikatów okien został pomyślnie obsłużony. Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość 1.

##  <a name="onpaint"></a>  CComControlBase::OnPaint

Przygotowuje obraz kontenera, pobiera obszaru klienckiego kontrolki, a następnie wywołuje Twojej klasy kontrolki `OnDrawAdvanced` metody.

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Zastrzeżone.

*wParam*<br/>
Istniejącego elementu HDC.

*lParam*<br/>
Zastrzeżone.

*lResult*<br/>
Zastrzeżone.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość zero.

### <a name="remarks"></a>Uwagi

Jeśli *wParam* nie ma wartości NULL, `OnPaint` zakłada on zawiera nieprawidłowy elementu HDC i używający tych informacji zamiast [CComControlBase::m_hWndCD](#m_hwndcd).

##  <a name="onsetfocus"></a>  CComControlBase::OnSetFocus

Sprawdza, czy formant jest aktywny w miejscu i ma prawidłową kontroli lokacji, a następnie informuje kontenera kontrolki zyskało fokus.

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Zastrzeżone.

*wParam*<br/>
Zastrzeżone.

*lParam*<br/>
Zastrzeżone.

*bHandled*<br/>
Flaga wskazująca, czy komunikatów okien został pomyślnie obsłużony. Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość 1.

### <a name="remarks"></a>Uwagi

Wysyła powiadomienie do kontenera, że kontrolka otrzymała fokus.

##  <a name="pretranslateaccelerator"></a>  CComControlBase::PreTranslateAccelerator

Przesłonić tę metodę, aby podać własne programy obsługi akceleratora.

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Zastrzeżone.

*hRet*<br/>
Zastrzeżone.

### <a name="return-value"></a>Wartość zwracana

Domyślnie zwraca wartość FALSE.

##  <a name="sendonclose"></a>  CComControlBase::SendOnClose

Powiadamia o wszystkich doradztwa ujść zarejestrowany właściciel Porada formant został zamknięty.

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wysyła powiadomienie, czy kontrolka zostało zamknięte jego doradztwa technicznego dotyczącego ujścia.

##  <a name="sendondatachange"></a>  CComControlBase::SendOnDataChange

Powiadamia o wszystkich doradztwa ujść zarejestrowany właściciel Porada, które uległy zmianie danych formantu.

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>Parametry

*advf*<br/>
Aby flagi określające, jak wywołanie [IAdviseSink::OnDataChange](/windows/desktop/api/objidl/nf-objidl-iadvisesink-ondatachange) wykonano. Wartości pochodzą z [ADVF](/windows/desktop/api/objidl/ne-objidl-tagadvf) wyliczenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="sendonrename"></a>  CComControlBase::SendOnRename

Powiadamia wszystkie doradztwa ujść zarejestrowane w usłudze posiadacza Porada kontrolkę nowego krótkiej nazwy.

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>Parametry

*kluczy głównych parowania*<br/>
Wskaźnik do nowego moniker formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wysyła powiadomienie o zmianie moniker formantu.

##  <a name="sendonsave"></a>  CComControlBase::SendOnSave

Powiadamia o wszystkich doradztwa ujść zarejestrowane w usłudze posiadacza Porada, który formant został zapisany.

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wysyła powiadomienie, czy formant ma zapisany swoje dane.

##  <a name="sendonviewchange"></a>  CComControlBase::SendOnViewChange

Powiadamia wszystkie zarejestrowane doradztwa technicznego dotyczącego ujścia, które kontrolki widok został zmieniony.

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>Parametry

*dwAspect*<br/>
Aspekt lub w widoku formantu.

*lindex*<br/>
Części widoku, które uległy zmianie. Tylko wartość -1 jest prawidłowy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`SendOnViewChange` wywołania [IAdviseSink::OnViewChange](/windows/desktop/api/objidl/nf-objidl-iadvisesink-onviewchange). Tylko wartość *wartość lindex* jest obecnie obsługiwane wartości -1, co oznacza, że cały widok ma znaczenie.

##  <a name="setcontrolfocus"></a>  CComControlBase::SetControlFocus

Ustawia lub usuwa fokus klawiatury do lub z formantu.

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>Parametry

*bGrab*<br/>
W przypadku opcji TRUE Ustawia fokus klawiatury do kontrolki wywoływania. W przypadku wartości FAŁSZ spowoduje usunięcie fokus klawiatury z wywołującym kontroli, pod warunkiem ma fokus.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli formant pomyślnie uzyskuje fokus; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Kontrolki okna, funkcji Windows API [SetFocus](https://msdn.microsoft.com/library/windows/desktop/ms646312) jest wywoływana. Na kontrolce [IOleInPlaceSiteWindowless::SetFocus](/windows/desktop/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) jest wywoływana. Za pomocą tego wywołania kontrolce uzyskuje fokus klawiatury i mogą odpowiadać na komunikaty okna.

##  <a name="setdirty"></a>  CComControlBase::SetDirty

Ustawia element członkowski danych `m_bRequiresSave` wartość *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*bDirty*<br/>
Wartość elementu członkowskiego danych [CComControlBase::m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Uwagi

`SetDirty(TRUE)` powinna być wywoływana mógł oflagować, że formant został zmieniony od ostatniego zapisu. Wartość `m_bRequiresSave` jest pobierany za pomocą [CComControlBase::GetDirty](#getdirty).

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
