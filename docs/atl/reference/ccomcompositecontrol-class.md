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
ms.openlocfilehash: b57eaf105bfca1a49d53b5e5e99969b0fa2fc82f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417909"
---
# <a name="ccomcompositecontrol-class"></a>Klasa CComCompositeControl

Ta klasa dostarcza metody wymagane do zaimplementowania formantu złożonego.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>Parametry

*&*<br/>
Klasa, pochodząca z [klasy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), a także z innych interfejsów, które mają być obsługiwane dla formantu złożonego.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|Konstruktor.|
|[CComCompositeControl:: ~ CComCompositeControl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Wywołaj tę metodę, aby zalecić lub wycofać wszystkie kontrolki hostowane przez formant złożony.|
|[CComCompositeControl::CalcExtent](#calcextent)|Wywołaj tę metodę, aby obliczyć rozmiar w jednostkach HIMETRIC zasobu okna dialogowego używanego do hostowania złożonego formantu.|
|[CComCompositeControl:: Create](#create)|Ta metoda jest wywoływana w celu utworzenia okna kontroli dla formantu złożonego.|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Wywołaj tę metodę, aby utworzyć okno kontroli i zalecić kontrolkę hostowaną.|
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Wywołaj tę metodę, aby ustawić kolor tła kontrolki złożonej przy użyciu koloru tła kontenera.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CComCompositeControl:: m_hbrBackground](#m_hbrbackground)|Pędzel w tle.|
|[CComCompositeControl:: m_hWndFocus](#m_hwndfocus)|Uchwyt okna, które aktualnie ma fokus.|

## <a name="remarks"></a>Uwagi

Klasy pochodne klasy `CComCompositeControl` dziedziczą funkcje kontrolki złożonej ActiveX. Kontrolki ActiveX pochodzące z `CComCompositeControl` są hostowane w standardowym oknie dialogowym. Te typy kontrolek są nazywane kontrolkami złożonymi, ponieważ mogą hostować inne kontrolki (natywne formanty systemu Windows i kontrolki ActiveX).

`CComCompositeControl` identyfikuje zasób okna dialogowego do użycia podczas tworzenia kontrolki złożonej przez wyszukanie wyliczanej składowej danych w klasie podrzędnej. Element członkowski IDD tej klasy podrzędnej jest ustawiany na identyfikator zasobu okna dialogowego, który będzie używany jako okno kontrolki. Poniżej znajduje się przykład elementu członkowskiego danych, który Klasa pochodna `CComCompositeControl` powinna zawierać, aby zidentyfikować zasób okna dialogowego, który ma być używany dla okna kontrolki:

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
>  Kontrolki złożone są zawsze kontrolkami okienkowymi, chociaż mogą zawierać kontrolki bez okien.

Kontrolka zaimplementowana przez klasę pochodną `CComCompositeControl`ma domyślnie wbudowane zachowanie tabulacji. Gdy kontrolka odbierze fokus przy użyciu tabulacji w aplikacji zawierającej, naciśnięcie klawisza TAB spowoduje, że fokus będzie przełączany przez wszystkie kontrolki zawarte w kontrolce złożonej, a następnie poza formant złożony i do następnego elementu w kolejność tabulacji w kontenerze. Kolejność tabulacji formantów hostowanych jest określana przez zasób okna dialogowego i określa kolejność, w której nastąpi tabulacja.

> [!NOTE]
>  Aby akceleratory działały prawidłowo z `CComCompositeControl`, konieczne jest załadowanie tabeli akceleratora w miarę tworzenia kontrolki, przekazanie uchwytu i liczby akceleratorów z powrotem do [IOleControlImpl:: GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo), a następnie zniszczenie tabeli po wydaniu formantu.

## <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

##  <a name="advisesinkmap"></a>CComCompositeControl::AdviseSinkMap

Wywołaj tę metodę, aby zalecić lub wycofać wszystkie kontrolki hostowane przez formant złożony.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parametry

*bAdvise*<br/>
Prawda, jeśli wszystkie kontrolki mają być zalecane; w przeciwnym razie false.

### <a name="return-value"></a>Wartość zwrócona

|||
|-|-|
|S_OK  |Wszystkie kontrolki w mapie ujścia zdarzeń zostały połączone lub odłączone pomyślnie ze źródłem zdarzenia.|
|E_FAIL  |Nie wszystkie formanty w mapie ujścia zdarzeń mogą być połączone lub odłączone pomyślnie od źródła zdarzenia.|
|E_POINTER  |Ten błąd zazwyczaj wskazuje na problem z wpisem w mapie ujścia zdarzeń kontrolki lub problemem z argumentem szablonu używanym w `IDispEventImpl` lub `IDispEventSimpleImpl` klasie bazowej.|
|CONNECT_E_ADVISELIMIT  |Punkt połączenia osiągnął już limit połączeń i nie może zaakceptować więcej.|
|CONNECT_E_CANNOTCONNECT  |Obiekt ujścia nie obsługuje interfejsu wymaganego przez ten punkt połączenia.|
|CONNECT_E_NOCONNECTION  |Wartość pliku cookie nie reprezentuje prawidłowego połączenia. Ten błąd zazwyczaj wskazuje na problem z wpisem w mapie ujścia zdarzeń kontrolki lub problemem z argumentem szablonu używanym w `IDispEventImpl` lub `IDispEventSimpleImpl` klasie bazowej.|

### <a name="remarks"></a>Uwagi

Podstawowa implementacja tej metody przeszukuje wpisy na mapie ujścia zdarzeń. Następnie doradza lub odradza punkty połączenia z obiektami COM opisanymi przez wpisy ujścia mapy ujścia zdarzeń. Ta metoda członkowska również polega na tym, że Klasa pochodna dziedziczy z jednego wystąpienia `IDispEventImpl` dla każdej kontrolki w mapie ujścia, która ma być zalecana lub niezalecana.

##  <a name="calcextent"></a>CComCompositeControl::CalcExtent

Wywołaj tę metodę, aby obliczyć rozmiar w jednostkach HIMETRIC zasobu okna dialogowego używanego do hostowania złożonego formantu.

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
Odwołanie do struktury `SIZE`, która ma zostać wypełniona przez tę metodę.

### <a name="return-value"></a>Wartość zwrócona

TRUE, Jeśli kontrolka jest hostowana przez okno dialogowe; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Rozmiar jest zwracany w parametrze *size* .

##  <a name="create"></a>CComCompositeControl:: Create

Ta metoda jest wywoływana w celu utworzenia okna kontroli dla formantu złożonego.

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Uchwyt do okna nadrzędnego formantu.

*rcPos*<br/>
Rezerwacj.

*dwInitParam*<br/>
Dane, które mają zostać przesłane do kontrolki podczas tworzenia kontrolki. Dane przekazywane jako *dwInitParam* będą wyświetlane jako parametr LPARAM komunikatu [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) , który zostanie wysłany do kontrolki złożonej, gdy zostanie utworzony.

### <a name="return-value"></a>Wartość zwrócona

Uchwyt do nowo utworzonego okna dialogowego formantu złożonego.

### <a name="remarks"></a>Uwagi

Ta metoda jest zwykle wywoływana podczas aktywacji w miejscu formantu.

##  <a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl

Konstruktor.

```
CComCompositeControl();
```

### <a name="remarks"></a>Uwagi

Inicjuje element członkowski danych [CComCompositeControl:: m_hbrBackground](#m_hbrbackground) i [CComCompositeControl:: m_hWndFocus](#m_hwndfocus) do wartości null.

##  <a name="dtor"></a>CComCompositeControl:: ~ CComCompositeControl

Destruktor.

```
~CComCompositeControl();
```

### <a name="remarks"></a>Uwagi

Usuwa obiekt tła (jeśli istnieje).

##  <a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow

Wywołaj tę metodę, aby utworzyć okno kontroli i zalecić kontrolki hostowane.

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Uchwyt do okna nadrzędnego formantu.

*rcPos*<br/>
Prostokąt położenia kontrolki złożonej w współrzędnej klienta względem *hWndParent*.

### <a name="return-value"></a>Wartość zwrócona

Zwraca uchwyt do nowo utworzonego okna dialogowego formantu złożonego.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [CComCompositeControl:: Create](#create) i [CComCompositeControl:: AdviseSinkMap](#advisesinkmap).

##  <a name="m_hbrbackground"></a>CComCompositeControl:: m_hbrBackground

Pędzel w tle.

```
HBRUSH m_hbrBackground;
```

##  <a name="m_hwndfocus"></a>CComCompositeControl:: m_hWndFocus

Uchwyt okna, które aktualnie ma fokus.

```
HWND m_hWndFocus;
```

##  <a name="setbackgroundcolorfromambient"></a>CComCompositeControl::SetBackgroundColorFromAmbient

Wywołaj tę metodę, aby ustawić kolor tła kontrolki złożonej przy użyciu koloru tła kontenera.

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Podstawy kontroli złożonej](../../atl/atl-composite-control-fundamentals.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
