---
title: Klasa CComControlBase | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords: CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8e7e3ab049a7fc7935b9027746fc4cdebb3428cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccomcontrolbase-class"></a>Klasa CComControlBase
Ta klasa dostarcza metody do tworzenia i zarządzania kontrolek ALT.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class ATL_NO_VTABLE CComControlBase
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComControlBase::AppearanceType](#appearancetype)|Zastąp, jeśli Twoje `m_nAppearance` właściwości podstawowych, nie jest typu `short`.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComControlBase::CComControlBase](#ccomcontrolbase)|Konstruktor.|  
|[CComControlBase:: ~ CComControlBase](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Pobiera wskaźnik do żądanego interfejsu.|  
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Sprawdza, czy `iVerb` używane przez parametr `IOleObjectImpl::DoVerb` albo aktywuje formantu interfejsu użytkownika ( `iVerb` jest równe `OLEIVERB_UIACTIVATE`), określa akcję wykonywaną, gdy użytkownik kliknie dwukrotnie formantu ( `iVerb` jest równe `OLEIVERB_PRIMARY`), wyświetla kontrolkę ( `iVerb` jest równe `OLEIVERB_SHOW`), lub aktywuje formant ( `iVerb` jest równe **OLEIVERB_INPLACEACTIVATE**).|  
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Sprawdza, czy `iVerb` używane przez parametr `IOleObjectImpl::DoVerb` powoduje formantu interfejsu użytkownika aktywować i zwraca **TRUE**.|  
|[CComControlBase::DoVerbProperties](#doverbproperties)|Wyświetla strony właściwości formantu.|  
|[CComControlBase::FireViewChange](#fireviewchange)|Wywołanie tej metody mówić kontener, aby odświeżyć formant lub powiadomić wychwytywanie zarejestrowanych Porada, które formantu widoku został zmieniony.|  
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Pobiera **DISPID_AMBIENT_APPEARANCE**, wygląd bieżące ustawienia dla formantu: 0 płaski i 1 dla 3W.|  
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Pobiera **DISPID_AMBIENT_AUTOCLIP**, flagę wskazującą, czy kontener obsługuje automatyczne wycinka obszaru wyświetlania formantu.|  
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Pobiera **DISPID_AMBIENT_BACKCOLOR**, kolor tła otoczenia dla wszystkich kontrolek, zdefiniowany przez kontener.|  
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Pobiera **DISPID_AMBIENT_CHARSET**, zestaw znaków otoczenia dla wszystkich kontrolek, zdefiniowany przez kontener.|  
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Pobiera **DISPID_AMBIENT_CODEPAGE**, zestaw znaków otoczenia dla wszystkich kontrolek, zdefiniowany przez kontener.|  
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Pobiera **DISPID_AMBIENT_DISPLAYASDEFAULT**, Flaga, która jest **TRUE** Jeśli kontener został oznaczony do formantu w tej lokacji jako przycisk domyślny, a w związku z tym kontrolkę przycisku powinien być rysowany z grubszy ramki.|  
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Pobiera **DISPID_AMBIENT_DISPLAYNAME**, nazwa kontenera jest dostarczona do formantu.|  
|[CComControlBase::GetAmbientFont](#getambientfont)|Pobiera wskaźnik do kontenera obiektu otoczenia `IFont` interfejsu.|  
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Pobiera wskaźnik do kontenera obiektu otoczenia **IFontDisp** interfejs wysyłania.|  
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Pobiera **DISPID_AMBIENT_FORECOLOR**, kolor otoczenia dla wszystkich kontrolek, zdefiniowany przez kontener.|  
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Pobiera **DISPID_AMBIENT_LOCALEID**, identyfikator języka używanego przez kontener.|  
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Pobiera **DISPID_AMBIENT_MESSAGEREFLECT**, flagę wskazującą, czy chce odbierać komunikaty okna kontenera (takie jak `WM_DRAWITEM`) jako zdarzenia.|  
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Pobiera **DISPID_AMBIENT_PALETTE**, umożliwia dostęp do kontenera `HPALETTE`.|  
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Pobiera określony przez właściwość kontenera `id`.|  
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Pobiera **DISPID_AMBIENT_RIGHTTOLEFT**, kierunek, w którym zawartość jest wyświetlana przez kontener.|  
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Pobiera **DISPID_AMBIENT_SCALEUNITS**, jednostki otoczenia kontenera (takich jak cale lub cm) na etykietach Wyświetla.|  
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Pobiera **DISPID_AMBIENT_SHOWGRABHANDLES**, flagę wskazującą, czy kontener zezwala kontrolka do wyświetlenia uchwytów dla siebie, gdy jest aktywny.|  
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Pobiera **DISPID_AMBIENT_SHOWHATCHING**, flagę wskazującą, czy kontener zezwala formantu, aby wyświetlić się wzorem kreskowanym, gdy interfejs użytkownika jest aktywna.|  
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Pobiera **DISPID_AMBIENT_SUPPORTSMNEMONICS**, flagę wskazującą, czy kontener obsługuje klawiszy skrótu klawiatury.|  
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Pobiera **DISPID_AMBIENT_TEXTALIGN**, wyrównanie tekstu preferowany przez kontener: 0 dla opcji Ogólne (liczb, tekst do prawej po lewej), 1 dla wyrównania do lewej, 2 dla wyrównania center i 3-wyrównanie do prawej.|  
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Pobiera **DISPID_AMBIENT_TOPTOBOTTOM**, kierunek, w którym zawartość jest wyświetlana przez kontener.|  
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Pobiera **DISPID_AMBIENT_UIDEAD**, flagę wskazującą, czy kontener chce kontroli odpowiada na działania interfejsu użytkownika.|  
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Pobiera **DISPID_AMBIENT_USERMODE**, flagę wskazującą, czy kontener jest w trybie wykonywania ( **TRUE**) lub w trybie projektowania ( **FALSE**).|  
|[CComControlBase::GetDirty](#getdirty)|Zwraca wartość elementu członkowskiego danych `m_bRequiresSave`.|  
|[CComControlBase::GetZoomInfo](#getzoominfo)|Pobiera x i y wartości licznika i denominator współczynnika powiększenia dla formantu aktywowana dla w miejscu edycji.|  
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Powoduje, że formant do przejścia z stan nieaktywny do stanu niezależnie od zleceń w `iVerb` wskazuje.|  
|[CComControlBase::InternalGetSite](#internalgetsite)|Wywołać tę metodę do badania lokacji kontroli dla wskaźnika interfejsu zidentyfikowane.|  
|[CComControlBase::OnDraw](#ondraw)|Zastępuje tę metodę, by narysować Twoją kontrolkę.|  
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|Wartość domyślna **OnDrawAdvanced** przygotowuje znormalizowany kontekst urządzenia do rysowania, a następnie wywołuje Twojej klasy kontrolki `OnDraw` metody.|  
|[CComControlBase::OnKillFocus](#onkillfocus)|Sprawdza, czy formant jest aktywny w miejscu i ma prawidłową sterowania lokacji, a następnie kontenera informuje, że kontrolka utraciła fokus.|  
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Sprawdza, czy interfejs użytkownika działa w trybie użytkownika, a następnie aktywuje formant.|  
|[CComControlBase::OnPaint](#onpaint)|Przygotowuje kontenera do rysowania, pobiera obszaru klienckiego formantu, a następnie wywołuje klasy formantu `OnDraw` metody.|  
|[CComControlBase::OnSetFocus](#onsetfocus)|Sprawdza, czy formant jest aktywny w miejscu i ma prawidłową sterowania lokacji, a następnie informuje kontenera formantu zyskały fokus.|  
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Przesłonić tę metodę, aby podać własne programy obsługi akceleratora.|  
|[CComControlBase::SendOnClose](#sendonclose)|Powiadamia wszystkie advisory wychwytywanie zarejestrowany posiadacz Porada, że formant został zamknięty.|  
|[CComControlBase::SendOnDataChange](#sendondatachange)|Powiadamia wszystkie advisory wychwytywanie zarejestrowany właściciel Porada o zmianie danych formantu.|  
|[CComControlBase::SendOnRename](#sendonrename)|Powiadamia wszystkie advisory wychwytywanie zarejestrowany posiadacz Porada formantem nowe krótkiej nazwy.|  
|[CComControlBase::SendOnSave](#sendonsave)|Powiadamia wszystkie advisory wychwytywanie zarejestrowany posiadacz Porada, że formant został zapisany.|  
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Powiadamia wszystkie zarejestrowane advisory wychwytywanie, które formantu widoku został zmieniony.|  
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Ustawia lub usuwa fokus klawiatury do lub z formantu.|  
|[CComControlBase::SetDirty](#setdirty)|Ustawia element członkowski danych `m_bRequiresSave` wartość `bDirty`.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComControlBase::m_bAutoSize](#m_bautosize)|Flaga wskazująca, że formant nie może być dowolnym rozmiarze.|  
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Flaga wskazująca, że `IDataObjectImpl::GetData` i `CComControlBase::GetZoomInfo` powinien być ustawiony rozmiar formantu z `m_sizeNatural` , a nie z `m_sizeExtent`.|  
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Flaga wskazująca, że `IDataObjectImpl::GetData` należy używać HIMETRIC jednostki i nie pikseli podczas rysowania.|  
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Flaga wskazująca, czy formant jest aktywny w miejscu.|  
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Flaga oznaczająca, który obsługuje kontenera **IOleInPlaceSiteEx** interfejsu i OCX96 sterowanie funkcjami, takimi jak formanty bez okien i pozbawione migotania.|  
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Flaga wskazująca, czy formant ma negocjowane z kontenera o obsługę funkcji kontroli OCX96 (np. formanty bez okien i pozbawione migotania) i określa, czy formant jest okna lub bez okien.|  
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Flaga wskazująca, że kontrolka chce przeskładać jego prezentacji, gdy zmienia się rozmiar wyświetlania formantu kontenera.|  
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Flaga wskazująca, że formant został zmieniony od ostatniego zapisu.|  
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Flaga wskazująca formantu chce zmienić rozmiar jego zakres fizycznych (nieskalowanego fizycznego rozmiaru) gdy kontenera zmienia rozmiar wyświetlania formantu.|  
|[CComControlBase::m_bUIActive](#m_buiactive)|Flaga wskazująca formantu interfejsu użytkownika, takich jak menu i pasków narzędzi, jest aktywna.|  
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Flaga wskazująca, że formant używa regionu okna dostarczone przez kontener.|  
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Flaga oznaczająca formant został bez okien, ale może lub nie może być niepowiązane z oknami teraz.|  
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Flaga wskazująca, że formant powinien być okna, nawet wtedy, gdy kontener obsługuje formanty bez okien.|  
|[CComControlBase::m_bWndLess](#m_bwndless)|Flaga wskazująca, czy formant jest powiązany z oknami.|  
|[CComControlBase::m_hWndCD](#m_hwndcd)|Zawiera odwołania do uchwytu okna skojarzony z formantem.|  
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Licznik Czas kontenera ma zablokowane zdarzenia (odmówił Akceptuj zdarzenia) bez pośredniczące odblokowania zdarzeń (akceptacji zdarzeń).|  
|[CComControlBase::m_rcPos](#m_rcpos)|Pozycja w pikselach formantu wyrażone we współrzędnych kontenera.|  
|[CComControlBase::m_sizeExtent](#m_sizeextent)|Stopień kontroli w jednostkach HIMETRIC (każda jednostka jest 0,01 milimetry) do wyświetlenia określonej.|  
|[CComControlBase::m_sizeNatural](#m_sizenatural)|Fizyczny rozmiar formantu w jednostkach HIMETRIC (każda jednostka jest 0,01 milimetry).|  
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Bezpośrednie wskaźnik do advisory połączenie w kontenerze (kontenera [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)).|  
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|A `CComDispatchDriver` obiekt, który pozwala pobierać i ustawiać właściwości kontenera za pośrednictwem `IDispatch` wskaźnika.|  
|[CComControlBase::m_spClientSite](#m_spclientsite)|Wskaźnik do lokacji klienta formantu w kontenerze.|  
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Zapewnia standard sposoby przechowywania advisory połączeń między obiekty danych i służyć poradą sink.|  
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Wskaźnik do kontenera [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), lub [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) wskaźnika interfejsu.|  
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Udostępnia implementację standardowe sposób przechowywania advisory połączenia.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dostarcza metody do tworzenia i zarządzania kontrolek ALT. [Klasa CComControl](../../atl/reference/ccomcontrol-class.md) pochodną `CComControlBase`. Podczas tworzenia formantu standardowego lub DHTML formantu przy użyciu Kreator formantu ATL kreatora automatycznie zostanie pochodzi z klasy `CComControlBase`.  
  
 Aby uzyskać więcej informacji o tworzeniu formantu, zobacz [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md). Aby uzyskać więcej informacji o Kreatorze Projekt ATL, zobacz artykuł [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="appearancetype"></a>CComControlBase::AppearanceType  
 Zastąpić, jeśli Twoje **m_nAppearance** właściwości podstawowych, nie jest typu **krótki**.  
  
```
typedef short AppearanceType;
```  
  
### <a name="remarks"></a>Uwagi  
 Kreator formantu ATL dodaje **m_nAppearance** podstawowa właściwość typu krótki. Zastąpienie `AppearanceType` użycie innego typu danych.  
  
##  <a name="ccomcontrolbase"></a>CComControlBase::CComControlBase  
 Konstruktor.  
  
```
CComControlBase(HWND& h);
```  
  
### <a name="parameters"></a>Parametry  
 `h`  
 Dojście do okna skojarzony z formantem.  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje rozmiar formantu 5080 X 5080 HIMETRIC jednostek (2 "X 2") i inicjuje `CComControlBase` wartości elementu członkowskiego danych do **NULL** lub **FALSE**.  
  
##  <a name="dtor"></a>CComControlBase:: ~ CComControlBase  
 Destruktor.  
  
```
~CComControlBase();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli formant jest okna, `~CComControlBase` niszczy go przez wywołanie metody [DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682).  
  
##  <a name="controlqueryinterface"></a>CComControlBase::ControlQueryInterface  
 Pobiera wskaźnik do żądanego interfejsu.  
  
```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 Identyfikator GUID żądanego interfejsu.  
  
 `ppv`  
 Wskaźnik do wskaźnika interfejsu identyfikowane przez `iid`, lub **NULL** Jeśli nie można odnaleźć interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Obsługuje tylko interfejsy COM tabeli mapy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]  
  
##  <a name="doesverbactivate"></a>CComControlBase::DoesVerbActivate  
 Sprawdza, czy `iVerb` używane przez parametr `IOleObjectImpl::DoVerb` albo aktywuje formantu interfejsu użytkownika ( `iVerb` jest równe `OLEIVERB_UIACTIVATE`), określa akcję wykonywaną, gdy użytkownik kliknie dwukrotnie formantu ( `iVerb` jest równe `OLEIVERB_PRIMARY`), wyświetla kontrolkę ( `iVerb` jest równe `OLEIVERB_SHOW`), lub aktywuje formant ( `iVerb` jest równe **OLEIVERB_INPLACEACTIVATE**).  
  
```
BOOL DoesVerbActivate(LONG iVerb);
```  
  
### <a name="parameters"></a>Parametry  
 `iVerb`  
 Wartość wskazujący akcję do wykonania przez `DoVerb`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** Jeśli `iVerb` jest równe `OLEIVERB_UIACTIVATE`, `OLEIVERB_PRIMARY`, `OLEIVERB_SHOW`, lub **OLEIVERB_INPLACEACTIVATE**; w przeciwnym razie zwraca **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Mogą przesłaniać tę metodę do zdefiniowania własnych zlecenie aktywacji.  
  
##  <a name="doesverbuiactivate"></a>CComControlBase::DoesVerbUIActivate  
 Sprawdza, czy `iVerb` używane przez parametr `IOleObjectImpl::DoVerb` powoduje formantu interfejsu użytkownika aktywować i zwraca **TRUE**.  
  
```
BOOL DoesVerbUIActivate(LONG iVerb);
```  
  
### <a name="parameters"></a>Parametry  
 `iVerb`  
 Wartość wskazujący akcję do wykonania przez `DoVerb`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** Jeśli `iVerb` jest równe `OLEIVERB_UIACTIVATE`, `OLEIVERB_PRIMARY`, `OLEIVERB_SHOW`, lub **OLEIVERB_INPLACEACTIVATE**. W przeciwnym razie metoda zwraca **FALSE**.  
  
##  <a name="doverbproperties"></a>CComControlBase::DoVerbProperties  
 Wyświetla strony właściwości formantu.  
  
```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 Zastrzeżone.  
  
 *hwndParent*  
 Uchwyt okna zawierającego ten formant.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]  
  
 [!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]  
  
##  <a name="fireviewchange"></a>CComControlBase::FireViewChange  
 Wywołanie tej metody mówić kontener, aby odświeżyć formant lub powiadomić wychwytywanie zarejestrowanych Porada, które formantu widoku został zmieniony.  
  
```
HRESULT FireViewChange();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli formant jest aktywny (element członkowski danych klasy formantu [CComControlBase::m_bInPlaceActive](#m_binplaceactive) jest **TRUE**), powiadamia kontenera chcesz odświeżyć całego formantu. Jeśli formant jest nieaktywny, powiadamia zarejestrowany przez formant poinformowania wychwytywanie (przez element członkowski danych klasy formantu [CComControlBase::m_spAdviseSink](#m_spadvisesink)) zmodyfikowaną formantu widoku.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]  
  
##  <a name="getambientappearance"></a>CComControlBase::GetAmbientAppearance  
 Pobiera **DISPID_AMBIENT_APPEARANCE**, wygląd bieżące ustawienia dla formantu: 0 płaski i 1 dla 3W.  
  
```
HRESULT GetAmbientAppearance(short& nAppearance);
```  
  
### <a name="parameters"></a>Parametry  
 `nAppearance`  
 Właściwość **DISPID_AMBIENT_APPEARANCE**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]  
  
##  <a name="getambientautoclip"></a>CComControlBase::GetAmbientAutoClip  
 Pobiera **DISPID_AMBIENT_AUTOCLIP**, flagę wskazującą, czy kontener obsługuje automatyczne wycinka obszaru wyświetlania formantu.  
  
```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```  
  
### <a name="parameters"></a>Parametry  
 *bAutoClip*  
 Właściwość **DISPID_AMBIENT_AUTOCLIP**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="getambientbackcolor"></a>CComControlBase::GetAmbientBackColor  
 Pobiera **DISPID_AMBIENT_BACKCOLOR**, kolor tła otoczenia dla wszystkich kontrolek, zdefiniowany przez kontener.  
  
```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```  
  
### <a name="parameters"></a>Parametry  
 *Kolor tła*  
 Właściwość **DISPID_AMBIENT_BACKCOLOR**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet  
 Pobiera **DISPID_AMBIENT_CHARSET**, zestaw znaków otoczenia dla wszystkich kontrolek, zdefiniowany przez kontener.  
  
```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```  
  
### <a name="parameters"></a>Parametry  
 *bstrCharSet*  
 Właściwość **DISPID_AMBIENT_CHARSET**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="getambientcodepage"></a>CComControlBase::GetAmbientCodePage  
 Pobiera **DISPID_AMBIENT_CODEPAGE**, strona otaczającego kodu dla wszystkich kontrolek, zdefiniowany przez kontener.  
  
```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```  
  
### <a name="parameters"></a>Parametry  
 *ulCodePage*  
 Właściwość **DISPID_AMBIENT_CODEPAGE**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="getambientdisplayasdefault"></a>CComControlBase::GetAmbientDisplayAsDefault  
 Pobiera **DISPID_AMBIENT_DISPLAYASDEFAULT**, Flaga, która jest **TRUE** Jeśli kontener został oznaczony do formantu w tej lokacji jako przycisk domyślny, a w związku z tym kontrolkę przycisku powinien być rysowany z grubszy ramki.  
  
```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```  
  
### <a name="parameters"></a>Parametry  
 `bDisplayAsDefault`  
 Właściwość **DISPID_AMBIENT_DISPLAYASDEFAULT**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="getambientdisplayname"></a>CComControlBase::GetAmbientDisplayName  
 Pobiera **DISPID_AMBIENT_DISPLAYNAME**, nazwa kontenera jest dostarczona do formantu.  
  
```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```  
  
### <a name="parameters"></a>Parametry  
 *bstrDisplayName*  
 Właściwość **DISPID_AMBIENT_DISPLAYNAME**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="getambientfont"></a>CComControlBase::GetAmbientFont  
 Pobiera wskaźnik do kontenera obiektu otoczenia `IFont` interfejsu.  
  
```
HRESULT GetAmbientFont(IFont** ppFont);
```  
  
### <a name="parameters"></a>Parametry  
 `ppFont`  
 Wskaźnik do kontenera obiektu otoczenia [IFont](http://msdn.microsoft.com/library/windows/desktop/ms680673) interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli właściwość jest **NULL**, wskaźnik jest **NULL**. Jeśli wskaźnik jest nie **NULL**, wywołujący musi zwolnić wskaźnika.  
  
##  <a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp  
 Pobiera wskaźnik do kontenera obiektu otoczenia **IFontDisp** interfejs wysyłania.  
  
```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```  
  
### <a name="parameters"></a>Parametry  
 `ppFont`  
 Wskaźnik do kontenera obiektu otoczenia [IFontDisp](http://msdn.microsoft.com/library/windows/desktop/ms692695) interfejs wysyłania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli właściwość jest **NULL**, wskaźnik jest **NULL**. Jeśli wskaźnik jest nie **NULL**, wywołujący musi zwolnić wskaźnika.  
  
##  <a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor  
 Pobiera **DISPID_AMBIENT_FORECOLOR**, kolor otoczenia dla wszystkich kontrolek, zdefiniowany przez kontener.  
  
```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```  
  
### <a name="parameters"></a>Parametry  
 *ForeColor*  
 Właściwość **DISPID_AMBIENT_FORECOLOR**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID  
 Pobiera **DISPID_AMBIENT_LOCALEID**, identyfikator języka używanego przez kontener.  
  
```
HRESULT GetAmbientLocaleID(LCID& lcid);
```  
  
### <a name="parameters"></a>Parametry  
 `lcid`  
 Właściwość **DISPID_AMBIENT_LOCALEID**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Formant może użyć tego identyfikatora do dostosowania interfejsu użytkownika w różnych językach.  
  
##  <a name="getambientmessagereflect"></a>CComControlBase::GetAmbientMessageReflect  
 Pobiera **DISPID_AMBIENT_MESSAGEREFLECT**, flagę wskazującą, czy chce odbierać komunikaty okna kontenera (takie jak `WM_DRAWITEM`) jako zdarzenia.  
  
```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```  
  
### <a name="parameters"></a>Parametry  
 `bMessageReflect`  
 Właściwość **DISPID_AMBIENT_MESSAGEREFLECT**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="getambientpalette"></a>CComControlBase::GetAmbientPalette  
 Pobiera **DISPID_AMBIENT_PALETTE**, umożliwia dostęp do kontenera `HPALETTE`.  
  
```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```  
  
### <a name="parameters"></a>Parametry  
 `hPalette`  
 Właściwość **DISPID_AMBIENT_PALETTE**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="getambientproperty"></a>CComControlBase::GetAmbientProperty  
 Pobiera określony przez właściwość kontenera `dispid`.  
  
```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```  
  
### <a name="parameters"></a>Parametry  
 `dispid`  
 Identyfikator właściwości kontenera do pobrania.  
  
 `var`  
 Zmiennej właściwość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 ATL udostępnił zestaw funkcji pomocnika można pobrać określone właściwości, na przykład [CComControlBase::GetAmbientBackColor](#getambientbackcolor). Jeśli nie ma żadnych odpowiedniej metody, użyć `GetAmbientProperty`.  
  
##  <a name="getambientrighttoleft"></a>CComControlBase::GetAmbientRightToLeft  
 Pobiera **DISPID_AMBIENT_RIGHTTOLEFT**, kierunek, w którym zawartość jest wyświetlana przez kontener.  
  
```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```  
  
### <a name="parameters"></a>Parametry  
 *bRightToLeft*  
 Właściwość **DISPID_AMBIENT_RIGHTTOLEFT**. Ustaw **TRUE** Jeśli zawartość jest wyświetlane od prawej do lewej, **FALSE** Jeśli jest wyświetlana po lewej do prawej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="getambientscaleunits"></a>CComControlBase::GetAmbientScaleUnits  
 Pobiera **DISPID_AMBIENT_SCALEUNITS**, jednostki otoczenia kontenera (takich jak cale lub cm) na etykietach Wyświetla.  
  
```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```  
  
### <a name="parameters"></a>Parametry  
 *bstrScaleUnits*  
 Właściwość **DISPID_AMBIENT_SCALEUNITS**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles  
 Pobiera **DISPID_AMBIENT_SHOWGRABHANDLES**, flagę wskazującą, czy kontener zezwala kontrolka do wyświetlenia uchwytów dla siebie, gdy jest aktywny.  
  
```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```  
  
### <a name="parameters"></a>Parametry  
 *bShowGrabHandles*  
 Właściwość **DISPID_AMBIENT_SHOWGRABHANDLES**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching  
 Pobiera **DISPID_AMBIENT_SHOWHATCHING**, flagę wskazującą, czy kontener zezwala formantu, aby wyświetlić się wzorem kreskowanym, gdy formantu interfejsu użytkownika jest aktywna.  
  
```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```  
  
### <a name="parameters"></a>Parametry  
 *bShowHatching*  
 Właściwość **DISPID_AMBIENT_SHOWHATCHING**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientSupportsMnemonics  
 Pobiera **DISPID_AMBIENT_SUPPORTSMNEMONICS**, flagę wskazującą, czy kontener obsługuje klawiszy skrótu klawiatury.  
  
```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```  
  
### <a name="parameters"></a>Parametry  
 *bSupportsMnemonics*  
 Właściwość **DISPID_AMBIENT_SUPPORTSMNEMONICS**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="getambienttextalign"></a>CComControlBase::GetAmbientTextAlign  
 Pobiera **DISPID_AMBIENT_TEXTALIGN**, wyrównanie tekstu preferowany przez kontener: 0 dla opcji Ogólne (liczb, tekst do prawej po lewej), 1 dla wyrównania do lewej, 2 dla wyrównania center i 3-wyrównanie do prawej.  
  
```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```  
  
### <a name="parameters"></a>Parametry  
 *nTextAlign*  
 Właściwość **DISPID_AMBIENT_TEXTALIGN**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="getambienttoptobottom"></a>CComControlBase::GetAmbientTopToBottom  
 Pobiera **DISPID_AMBIENT_TOPTOBOTTOM**, kierunek, w którym zawartość jest wyświetlana przez kontener.  
  
```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```  
  
### <a name="parameters"></a>Parametry  
 *bTopToBottom*  
 Właściwość **DISPID_AMBIENT_TOPTOBOTTOM**. Ustaw **TRUE** Jeśli tekst jest wyświetlany góry do dołu, **FALSE** Jeśli zostanie wyświetlone dołu do góry.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="getambientuidead"></a>CComControlBase::GetAmbientUIDead  
 Pobiera **DISPID_AMBIENT_UIDEAD**, flagę wskazującą, czy kontener chce kontroli odpowiada na działania interfejsu użytkownika.  
  
```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```  
  
### <a name="parameters"></a>Parametry  
 *bUIDead*  
 Właściwość **DISPID_AMBIENT_UIDEAD**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli **TRUE**, nie powinny odpowiadać formantu. Ta flaga ma zastosowanie bez względu na to **DISPID_AMBIENT_USERMODE** flagi. Zobacz [CComControlBase::GetAmbientUserMode](#getambientusermode).  
  
##  <a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode  
 Pobiera **DISPID_AMBIENT_USERMODE**, flagę wskazującą, czy kontener jest w trybie wykonywania ( **TRUE**) lub w trybie projektowania ( **FALSE**).  
  
```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```  
  
### <a name="parameters"></a>Parametry  
 `bUserMode`  
 Właściwość **DISPID_AMBIENT_USERMODE**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="getdirty"></a>CComControlBase::GetDirty  
 Zwraca wartość elementu członkowskiego danych `m_bRequiresSave`.  
  
```
BOOL GetDirty();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość elementu członkowskiego danych [m_bRequiresSave](#m_brequiressave).  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość jest ustawiana za pomocą [CComControlBase::SetDirty](#setdirty).  
  
##  <a name="getzoominfo"></a>CComControlBase::GetZoomInfo  
 Pobiera x i y wartości licznika i denominator współczynnika powiększenia dla formantu aktywowana dla w miejscu edycji.  
  
```
void GetZoomInfo(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>Parametry  
 `di`  
 Struktura, którym będą przechowywane licznik i mianownik współczynnika powiększenia. Aby uzyskać więcej informacji, zobacz [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).  
  
### <a name="remarks"></a>Uwagi  
 Współczynnika powiększenia jest część fizycznych rozmiar formantu jego bieżącym zakresie.  
  
##  <a name="inplaceactivate"></a>CComControlBase::InPlaceActivate  
 Powoduje, że formant do przejścia z stan nieaktywny do stanu niezależnie od zleceń w `iVerb` wskazuje.  
  
```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `iVerb`  
 Wartość wskazujący akcję do wykonania przez [IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb).  
  
 *prcPosRect*  
 Wskaźnik do położenia kontrolki w miejscu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Przed aktywacji ta metoda sprawdza, czy formant ma lokacji klienta, sprawdza, ile formant jest widoczny i pobiera lokalizacji kontrolki w oknie nadrzędnym. Po aktywowaniu formantu, ta metoda aktywuje formantu interfejsu użytkownika i informuje kontener, aby uwidocznić formantu.  
  
 Ta metoda umożliwia również pobranie `IOleInPlaceSite`, **IOleInPlaceSiteEx**, lub **IOleInPlaceSiteWindowless** wskaźnika interfejsu dla formantu i zapisuje go w element członkowski danych klasy formantu [CComControlBase::m_spInPlaceSite](#m_spinplacesite). Elementy członkowskie danych klasy formantu [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase::m_bWndLess](#m_bwndless), [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)i [ CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) są ustawione na wartość true jako odpowiednie.  
  
##  <a name="internalgetsite"></a>CComControlBase::InternalGetSite  
 Wywołać tę metodę do badania lokacji kontroli dla wskaźnika interfejsu zidentyfikowane.  
  
```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```  
  
### <a name="parameters"></a>Parametry  
 `riid`  
 Uzyskanie identyfikatora IID wskaźnika interfejsu, który ma zostać zwrócony w `ppUnkSite`.  
  
 `ppUnkSite`  
 Adres zmienna wskaźnika, która odbiera wskaźnika interfejsu w `riid`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli lokacja obsługuje interfejs w `riid`, zwracany jest wskaźnik za pomocą klasy `ppUnkSite`. W przeciwnym razie `ppUnkSite` jest równa NULL.  
  
##  <a name="m_bautosize"></a>CComControlBase::m_bAutoSize  
 Flaga wskazująca, że formant nie może być dowolnym rozmiarze.  
  
```
unsigned m_bAutoSize:1;
```  
  
### <a name="remarks"></a>Uwagi  
 Ta flaga jest sprawdzana przez `IOleObjectImpl::SetExtent` i, jeżeli **TRUE**, powoduje, że funkcja zwraca **E_FAIL**.  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
 Jeśli dodasz **automatyczny rozmiar** opcja [właściwości zasobu](../../atl/reference/stock-properties-atl-control-wizard.md) kartę Kreator formantu ATL, Kreator automatycznie utworzy ten element członkowski danych w Twojej klasy kontrolki, put i pobrać metod dla właściwości i obsługuje [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) automatycznie powiadamiać kontenera, gdy właściwość zostanie zmieniona.  
  
##  <a name="m_bdrawfromnatural"></a>CComControlBase::m_bDrawFromNatural  
 Flaga wskazująca, że `IDataObjectImpl::GetData` i `CComControlBase::GetZoomInfo` powinien być ustawiony rozmiar formantu z `m_sizeNatural` , a nie z `m_sizeExtent`.  
  
```
unsigned m_bDrawFromNatural:1;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_bdrawgetdatainhimetric"></a>CComControlBase::m_bDrawGetDataInHimetric  
 Flaga wskazująca, że `IDataObjectImpl::GetData` należy używać HIMETRIC jednostki i nie pikseli podczas rysowania.  
  
```
unsigned m_bDrawGetDataInHimetric:1;
```  
  
### <a name="remarks"></a>Uwagi  
 Każda jednostka logiczna HIMETRIC jest 0,01 milimetra.  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_binplaceactive"></a>CComControlBase::m_bInPlaceActive  
 Flaga wskazująca, czy formant jest aktywny w miejscu.  
  
```
unsigned m_bInPlaceActive:1;
```  
  
### <a name="remarks"></a>Uwagi  
 To oznacza, że formant jest widoczny i okna, jeśli istnieje, jest widoczne, ale jego menu i pasków narzędzi nie mogą być aktywne. `m_bUIActive` Flaga wskazuje formantu interfejsu użytkownika, takich jak menu, również jest aktywny.  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx  
 Flaga oznaczająca, który obsługuje kontenera **IOleInPlaceSiteEx** interfejsu i OCX96 sterowanie funkcjami, takimi jak formanty bez okien i pozbawione migotania.  
  
```
unsigned m_bInPlaceSiteEx:1;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
 Element członkowski danych `m_spInPlaceSite` wskazuje [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), lub [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) interfejsu, w zależności od wartości `m_bWndLess` i `m_bInPlaceSiteEx` flagi. (Element członkowski danych `m_bNegotiatedWnd` musi być **TRUE** dla `m_spInPlaceSite` wskaźnika jest nieprawidłowy.)  
  
 Jeśli `m_bWndLess` jest **FALSE** i `m_bInPlaceSiteEx` jest **TRUE**, `m_spInPlaceSite` jest **IOleInPlaceSiteEx** wskaźnika interfejsu. Zobacz [m_spInPlaceSite](#m_spinplacesite) dla tabelę przedstawiającą relacji między elementami te trzy danych.  
  
##  <a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd  
 Flaga wskazująca, czy formant ma negocjowane z kontenera o obsługę funkcji kontroli OCX96 (np. formanty bez okien i pozbawione migotania) i określa, czy formant jest okna lub bez okien.  
  
```
unsigned m_bNegotiatedWnd:1;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
 `m_bNegotiatedWnd` Flagi musi być **TRUE** dla `m_spInPlaceSite` wskaźnika jest nieprawidłowy.  
  
##  <a name="m_brecomposeonresize"></a>CComControlBase::m_bRecomposeOnResize  
 Flaga wskazująca, że kontrolka chce przeskładać jego prezentacji, gdy zmienia się rozmiar wyświetlania formantu kontenera.  
  
```
unsigned m_bRecomposeOnResize:1;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
 Ta flaga jest sprawdzana przez [IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) i, jeżeli **TRUE**, `SetExtent` powiadamia kontenera zmiany widoku. Jeśli ta flaga jest ustawiona, **OLEMISC_RECOMPOSEONRESIZE** bitu w [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) również musi mieć wartość wyliczenia.  
  
##  <a name="m_brequiressave"></a>CComControlBase::m_bRequiresSave  
 Flaga wskazująca, że formant został zmieniony od ostatniego zapisu.  
  
```
unsigned m_bRequiresSave:1;
```  
  
### <a name="remarks"></a>Uwagi  
 Wartość `m_bRequiresSave` można ustawić za pomocą [CComControlBase::SetDirty](#setdirty) i pobrane z [CComControlBase::GetDirty](#getdirty).  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural  
 Flaga wskazująca formantu chce zmienić rozmiar jego zakres fizycznych (nieskalowanego fizycznego rozmiaru) gdy kontenera zmienia rozmiar wyświetlania formantu.  
  
```
unsigned m_bResizeNatural:1;
```  
  
### <a name="remarks"></a>Uwagi  
 Ta flaga jest sprawdzana przez `IOleObjectImpl::SetExtent` i, jeżeli **TRUE**, rozmiar przekazany `SetExtent` jest przypisany do `m_sizeNatural`.  
  
 Rozmiar przekazanego do `SetExtent` jest zawsze przypisywana do `m_sizeExtent`, niezależnie od wartości `m_bResizeNatural`.  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_buiactive"></a>CComControlBase::m_bUIActive  
 Flaga wskazująca formantu interfejsu użytkownika, takich jak menu i pasków narzędzi, jest aktywna.  
  
```
unsigned m_bUIActive:1;
```  
  
### <a name="remarks"></a>Uwagi  
 `m_bInPlaceActive` Flaga wskazuje, że formant jest aktywny, ale nie który interfejs użytkownika jest aktywna.  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn  
 Flaga wskazująca, że formant używa regionu okna dostarczone przez kontener.  
  
```
unsigned m_bUsingWindowRgn:1;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_bwasoncewindowless"></a>CComControlBase::m_bWasOnceWindowless  
 Flaga oznaczająca formant został bez okien, ale może lub nie może być niepowiązane z oknami teraz.  
  
```
unsigned m_bWasOnceWindowless:1;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_bwindowonly"></a>CComControlBase::m_bWindowOnly  
 Flaga wskazująca, że formant powinien być okna, nawet wtedy, gdy kontener obsługuje formanty bez okien.  
  
```
unsigned m_bWindowOnly:1;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_bwndless"></a>CComControlBase::m_bWndLess  
 Flaga wskazująca, czy formant jest powiązany z oknami.  
  
```
unsigned m_bWndLess:1;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
 Element członkowski danych `m_spInPlaceSite` wskazuje [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), lub [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) interfejsu, w zależności od wartości `m_bWndLess` i [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex) flagi. (Element członkowski danych [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) musi być **TRUE** dla [CComControlBase::m_spInPlaceSite](#m_spinplacesite) wskaźnika jest nieprawidłowy.)  
  
 Jeśli `m_bWndLess` jest **TRUE**, `m_spInPlaceSite` jest **IOleInPlaceSiteWindowless** wskaźnika interfejsu. Zobacz [CComControlBase::m_spInPlaceSite](#m_spinplacesite) dla tabelę przedstawiającą pełną relacji między elementami członkowskimi tych danych.  
  
##  <a name="m_hwndcd"></a>CComControlBase::m_hWndCD  
 Zawiera odwołania do uchwytu okna skojarzony z formantem.  
  
```
HWND& m_hWndCD;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents  
 Licznik Czas kontenera ma zablokowane zdarzenia (odmówił Akceptuj zdarzenia) bez pośredniczące odblokowania zdarzeń (akceptacji zdarzeń).  
  
```
short m_nFreezeEvents;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_rcpos"></a>CComControlBase::m_rcPos  
 Pozycja w pikselach formantu wyrażone we współrzędnych kontenera.  
  
```
RECT m_rcPos;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_sizeextent"></a>CComControlBase::m_sizeExtent  
 Stopień kontroli w jednostkach HIMETRIC (każda jednostka jest 0,01 milimetry) do wyświetlenia określonej.  
  
```
SIZE m_sizeExtent;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
 Ten rozmiar jest skalowana przez wyświetlanie. Fizyczny rozmiar formantu jest określona w `m_sizeNatural` element członkowski danych i zostanie rozwiązany.  
  
 Rozmiar można przekonwertować na pikseli z funkcji globalnej [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).  
  
##  <a name="m_sizenatural"></a>CComControlBase::m_sizeNatural  
 Fizyczny rozmiar formantu w jednostkach HIMETRIC (każda jednostka jest 0,01 milimetry).  
  
```
SIZE m_sizeNatural;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
 Ten rozmiar jest ustalone podczas rozmiar w `m_sizeExtent` jest skalowana przez wyświetlanie.  
  
 Rozmiar można przekonwertować na pikseli z funkcji globalnej [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).  
  
##  <a name="m_spadvisesink"></a>CComControlBase::m_spAdviseSink  
 Bezpośrednie wskaźnik do advisory połączenie w kontenerze (kontenera [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)).  
  
```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```     
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_spambientdispatch"></a>CComControlBase::m_spAmbientDispatch  
 A `CComDispatchDriver` obiekt, który pozwala pobierać i ustawiać właściwości obiektu za pomocą `IDispatch` wskaźnika.  
  
```
CComDispatchDriver m_spAmbientDispatch;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_spclientsite"></a>CComControlBase::m_spClientSite  
 Wskaźnik do lokacji klienta formantu w kontenerze.  
  
```
CComPtr<IOleClientSite>
    m_spClientSite;
```     
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
##  <a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder  
 Zapewnia standard sposoby przechowywania advisory połączeń między obiekty danych i służyć poradą sink.  
  
```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```     
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
 Obiekt danych jest formant, który transferu danych i implementującej [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421), której metody Określ średni format i transferu danych.  
  
 Interfejs `m_spDataAdviseHolder` implementuje [IDataObject::DAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692579) i [IDataObject::DUnadvise](http://msdn.microsoft.com/library/windows/desktop/ms692448) metod w celu ustanowienia oraz usuwanie połączeń zespół doradczy do kontenera. Formantu kontenera musi implementować zbiornika Porada dzięki obsłudze [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) interfejsu.  
  
##  <a name="m_spinplacesite"></a>CComControlBase::m_spInPlaceSite  
 Wskaźnik do kontenera [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), lub [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) wskaźnika interfejsu.  
  
```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```     
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
 `m_spInPlaceSite` Wskaźnik jest prawidłowy tylko wtedy, gdy [m_bNegotiatedWnd](#m_bnegotiatedwnd) flaga jest **TRUE**.  
  
 W poniższej tabeli przedstawiono sposób `m_spInPlaceSite` zależy od typu wskaźnika [m_bWndLess](#m_bwndless) i [m_bInPlaceSiteEx](#m_binplacesiteex) flagi elementu członkowskiego danych:  
  
|m_spInPlaceSite typu|m_bWndLess wartość|m_bInPlaceSiteEx wartość|  
|---------------------------|-----------------------|-----------------------------|  
|**IOleInPlaceSiteWindowless**|**WARTOŚĆ TRUE**|**Wartość TRUE,** lub **FALSE**|  
|**IOleInPlaceSiteEx**|**WARTOŚĆ FALSE**|**WARTOŚĆ TRUE**|  
|`IOleInPlaceSite`|**WARTOŚĆ FALSE**|**WARTOŚĆ FALSE**|  
  
##  <a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder  
 Udostępnia implementację standardowe sposób przechowywania advisory połączenia.  
  
```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```     
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć tego elementu członkowskiego danych w ramach Twojej klasy kontrolki, należy zadeklarować go jako element członkowski danych w Twojej klasy kontrolki. Twojej klasy kontrolki nie będzie dziedziczyć ten element członkowski danych z klasy podstawowej, ponieważ jest ona zadeklarowana w obrębie elementu union w klasie podstawowej.  
  
 Interfejs `m_spOleAdviseHolder` implementuje [IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573) i [IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749) metod w celu ustanowienia oraz usuwanie połączeń zespół doradczy do kontenera. Formantu kontenera musi implementować zbiornika Porada dzięki obsłudze [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) interfejsu.  
  
##  <a name="ondraw"></a>CComControlBase::OnDraw  
 Zastępuje tę metodę, by narysować Twoją kontrolkę.  
  
```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>Parametry  
 `di`  
 Odwołanie do [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) strukturę, która zawiera rysowania informacje takie jak aspekt rysowania, granice formantu i określa, czy Rysowanie jest zoptymalizowana, czy nie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Wartość domyślna `OnDraw` usuwa przywraca kontekst urządzenia lub nie działa, w zależności od flagi w [CComControlBase::OnDrawAdvanced](#ondrawadvanced).  
  
 `OnDraw` Metody jest automatycznie dodawany do Twojej klasy kontrolki, podczas tworzenia formantu z Kreator formantu ATL. Domyślne kreatora `OnDraw` rysuje prostokąt z etykietą "ATL 8.0".  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CComControlBase::GetAmbientAppearance](#getambientappearance).  
  
##  <a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced  
 Wartość domyślna `OnDrawAdvanced` przygotowuje znormalizowany kontekst urządzenia do rysowania, a następnie wywołuje Twojej klasy kontrolki `OnDraw` metody.  
  
```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>Parametry  
 `di`  
 Odwołanie do [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) strukturę, która zawiera rysowania informacje takie jak aspekt rysowania, granice formantu i określa, czy Rysowanie jest zoptymalizowana, czy nie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Przesłania tę metodę, jeśli chcesz zaakceptować kontekst urządzenia przekazany przez kontener bez jego normalizacji.  
  
 Zobacz [CComControlBase::OnDraw](#ondraw) więcej szczegółów.  
  
##  <a name="onkillfocus"></a>CComControlBase::OnKillFocus  
 Sprawdza, czy formant jest aktywny w miejscu i ma prawidłową sterowania lokacji, a następnie kontenera informuje, że kontrolka utraciła fokus.  
  
```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Parametry  
 `nMsg`  
 Zastrzeżone.  
  
 `wParam`  
 Zastrzeżone.  
  
 `lParam`  
 Zastrzeżone.  
  
 `bHandled`  
 Flaga wskazująca, czy komunikatów okien zostało obsłużone pomyślnie. Wartość domyślna to `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość 1.  
  
##  <a name="onmouseactivate"></a>CComControlBase::OnMouseActivate  
 Sprawdza, czy interfejs użytkownika działa w trybie użytkownika, a następnie aktywuje formant.  
  
```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Parametry  
 `nMsg`  
 Zastrzeżone.  
  
 `wParam`  
 Zastrzeżone.  
  
 `lParam`  
 Zastrzeżone.  
  
 `bHandled`  
 Flaga wskazująca, czy komunikatów okien zostało obsłużone pomyślnie. Wartość domyślna to `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość 1.  
  
##  <a name="onpaint"></a>CComControlBase::OnPaint  
 Przygotowuje kontenera do rysowania, pobiera obszaru klienckiego formantu, a następnie wywołuje klasy formantu `OnDrawAdvanced` metody.  
  
```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```  
  
### <a name="parameters"></a>Parametry  
 `nMsg`  
 Zastrzeżone.  
  
 `wParam`  
 Istniejącego elementu HDC.  
  
 `lParam`  
 Zastrzeżone.  
  
 `lResult`  
 Zastrzeżone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `wParam` nie ma wartości NULL, `OnPaint` przyjęto założenie, zawiera nieprawidłowy elementu HDC i używa jej zamiast [CComControlBase::m_hWndCD](#m_hwndcd).  
  
##  <a name="onsetfocus"></a>CComControlBase::OnSetFocus  
 Sprawdza, czy formant jest aktywny w miejscu i ma prawidłową sterowania lokacji, a następnie informuje kontenera formantu zyskały fokus.  
  
```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Parametry  
 `nMsg`  
 Zastrzeżone.  
  
 `wParam`  
 Zastrzeżone.  
  
 `lParam`  
 Zastrzeżone.  
  
 `bHandled`  
 Flaga wskazująca, czy komunikatów okien zostało obsłużone pomyślnie. Wartość domyślna to `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość 1.  
  
### <a name="remarks"></a>Uwagi  
 Wysyła powiadomienie do kontenera, że kontrolka otrzymała fokus.  
  
##  <a name="pretranslateaccelerator"></a>CComControlBase::PreTranslateAccelerator  
 Przesłonić tę metodę, aby podać własne programy obsługi akceleratora.  
  
```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```  
  
### <a name="parameters"></a>Parametry  
 `pMsg`  
 Zastrzeżone.  
  
 *hRet*  
 Zastrzeżone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślnie zwraca **FALSE**.  
  
##  <a name="sendonclose"></a>CComControlBase::SendOnClose  
 Powiadamia wszystkie advisory wychwytywanie zarejestrowany posiadacz Porada, że formant został zamknięty.  
  
```
HRESULT SendOnClose();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wysyła powiadomienie, że formant został zamknięty jego advisory wychwytywanie.  
  
##  <a name="sendondatachange"></a>CComControlBase::SendOnDataChange  
 Powiadamia wszystkie advisory wychwytywanie zarejestrowany właściciel Porada o zmianie danych formantu.  
  
```
HRESULT SendOnDataChange(DWORD advf = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *advf*  
 Zalecamy flagi określające, jak wywołanie [IAdviseSink::OnDataChange](http://msdn.microsoft.com/library/windows/desktop/ms687283) staje się. Wartości pochodzą z [ADVF](http://msdn.microsoft.com/library/windows/desktop/ms693742) wyliczenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="sendonrename"></a>CComControlBase::SendOnRename  
 Powiadamia wszystkie advisory wychwytywanie zarejestrowany posiadacz Porada formantem nowe krótkiej nazwy.  
  
```
HRESULT SendOnRename(IMoniker* pmk);
```  
  
### <a name="parameters"></a>Parametry  
 *kluczy głównych parowania*  
 Wskaźnik do nowego krótkiej nazwy formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wysyła powiadomienie, że moniker kontrolki została zmieniona.  
  
##  <a name="sendonsave"></a>CComControlBase::SendOnSave  
 Powiadamia wszystkie advisory wychwytywanie zarejestrowany posiadacz Porada, że formant został zapisany.  
  
```
HRESULT SendOnSave();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wysyła powiadomienie, że formant ochroniła jego dane.  
  
##  <a name="sendonviewchange"></a>CComControlBase::SendOnViewChange  
 Powiadamia wszystkie zarejestrowane advisory wychwytywanie, które formantu widoku został zmieniony.  
  
```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```  
  
### <a name="parameters"></a>Parametry  
 `dwAspect`  
 Aspekt lub widoku formantu.  
  
 *wartość lindex.*  
 Część widoku, który został zmieniony. Prawidłowy jest tylko wartość -1.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 `SendOnViewChange`wywołania [IAdviseSink::OnViewChange](http://msdn.microsoft.com/library/windows/desktop/ms694337). Tylko wartość *wartość lindex* jest obecnie obsługiwane -1, co oznacza, że cały widok ma znaczenie.  
  
##  <a name="setcontrolfocus"></a>CComControlBase::SetControlFocus  
 Ustawia lub usuwa fokus klawiatury do lub z formantu.  
  
```
BOOL SetControlFocus(BOOL bGrab);
```  
  
### <a name="parameters"></a>Parametry  
 *bGrab*  
 Jeśli **TRUE**, ustawia fokus klawiatury do wywoływania formantu. Jeśli **FALSE**, usuwa fokus klawiatury wywołujący formantu, pod warunkiem jego ma fokus.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** Jeśli formant pomyślnie uzyskuje fokus; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Kontrolki okna funkcji Windows API [SetFocus](http://msdn.microsoft.com/library/windows/desktop/ms646312) jest wywoływana. Bez okien kontrolki [IOleInPlaceSiteWindowless::SetFocus](http://msdn.microsoft.com/library/windows/desktop/ms679745) jest wywoływana. Za pomocą tego wywołania bez okien formant uzyskuje fokus klawiatury i mogą odpowiadać na komunikaty okna.  
  
##  <a name="setdirty"></a>CComControlBase::SetDirty  
 Ustawia element członkowski danych `m_bRequiresSave` wartość `bDirty`.  
  
```
void SetDirty(BOOL bDirty);
```  
  
### <a name="parameters"></a>Parametry  
 `bDirty`  
 Wartość elementu członkowskiego danych [CComControlBase::m_bRequiresSave](#m_brequiressave).  
  
### <a name="remarks"></a>Uwagi  
 **SetDirty(TRUE)** powinna być wywoływana do flagi, że formant został zmieniony od ostatniego zapisu. Wartość `m_bRequiresSave` są pobierane z [CComControlBase::GetDirty](#getdirty).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
