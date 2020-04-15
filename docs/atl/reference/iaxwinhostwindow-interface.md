---
title: Interfejs IAxWinHostWindow
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
ms.openlocfilehash: ebecc611660a788ce59bb11beb95bd60eacaf01b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329997"
---
# <a name="iaxwinhostwindow-interface"></a>Interfejs IAxWinHostWindow

Ten interfejs zawiera metody manipulowania formantem i jego obiektem hosta.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Załączkontrolę](#attachcontrol)|Dołącza istniejący formant do obiektu hosta.|
|[CreateControl (Kontrola tworzenia)](#createcontrol)|Tworzy formant i dołącza go do obiektu hosta.|
|[UtwórzControlEx](#createcontrolex)|Tworzy formant, dołącza go do obiektu hosta i opcjonalnie konfiguruje program obsługi zdarzeń.|
|[Kontrola zapytania](#querycontrol)|Zwraca wskaźnik interfejsu do hostowanego formantu.|
|[SetExternalDispatch (Niewyrównanie)](#setexternaldispatch)|Ustawia interfejs `IDispatch` zewnętrzny.|
|[ZestawExternalUiHandler](#setexternaluihandler)|Ustawia interfejs `IDocHostUIHandlerDispatch` zewnętrzny.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest narażony przez obiekty hostingowe activex formantu ATL. Wywołanie metod w tym interfejsie, aby utworzyć i/lub dołączyć formant do obiektu hosta, aby uzyskać interfejs z hosta formantu lub ustawić zewnętrzny dispinterface lub obsługi interfejsu użytkownika do użycia podczas hostowania przeglądarki sieci Web.

## <a name="requirements"></a>Wymagania

Definicja tego interfejsu jest dostępna jako IDL lub C++, jak pokazano poniżej.

|Typ definicji|Plik|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (również w ATLBase.h)|

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHostWindow::AttachControl

Dołącza istniejący (i wcześniej zainicjowany) formant do obiektu hosta przy użyciu okna identyfikowanego przez *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parametry

*pUnkControl (Kontrola nie)*<br/>
[w] Wskaźnik do `IUnknown` interfejsu formantu, który ma być dołączony do obiektu hosta.

*Hwnd*<br/>
[w] Dojście do okna, które ma być używane do hostingu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHostWindow::CreateControl

Tworzy formant, inicjuje go i hostuje go w oknie identyfikowanym przez *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parametry

*lpTricsData*<br/>
[w] Ciąg identyfikujący formant do utworzenia. Może to być identyfikator CLSID (musi zawierać nawiasy klamrowe), progid, adres URL lub nieprzetworzony kod HTML (poprzedzony **mshtml:**).

*Hwnd*<br/>
[w] Dojście do okna, które ma być używane do hostingu.

*pStream (Strumień)*<br/>
[w] Wskaźnik interfejsu dla strumienia zawierającego dane inicjowania dla formantu. Może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

To okno będzie podklasyfikowane przez obiekt hosta ujawniający ten interfejs, dzięki czemu wiadomości mogą być odzwierciedlane do formantu i inne funkcje kontenera będą działać.

Wywołanie tej metody jest równoznaczne z [wywołaniem IAxWinHostWindow::CreateControlEx](#createcontrolex).

Aby utworzyć licencjonowany formant ActiveX, zobacz [IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx

Tworzy formant ActiveX, inicjuje go i obsługuje w określonym oknie, podobnie jak [IAxWinHostWindow::CreateControl](#createcontrol).

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
[w] Ciąg identyfikujący formant do utworzenia. Może to być identyfikator CLSID (musi zawierać nawiasy klamrowe), progid, adres URL lub nieprzetworzony kod HTML (poprzedzony **mshtml:**).

*Hwnd*<br/>
[w] Dojście do okna, które ma być używane do hostingu.

*pStream (Strumień)*<br/>
[w] Wskaźnik interfejsu dla strumienia zawierającego dane inicjowania dla formantu. Może mieć wartość NULL.

*ppUnk (polski)*<br/>
[na zewnątrz] Adres wskaźnika, który otrzyma `IUnknown` interfejs utworzonego formantu. Może mieć wartość NULL.

*riidAdvise*<br/>
[w] Identyfikator interfejsu wychodzącego interfejsu w contained object. Można IID_NULL.

*punkAdvise*<br/>
[w] Wskaźnik do `IUnknown` interfejsu obiektu ujścia, który ma być połączony z punktem połączenia na zawartym obiekcie określonym przez `iidSink`program .

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

W `CreateControl` przeciwieństwie `CreateControlEx` do metody, umożliwia również odbieranie wskaźnik interfejsu do nowo utworzonego formantu i skonfigurować ujście zdarzeń, aby odbierać zdarzenia uruchamiane przez formant.

Aby utworzyć licencjonowany formant ActiveX, zobacz [IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHostWindow::QueryControl

Zwraca określony wskaźnik interfejsu dostarczony przez kontrolę hosta.

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Riid*<br/>
[w] Identyfikator interfejsu na formancie, o który się prosi.

*ppvObiekt*<br/>
[na zewnątrz] Adres wskaźnika, który otrzyma określony interfejs utworzonego formantu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch

Ustawia zewnętrzny dispinterface, który jest dostępny do zawartych formantów za pośrednictwem [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) metody.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp (Niem.*<br/>
[w] Wskaźnik do `IDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUiHandler

Wywołanie tej funkcji, aby ustawić zewnętrzny interfejs [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) dla `CAxWindow` obiektu.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp (Niem.*<br/>
[w] Wskaźnik do `IDocHostUIHandlerDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana przez formanty (takie jak formant przeglądarki `IDocHostUIHandlerDispatch` sieci Web), które przeszukują witrynę hosta dla interfejsu.

## <a name="see-also"></a>Zobacz też

[Interfejs IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost (AtlAxGetHost)](composite-control-global-functions.md#atlaxgethost)
