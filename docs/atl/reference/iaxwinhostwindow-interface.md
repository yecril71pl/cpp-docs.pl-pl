---
title: Interfejs IAxWinHostWindow | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAxWinHostWindow
- ATLIFACE/ATL::IAxWinHostWindow
- ATLIFACE/ATL::AttachControl
- ATLIFACE/ATL::CreateControl
- ATLIFACE/ATL::CreateControlEx
- ATLIFACE/ATL::QueryControl
- ATLIFACE/ATL::SetExternalDispatch
- ATLIFACE/ATL::SetExternalUIHandler
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1d0d41439748cd0ddbc981ecb1d74194d5fbd59
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="iaxwinhostwindow-interface"></a>Interfejs IAxWinHostWindow
Ten interfejs zawiera metody formantu i jego obiektu hosta.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
interface IAxWinHostWindow : IUnknown
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AttachControl](#attachcontrol)|Dołącza formant do obiektu hosta.|  
|[CreateControl](#createcontrol)|Tworzy kontrolkę i dołącza go do obiektu hosta.|  
|[CreateControlEx](#createcontrolex)|Tworzy kontrolkę, dołącza go do obiektu hosta i opcjonalnie Ustawia program obsługi zdarzeń.|  
|[QueryControl](#querycontrol)|Zwraca wskaźnik interfejsu do obsługiwanego formantu.|  
|[SetExternalDispatch](#setexternaldispatch)|Ustawia zewnętrznej `IDispatch` interfejsu.|  
|[SetExternalUIHandler](#setexternaluihandler)|Ustawia zewnętrznej `IDocHostUIHandlerDispatch` interfejsu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest udostępniany przez formant ActiveX w ATL hosting obiektów. Wywołanie metody tego interfejsu do utworzenia i/lub dołączanie formantu do obiektu hosta, można pobrać interfejsu za pomocą formantu hostowanej lub ustawić zewnętrznego dispinterface obsługi interfejsu użytkownika do użytku odnośnie do hostowania przeglądarki sieci Web.  
  
## <a name="requirements"></a>Wymagania  
 Definicja tego interfejsu jest dostępna jako IDL lub C++, jak pokazano poniżej.  
  
|Typ definicji|Plik|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (również zawarte w ATLBase.h)|  
  
##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl  
 Dołącza kontrolkę istniejących (i wcześniej zainicjowana) do obiektu hosta, za pomocą okna identyfikowane przez `hWnd`.  
  
```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkControl*  
 [in] Wskaźnik do **IUnknown** interfejsu formantu jest dołączony do obiektu hosta.  
  
 `hWnd`  
 [in] Dojście do okna używanego do hostowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl  
 Tworzy kontrolkę, inicjowane i znajduje się w oknie identyfikowane przez `hWnd`.  
  
```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```  
  
### <a name="parameters"></a>Parametry  
 `lpTricsData`  
 [in] Ciąg identyfikujący formantu do utworzenia. Może to być identyfikator CLSID (należy uwzględnić nawiasy), identyfikator ProgID, adres URL lub kod HTML (poprzedzony **MSHTML:**).  
  
 `hWnd`  
 [in] Dojście do okna używanego do hostowania.  
  
 `pStream`  
 [in] Wskaźnik interfejsu dla strumienia zawierające dane inicjowania dla formantu. Może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 To okno zostanie podklasy przez obiekt hosta Udostępnianie ten interfejs, dzięki czemu komunikaty mogą pojawiają się do formantu i inne funkcje kontenera będą działać.  
  
 Wywołanie tej metody jest odpowiednikiem wywołania [IAxWinHostWindow::CreateControlEx](#createcontrolex).  
  
 Aby utworzyć licencjonowanego formantu ActiveX, zobacz [IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).  
  
##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx  
 Tworzy formantu ActiveX, inicjowane i znajduje się w określonym okna, podobnie jak [IAxWinHostWindow::CreateControl](#createcontrol).  
  
```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```  
  
### <a name="parameters"></a>Parametry  
 `lpTricsData`  
 [in] Ciąg identyfikujący formantu do utworzenia. Może to być identyfikator CLSID (należy uwzględnić nawiasy), identyfikator ProgID, adres URL lub kod HTML (prefiksem **MSHTML:**).  
  
 `hWnd`  
 [in] Dojście do okna używanego do hostowania.  
  
 `pStream`  
 [in] Wskaźnik interfejsu dla strumienia zawierające dane inicjowania dla formantu. Może być **NULL**.  
  
 `ppUnk`  
 [out] Adres wskaźnika, który będzie otrzymywał **IUnknown** interfejsu utworzony formantu. Może być **NULL**.  
  
 *riidAdvise*  
 [in] Identyfikator interfejsu interfejs wychodzących w zawartego w nim obiektu. Może być **ma wartości IID_NULL**.  
  
 *punkAdvise*  
 [in] Wskaźnik do **IUnknown** interfejsu połączenia z punktem połączenia zawartych w niej obiektu określonego przez obiekt sink `iidSink`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 W odróżnieniu od `CreateControl` metody `CreateControlEx` umożliwia również otrzymywać wskaźnik interfejsu do sterowania nowo utworzony i skonfigurowany obiekt sink zdarzenia do odbierania zdarzenia wywoływane przez formant.  
  
 Aby utworzyć licencjonowanego formantu ActiveX, zobacz [IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).  
  
##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl  
 Zwraca wskaźnik określonego interfejsu podał obsługiwanego formantu.  
  
```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `riid`  
 [in] Identyfikator formantu żądanego interfejsu.  
  
 `ppvObject`  
 [out] Adres wskaźnika odbioru określonego interfejsu utworzony formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch  
 Ustawia dispinterface zewnętrznego, który jest dostępny do zawartych w niej formantów za pomocą [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) metody.  
  
```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisp`  
 [in] Wskaźnik do `IDispatch` interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler  
 Wywołanie tej funkcji, aby ustawić zewnętrznej [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) interfejs na potrzeby `CAxWindow` obiektu.  
  
```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisp`  
 [in] Wskaźnik do **IDocHostUIHandlerDispatch** interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest używana przez formanty (na przykład formant przeglądarki sieci Web), które zapytania witryny hosta dla `IDocHostUIHandlerDispatch` interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)   
 [CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)









