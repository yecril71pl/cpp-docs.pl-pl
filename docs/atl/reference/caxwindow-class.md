---
title: Klasa CAxWindow
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
ms.openlocfilehash: 6f5c178090a970906209e41da9298be61a61c639
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927856"
---
# <a name="caxwindow-class"></a>Klasa CAxWindow

Ta klasa udostępnia metody manipulowania oknem obsługującym formant ActiveX.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAxWindow : public CWindow
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[AttachControl](#attachcontrol)|Dołącza istniejący formant ActiveX do `CAxWindow` obiektu.|
|[CAxWindow](#caxwindow)|Konstruuje `CAxWindow` obiekt.|
|[CreateControl](#createcontrol)|Tworzy formant ActiveX, inicjuje go i hostuje w `CAxWindow` oknie.|
|[CreateControlEx](#createcontrolex)|Tworzy kontrolkę ActiveX i Pobiera wskaźnik interfejsu (lub wskaźniki) z formantu.|
|[GetWndClassName](#getwndclassname)|Ruchom Pobiera wstępnie zdefiniowaną nazwę `CAxWindow` klasy obiektu.|
|[QueryControl](#querycontrol)|`IUnknown` Pobiera obsługiwaną kontrolkę ActiveX.|
|[QueryHost](#queryhost)|`IUnknown` Pobiera wskaźnik`CAxWindow` obiektu.|
|[SetExternalDispatch](#setexternaldispatch)|Ustawia zewnętrzny interfejs wysyłania używany przez `CAxWindow` obiekt.|
|[SetExternalUIHandler](#setexternaluihandler)|Ustawia zewnętrzny `IDocHostUIHandler` interfejs używany `CAxWindow` przez obiekt.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#operator_eq)|Przypisuje Właściwość HWND do istniejącego `CAxWindow` obiektu.|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia metody manipulowania oknem, które obsługuje kontrolkę ActiveX. Hosting jest dostarczany przez " **AtlAxWin80"** , który jest opakowany przez `CAxWindow`.

Klasa `CAxWindow` jest zaimplementowana jako specjalizacja `CAxWindowT` klasy. Ta specjalizacja jest zadeklarowana jako:

`typedef CAxWindowT<CWindow> CAxWindow;`

Jeśli trzeba zmienić klasę bazową, można użyć `CAxWindowT` i określić nową klasę bazową jako argument szablonu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

##  <a name="attachcontrol"></a>CAxWindow::AttachControl

Tworzy nowy obiekt hosta, jeśli jeszcze nie istnieje, i dołącza określony formant do hosta.

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
podczas Wskaźnik do `IUnknown` kontrolki.

*ppUnkContainer*<br/>
określoną Wskaźnik do `IUnknown` hosta `AxWin` (obiektu).

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Dołączenie obiektu sterującego musi być poprawnie zainicjowane przed `AttachControl`wywołaniem metody.

##  <a name="caxwindow"></a>CAxWindow::CAxWindow

Konstruuje `CAxWindow` Obiekt przy użyciu istniejącego uchwytu obiektu okna.

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
Uchwyt do istniejącego obiektu okna.

##  <a name="createcontrol"></a>CAxWindow:: IsControl

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

*lpszName*<br/>
Wskaźnik do ciągu, aby utworzyć kontrolkę. Muszą być sformatowane w jeden z następujących sposobów:

- Identyfikator ProgID, taki jak`"MSCAL.Calendar.7"`

- Identyfikator CLSID, taki jak`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adres URL, taki jak`"<https://www.microsoft.com>"`

- Odwołanie do aktywnego dokumentu, takiego jak`"file://\\\Documents\MyDoc.doc"`

- Fragment kodu HTML, taki jak`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musi poprzedzać fragment kodu HTML, aby został wyznaczył jako strumień MSHTML. Tylko identyfikatory ProgID i CLSID są obsługiwane na platformach Windows Mobile. Windows CE Platform osadzonych, innych niż Windows Mobile z obsługą usługi CE IE, obsługują wszystkie typy, w tym identyfikator ProgID, identyfikator CLSID, adres URL, odwołanie do aktywnego dokumentu oraz fragment kodu HTML.

*pStream*<br/>
podczas Wskaźnik do strumienia, który jest używany do inicjowania właściwości formantu. Może mieć wartość NULL.

*ppUnkContainer*<br/>
określoną Adres wskaźnika, który będzie otrzymywał `IUnknown` kontener. Może mieć wartość NULL.

*dwResID*<br/>
Identyfikator zasobu zasobu HTML. Formant WebBrowser zostanie utworzony i załadowany z określonym zasobem.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

W przypadku użycia drugiej wersji tej metody kontrolka HTML jest tworzona i powiązana z zasobem identyfikowanym przez *dwResID*.

Ta metoda daje ten sam wynik co wywołanie:

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

Aby utworzyć, zainicjować i hostować licencjonowany formant ActiveX, zobacz [CAxWindow2T::.](../../atl/reference/caxwindow2t-class.md#createcontrollic)

### <a name="example"></a>Przykład

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego `CreateControl`z programu.

##  <a name="createcontrolex"></a>CAxWindow::CreateControlEx

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

*lpszName*<br/>
Wskaźnik do ciągu, aby utworzyć kontrolkę. Muszą być sformatowane w jeden z następujących sposobów:

- Identyfikator ProgID, taki jak`"MSCAL.Calendar.7"`

- Identyfikator CLSID, taki jak`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adres URL, taki jak`"<https://www.microsoft.com>"`

- Odwołanie do aktywnego dokumentu, takiego jak`"file://\\\Documents\MyDoc.doc"`

- Fragment kodu HTML, taki jak`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musi poprzedzać fragment kodu HTML, aby został wyznaczył jako strumień MSHTML. Tylko identyfikatory ProgID i CLSID są obsługiwane na platformach Windows Mobile. Windows CE Platform osadzonych, innych niż Windows Mobile z obsługą usługi CE IE, obsługują wszystkie typy, w tym identyfikator ProgID, identyfikator CLSID, adres URL, odwołanie do aktywnego dokumentu oraz fragment kodu HTML.

*pStream*<br/>
podczas Wskaźnik do strumienia, który jest używany do inicjowania właściwości formantu. Może mieć wartość NULL.

*ppUnkContainer*<br/>
określoną Adres wskaźnika, który będzie otrzymywał `IUnknown` kontener. Może mieć wartość NULL.

*ppUnkControl*<br/>
określoną Adres wskaźnika, który będzie otrzymywał `IUnknown` formant. Może mieć wartość NULL.

*iidSink*<br/>
podczas Identyfikator interfejsu interfejsu wychodzącego na zawartym obiekcie. Może być IID_NULL.

*punkSink*<br/>
podczas Wskaźnik do `IUnknown` interfejsu obiektu ujścia, który ma być połączony z punktem połączenia w zawartym obiekcie określonym przez *iidSink*.

*dwResID*<br/>
podczas Identyfikator zasobu zasobu HTML. Formant WebBrowser zostanie utworzony i załadowany z określonym zasobem.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda jest podobna do [CAxWindow:: IsControl](#createcontrol), ale w przeciwieństwie do tej `CreateControlEx` metody, umożliwia również otrzymywanie wskaźnika interfejsu do nowo utworzonej kontrolki i Konfigurowanie ujścia zdarzeń do odbierania zdarzeń wyzwalanych przez formant.

Zobacz [CAxWindow2T:: CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) , aby utworzyć, zainicjować i hostować licencjonowany formant ActiveX.

### <a name="example"></a>Przykład

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego `CreateControlEx`z programu.

##  <a name="getwndclassname"></a>CAxWindow::GetWndClassName

Pobiera nazwę klasy okna.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu zawierającego nazwę klasy okna, która może hostować nielicencjonowane kontrolki ActiveX.

##  <a name="operator_eq"></a>CAxWindow:: operator =

Przypisuje Właściwość HWND do istniejącego `CAxWindow` obiektu.

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
Uchwyt do istniejącego okna.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do bieżącego `CAxWindow` obiektu.

##  <a name="querycontrol"></a>CAxWindow::QueryControl

Pobiera określony interfejs hostowanej kontroli.

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Określa identyfikator IID interfejsu formantu.

*ppUnk*<br/>
określoną Wskaźnik do interfejsu formantu. W wersji szablonu tej metody nie ma potrzeby o IDENTYFIKATORze odwołania, o ile jest przesyłany interfejs o określonym typie ze skojarzonym identyfikatorem UUID.

*PYTANIA*<br/>
podczas Interfejs, dla którego jest przeprowadzana kwerenda.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

##  <a name="queryhost"></a>CAxWindow::QueryHost

Zwraca określony interfejs hosta.

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Określa identyfikator IID interfejsu formantu.

*ppUnk*<br/>
określoną Wskaźnik do interfejsu na hoście. W wersji szablonu tej metody nie ma potrzeby o IDENTYFIKATORze odwołania, o ile jest przesyłany interfejs o określonym typie ze skojarzonym identyfikatorem UUID.

*PYTANIA*<br/>
podczas Interfejs, dla którego jest przeprowadzana kwerenda.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Interfejs hosta umożliwia dostęp do podstawowych funkcji kodu hostingu okna wdrożonych przez `AxWin`program.

##  <a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch

Ustawia zewnętrzny interfejs wysyłania dla `CAxWindow` obiektu.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
podczas Wskaźnik do `IDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

##  <a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler

Ustawia zewnętrzny interfejs [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) dla `CAxWindow` obiektu.

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>Parametry

*pUIHandler*<br/>
podczas Wskaźnik do `IDocHostUIHandlerDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Interfejs zewnętrzny `IDocHostUIHandlerDispatch` jest używany przez kontrolki, które wysyłają zapytania do lokacji hosta `IDocHostUIHandlerDispatch` dla interfejsu. Formant WebBrowser to jeden formant, który to robi.

## <a name="see-also"></a>Zobacz także

[Przykład ATLCON](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWindow](../../atl/reference/cwindow-class.md)<br/>
[Podstawy kontroli złożonej](../../atl/atl-composite-control-fundamentals.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Kontrolki zawierania — często zadawane pytania](../../atl/atl-control-containment-faq.md)
