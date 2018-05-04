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
ms.openlocfilehash: 052e7ad2bfa8cc03c4eadd4926dbd84c4fd60223
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="caxwindow-class"></a>Klasa CAxWindow
Ta klasa dostarcza metody do manipulowania okna hostowania kontrolki ActiveX.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAxWindow : public CWindow
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AttachControl](#attachcontrol)|Dołącza do istniejącego formantu ActiveX `CAxWindow` obiektu.|  
|[CAxWindow](#caxwindow)|Konstruuje `CAxWindow` obiektu.|  
|[CreateControl](#createcontrol)|Tworzy formantu ActiveX, inicjowane i znajduje się on w `CAxWindow` okna.|  
|[CreateControlEx](#createcontrolex)|Tworzy kontrolkę ActiveX i pobiera wskaźnika interfejsu (lub wskaźniki) z formantu.|  
|[GetWndClassName](#getwndclassname)|(Statyczny) Pobiera nazwę klasy wstępnie zdefiniowanych `CAxWindow` obiektu.|  
|[QueryControl](#querycontrol)|Pobiera **IUnknown** hostowanej formantu ActiveX.|  
|[QueryHost](#queryhost)|Pobiera **IUnknown** wskaźnik `CAxWindow` obiektu.|  
|[SetExternalDispatch](#setexternaldispatch)|Ustawia interfejs wysyłania zewnętrzne używane przez `CAxWindow` obiektu.|  
|[SetExternalUIHandler](#setexternaluihandler)|Ustawia zewnętrznej **IDocHostUIHandler** interfejs używany przez `CAxWindow` obiektu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](#operator_eq)|Przypisuje **HWND** do istniejącej **CAxWindow** obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dostarcza metody do manipulowania okna obsługującego formantu ActiveX. Hosting są dostarczane przez " **AtlAxWin80"**, który jest opakowane przez `CAxWindow`.  
  
 Klasa `CAxWindow` jest zaimplementowany jako specjalizacji `CAxWindowT` klasy. Ta specjalizacja jest zadeklarowany jako:  
  
 `typedef CAxWindowT<CWindow> CAxWindow;`  
  
 Jeśli musisz zmienić klasy podstawowej, można użyć `CAxWindowT` i określ nowe klasy podstawowej jako argument szablonu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="attachcontrol"></a>  CAxWindow::AttachControl  
 Tworzy nowy obiekt hosta, jeżeli nie jest już obecny i dołącza określony formant do hosta.  
  
```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>Parametry  
 `pControl`  
 [in] Wskaźnik do **IUnknown** formantu.  
  
 `ppUnkContainer`  
 [out] Wskaźnik do **IUnknown** hosta ( **AxWin** obiektu).  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Dołączany obiekt formantu musi być poprawnie zainicjowana przed wywołaniem `AttachControl`.  
  
##  <a name="caxwindow"></a>  CAxWindow::CAxWindow  
 Konstruuje `CAxWindow` przy użyciu dojścia istniejącego obiektu okna.  
  
```
CAxWindow(HWND hWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
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
 `lpszName`  
 Wskaźnik do ciągu można utworzyć formantu. Musi być sformatowany w jednym z następujących sposobów:  
  
-   ProgID takie jak "MSCAL. Calendar.7 "  
  
-   Identyfikatora CLSID, takie jak "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adres URL, takie jak "http://www.microsoft.com"  
  
-   Odwołanie do aktywnego dokumentu, takie jak "file://\\\Documents\MyDoc.doc"  
  
-   Fragment kodu HTML, takie jak "MSHTML:\<HTML >\<treści > to jest wiersza tekstu\</BODY >\<polecenia >"  
  
    > [!NOTE]
    >  "MSHTML:" musi występować przed fragment kodu HTML, dzięki czemu jest wyznaczony jako strumień MSHTML. Tylko ProgID i CLSID są obsługiwane na platformach Windows Mobile. Platformy osadzonych systemu Windows CE, innym niż Windows Mobile z obsługą Obsługa CE IE wszystkie typy w tym ProgID, identyfikatora CLSID, adres URL, referencyjnych aktywny dokument i fragment kodu HTML.  
  
 `pStream`  
 [in] Wskaźnik do strumienia, który służy do inicjowania właściwości formantu. Może być **NULL**.  
  
 `ppUnkContainer`  
 [out] Adres wskaźnika, który będzie otrzymywał **IUnknown** kontenera. Może być **NULL**.  
  
 `dwResID`  
 Identyfikator zasobu zasobu HTML. Formant WebBrowser zostanie utworzone i załadowany z określonego zasobu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli druga wersja ta metoda jest używana, kontrolka HTML jest tworzony i powiązany z zasobu identyfikowanego przez `dwResID`.  
  
 Ta metoda umożliwia to samo co wywołanie:  
  
 [!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]  
  
 Zobacz [CAxWindow2T::CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) tworzenie, inicjowanie i hosta licencjonowanego formantu ActiveX.  
  
### <a name="example"></a>Przykład  
 Zobacz [Hosting AXHost za pomocą biblioteki ATL programu ActiveX formanty](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego z `CreateControl`.  
  
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
 `lpszName`  
 Wskaźnik do ciągu można utworzyć formantu. Musi być sformatowany w jednym z następujących sposobów:  
  
-   ProgID takie jak "MSCAL. Calendar.7 "  
  
-   Identyfikatora CLSID, takie jak "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adres URL, takie jak "http://www.microsoft.com"  
  
-   Odwołanie do aktywnego dokumentu, takie jak "file://\\\Documents\MyDoc.doc"  
  
-   Fragment kodu HTML, takie jak "MSHTML:\<HTML >\<treści > to jest wiersza tekstu\</BODY >\<polecenia >"  
  
    > [!NOTE]
    >  "MSHTML:" musi występować przed fragment kodu HTML, dzięki czemu jest wyznaczony jako strumień MSHTML. Tylko ProgID i CLSID są obsługiwane na platformach Windows Mobile. Platformy osadzonych systemu Windows CE, innym niż Windows Mobile z obsługą Obsługa CE IE wszystkie typy w tym ProgID, identyfikatora CLSID, adres URL, referencyjnych aktywny dokument i fragment kodu HTML.  
  
 `pStream`  
 [in] Wskaźnik do strumienia, który służy do inicjowania właściwości formantu. Może być **NULL**.  
  
 `ppUnkContainer`  
 [out] Adres wskaźnika, który będzie otrzymywał **IUnknown** kontenera. Może być **NULL**.  
  
 `ppUnkControl`  
 [out] Adres wskaźnika, który będzie otrzymywał **IUnknown** formantu. Może być **NULL**.  
  
 `iidSink`  
 [in] Identyfikator interfejsu interfejs wychodzących w zawartego w nim obiektu. Może być **ma wartości IID_NULL**.  
  
 *punkSink*  
 [in] Wskaźnik do **IUnknown** interfejsu połączenia z punktem połączenia zawartych w niej obiektu określonego przez obiekt sink `iidSink`.  
  
 `dwResID`  
 [in] Identyfikator zasobu zasobu HTML. Formant WebBrowser zostanie utworzone i załadowany z określonego zasobu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do [CAxWindow::CreateControl](#createcontrol), ale w przeciwieństwie do tej metody, `CreateControlEx` umożliwia również otrzymywać wskaźnik interfejsu do sterowania nowo utworzony i skonfigurowany obiekt sink zdarzenia do odbierania zdarzenia wywoływane przez formant.  
  
 Zobacz [CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) tworzenie, inicjowanie i hosta licencjonowanego formantu ActiveX.  
  
### <a name="example"></a>Przykład  
 Zobacz [Hosting AXHost za pomocą biblioteki ATL programu ActiveX formanty](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego z `CreateControlEx`.  
  
##  <a name="getwndclassname"></a>  CAxWindow::GetWndClassName  
 Pobiera nazwę klasy okna.  
  
```
static LPCTSTR GetWndClassName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do ciągu zawierającego nazwę klasy okna, który może obsługiwać nonlicensed formantów ActiveX.  
  
##  <a name="operator_eq"></a>  CAxWindow::operator =  
 Przypisuje `HWND` do istniejącej `CAxWindow` obiektu.  
  
```
CAxWindow<TBase>& operator=(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
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
 `iid`  
 [in] Określa identyfikator IID interfejsu formantu.  
  
 `ppUnk`  
 [out] Wskaźnik do interfejsu formantu. W wersji szablonu tej metody nie ma Identyfikatora odwołania nie jest konieczne, tak długo, jak typu interfejsu z skojarzony identyfikator UUID jest przekazywana.  
  
 `Q`  
 [in] Interfejs, którego dotyczy zapytanie dla.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="queryhost"></a>  CAxWindow::QueryHost  
 Zwraca interfejs określonego hosta.  
  
```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Określa identyfikator IID interfejsu formantu.  
  
 `ppUnk`  
 [out] Wskaźnik do interfejsu na hoście. W wersji szablonu tej metody nie ma Identyfikatora odwołania nie jest konieczne, tak długo, jak typu interfejsu z skojarzony identyfikator UUID jest przekazywana.  
  
 `Q`  
 [in] Interfejs, którego dotyczy zapytanie dla.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Interfejs hosta umożliwia dostęp do podstawowych funkcji hosting okna kodu implementowanych przez **AxWin**.  
  
##  <a name="setexternaldispatch"></a>  CAxWindow::SetExternalDispatch  
 Ustawia interfejs wysyłania zewnętrznych dla `CAxWindow` obiektu.  
  
```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisp`  
 [in] Wskaźnik do `IDispatch` interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="setexternaluihandler"></a>  CAxWindow::SetExternalUIHandler  
 Ustawia zewnętrznej [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) interfejs na potrzeby `CAxWindow` obiektu.  
  
```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```  
  
### <a name="parameters"></a>Parametry  
 *pUIHandler*  
 [in] Wskaźnik do **IDocHostUIHandlerDispatch** interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Zewnętrznej `IDocHostUIHandlerDispatch` interfejsu jest używany przez formanty, które zapytania witryny hosta dla `IDocHostUIHandlerDispatch` interfejsu. Formant WebBrowser jest to jeden formant.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe ATLCON](../../visual-cpp-samples.md)   
 [Klasa CWindow](../../atl/reference/cwindow-class.md)   
 [Podstawy złożonych kontrolek](../../atl/atl-composite-control-fundamentals.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Zawierania kontrolek — często zadawane pytania](../../atl/atl-control-containment-faq.md)

