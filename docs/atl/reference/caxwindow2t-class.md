---
title: Klasa CAxWindow2T
ms.date: 11/04/2016
f1_keywords:
- CAxWindow2T
- ATLWIN/ATL::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::Create
- ATLWIN/ATL::CAxWindow2T::CreateControlLic
- ATLWIN/ATL::CAxWindow2T::CreateControlLicEx
- ATLWIN/ATL::CAxWindow2T::GetWndClassName
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
ms.openlocfilehash: e29c30e95116ad68d3498f3f8d3231a63c92c0a7
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353067"
---
# <a name="caxwindow2t-class"></a>Klasa CAxWindow2T

Ta klasa udostępnia metody manipulowania oknem, które obsługuje kontrolkę ActiveX, a także obsługuje hostowanie kontrolek ActiveX licencjonowanych.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>Parametry

*TBase*<br/>
Klasa, z której `CAxWindowT` pochodzi.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Konstruuje `CAxWindow2T` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAxWindow2T:: Create](#create)|Tworzy okno hosta.|
|[CAxWindow2T:: issterowane](#createcontrollic)|Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie.|
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|Tworzy licencjonowany formant ActiveX, inicjuje go, hostuje w określonym oknie i Pobiera wskaźnik interfejsu (lub wskaźniki) z formantu.|
|[CAxWindow2T::GetWndClassName](#getwndclassname)|Metoda statyczna pobierająca nazwę klasy okna.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAxWindow2T:: operator =](#operator_eq)|Przypisuje Właściwość HWND do istniejącego `CAxWindow2T` obiektu.|

## <a name="remarks"></a>Uwagi

`CAxWindow2T` zapewnia metody manipulowania oknem, które obsługuje kontrolkę ActiveX. `CAxWindow2T` zapewnia również obsługę hostingu licencjonowanych kontrolek ActiveX. Hosting jest dostarczany przez " **AtlAxWinLic80**", który jest opakowany przez `CAxWindow2T` .

Klasa `CAxWindow2` jest zaimplementowana jako specjalizacja `CAxWindow2T` klasy. Ta specjalizacja jest zadeklarowana jako:

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT` elementy członkowskie są udokumentowane w [CAxWindow](../../atl/reference/caxwindow-class.md).

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) dla przykładu, który używa elementów członkowskich tej klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="caxwindow2tcaxwindow2t"></a><a name="caxwindow2t"></a> CAxWindow2T::CAxWindow2T

Konstruuje `CAxWindow2T` obiekt.

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
Uchwyt istniejącego okna.

## <a name="caxwindow2tcreate"></a><a name="create"></a> CAxWindow2T:: Create

Tworzy okno hosta.

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="remarks"></a>Uwagi

`CAxWindow2T::Create` wywołuje [CWindow:: Create](../../atl/reference/cwindow-class.md#create) z parametrem LPCTSTR *lpstrWndClass* ustawionym na klasę Window, która zapewnia hosting kontroli ( `AtlAxWinLic80` ).

Zobacz, `CWindow::Create` Aby uzyskać opis parametrów i zwracanej wartości.

**Uwaga** Jeśli wartość jest równa 0, parametr *MenuOrID* musi być określony jako 0u (wartość domyślna), aby uniknąć błędu kompilatora.

### <a name="example"></a>Przykład

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) dla przykładu korzystającego z programu `CAxWindow2T::Create` .

## <a name="caxwindow2tcreatecontrollic"></a><a name="createcontrollic"></a> CAxWindow2T:: issterowane

Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie.

```
HRESULT CreateControlLic(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);

HRESULT CreateControlLic(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);
```

### <a name="parameters"></a>Parametry

*bstrLicKey*<br/>
Klucz licencji dla kontrolki; Wartość NULL w przypadku tworzenia kontrolki nielicencjonowanej.

### <a name="remarks"></a>Uwagi

Aby uzyskać opis pozostałych parametrów i wartości zwracanej, zobacz [CAxWindow:: IsControl](../../atl/reference/caxwindow-class.md#createcontrol) .

### <a name="example"></a>Przykład

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) dla przykładu korzystającego z programu `CAxWindow2T::CreateControlLic` .

## <a name="caxwindow2tcreatecontrollicex"></a><a name="createcontrollicex"></a> CAxWindow2T::CreateControlLicEx

Tworzy licencjonowany formant ActiveX, inicjuje go, hostuje w określonym oknie i Pobiera wskaźnik interfejsu (lub wskaźniki) z formantu.

```
HRESULT CreateControlLicEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLicKey = NULL);

    HRESULT CreateControlLicEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLickey = NULL);
```

### <a name="parameters"></a>Parametry

*bstrLicKey*<br/>
Klucz licencji dla kontrolki; Wartość NULL w przypadku tworzenia kontrolki nielicencjonowanej.

### <a name="remarks"></a>Uwagi

Aby uzyskać opis pozostałych parametrów i wartości zwracanej, zobacz [CAxWindow:: CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) .

### <a name="example"></a>Przykład

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) dla przykładu korzystającego z programu `CAxWindow2T::CreateControlLicEx` .

## <a name="caxwindow2tgetwndclassname"></a><a name="getwndclassname"></a> CAxWindow2T::GetWndClassName

Pobiera nazwę klasy okna.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu zawierającego nazwę klasy okna ( `AtlAxWinLic80` ), która może hostować licencjonowane i nielicencjonowane kontrolki ActiveX.

## <a name="caxwindow2toperator-"></a><a name="operator_eq"></a> CAxWindow2T:: operator =

Przypisuje Właściwość HWND do istniejącego `CAxWindow2T` obiektu.

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
Uchwyt istniejącego okna.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Kontrolki zawierania — często zadawane pytania](../../atl/atl-control-containment-faq.md)
