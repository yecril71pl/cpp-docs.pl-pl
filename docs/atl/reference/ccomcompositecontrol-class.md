---
title: Klasa CComCompositeControl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5940461a16dcb86fbb062937fe7330c1b6e04f75
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021138"
---
# <a name="ccomcompositecontrol-class"></a>Klasa CComCompositeControl

Ta klasa dostarcza metody, o których trzeba do zaimplementowania kontrolek złożonych.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsów, które chcesz obsługiwać złożonej kontrolki.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|Konstruktor.|
|[CComCompositeControl:: ~ CComCompositeControl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Wywołaj tę metodę, aby przeprowadzić operację advise lub unadvise wszystkich kontrolek pracujących złożonego formantu.|
|[CComCompositeControl::CalcExtent](#calcextent)|Wywołaj tę metodę w celu obliczania rozmiaru w jednostkach HIMETRIC zasobu okna dialogowego używane do hostowania kontrolek złożonych.|
|[CComCompositeControl::Create](#create)|Ta metoda jest wywoływana, aby utworzyć okno kontrolki złożonej kontrolki.|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Wywołaj tę metodę, aby utworzyć okno Kontrola i doradztwa dowolnego obsługiwanego formantu.|
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Wywołaj tę metodę, aby ustawić kolor tła kontrolki złożonej za pomocą koloru tła kontenera.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|Pędzel tła.|
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|Uchwyt okna, który aktualnie ma fokus.|

## <a name="remarks"></a>Uwagi

Klasy pochodne klasy `CComCompositeControl` dziedziczą funkcje złożonego formantu ActiveX. Kontrolki ActiveX pochodną `CComCompositeControl` są hostowane przez standardowe okno dialogowe. Te rodzaje formantów są nazywane formanty złożone, ponieważ są w stanie hostują inne kontrolki (natywne kontrolki Windows i formantów ActiveX).

`CComCompositeControl` Umożliwia określenie zasobu okna dialogowego do użycia w celu utworzenia złożonego formantu, wyszukując element członkowski danych wyliczany klasy podrzędnej. Element członkowski IDD tej klasy podrzędnej jest ustawiony na identyfikator zasobu dla zasobu okna dialogowego, która będzie służyć jako okno formantu. Oto przykład składowej danych, która jest pochodną klasy `CComCompositeControl` może zawierać do identyfikacji zasobu okna dialogowego, które ma być używany dla formantu okna:

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
>  Formanty złożone są zawsze okna kontrolki, mimo że zawierają one od kontrolek bez okien.

Formant implementowany przez `CComCompositeControl`— Klasa pochodna zawiera tabulacji wbudowane zachowanie domyślne. Gdy formant uzyskuje fokus, jest tabulatorem zawierającego aplikację, kolejno naciśnięcie klawisza TAB spowoduje, że fokus na jest cyklom za pośrednictwem wszystkich kontrolek złożonych zawartych w nim formantów, a następnie poza złożonej kontrolki i do następnego elementu w kolejność tabulacji kontenera. Kolejność tabulacji kontrolek hostowana zależy od zasobu okna dialogowego i określa kolejność, w której tabulacji wystąpi.

> [!NOTE]
>  Aby akceleratorów działać prawidłowo z `CComCompositeControl`, należy go załadować tabeli akceleratora, jak formant zostanie utworzony, Przekaż dojścia i liczba akceleratorów do [IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo), i na koniec należy zniszczyć tabeli, po zwolnieniu formantu.

## <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="advisesinkmap"></a>  CComCompositeControl::AdviseSinkMap

Wywołaj tę metodę, aby przeprowadzić operację advise lub unadvise wszystkich kontrolek pracujących złożonego formantu.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parametry

*bAdvise*<br/>
Wartość true, jeśli wszystkie formanty, które mają zaleceniem; w przeciwnym razie wartość false.

### <a name="return-value"></a>Wartość zwracana

|||
|-|-|
|S_OK  |Wszystkie kontrolki w przypadku ujścia mapy zostały połączone lub pomyślnie Rozłączono z ich źródła zdarzeń.|
|E_FAIL  |Nie wszystkie kontrolki w przypadku ujścia mapy, które mogą zostać połączone lub pomyślnie Rozłączono z ich źródła zdarzeń.|
|E_POINTER  |Błąd ten zwykle wskazuje problem z wpisem na mapie obiektu sink zdarzenia formantu lub problem z argumentem szablonu, używanym w `IDispEventImpl` lub `IDispEventSimpleImpl` klasy bazowej.|
|CONNECT_E_ADVISELIMIT  |Punkt połączenia jest już osiągnął limit liczby połączeń i nie akceptuje żadnych innych.|
|CONNECT_E_CANNOTCONNECT  |Obiekt sink nie obsługuje interfejsu wymaganego przez ten punkt połączenia.|
|CONNECT_E_NOCONNECTION  |Wartość pliku cookie nie reprezentują prawidłowego połączenia. Błąd ten zwykle wskazuje problem z wpisem na mapie obiektu sink zdarzenia formantu lub problem z argumentem szablonu, używanym w `IDispEventImpl` lub `IDispEventSimpleImpl` klasy bazowej.|

### <a name="remarks"></a>Uwagi

Podstawowa implementacja tej metody przeszukuje wpisy w zdarzeniu mapy ujścia. Następnie z informacją o tym lub unadvises punkty połączeń do obiektów COM, opisanego przez wpisy ujścia mapy obiektu sink zdarzenia. Ta metoda elementu członkowskiego opiera się również na fakt, że klasa pochodna dziedziczy z jednego wystąpienia `IDispEventImpl` dla każdej kontrolki w mapie ujścia, który ma być zalecany lub unadvised.

##  <a name="calcextent"></a>  CComCompositeControl::CalcExtent

Wywołaj tę metodę w celu obliczania rozmiaru w jednostkach HIMETRIC zasobu okna dialogowego używane do hostowania kontrolek złożonych.

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Odwołanie do `SIZE` struktury do wypełnienia przez tę metodę.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli kontrolka jest hostowana przez okno dialogowe; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Rozmiar jest zwracany w *rozmiar* parametru.

##  <a name="create"></a>  CComCompositeControl::Create

Ta metoda jest wywoływana, aby utworzyć okno kontrolki złożonej kontrolki.

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Dojście do nadrzędnego okna kontrolki.

*rcPos*<br/>
Zastrzeżone.

*dwInitParam*<br/>
Dane mają być przekazane do formantu podczas tworzenia kontrolki. Dane przekazywane jako *dwInitParam* będzie wyświetlany jako wartość parametru LPARAM [/ / Złap](/windows/desktop/dlgbox/wm-initdialog) wiadomości, które zostanie wysłane do kontrolek złożonych, gdy powstaje.

### <a name="return-value"></a>Wartość zwracana

Uchwyt do nowo utworzonego złożonej kontrolki okna dialogowego.

### <a name="remarks"></a>Uwagi

Ta metoda jest zazwyczaj wywoływana podczas aktywacji w miejscu formantu.

##  <a name="ccomcompositecontrol"></a>  CComCompositeControl::CComCompositeControl

Konstruktor.

```
CComCompositeControl();
```

### <a name="remarks"></a>Uwagi

Inicjuje [CComCompositeControl::m_hbrBackground](#m_hbrbackground) i [CComCompositeControl::m_hWndFocus](#m_hwndfocus) elementów członkowskich danych o wartości NULL.

##  <a name="dtor"></a>  CComCompositeControl:: ~ CComCompositeControl

Destruktor.

```
~CComCompositeControl();
```

### <a name="remarks"></a>Uwagi

Usuwa obiekt tła, jeśli taki istnieje.

##  <a name="createcontrolwindow"></a>  CComCompositeControl::CreateControlWindow

Wywołaj tę metodę, aby utworzyć okno Kontrola i doradztwa kontrolkami hostowanej.

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
Dojście do nadrzędnego okna kontrolki.

*rcPos*<br/>
Pozycja prostokąta złożonego formantu w kliencie koordynuje względem *hWndParent*.

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do nowo utworzonego złożonej kontrolki okna dialogowego.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [CComCompositeControl::Create](#create) i [CComCompositeControl::AdviseSinkMap](#advisesinkmap).

##  <a name="m_hbrbackground"></a>  CComCompositeControl::m_hbrBackground

Pędzel tła.

```
HBRUSH m_hbrBackground;
```

##  <a name="m_hwndfocus"></a>  CComCompositeControl::m_hWndFocus

Uchwyt okna, który aktualnie ma fokus.

```
HWND m_hWndFocus;
```

##  <a name="setbackgroundcolorfromambient"></a>  CComCompositeControl::SetBackgroundColorFromAmbient

Wywołaj tę metodę, aby ustawić kolor tła kontrolki złożonej za pomocą koloru tła kontenera.

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Podstawy złożonych kontrolek](../../atl/atl-composite-control-fundamentals.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
