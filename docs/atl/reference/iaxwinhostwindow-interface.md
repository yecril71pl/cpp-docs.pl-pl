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
ms.openlocfilehash: 8cf8c27d118984422ec3a78f442a3f11f13e1c75
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766035"
---
# <a name="iaxwinhostwindow-interface"></a>Interfejs IAxWinHostWindow

Ten interfejs zapewnia metody do manipulowania formantu i jego obiekt hosta.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[AttachControl](#attachcontrol)|Dołącza istniejącego formantu do obiektu hosta.|
|[CreateControl —](#createcontrol)|Tworzy formant i dołącza je do obiektu hosta.|
|[CreateControlEx](#createcontrolex)|Tworzy formant, a następnie dołącza je do obiektu hosta i opcjonalnie konfiguruje program obsługi zdarzeń.|
|[QueryControl](#querycontrol)|Zwraca wskaźnik interfejsu do obsługiwanego formantu.|
|[SetExternalDispatch](#setexternaldispatch)|Zestawy zewnętrzne `IDispatch` interfejsu.|
|[SetExternalUIHandler](#setexternaluihandler)|Zestawy zewnętrzne `IDocHostUIHandlerDispatch` interfejsu.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest udostępniany przez ActiveX hostingu formantu ATL, obiekty. W tym interfejsie, aby utworzyć i/lub dołączyć formantu do obiektu hosta, można pobrać interfejsu z obsługiwanego formantu lub ustawić dispinterface zewnętrznych lub obsługi interfejsu użytkownika do użycia w przypadku hostowania w przeglądarce sieci Web, należy wywołać metodę.

## <a name="requirements"></a>Wymagania

Definicja tego interfejsu jest dostępna jako IDL lub C++, jak pokazano poniżej.

|Typ definicji|Plik|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h (dołączone do dodatków ATLBase.h)|

##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl

Dołącza kontrolkę istniejących (i wcześniej zainicjowane) do obiektu hosta, za pomocą okna identyfikowane przez *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parametry

*pUnkControl*  
[in] Wskaźnik do `IUnknown` interfejsu formant mógł być dołączony do obiektu hosta.

*hWnd*  
[in] Dojście do okna, które ma być używany do hostowania.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl

Tworzy formant, inicjuje go i umieszcza w oknie identyfikowane przez *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parametry

*lpTricsData*  
[in] Ciąg identyfikujący formantu do utworzenia. Może być CLSID (musi zawierać nawiasów klamrowych), identyfikator ProgID, adres URL lub kod HTML (poprzedzony **MSHTML:**).

*hWnd*  
[in] Dojście do okna, które ma być używany do hostowania.

*pStream*  
[in] Wskaźnik interfejsu dla strumienia zawierający dane inicjowania dla formantu. Może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

To okno zostanie należy do podklasy przez obiekt hosta udostępnianie tego interfejsu, tak aby komunikaty mogą pojawiają się do kontrolki i inne funkcje kontenera będzie działać.

Wywołanie tej metody jest równoważne z wywoływaniem [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Aby utworzyć licencjonowany formant ActiveX, zobacz [IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx

Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie, podobnie jak [IAxWinHostWindow::CreateControl](#createcontrol).

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

*lpTricsData*  
[in] Ciąg identyfikujący formantu do utworzenia. Może być CLSID (musi zawierać nawiasów klamrowych), identyfikator ProgID, adres URL lub kod HTML (z prefiksem **MSHTML:**).

*hWnd*  
[in] Dojście do okna, które ma być używany do hostowania.

*pStream*  
[in] Wskaźnik interfejsu dla strumienia zawierający dane inicjowania dla formantu. Może mieć wartości NULL.

*ppUnk*  
[out] Adres wskaźnika, który będzie otrzymywał `IUnknown` interfejsu utworzony formant. Może mieć wartości NULL.

*riidAdvise*  
[in] Identyfikator interfejsu interfejsu wychodzącego w zawartego w nim obiektu. Może być wartością IID_NULL.

*punkAdvise*  
[in] Wskaźnik do `IUnknown` interfejs obiektu sink połączenia z punktem połączenia na przechowywany obiekt określony przez `iidSink`.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

W odróżnieniu od `CreateControl` metody `CreateControlEx` umożliwia również odbierać wskaźnika interfejsu do nowo utworzonego formantu i skonfigurować obiekt sink zdarzenia, aby odbierać zdarzenia wywoływane przez formant.

Aby utworzyć licencjonowany formant ActiveX, zobacz [IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl

Zwraca określony wskaźnik interfejsu dostarczone przez obsługiwanego formantu.

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Parametr riid*  
[in] Identyfikator kontrolki żądanego interfejsu.

*ppvObject*  
[out] Adres wskaźnika, który otrzyma określony interfejs utworzony formant.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch

Zestawy zewnętrzne dispinterface, która jest dostępna dla zawartych w nim formantów za pośrednictwem [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) metody.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*  
[in] Wskaźnik do `IDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler

Wywołaj tę funkcję, aby ustawić zewnętrzne [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) interfejs na potrzeby `CAxWindow` obiektu.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*  
[in] Wskaźnik do `IDocHostUIHandlerDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana przez formanty (na przykład formant przeglądarki sieci Web), które tworzą zapytania dotyczące witryny hosta dla `IDocHostUIHandlerDispatch` interfejsu.

## <a name="see-also"></a>Zobacz też

[Interfejs IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)   
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)

