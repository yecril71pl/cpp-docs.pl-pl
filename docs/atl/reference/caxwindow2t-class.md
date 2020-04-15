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
ms.openlocfilehash: 14080b624132979df533135bc1eef108dc793398
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318696"
---
# <a name="caxwindow2t-class"></a>Klasa CAxWindow2T

Ta klasa udostępnia metody manipulowania oknem, w którym znajduje się formant ActiveX, a także obsługuje hosting licencjonowanych formantów ActiveX.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>Parametry

*Baza danych TBase*<br/>
Klasa, z `CAxWindowT` której pochodzi.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Konstruuje `CAxWindow2T` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAxWindow2T::Tworzenie](#create)|Tworzy okno hosta.|
|[CAxWindow2T::CreateControlLic](#createcontrollic)|Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie.|
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|Tworzy licencjonowany formant ActiveX, inicjuje go, hostuje go w określonym oknie i pobiera wskaźnik interfejsu (lub wskaźniki) z formantu.|
|[CAxWindow2T::Nazwa klasy GetWnd](#getwndclassname)|Metoda statyczna, która pobiera nazwę klasy okna.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAxWindow2T::operator =](#operator_eq)|Przypisuje HWND do istniejącego `CAxWindow2T` obiektu.|

## <a name="remarks"></a>Uwagi

`CAxWindow2T`udostępnia metody manipulowania oknem, w którym znajduje się formant ActiveX. `CAxWindow2T`posiada również obsługę hostingu licencjonowanych formantów ActiveX. Hosting jest dostarczany przez " **AtlAxWinLic80** `CAxWindow2T`", który jest zawinięty przez .

Klasa `CAxWindow2` jest implementowana jako specjalizacja `CAxWindow2T` klasy. Specjalizacja ta jest zadeklarowana jako:

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT`elementy są udokumentowane w obszarze [CAxWindow](../../atl/reference/caxwindow-class.md).

Zobacz [Hosting ActiveX Formanty przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla próbki, która używa członków tej klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="caxwindow2tcaxwindow2t"></a><a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T

Konstruuje `CAxWindow2T` obiekt.

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Dojście istniejącego okna.

## <a name="caxwindow2tcreate"></a><a name="create"></a>CAxWindow2T::Tworzenie

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

`CAxWindow2T::Create`wywołuje [CWindow::Create](../../atl/reference/cwindow-class.md#create) z parametrem LPCTSTR *lpstrWndClass* ustawionym na`AtlAxWinLic80`klasę okna, która zapewnia hosting sterowania ( ).

Zobacz `CWindow::Create` opis parametrów i zwracaną wartość.

**Uwaga** Jeśli 0 jest używana jako wartość dla *parametru MenuOrID,* musi być określona jako 0U (wartość domyślna), aby uniknąć błędu kompilatora.

### <a name="example"></a>Przykład

Zobacz [Hosting ActiveX Formanty przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla próbki, która używa `CAxWindow2T::Create`.

## <a name="caxwindow2tcreatecontrollic"></a><a name="createcontrollic"></a>CAxWindow2T::CreateControlLic

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

*klawisz bstrLicKey*<br/>
Klucz licencyjny formantu; NULL w przypadku tworzenia formantu bez licencji.

### <a name="remarks"></a>Uwagi

Zobacz [CAxWindow::CreateControl](../../atl/reference/caxwindow-class.md#createcontrol) opis pozostałych parametrów i zwracanej wartości.

### <a name="example"></a>Przykład

Zobacz [Hosting ActiveX Formanty przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla próbki, która używa `CAxWindow2T::CreateControlLic`.

## <a name="caxwindow2tcreatecontrollicex"></a><a name="createcontrollicex"></a>CAxWindow2T::CreateControlLicEx

Tworzy licencjonowany formant ActiveX, inicjuje go, hostuje go w określonym oknie i pobiera wskaźnik interfejsu (lub wskaźniki) z formantu.

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

*klawisz bstrLicKey*<br/>
Klucz licencyjny formantu; NULL w przypadku tworzenia formantu bez licencji.

### <a name="remarks"></a>Uwagi

Zobacz [CAxWindow::CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) opis pozostałych parametrów i zwracanej wartości.

### <a name="example"></a>Przykład

Zobacz [Hosting ActiveX Formanty przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla próbki, która używa `CAxWindow2T::CreateControlLicEx`.

## <a name="caxwindow2tgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow2T::Nazwa klasy GetWnd

Pobiera nazwę klasy okna.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu zawierającego nazwę klasy okna`AtlAxWinLic80`( ), który może obsługiwać licencjonowane i nielicencjonowane formanty ActiveX.

## <a name="caxwindow2toperator-"></a><a name="operator_eq"></a>CAxWindow2T::operator =

Przypisuje HWND do istniejącego `CAxWindow2T` obiektu.

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Dojście istniejącego okna.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Często zadawane pytania dotyczące hermetyzacji sterowania](../../atl/atl-control-containment-faq.md)
