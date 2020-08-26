---
title: IAxWinHostWindow, interfejs
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindow
- ATLIFACE/ATL::IAxWinHostWindow
- ATLIFACE/ATL::AttachControl
- ATLIFACE/ATL::CreateControl
- ATLIFACE/ATL::CreateControlEx
- ATLIFACE/ATL::QueryControl
- ATLIFACE/ATL::SetExternalDispatch
- ATLIFACE/ATL::SetExternalUIHandler
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
ms.openlocfilehash: 44681b94e0bd1dfd757ebfa19f83074785dd95f5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833377"
---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow, interfejs

Ten interfejs zapewnia metody manipulowania kontrolką i jego obiektem hosta.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|Nazwa|Opis|
|-|-|
|[AttachControl](#attachcontrol)|Dołącza istniejący formant do obiektu hosta.|
|[Formant kontrolny](#createcontrol)|Tworzy formant i dołącza go do obiektu hosta.|
|[CreateControlEx](#createcontrolex)|Tworzy kontrolkę, dołącza ją do obiektu hosta i opcjonalnie konfiguruje procedurę obsługi zdarzeń.|
|[QueryControl](#querycontrol)|Zwraca wskaźnik interfejsu do kontrolki hostowanej.|
|[SetExternalDispatch](#setexternaldispatch)|Ustawia interfejs zewnętrzny `IDispatch` .|
|[SetExternalUIHandler](#setexternaluihandler)|Ustawia interfejs zewnętrzny `IDocHostUIHandlerDispatch` .|

## <a name="remarks"></a>Uwagi

Ten interfejs jest udostępniany przez obiekty obsługujące kontrolki ActiveX ATL. Wywołaj metody z tego interfejsu, aby utworzyć i/lub dołączyć kontrolkę do obiektu hosta, uzyskać interfejs z hostowanej kontrolki lub ustawić zewnętrzny dispinterface lub procedurę obsługi interfejsu użytkownika do użycia podczas hostowania przeglądarki sieci Web.

## <a name="requirements"></a>Wymagania

Definicja tego interfejsu jest dostępna jako IDL lub C++, jak pokazano poniżej.

|Typ definicji|Plik|
|---------------------|----------|
|IDL|ATLIFace. idl|
|C++|ATLIFace. h (również zawarte w ATLBase. h)|

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a> IAxWinHostWindow::AttachControl

Dołącza istniejący (i wcześniej zainicjowany) formant do obiektu hosta przy użyciu okna identyfikowanego przez *Właściwość HWND*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parametry

*pUnkControl*<br/>
podczas Wskaźnik do `IUnknown` interfejsu formantu, który ma zostać dołączony do obiektu hosta.

*Właściwość*<br/>
podczas Dojście do okna, które ma być używane na potrzeby hostingu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a> IAxWinHostWindow:: IsControl

Tworzy kontrolkę, inicjuje ją i hostuje w oknie identyfikowanym przez *Właściwość HWND*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parametry

*lpTricsData*<br/>
podczas Ciąg identyfikujący formant do utworzenia. Może to być identyfikator CLSID (musi zawierać nawiasy klamrowe), ProgID, URL lub nieprzetworzony kod HTML (poprzedzony przez **MSHTML:**).

*Właściwość*<br/>
podczas Dojście do okna, które ma być używane na potrzeby hostingu.

*pStream*<br/>
podczas Wskaźnik interfejsu dla strumienia zawierającego dane inicjujące dla kontrolki. Może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

To okno zostanie poddana podklasie obiektu hosta, który uwidacznia ten interfejs, tak aby komunikaty mogły być odzwierciedlone na kontrolce, a inne funkcje kontenera będą działać.

Wywołanie tej metody jest równoważne wywołaniu [IAxWinHostWindow:: CreateControlEx](#createcontrolex).

Aby utworzyć licencjonowany formant ActiveX, zobacz [IAxWinHostWindowLic::](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)iscontroling.

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a> IAxWinHostWindow::CreateControlEx

Tworzy formant ActiveX, inicjuje go i hostuje w określonym oknie, podobnie jak [IAxWinHostWindow:: IsControl](#createcontrol).

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

*lpTricsData*<br/>
podczas Ciąg identyfikujący formant do utworzenia. Może to być identyfikator CLSID (musi zawierać nawiasy klamrowe), ProgID, URL lub nieprzetworzony kod HTML (poprzedzony prefiksem **MSHTML:**).

*Właściwość*<br/>
podczas Dojście do okna, które ma być używane na potrzeby hostingu.

*pStream*<br/>
podczas Wskaźnik interfejsu dla strumienia zawierającego dane inicjujące dla kontrolki. Może mieć wartość NULL.

*ppUnk*<br/>
określoną Adres wskaźnika, który będzie otrzymywał `IUnknown` interfejs utworzonej kontrolki. Może mieć wartość NULL.

*riidAdvise*<br/>
podczas Identyfikator interfejsu interfejsu wychodzącego na zawartym obiekcie. Może być IID_NULL.

*punkAdvise*<br/>
podczas Wskaźnik do `IUnknown` interfejsu obiektu ujścia, który ma być połączony z punktem połączenia na zawartym obiekcie określonym przez `iidSink` .

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do `CreateControl` metody, `CreateControlEx` umożliwia również otrzymywanie wskaźnika interfejsu do nowo utworzonej kontrolki i Konfigurowanie ujścia zdarzeń do odbierania zdarzeń wyzwalanych przez formant.

Aby utworzyć licencjonowany formant ActiveX, zobacz [IAxWinHostWindowLic:: CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a> IAxWinHostWindow::QueryControl

Zwraca określony wskaźnik interfejsu dostarczony przez obsługiwaną kontrolę.

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
podczas Identyfikator interfejsu na żądanym formancie.

*ppvObject*<br/>
określoną Adres wskaźnika, który będzie otrzymywał określony interfejs utworzonej kontrolki.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a> IAxWinHostWindow::SetExternalDispatch

Ustawia zewnętrzny dispinterface, który jest dostępny dla zawartych kontrolek za pomocą metody [IDocHostUIHandlerDispatch:: getexternal](../../atl/reference/idochostuihandlerdispatch-interface.md) .

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
podczas Wskaźnik do `IDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a> IAxWinHostWindow::SetExternalUIHandler

Wywołaj tę funkcję, aby ustawić zewnętrzny interfejs [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) dla `CAxWindow` obiektu.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
podczas Wskaźnik do `IDocHostUIHandlerDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana przez kontrolki (takie jak kontrolka przeglądarki sieci Web), które wysyła zapytanie do lokacji hosta dla `IDocHostUIHandlerDispatch` interfejsu.

## <a name="see-also"></a>Zobacz też

[IAxWinAmbientDispatch, interfejs](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
