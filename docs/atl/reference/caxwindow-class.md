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
ms.openlocfilehash: 6f5629370bc1f821dac0a08cc76b5df1450f7a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318721"
---
# <a name="caxwindow-class"></a>Klasa CAxWindow

Ta klasa zawiera metody manipulowania oknem hostingu ActiveX formantu.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAxWindow : public CWindow
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Załączkontrolę](#attachcontrol)|Dołącza do `CAxWindow` obiektu istniejący formant ActiveX.|
|[CAxWindow ( CAxWindow )](#caxwindow)|Konstruuje `CAxWindow` obiekt.|
|[CreateControl (Kontrola tworzenia)](#createcontrol)|Tworzy formant ActiveX, inicjuje go `CAxWindow` i hostuje go w oknie.|
|[UtwórzControlEx](#createcontrolex)|Tworzy formant ActiveX i pobiera wskaźnik interfejsu (lub wskaźniki) z formantu.|
|[Nazwa Klasy GetWnd](#getwndclassname)|(Statyczne) Pobiera wstępnie zdefiniowaną nazwę klasy `CAxWindow` obiektu.|
|[Kontrola zapytania](#querycontrol)|Pobiera `IUnknown` hostowany formant ActiveX.|
|[Host zapytania](#queryhost)|Pobiera `IUnknown` wskaźnik `CAxWindow` obiektu.|
|[SetExternalDispatch (Niewyrównanie)](#setexternaldispatch)|Ustawia zewnętrzny interfejs wysyłki `CAxWindow` używany przez obiekt.|
|[ZestawExternalUiHandler](#setexternaluihandler)|Ustawia interfejs `IDocHostUIHandler` zewnętrzny `CAxWindow` używany przez obiekt.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#operator_eq)|Przypisuje HWND do istniejącego `CAxWindow` obiektu.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera metody manipulowania oknem, w którym znajduje się formant ActiveX. Hosting jest dostarczany przez " **AtlAxWin80**", `CAxWindow`który jest zawinięty przez .

Klasa `CAxWindow` jest implementowana jako specjalizacja `CAxWindowT` klasy. Specjalizacja ta jest zadeklarowana jako:

`typedef CAxWindowT<CWindow> CAxWindow;`

Jeśli chcesz zmienić klasę podstawową, `CAxWindowT` można użyć i określić nową klasę podstawową jako argument szablonu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="caxwindowattachcontrol"></a><a name="attachcontrol"></a>CAxWindow::AttachControl

Tworzy nowy obiekt hosta, jeśli nie jest jeszcze obecny i dołącza określony formant do hosta.

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*pKontroluj*<br/>
[w] Wskaźnik do `IUnknown` formantu.

*PpUnkContainer*<br/>
[na zewnątrz] Wskaźnik do `IUnknown` hosta `AxWin` (obiektu).

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Dołączony obiekt sterujący musi zostać poprawnie `AttachControl`zainicjowany przed wywołaniem .

## <a name="caxwindowcaxwindow"></a><a name="caxwindow"></a>CAxWindow::CAxWindow

Konstruuje `CAxWindow` obiekt przy użyciu istniejącego uchwytu obiektu okna.

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Dojście do istniejącego obiektu okna.

## <a name="caxwindowcreatecontrol"></a><a name="createcontrol"></a>CAxWindow::CreateControl

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

*Lpszname*<br/>
Wskaźnik do ciągu, aby utworzyć formant. Musi być sformatowany w jeden z następujących sposobów:

- ProgID, taki jak`"MSCAL.Calendar.7"`

- ClSID, taki jak`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adres URL, taki jak`"<https://www.microsoft.com>"`

- Odwołanie do aktywnego dokumentu, takiego jak`"file://\\\Documents\MyDoc.doc"`

- Fragment html, taki jak`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musi poprzedzać fragment HTML, tak aby został wyznaczony jako strumień MSHTML. Tylko progid i CLSID są obsługiwane na platformach Windows Mobile. Platformy osadzone systemu Windows CE, inne niż Windows Mobile z obsługą CE IE obsługują wszystkie typy, w tym ProgID, CLSID, URL, odwołanie do aktywnego dokumentu i fragment html.

*pStream (Strumień)*<br/>
[w] Wskaźnik do strumienia, który jest używany do inicjowania właściwości formantu. Może mieć wartość NULL.

*PpUnkContainer*<br/>
[na zewnątrz] Adres wskaźnika, który otrzyma `IUnknown` kontenera. Może mieć wartość NULL.

*dwResID (700)*<br/>
Identyfikator zasobu HTML. WebBrowser formant zostanie utworzony i załadowany z określonego zasobu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli używana jest druga wersja tej metody, formant HTML jest tworzony i powiązanych z zasobem identyfikowanym przez *dwResID*.

Ta metoda daje taki sam wynik jak wywołanie:

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

Zobacz [CAxWindow2T::CreateControlLic,](../../atl/reference/caxwindow2t-class.md#createcontrollic) aby utworzyć, zainicjować i obsługiwać licencjonowany formant ActiveX.

### <a name="example"></a>Przykład

Zobacz [Hosting ActiveX Formanty przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla próbki, która używa `CreateControl`.

## <a name="caxwindowcreatecontrolex"></a><a name="createcontrolex"></a>CAxWindow::CreateControlEx

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

*Lpszname*<br/>
Wskaźnik do ciągu, aby utworzyć formant. Musi być sformatowany w jeden z następujących sposobów:

- ProgID, taki jak`"MSCAL.Calendar.7"`

- ClSID, taki jak`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adres URL, taki jak`"<https://www.microsoft.com>"`

- Odwołanie do aktywnego dokumentu, takiego jak`"file://\\\Documents\MyDoc.doc"`

- Fragment html, taki jak`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musi poprzedzać fragment HTML, tak aby został wyznaczony jako strumień MSHTML. Tylko progid i CLSID są obsługiwane na platformach Windows Mobile. Platformy osadzone systemu Windows CE, inne niż Windows Mobile z obsługą CE IE obsługują wszystkie typy, w tym ProgID, CLSID, URL, odwołanie do aktywnego dokumentu i fragment html.

*pStream (Strumień)*<br/>
[w] Wskaźnik do strumienia, który jest używany do inicjowania właściwości formantu. Może mieć wartość NULL.

*PpUnkContainer*<br/>
[na zewnątrz] Adres wskaźnika, który otrzyma `IUnknown` kontenera. Może mieć wartość NULL.

*kontrola ppUnkControl*<br/>
[na zewnątrz] Adres wskaźnika, który otrzyma `IUnknown` formantu. Może mieć wartość NULL.

*iidSink ( iidSink )*<br/>
[w] Identyfikator interfejsu wychodzącego interfejsu w contained object. Można IID_NULL.

*punkSink (polski)*<br/>
[w] Wskaźnik do `IUnknown` interfejsu obiektu ujścia, który ma być połączony z punktem połączenia na zawartym obiekcie określonym przez *iidSink*.

*dwResID (700)*<br/>
[w] Identyfikator zasobu HTML. WebBrowser formant zostanie utworzony i załadowany z określonego zasobu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda jest podobna do [CAxWindow::CreateControl](#createcontrol), ale w przeciwieństwie do tej metody, `CreateControlEx` umożliwia również odbieranie wskaźnika interfejsu do nowo utworzonego formantu i konfigurowanie ujścia zdarzeń do odbierania zdarzeń uruchamianych przez formant.

Zobacz [CAxWindow2T::CreateControlLicEx,](../../atl/reference/caxwindow2t-class.md#createcontrollicex) aby utworzyć, zainicjować i obsługiwać licencjonowany formant ActiveX.

### <a name="example"></a>Przykład

Zobacz [Hosting ActiveX Formanty przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla próbki, która używa `CreateControlEx`.

## <a name="caxwindowgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow::Nazwa klasy GetWnd

Pobiera nazwę klasy okna.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu zawierającego nazwę klasy okna, która może obsługiwać nielicencjonowane formanty ActiveX.

## <a name="caxwindowoperator-"></a><a name="operator_eq"></a>CAxWindow::operator =

Przypisuje HWND do istniejącego `CAxWindow` obiektu.

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Dojście do istniejącego okna.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do `CAxWindow` bieżącego obiektu.

## <a name="caxwindowquerycontrol"></a><a name="querycontrol"></a>CAxWindow::Sterowanie kwerendą

Pobiera określony interfejs hostowanego formantu.

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Określa identyfikator interfejsu formantu.

*ppUnk (polski)*<br/>
[na zewnątrz] Wskaźnik do interfejsu formantu. W wersji szablonu tej metody nie ma potrzeby identyfikatora odwołania tak długo, jak wpisany interfejs ze skojarzonym identyfikatorem UUID jest przekazywany.

*P*<br/>
[w] Interfejs, o który jest poszukiwany.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="caxwindowqueryhost"></a><a name="queryhost"></a>CAxWindow::QueryHost

Zwraca określony interfejs hosta.

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Określa identyfikator interfejsu formantu.

*ppUnk (polski)*<br/>
[na zewnątrz] Wskaźnik do interfejsu na hoście. W wersji szablonu tej metody nie ma potrzeby identyfikatora odwołania tak długo, jak wpisany interfejs ze skojarzonym identyfikatorem UUID jest przekazywany.

*P*<br/>
[w] Interfejs, o który jest poszukiwany.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Interfejs hosta umożliwia dostęp do podstawowej funkcjonalności kodu hostingu okien, zaimplementowanego przez `AxWin`.

## <a name="caxwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch

Ustawia zewnętrzny interfejs `CAxWindow` wysyłki dla obiektu.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp (Niem.*<br/>
[w] Wskaźnik do `IDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="caxwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler

Ustawia zewnętrzny interfejs [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) dla `CAxWindow` obiektu.

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>Parametry

*pUIHandler*<br/>
[w] Wskaźnik do `IDocHostUIHandlerDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Interfejs `IDocHostUIHandlerDispatch` zewnętrzny jest używany przez formanty, `IDocHostUIHandlerDispatch` które kwerendy witryny hosta dla interfejsu. WebBrowser formant jest jeden formant, który to robi.

## <a name="see-also"></a>Zobacz też

[Próbka ATLCON](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWindow](../../atl/reference/cwindow-class.md)<br/>
[Podstawy kontroli złożonej](../../atl/atl-composite-control-fundamentals.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Często zadawane pytania dotyczące hermetyzacji sterowania](../../atl/atl-control-containment-faq.md)
