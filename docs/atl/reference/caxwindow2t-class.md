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
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326520"
---
# <a name="caxwindow2t-class"></a>Klasa CAxWindow2T

Ta klasa dostarcza metody do manipulowania okno które obsługuje formant ActiveX, a także zapewnia obsługę licencjonowanych kontrolki hostingu ActiveX.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>Parametry

*Tpodstawowe*<br/>
Klasa, z której `CAxWindowT` pochodzi.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Konstruuje `CAxWindow2T` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAxWindow2T::Create](#create)|Tworzy okno z hosta.|
|[CAxWindow2T::CreateControlLic](#createcontrollic)|Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie.|
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie oraz pobiera wskaźnika interfejsu (lub wskaźniki) z formantu.|
|[CAxWindow2T::GetWndClassName](#getwndclassname)|Statyczna metoda, która pobiera nazwę klasy okna.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAxWindow2T::operator =](#operator_eq)|Przypisuje HWND do istniejącego `CAxWindow2T` obiektu.|

## <a name="remarks"></a>Uwagi

`CAxWindow2T` udostępnia metody do manipulowania oknem, który jest hostem formantu ActiveX. `CAxWindow2T` ma również obsługę hostowania licencjonowane formanty ActiveX. Hosting są dostarczane przez " **AtlAxWinLic80**", który jest otoczony przez `CAxWindow2T`.

Klasa `CAxWindow2` jest implementowany jako specjalizacji `CAxWindow2T` klasy. Ta specjalizacja jest zadeklarowany jako:

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT` elementy członkowskie są udokumentowane w obszarze [CAxWindow](../../atl/reference/caxwindow-class.md).

Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu, który używa elementy członkowskie tej klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="caxwindow2t"></a>  CAxWindow2T::CAxWindow2T

Konstruuje `CAxWindow2T` obiektu.

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Uchwyt istniejącego okna.

##  <a name="create"></a>  CAxWindow2T::Create

Tworzy okno z hosta.

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

`CAxWindow2T::Create` wywołania [CWindow::Create](../../atl/reference/cwindow-class.md#create) z LPCTSTR *lpstrWndClass* zestaw parametrów do klasy okna, który zapewnia hosting kontrolki (`AtlAxWinLic80`).

Zobacz `CWindow::Create` opis parametrów i wartości zwracanej.

**Uwaga** Jeśli 0 jest używany jako wartość *MenuOrID* parametru musi być określona jako 0U (wartość domyślna) w celu uniknięcia błędu kompilatora.

### <a name="example"></a>Przykład

Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu, który używa `CAxWindow2T::Create`.

##  <a name="createcontrollic"></a>  CAxWindow2T::CreateControlLic

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
Klucz licencji dla formantu; Wartość NULL, jeśli tworzenie nonlicensed kontrolki.

### <a name="remarks"></a>Uwagi

Zobacz [CAxWindow::CreateControl](../../atl/reference/caxwindow-class.md#createcontrol) opis pozostałych parametrów i zwracanej wartości.

### <a name="example"></a>Przykład

Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu, który używa `CAxWindow2T::CreateControlLic`.

##  <a name="createcontrollicex"></a>  CAxWindow2T::CreateControlLicEx

Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie oraz pobiera wskaźnika interfejsu (lub wskaźniki) z formantu.

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
Klucz licencji dla formantu; Wartość NULL, jeśli tworzenie nonlicensed kontrolki.

### <a name="remarks"></a>Uwagi

Zobacz [CAxWindow::CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) opis pozostałych parametrów i zwracanej wartości.

### <a name="example"></a>Przykład

Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu, który używa `CAxWindow2T::CreateControlLicEx`.

##  <a name="getwndclassname"></a>  CAxWindow2T::GetWndClassName

Pobiera nazwę klasy okna.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu zawierającego nazwę klasy okna (`AtlAxWinLic80`) który może hostować licencjonowany i objęty pomocą nonlicensed formantów ActiveX.

##  <a name="operator_eq"></a>  CAxWindow2T::operator =

Przypisuje HWND do istniejącego `CAxWindow2T` obiektu.

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Uchwyt istniejącego okna.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Zawieranie kontrolek — często zadawane pytania](../../atl/atl-control-containment-faq.md)
