---
title: Klasa CAxWindow | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAxWindow
- ATLWIN/ATL::CAxWindow
- ATLWIN/ATL::AttachControl
- ATLWIN/ATL::CreateControl
- ATLWIN/ATL::CreateControlEx
- ATLWIN/ATL::GetWndClassName
- ATLWIN/ATL::QueryControl
- ATLWIN/ATL::QueryHost
- ATLWIN/ATL::SetExternalDispatch
- ATLWIN/ATL::SetExternalUIHandler
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b577e9ffdce651af1e8fcbec741ec259a37c65d6
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880989"
---
# <a name="caxwindow-class"></a>Klasa CAxWindow
Ta klasa dostarcza metody do manipulowania okna hostowania kontrolki ActiveX.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAxWindow : public CWindow
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AttachControl](#attachcontrol)|Dołącza do istniejącego kontrolki ActiveX `CAxWindow` obiektu.|  
|[CAxWindow](#caxwindow)|Konstruuje `CAxWindow` obiektu.|  
|[CreateControl —](#createcontrol)|Tworzy formant ActiveX, inicjuje go i umieszcza w `CAxWindow` okna.|  
|[CreateControlEx](#createcontrolex)|Tworzy formant ActiveX i pobiera wskaźnika interfejsu (lub wskaźniki) z formantu.|  
|[GetWndClassName](#getwndclassname)|(Statyczny) Pobiera nazwę klasy wstępnie zdefiniowanych `CAxWindow` obiektu.|  
|[QueryControl](#querycontrol)|Pobiera `IUnknown` hostowanej formantu ActiveX.|  
|[QueryHost](#queryhost)|Pobiera `IUnknown` wskaźnika `CAxWindow` obiektu.|  
|[SetExternalDispatch](#setexternaldispatch)|Ustawia interfejs ekspedycji zewnętrznych, używane przez `CAxWindow` obiektu.|  
|[SetExternalUIHandler](#setexternaluihandler)|Zestawy zewnętrzne `IDocHostUIHandler` interfejs używany przez `CAxWindow` obiektu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](#operator_eq)|Przypisuje HWND do istniejącego `CAxWindow` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dostarcza metody do manipulowania oknem, który jest hostem formantu ActiveX. Hosting są dostarczane przez " **AtlAxWin80"**, który jest otoczony przez `CAxWindow`.  
  
 Klasa `CAxWindow` jest implementowany jako specjalizacji `CAxWindowT` klasy. Ta specjalizacja jest zadeklarowany jako:  
  
 `typedef CAxWindowT<CWindow> CAxWindow;`  
  
 Jeśli zachodzi potrzeba Zmień klasę bazową, możesz użyć `CAxWindowT` i określ nowe klasy bazowej jako argument szablonu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="attachcontrol"></a>  CAxWindow::AttachControl  
 Tworzy nowy obiekt hosta, jeśli jeden nie będą już dostępne i dołącza określoną kontrolkę do hosta.  
  
```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>Parametry  
 *pControl*  
 [in] Wskaźnik do `IUnknown` formantu.  
  
 *ppUnkContainer*  
 [out] Wskaźnik do `IUnknown` hosta ( `AxWin` obiektu).  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Dołączany obiekt kontrolki musi zostać prawidłowo zainicjowany przed wywołaniem `AttachControl`.  
  
##  <a name="caxwindow"></a>  CAxWindow::CAxWindow  
 Konstruuje `CAxWindow` przy użyciu istniejących uchwyt obiektu okna.  
  
```
CAxWindow(HWND hWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *hWnd*  
 Dojście do istniejącego obiektu okna.  
  
##  <a name="createcontrol"></a>  CAxWindow::CreateControl  
 Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie.  
  
```
HRESULT CreateControl(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);

HRESULT CreateControl(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszName*  
 Wskaźnik do ciągu, aby utworzyć formant. Musi być sformatowany w jednym z następujących sposobów:  
  
-   Identyfikator ProgID takich jak "MSCAL. Calendar.7 "  
  
-   CLSID, takie jak "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adres URL, takich jak "http://www.microsoft.com"  
  
-   Odwołanie do aktywnego dokumentu, takie jak "file://\\\Documents\MyDoc.doc"  
  
-   Fragment kodu HTML, takich jak "MSHTML:\<HTML >\<treści > jest to wiersz tekstu\</BODY >\<polecenia >"  
  
    > [!NOTE]
    >  "MSHTML:" musi poprzedzać fragment kodu HTML, dzięki czemu jest wyznaczony jako strumień MSHTML. Tylko identyfikator ProgID i CLSID są obsługiwane na platformach Windows Mobile. Windows CE osadzić platformy, innym niż Windows Mobile, z obsługą techniczną CE programu Internet Explorer wszystkie typy w tym ProgID, CLSID, adres URL, odwołanie do aktywnego dokumentu i fragment kodu HTML.  
  
 *pStream*  
 [in] Wskaźnik do strumienia, który służy do inicjowania właściwości formantu. Może mieć wartości NULL.  
  
 *ppUnkContainer*  
 [out] Adres wskaźnika, który będzie otrzymywał `IUnknown` kontenera. Może mieć wartości NULL.  
  
 *dwResID*  
 Identyfikator zasobu zasobu HTML. WebBrowser — formant zostanie utworzona i załadowany przy użyciu określonego zasobu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli jest używana druga wersja tej metody, kontrolkę HTML jest tworzony i powiązane z zasobu zidentyfikowanego z użyciem *dwResID*.  
  
 Ta metoda zapewnia ten sam wynik co wywołanie metody:  
  
 [!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]  
  
 Zobacz [CAxWindow2T::CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) tworzenie, inicjowanie i hostowania licencjonowany formant ActiveX.  
  
### <a name="example"></a>Przykład  
 Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu, który używa `CreateControl`.  
  
##  <a name="createcontrolex"></a>  CAxWindow::CreateControlEx  
 Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie.  
  
```
HRESULT CreateControlEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);

HRESULT CreateControlEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszName*  
 Wskaźnik do ciągu, aby utworzyć formant. Musi być sformatowany w jednym z następujących sposobów:  
  
-   Identyfikator ProgID takich jak "MSCAL. Calendar.7 "  
  
-   CLSID, takie jak "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adres URL, takich jak "http://www.microsoft.com"  
  
-   Odwołanie do aktywnego dokumentu, takie jak "file://\\\Documents\MyDoc.doc"  
  
-   Fragment kodu HTML, takich jak "MSHTML:\<HTML >\<treści > jest to wiersz tekstu\</BODY >\<polecenia >"  
  
    > [!NOTE]
    >  "MSHTML:" musi poprzedzać fragment kodu HTML, dzięki czemu jest wyznaczony jako strumień MSHTML. Tylko identyfikator ProgID i CLSID są obsługiwane na platformach Windows Mobile. Windows CE osadzić platformy, innym niż Windows Mobile, z obsługą techniczną CE programu Internet Explorer wszystkie typy w tym ProgID, CLSID, adres URL, odwołanie do aktywnego dokumentu i fragment kodu HTML.  
  
 *pStream*  
 [in] Wskaźnik do strumienia, który służy do inicjowania właściwości formantu. Może mieć wartości NULL.  
  
 *ppUnkContainer*  
 [out] Adres wskaźnika, który będzie otrzymywał `IUnknown` kontenera. Może mieć wartości NULL.  
  
 *ppUnkControl*  
 [out] Adres wskaźnika, który będzie otrzymywał `IUnknown` formantu. Może mieć wartości NULL.  
  
 *iidSink*  
 [in] Identyfikator interfejsu interfejsu wychodzącego w zawartego w nim obiektu. Może być wartością IID_NULL.  
  
 *punkSink*  
 [in] Wskaźnik do `IUnknown` interfejs obiektu sink połączenia z punktem połączenia na przechowywany obiekt określony przez *iidSink*.  
  
 *dwResID*  
 [in] Identyfikator zasobu zasobu HTML. WebBrowser — formant zostanie utworzona i załadowany przy użyciu określonego zasobu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do [CAxWindow::CreateControl](#createcontrol), ale w przeciwieństwie do tej metody `CreateControlEx` umożliwia również odbierać wskaźnika interfejsu do nowo utworzonego formantu i skonfigurować obiekt sink zdarzenia, aby odbierać zdarzenia wywoływane przez formant.  
  
 Zobacz [CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) tworzenie, inicjowanie i hostowania licencjonowany formant ActiveX.  
  
### <a name="example"></a>Przykład  
 Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu, który używa `CreateControlEx`.  
  
##  <a name="getwndclassname"></a>  CAxWindow::GetWndClassName  
 Pobiera nazwę klasy okna.  
  
```
static LPCTSTR GetWndClassName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do ciągu zawierającego nazwę klasy okna, który może obsługiwać nonlicensed formantów ActiveX.  
  
##  <a name="operator_eq"></a>  CAxWindow::operator =  
 Przypisuje HWND do istniejącego `CAxWindow` obiektu.  
  
```
CAxWindow<TBase>& operator=(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *hWnd*  
 Dojście do istniejącego okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do bieżącego `CAxWindow` obiektu.  
  
##  <a name="querycontrol"></a>  CAxWindow::QueryControl  
 Pobiera określonego interfejsu obsługiwanego formantu.  
  
```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```  
  
### <a name="parameters"></a>Parametry  
 *IID*  
 [in] Określa identyfikator IID interfejsu formantu.  
  
 *ppUnk*  
 [out] Wskaźnik do interfejsu formantu. W wersji szablonu tej metody nie ma potrzeby dla Identyfikatora odwołania tak długo, jak wpisane interfejsu z skojarzony identyfikator UUID jest przekazywany.  
  
 *PYTANIA I ODPOWIEDZI*  
 [in] Interfejs, którego dotyczy zapytanie dla.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
##  <a name="queryhost"></a>  CAxWindow::QueryHost  
 Zwraca wartość określonego interfejsu hosta.  
  
```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```  
  
### <a name="parameters"></a>Parametry  
 *IID*  
 [in] Określa identyfikator IID interfejsu formantu.  
  
 *ppUnk*  
 [out] Wskaźnik do interfejsu na hoście. W wersji szablonu tej metody nie ma potrzeby dla Identyfikatora odwołania tak długo, jak wpisane interfejsu z skojarzony identyfikator UUID jest przekazywany.  
  
 *PYTANIA I ODPOWIEDZI*  
 [in] Interfejs, którego dotyczy zapytanie dla.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Interfejs hosta pozwala uzyskać dostęp do podstawowej funkcji hostingu okna Kod zaimplementowany przy `AxWin`.  
  
##  <a name="setexternaldispatch"></a>  CAxWindow::SetExternalDispatch  
 Ustawia interfejs ekspedycji zewnętrznego, dla `CAxWindow` obiektu.  
  
```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 *pDisp*  
 [in] Wskaźnik do `IDispatch` interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
##  <a name="setexternaluihandler"></a>  CAxWindow::SetExternalUIHandler  
 Zestawy zewnętrzne [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) interfejs na potrzeby `CAxWindow` obiektu.  
  
```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```  
  
### <a name="parameters"></a>Parametry  
 *pUIHandler*  
 [in] Wskaźnik do `IDocHostUIHandlerDispatch` interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Zewnętrzne `IDocHostUIHandlerDispatch` interfejs jest wykorzystywany przez formanty, które tworzą zapytania dotyczące witryny hosta dla `IDocHostUIHandlerDispatch` interfejsu. WebBrowser — formant jest jeden formant, który wykonuje to.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe ATLCON](../../visual-cpp-samples.md)   
 [Klasa CWindow](../../atl/reference/cwindow-class.md)   
 [Podstawy złożonych kontrolek](../../atl/atl-composite-control-fundamentals.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)   
 [Zawieranie kontrolek — często zadawane pytania](../../atl/atl-control-containment-faq.md)

