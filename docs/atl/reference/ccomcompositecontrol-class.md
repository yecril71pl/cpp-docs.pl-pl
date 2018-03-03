---
title: Klasa CComCompositeControl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2308c2c8da67a7d6fe048f3e498e6d7ba1e3cad6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcompositecontrol-class"></a>Klasa CComCompositeControl
Ta klasa udostępnia metody wymagane do wykonania formantu złożonego.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Pochodne klasy, [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsów mają być obsługiwane dla formantu złożonego.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|Konstruktor.|  
|[CComCompositeControl:: ~ CComCompositeControl](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Wywołaj tę metodę w celu poinformowania lub unadvise wszystkich kontrolek formantu złożonego na użytek.|  
|[CComCompositeControl::CalcExtent](#calcextent)|Wywołanie tej metody można obliczyć rozmiaru w **HIMETRIC** jednostki zasobu okna dialogowego używany do obsługi złożonych kontrolek.|  
|[CComCompositeControl::Create](#create)|Ta metoda jest wywoływana w celu utworzenia okna formantu złożonego formantu.|  
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Wywołaj tę metodę, aby utworzyć okno kontrolki i służyć poradą dowolnego obsługiwanego formantu.|  
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Wywołaj tę metodę, aby ustawić kolor tła formantu złożonego za pomocą kontenera kolor tła.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|Pędzel tła.|  
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|Uchwyt okna, który aktualnie ma fokus.|  
  
## <a name="remarks"></a>Uwagi  
 Klasy pochodne klasy `CComCompositeControl` dziedziczyć funkcje złożonego formantu ActiveX. Kontrolki ActiveX pochodną `CComCompositeControl` są obsługiwane przez standardowe okno dialogowe. Typy formantów są nazywane formanty złożone, ponieważ są w stanie obsługiwać inne formanty (native formantów systemu Windows i formantów ActiveX).  
  
 `CComCompositeControl`Określa zasób okna dialogowego do użycia w tworzenie formantu złożonego, wyszukując element członkowski wyliczenia danych klasy podrzędnej. Element członkowski IDD tej klasy podrzędnej jest ustawiony na identyfikator zasobu zasobu okna dialogowego, która będzie służyć jako okno formantu. Poniżej przedstawiono przykład elementu członkowskiego danych, która jest pochodną klasy `CComCompositeControl` powinien zawierać do identyfikacji zasobu okna dialogowego do użycia dla formantu okna:  
  
 [!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]  
  
> [!NOTE]
>  Formanty złożone są zawsze okna kontrolki, jednak zawierają one kontrolek bez okien.  
  
 Implementowany przez formant `CComCompositeControl`— Klasa pochodna ma domyślne klawisza TAB wbudowane zachowania. Gdy formant uzyskuje fokus przez trwa kartach do aplikacji zawierającego, kolejno naciśnięcie klawisza TAB spowoduje fokus się ponownym wszystkich zawartych w niej formantów złożonych kontrolek, a następnie poza złożonych kontrolek i do następnego elementu kolejność tabulacji kontenera. Kolejność tabulacji hostowanej formantów jest określana przez zasób okna dialogowego i określa kolejność, w których tabulacji zostanie przeprowadzona.  
  
> [!NOTE]
>  Aby akceleratorów do poprawnego działania z `CComCompositeControl`, należy załadować tabeli akceleratora, jako formant nie zostanie utworzony, przekazywać dojścia i liczba akceleratorów do [IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo), i na koniec zniszczyć tabeli po zwolnieniu formantu.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 [CComControl](../../atl/reference/ccomcontrol-class.md)  
  
 `CComCompositeControl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="advisesinkmap"></a>CComCompositeControl::AdviseSinkMap  
 Wywołaj tę metodę w celu poinformowania lub unadvise wszystkich kontrolek formantu złożonego na użytek.  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>Parametry  
 `bAdvise`  
 Wartość true, jeśli wszystkie formanty mają zaleceniem; w przeciwnym razie wartość false.  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`  
 Wszystkie formanty w przypadku mapy zbiornika zostały połączone lub rozłączone z ich źródłem zdarzeń pomyślnie.  
  
 **E_FAIL**  
 Nie wszystkie formanty, w przypadku mapy zbiornika może być połączone lub rozłączone z ich źródłem zdarzeń pomyślnie.  
  
 `E_POINTER`  
 Błąd ten zwykle wskazuje na problem z wpis w mapie obiekt sink zdarzenia formantu lub problem z argumentem szablonu używany w `IDispEventImpl` lub `IDispEventSimpleImpl` klasy podstawowej.  
  
 **CONNECT_E_ADVISELIMIT**  
 Punkt połączenia już osiągnęła limit połączeń i nie akceptuje kolejne.  
  
 **CONNECT_E_CANNOTCONNECT**  
 Obiekt sink nie obsługuje interfejsu wymaganego przez ten punkt połączenia.  
  
 **CONNECT_E_NOCONNECTION**  
 Wartość pliku cookie nie reprezentują prawidłowego połączenia. Błąd ten zwykle wskazuje na problem z wpis w mapie obiekt sink zdarzenia formantu lub problem z argumentem szablonu używany w `IDispEventImpl` lub `IDispEventSimpleImpl` klasy podstawowej.  
  
### <a name="remarks"></a>Uwagi  
 Podstawowa implementacja tej metody przeszuka wpisy zdarzeń zbiornika mapy. Następnie zaleceniem lub unadvises punkty połączenia do obiektów COM opisanego przez wpisy zbiornika mapy obiekt sink zdarzenia. Ta metoda elementu członkowskiego również jest oparta na fakt, że klasa pochodna dziedziczy z jednego wystąpienia `IDispEventImpl` dla każdego formantu w mapie zbiornika, który ma być zaleca lub unadvised.  
  
##  <a name="calcextent"></a>CComCompositeControl::CalcExtent  
 Wywołanie tej metody można obliczyć rozmiaru w **HIMETRIC** jednostki zasobu okna dialogowego używany do obsługi złożonych kontrolek.  
  
```
BOOL CalcExtent(SIZE& size);
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Odwołanie do **rozmiar** struktury zostać wypełnione przez tę metodę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli kontrolka jest hostowana przez okno dialogowe; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar jest zwracany w `size` parametru.  
  
##  <a name="create"></a>CComCompositeControl::Create  
 Ta metoda jest wywoływana w celu utworzenia okna formantu złożonego formantu.  
  
```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 Dojście do nadrzędnego okna formantu.  
  
 `rcPos`  
 Zastrzeżone.  
  
 `dwInitParam`  
 Dane do przekazania do formantu podczas tworzenia formantu. Dane przekazywane jako `dwInitParam` będzie wyświetlany jako **LPARAM** parametr [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) wiadomości, które zostanie wysłane do formantu złożonego pobiera tworzona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do okna dialogowego formantu złożonego za nowo utworzony.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest zazwyczaj wywoływana podczas aktywacji w miejscu formantu.  
  
##  <a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl  
 Konstruktor.  
  
```
CComCompositeControl();
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje [CComCompositeControl::m_hbrBackground](#m_hbrbackground) i [CComCompositeControl::m_hWndFocus](#m_hwndfocus) elementy członkowskie danych na wartość NULL.  
  
##  <a name="dtor"></a>CComCompositeControl:: ~ CComCompositeControl  
 Destruktor.  
  
```
~CComCompositeControl();
```  
  
### <a name="remarks"></a>Uwagi  
 Usuwa obiekt tła, jeśli istnieje.  
  
##  <a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow  
 Wywołaj tę metodę, aby utworzyć okno kontrolki i służyć poradą wszystkie formanty hostowanej.  
  
```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 Dojście do nadrzędnego okna formantu.  
  
 `rcPos`  
 Pozycja prostokąta złożonego formantu w kliencie koordynuje względem `hWndParent`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście do okna dialogowego formantu złożonego za nowo utworzony.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [CComCompositeControl::Create](#create) i [CComCompositeControl::AdviseSinkMap](#advisesinkmap).  
  
##  <a name="m_hbrbackground"></a>CComCompositeControl::m_hbrBackground  
 Pędzel tła.  
  
```
HBRUSH m_hbrBackground;
```  
  
##  <a name="m_hwndfocus"></a>CComCompositeControl::m_hWndFocus  
 Uchwyt okna, który aktualnie ma fokus.  
  
```
HWND m_hWndFocus;
```  
  
##  <a name="setbackgroundcolorfromambient"></a>CComCompositeControl::SetBackgroundColorFromAmbient  
 Wywołaj tę metodę, aby ustawić kolor tła formantu złożonego za pomocą kontenera kolor tła.  
  
```
HRESULT SetBackgroundColorFromAmbient();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Podstawy złożonych kontrolek](../../atl/atl-composite-control-fundamentals.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
