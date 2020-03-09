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
ms.openlocfilehash: 0d5991dcbf79d1c2415594636a09908586d1dc2f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864753"
---
# <a name="caxwindow2t-class"></a>Klasa CAxWindow2T

Ta klasa udostępnia metody manipulowania oknem, które obsługuje kontrolkę ActiveX, a także obsługuje hostowanie kontrolek ActiveX licencjonowanych.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>Parametry

*TBase*<br/>
Klasa, z której `CAxWindowT` dziedziczy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Konstruuje obiekt `CAxWindow2T`.|

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
|[CAxWindow2T:: operator =](#operator_eq)|Przypisuje Właściwość HWND do istniejącego obiektu `CAxWindow2T`.|

## <a name="remarks"></a>Uwagi

`CAxWindow2T` udostępnia metody manipulowania oknem, które obsługuje kontrolkę ActiveX. `CAxWindow2T` również ma obsługę hostingu licencjonowanych kontrolek ActiveX. Hosting jest dostarczany przez " **AtlAxWinLic80**", który jest opakowany przez `CAxWindow2T`.

Klasa `CAxWindow2` jest implementowana jako specjalizacja klasy `CAxWindow2T`. Ta specjalizacja jest zadeklarowana jako:

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT` składowe są udokumentowane w obszarze [CAxWindow](../../atl/reference/caxwindow-class.md).

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu, który używa elementów członkowskich tej klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

##  <a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T

Konstruuje obiekt `CAxWindow2T`.

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
Uchwyt istniejącego okna.

##  <a name="create"></a>CAxWindow2T:: Create

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

`CAxWindow2T::Create` wywołania [CWindow:: Create](../../atl/reference/cwindow-class.md#create) z parametrem LPCTSTR *lpstrWndClass* ustawionym na klasę Window, która zapewnia hosting kontroli (`AtlAxWinLic80`).

Aby uzyskać opis parametrów i wartości zwracanej, zobacz `CWindow::Create`.

**Uwaga** Jeśli wartość jest równa 0, parametr *MenuOrID* musi być określony jako 0u (wartość domyślna), aby uniknąć błędu kompilatora.

### <a name="example"></a>Przykład

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego z `CAxWindow2T::Create`.

##  <a name="createcontrollic"></a>CAxWindow2T:: issterowane

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

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego z `CAxWindow2T::CreateControlLic`.

##  <a name="createcontrollicex"></a>CAxWindow2T::CreateControlLicEx

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

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego z `CAxWindow2T::CreateControlLicEx`.

##  <a name="getwndclassname"></a>CAxWindow2T::GetWndClassName

Pobiera nazwę klasy okna.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu zawierającego nazwę klasy okna (`AtlAxWinLic80`), która może hostować licencjonowane i nielicencjonowane kontrolki ActiveX.

##  <a name="operator_eq"></a>CAxWindow2T:: operator =

Przypisuje Właściwość HWND do istniejącego obiektu `CAxWindow2T`.

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
Uchwyt istniejącego okna.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Kontrolki zawierania — często zadawane pytania](../../atl/atl-control-containment-faq.md)
