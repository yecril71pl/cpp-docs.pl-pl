---
title: Klasa CComCompositeControl
ms.date: 11/04/2016
f1_keywords:
- CComCompositeControl
- ATLCTL/ATL::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::AdviseSinkMap
- ATLCTL/ATL::CComCompositeControl::CalcExtent
- ATLCTL/ATL::CComCompositeControl::Create
- ATLCTL/ATL::CComCompositeControl::CreateControlWindow
- ATLCTL/ATL::CComCompositeControl::SetBackgroundColorFromAmbient
- ATLCTL/ATL::CComCompositeControl::m_hbrBackground
- ATLCTL/ATL::CComCompositeControl::m_hWndFocus
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
ms.openlocfilehash: 700a8047ab1fa9df85c8e6530eb3eed5f29bd3d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320804"
---
# <a name="ccomcompositecontrol-class"></a>Klasa CComCompositeControl

Ta klasa zawiera metody wymagane do zaimplementowania kontroli złożonej.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, pochodzące z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również z innych interfejsów, które mają być obsługiwane dla kontroli złożonej.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|Konstruktor.|
|[CComCompositeControl::~CComCompositeControl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Wywołanie tej metody, aby doradzić lub unadvise wszystkie formanty hostowane przez formant złożony.|
|[CComCompositeControl::CalcExtent](#calcextent)|Wywołanie tej metody, aby obliczyć rozmiar w jednostkach HIMETRIC zasobu okna dialogowego używanego do obsługi formantu złożonego.|
|[CComCompositeControl::Tworzenie](#create)|Ta metoda jest wywoływana, aby utworzyć okno formantu dla formantu złożonego.|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Wywołanie tej metody, aby utworzyć okno formantu i doradzić dowolny hostowany formant.|
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Wywołanie tej metody, aby ustawić kolor tła formantu złożonego przy użyciu koloru tła kontenera.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|Pędzel tła.|
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|Uchwyt okna, które obecnie ma fokus.|

## <a name="remarks"></a>Uwagi

Klasy uzyskane z `CComCompositeControl` klasy dziedziczą funkcjonalność formantu złożonego ActiveX. Formanty ActiveX `CComCompositeControl` pochodzące z są hostowane przez standardowe okno dialogowe. Te typy formantów są nazywane formantami złożonymi, ponieważ mogą obsługiwać inne formanty (natywne formanty systemu Windows i formanty ActiveX).

`CComCompositeControl`identyfikuje zasób okna dialogowego do użycia w tworzeniu formantu złożonego, wyszukując wyliczonym element członkowski danych w klasie podrzędnej. Identyfikator elementu członkowskiego tej klasy podrzędnej jest ustawiony na identyfikator zasobu zasób, który będzie używany jako okno formantu. Poniżej przedstawiono przykład elementu członkowskiego danych, `CComCompositeControl` który klasa pochodna powinna zawierać do identyfikowania zasobu okna dialogowego, który ma być używany w oknie formantu:

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
> Formanty złożone są zawsze okna formantów, chociaż mogą one zawierać formanty bez okien.

Formant zaimplementowany przez klasę pochodną `CComCompositeControl`ma wbudowane domyślne zachowanie tabulatora. Gdy formant odbiera fokus przez kartę do w aplikacji zawierającej, kolejno naciskając klawisz TAB spowoduje fokus do cyklicznego przechodzenia przez wszystkie formantów zawartych w formancie formantów kompozytowych, a następnie poza formantem złożonym i na następny element w kolejności tabulacji kontenera. Kolejność tabulatorów hostowanych formantów jest określana przez zasób okna dialogowego i określa kolejność tabulacji.

> [!NOTE]
> Aby akceleratory działały `CComCompositeControl`poprawnie z , konieczne jest załadowanie tabeli akceleratora podczas tworzenia formantu, przekazanie uchwytu i liczby akceleratorów z powrotem do [IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)i wreszcie zniszczenie tabeli po zwolnieniu formantu.

## <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`WinBase`

[Baza CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl (Kontrola CComControl)](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="ccomcompositecontroladvisesinkmap"></a><a name="advisesinkmap"></a>CComCompositeControl::AdviseSinkMap

Wywołanie tej metody, aby doradzić lub unadvise wszystkie formanty hostowane przez formant złożony.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parametry

*bAdvise*<br/>
Prawda, jeśli wszystkie kontrole mają być zalecane; w przeciwnym razie fałszywe.

### <a name="return-value"></a>Wartość zwracana

|||
|-|-|
|S_OK  |Wszystkie formanty na mapie ujścia zdarzeń zostały pomyślnie połączone lub odłączone od źródła zdarzeń.|
|E_fail  |Nie wszystkie formanty na mapie ujścia zdarzeń mogą być połączone lub odłączone od źródła zdarzeń pomyślnie.|
|E_pointer  |Ten błąd zwykle wskazuje na problem z wpisem na mapie ujścia zdarzeń formantu lub problem z argumentem szablonu używanym w klasie podstawowej `IDispEventImpl` lub. `IDispEventSimpleImpl`|
|CONNECT_E_ADVISELIMIT  |Punkt połączenia osiągnął już limit połączeń i nie może już akceptować.|
|CONNECT_E_CANNOTCONNECT  |Zlew nie obsługuje interfejsu wymaganego przez ten punkt połączenia.|
|CONNECT_E_NOCONNECTION  |Wartość pliku cookie nie reprezentuje prawidłowego połączenia. Ten błąd zwykle wskazuje na problem z wpisem na mapie ujścia zdarzeń formantu lub problem z argumentem szablonu używanym w klasie podstawowej `IDispEventImpl` lub. `IDispEventSimpleImpl`|

### <a name="remarks"></a>Uwagi

Podstawowa implementacja tej metody przeszukuje wpisy na mapie ujścia zdarzeń. Następnie zaleca lub unadvises punktów połączenia do obiektów COM opisane przez sink map zdarzeń sink wpisów ujścia. Ta metoda elementu członkowskiego opiera się również na fakcie, że klasa pochodna dziedziczy z jednego wystąpienia `IDispEventImpl` dla każdego formantu w mapie ujścia, który ma być zalecane lub nienadwisane.

## <a name="ccomcompositecontrolcalcextent"></a><a name="calcextent"></a>CComCompositeControl::CalcExtent

Wywołanie tej metody, aby obliczyć rozmiar w jednostkach HIMETRIC zasobu okna dialogowego używanego do obsługi formantu złożonego.

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Odwołanie do `SIZE` struktury, która ma być wypełniona tą metodą.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli formant jest obsługiwany przez okno dialogowe; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Rozmiar jest zwracany w parametrze *size.*

## <a name="ccomcompositecontrolcreate"></a><a name="create"></a>CComCompositeControl::Tworzenie

Ta metoda jest wywoływana, aby utworzyć okno formantu dla formantu złożonego.

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndRodziciek*<br/>
Dojście do okna nadrzędnego formantu.

*z o.o.*<br/>
Zarezerwowany.

*dwInitParam*<br/>
Dane, które mają być przekazywane do formantu podczas tworzenia formantu. Dane przekazywane jako *dwInitParam* pojawi się jako parametr LPARAM [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) komunikat, który zostanie wysłany do kontroli złożonej po jego utworzeniu.

### <a name="return-value"></a>Wartość zwracana

Uchwyt do nowo utworzonego okna dialogowego sterowania złożonego.

### <a name="remarks"></a>Uwagi

Ta metoda jest zwykle wywoływana podczas aktywacji w miejscu formantu.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl

Konstruktor.

```
CComCompositeControl();
```

### <a name="remarks"></a>Uwagi

Inicjuje [CComCompositeControl::m_hbrBackground](#m_hbrbackground) i [CComCompositeControl::m_hWndFocus](#m_hwndfocus) elementy członkowskie danych do wartości NULL.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="dtor"></a>CComCompositeControl::~CComCompositeControl

Destruktor.

```
~CComCompositeControl();
```

### <a name="remarks"></a>Uwagi

Usuwa obiekt tła, jeśli istnieje.

## <a name="ccomcompositecontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow

Wywołanie tej metody, aby utworzyć okno formantu i doradzić wszelkie hostowane formanty.

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>Parametry

*hWndRodziciek*<br/>
Dojście do okna nadrzędnego formantu.

*z o.o.*<br/>
Prostokąt położenia formantu złożonego we współrzędnych klienta względem *hWndParent*.

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do nowo utworzonego okna dialogowego sterowania złożonego.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [CComCompositeControl::Create](#create) i [CComCompositeControl::AdviseSinkMap](#advisesinkmap).

## <a name="ccomcompositecontrolm_hbrbackground"></a><a name="m_hbrbackground"></a>CComCompositeControl::m_hbrBackground

Pędzel tła.

```
HBRUSH m_hbrBackground;
```

## <a name="ccomcompositecontrolm_hwndfocus"></a><a name="m_hwndfocus"></a>CComCompositeControl::m_hWndFocus

Uchwyt okna, które obecnie ma fokus.

```
HWND m_hWndFocus;
```

## <a name="ccomcompositecontrolsetbackgroundcolorfromambient"></a><a name="setbackgroundcolorfromambient"></a>CComCompositeControl::SetBackgroundColorFromAmbient

Wywołanie tej metody, aby ustawić kolor tła formantu złożonego przy użyciu koloru tła kontenera.

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Podstawy kontroli złożonej](../../atl/atl-composite-control-fundamentals.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
