---
title: Klasa CComObjectRootEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectRootEx
- ATLCOM/ATL::CComObjectRootEx
- ATLCOM/ATL::InternalAddRef
- ATLCOM/ATL::InternalRelease
- ATLCOM/ATL::Lock
- ATLCOM/ATL::Unlock
- ATLCOM/ATL::FinalConstruct
- ATLCOM/ATL::FinalRelease
- ATLCOM/ATL::OuterAddRef
- ATLCOM/ATL::OuterQueryInterface
- ATLCOM/ATL::OuterRelease
- ATLCOM/ATL::InternalQueryInterface
- ATLCOM/ATL::ObjectMain
- ATLCOM/ATL::m_dwRef
- ATLCOM/ATL::m_pOuterUnknown
dev_langs:
- C++
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b147f0ad3f1a54c2ae640b6bf2426bcddf060b35
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ccomobjectrootex-class"></a>Klasa CComObjectRootEx
Ta klasa dostarcza metody zarządzania liczba odwołanie do obiektu zarówno nieagregowane zagregowane obiekty i.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class ThreadModel>  
class CComObjectRootEx : public CComObjectRootBase
```  
  
#### <a name="parameters"></a>Parametry  
 `ThreadModel`  
 Klasa, której metody wdrożenia odpowiednie modelu wątkowości. Model wątkowy można wybrać jawnie przez ustawienie `ThreadModel` do [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), lub [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Możesz zaakceptować serwera domyślnego modelu wątku przez ustawienie `ThreadModel` do [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) lub [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).  

  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CComObjectRootEx](#ccomobjectrootex)|Konstruktor.|  
|[InternalAddRef](#internaladdref)|Zwiększa liczbę odwołania dla obiekt nieagregowane.|  
|[InternalRelease](#internalrelease)|Zmniejsza odwołania są liczone dla obiekt nieagregowane.|  
|[blokady](#lock)|Jeśli model wątków jest wielowątkowe, uzyskuje prawo własności obiektu sekcja krytyczna.|  
|[odblokowywanie](#unlock)|W przypadku wielowątkowe modelu wątku zwalnia prawo własności obiektu sekcja krytyczna.|  
  
### <a name="ccomobjectrootbase-methods"></a>Metody CComObjectRootBase  
  
|||  
|-|-|  
|[FinalConstruct](#finalconstruct)|Musi zostać zastąpiona w klasie w celu przeprowadzenia wszelkich inicjowania wymagane przez obiekt.|  
|[FinalRelease](#finalrelease)|Musi zostać zastąpiona w klasie do wykonania oczyszczania wymaganego przez obiekt.|  
|[OuterAddRef](#outeraddref)|Zwiększa liczbę odwołania dla obiekt zagregowanych.|  
|[OuterQueryInterface](#outerqueryinterface)|Obiekty delegowane do zewnętrznego **IUnknown** zagregowane obiektu.|  
|[OuterRelease](#outerrelease)|Zmniejsza odwołania są liczone dla obiekt zagregowanych.|  
  
### <a name="static-functions"></a>Funkcje statyczne  
  
|||  
|-|-|  
|[InternalQueryInterface](#internalqueryinterface)|Deleguje do **IUnknown** nieagregowane obiektu.|  
|[ObjectMain](#objectmain)|Wywoływane podczas inicjowania modułu i kończenie działania dla klasy pochodne mapy obiektu na liście.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_dwRef](#m_dwref)|Z `m_pOuterUnknown`, część Unii. Używany, gdy obiekt nie jest agregowany do przechowywania liczebności referencyjnej równej `AddRef` i **wersji**.|  
|[m_pOuterUnknown](#m_pouterunknown)|Z `m_dwRef`, część Unii. Używany, gdy obiekt jest agregowana na wskaźnik do nieznanego zewnętrzne.|  
  
## <a name="remarks"></a>Uwagi  
 `CComObjectRootEx` obsługuje zarządzanie liczba odwołanie do obiektu zarówno nieagregowane zagregowane obiekty i. Jeśli obiekt nie jest agregowana i przechowuje wskaźnik do nieznanego zewnętrzne, jeśli obiekt jest agregowana posiada liczebności referencyjnej obiektu. Zagregowane obiekty `CComObjectRootEx` metody może służyć do obsługi błędów wewnętrzny obiekt w celu utworzenia i ochrony obiektu zewnętrznego przed usunięciem po udostępnieniu wewnętrzny interfejsów lub wewnętrzny obiekt jest usunięty.  
  
 Klasa, która implementuje serwer COM musi dziedziczyć z `CComObjectRootEx` lub [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).  
  
 Jeśli definicja klasy Określa [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) makra ATL tworzy wystąpienie **CComPolyObject\<CYourClass >** podczas **IClassFactory:: CreateInstance** jest wywoływana. Podczas tworzenia zaznaczono wartość zewnętrzne nieznany. Jeśli jest **NULL**, **IUnknown** jest zaimplementowany dla obiekt nieagregowane. Jeśli nie jest zewnętrzna nieznany **NULL**, **IUnknown** jest zaimplementowany dla obiekt zagregowanych.  
  
 Jeśli nie określono klasy `DECLARE_POLY_AGGREGATABLE` makra ATL tworzy wystąpienie **CAggComObject\<CYourClass >** zagregowane obiektów lub wystąpienia **element CComObject\<CYourClass >** nieagregowane obiektów.  
  
 Zaletą używania `CComPolyObject` jest uniknąć oba mających `CComAggObject` i `CComObject` w module obsługi zagregowane i nieagregowane przypadkach. Pojedynczy `CComPolyObject` obiektu obsługuje w obu przypadkach. W związku z tym tylko jedną kopię vtable i jedną kopię funkcji istnieje w module. Jeśli Twoje vtable jest duży, to znacznie zmniejszyć rozmiar modułu użytkownika. Jednak jeśli Twoje vtable jest mały, za pomocą `CComPolyObject` może spowodować nieco większy rozmiar modułu, ponieważ nie jest zoptymalizowana dla obiekt zagregowane lub nieagregowane są `CComAggObject` i `CComObject`.  
  
 Jeśli obiekt jest agregowana, [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) jest implementowany przez `CComAggObject` lub `CComPolyObject`. Te klasy delegować `QueryInterface`, `AddRef`, i **wersji** wywołań `CComObjectRootEx`w `OuterQueryInterface`, `OuterAddRef`, i `OuterRelease` do przekazywania do zewnętrznego nieznany. Zazwyczaj można zastąpić `CComObjectRootEx::FinalConstruct` w klasie utworzyć zagregowane obiekty i zastępowania `CComObjectRootEx::FinalRelease` zwolnienia żadnego zagregowane obiekty.  
  
 Jeśli obiekt nie jest agregowany, **IUnknown** jest implementowany przez `CComObject` lub `CComPolyObject`. W takim przypadku wywołań `QueryInterface`, `AddRef`, i **wersji** mają delegowane do `CComObjectRootEx`w `InternalQueryInterface`, `InternalAddRef`, i `InternalRelease` do rzeczywistego operacji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="ccomobjectrootex"></a>  CComObjectRootEx::CComObjectRootEx  
 Konstruktor inicjuje liczebności referencyjnej równą 0.  
  
```
CComObjectRootEx();
```  
  
##  <a name="finalconstruct"></a>  CComObjectRootEx::FinalConstruct  
 Mogą przesłaniać tę metodę w klasie pochodnej przeprowadzić inicjowanie wymagane dla obiekt.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` powodzenie lub jednego z standardowy błąd `HRESULT` wartości.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `CComObjectRootEx::FinalConstruct` po prostu zwraca `S_OK`.  
  
 Istnieją korzyści z wykonywaniem inicjowania w `FinalConstruct` zamiast konstruktora klasy:  
  
-   Kod stanu nie może zwracać z konstruktorem, ale może zwrócić `HRESULT` za pomocą klasy `FinalConstruct`w zwracają wartość. Obiekty klasy są tworzone przy użyciu fabryki klasy standardowe podał ATL, zwrócona wartość jest propagowany do klienta COM, umożliwiając dostarczać szczegółowe informacje o błędzie.  
  
-   Nie można wywołać funkcji wirtualnych za pośrednictwem mechanizmu funkcji wirtualnej z konstruktora klasy. Wywoływanie funkcji wirtualnej z konstruktora klasy powoduje statycznie rozwiązywane wywołania funkcji, ponieważ jest on zdefiniowany w tym momencie w hierarchii dziedziczenia. Czystych funkcji wirtualnych powodować błędy konsolidatora.  
  
     Klasa nie jest najbardziej pochodnej klasy w hierarchii dziedziczenia — zależy od klasy pochodnej dostarczonych przez ATL zapewnienie niektórych jej funkcji. Istnieje szansa, że Twoje inicjowania należy wykorzystać funkcje oferowane przez tę klasę (dotyczy to oczywiście obiekty klasy muszą agregacji innych obiektów), ale Konstruktor w klasie nie ma możliwości dostęp do tych funkcji. Kod konstrukcji klasy jest wykonywany przed najdalszych pochodnych klas jest dokończony.  
  
     Jednak `FinalConstruct` jest wywoływana natychmiast po najbardziej pochodnej klasy jest dokończony umożliwia wywołanie funkcji wirtualnych i użyj liczenie odwołań w implementacji, dostarczone przez ATL.  
  
### <a name="example"></a>Przykład  
 Zazwyczaj należy przesłonić tę metodę w klasie pochodnej z `CComObjectRootEx` można utworzyć dowolne zagregowane obiektów. Na przykład:  
  
 [!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]  
  
 W przypadku niepowodzenia konstrukcji może zwrócić błąd. Można również użyć makra [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) do ochrony przed zewnętrznego obiektu usunięte, jeśli podczas tworzenia obiektu wewnętrznego zagregowane zwiększa liczbę odwołań, a następnie zmniejsza liczbę 0.  
  
 Oto typowy sposób tworzenia agregacji:  
  
-   Dodaj **IUnknown** wskaźnika do klasy i zainicjować go do **NULL** w konstruktorze.  
  
-   Zastąpienie `FinalConstruct` można utworzyć agregacji.  
  
-   Użyj **IUnknown** zdefiniowany jako parametr do wskaźnika [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) makra.  
  
-   Zastąpienie `FinalRelease` zwolnienia **IUnknown** wskaźnika.  
  
##  <a name="finalrelease"></a>  CComObjectRootEx::FinalRelease  
 Mogą przesłaniać tę metodę w klasie pochodnej, aby wykonać wszelkie Oczyszczanie wymagane dla obiekt.  
  
```
void FinalRelease();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `CComObjectRootEx::FinalRelease` nie działają.  
  
 Oczyszczać w `FinalRelease` lepiej jest dodawanie kodu do destruktora klasy, ponieważ nadal pełni konstruowania obiektu w momencie, w którym `FinalRelease` jest wywoływana. Dzięki temu można bezpiecznie uzyskać dostępu do metody dostarczone przez klasę najdalszych pochodnych. Jest to szczególnie ważne w przypadku zwalnianie zagregowane obiekty przed usunięciem.  
  
##  <a name="internaladdref"></a>  CComObjectRootEx::InternalAddRef  
 Zwiększa liczbę odwołanie do obiektu nieagregowane o 1.  
  
```
ULONG InternalAddRef();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która może być przydatne w przypadku diagnostyki i testowania.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli model wątków jest wielowątkowe, **InterlockedIncrement** jest używany, aby uniemożliwić zmianę liczbę odwołań w tym samym czasie więcej niż jeden wątek.  
  
##  <a name="internalqueryinterface"></a>  CComObjectRootEx::InternalQueryInterface  
 Pobiera wskaźnik do żądanego interfejsu.  
  
```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pThis`  
 [in] Wskaźnik do obiektu zawierającego interfejsów narażonych na mapie modelu COM `QueryInterface`.  
  
 `pEntries`  
 [in] Wskaźnik do **_ATL_INTMAP_ENTRY** struktury, który uzyskuje dostęp do map interfejsów dostępne.  
  
 `iid`  
 [in] Identyfikator GUID żądanego interfejsu.  
  
 `ppvObject`  
 [out] Wskaźnik do wskaźnika interfejsu określonego w `iid`, lub **NULL** Jeśli nie można odnaleźć interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
### <a name="remarks"></a>Uwagi  
 `InternalQueryInterface` Obsługuje tylko interfejsy COM tabeli mapy. Jeśli obiekt jest agregowana, `InternalQueryInterface` nie delegować do zewnętrznego nieznany. Interfejsy można wprowadzić do tabeli mapy COM z makra [com_interface_entry —](com-interface-entry-macros.md#com_interface_entry) lub jednej z jej wariantów.  
  
##  <a name="internalrelease"></a>  CComObjectRootEx::InternalRelease  
 Zmniejsza odwołanie liczba nieagregowane obiektu o 1.  
  
```
ULONG InternalRelease();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W obu bez debugowania i kompilacje debugowania, funkcja zwraca wartość, która może być przydatne w przypadku diagnostyki lub testowania. Dokładną wartość zwracana zależy od wielu czynników, takich jak system operacyjny używany i może lub nie mogą, licznik odwołania.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli model wątków jest wielowątkowe, **InterlockedDecrement** jest używany, aby uniemożliwić zmianę liczbę odwołań w tym samym czasie więcej niż jeden wątek.  
  
##  <a name="lock"></a>  CComObjectRootEx::Lock  
 W przypadku wielowątkowe modelu wątków, ta metoda wywołuje funkcji Win32 API [EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608), które czeka, aż wątku mogą przejąć prawo własności obiektu sekcja krytyczna uzyskanymi za pośrednictwem elementu członkowskiego danych prywatnych.  
  
```
void Lock();
```  
  
### <a name="remarks"></a>Uwagi  
 Po zakończeniu wykonywania kodu chronionych wątek należy wywołać `Unlock` zwolnienia własność sekcja krytyczna.  
  
 W przypadku modelu wątku jednowątkowego, ta metoda nie działa.  
  
##  <a name="m_dwref"></a>  CComObjectRootEx::m_dwRef  
 Część Unii, który uzyskuje dostęp do czterech bajtów pamięci.  
  
```
long m_dwRef;
```  
  
### <a name="remarks"></a>Uwagi  
 Z `m_pOuterUnknown`, część Unii:  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 Jeśli obiekt nie jest agregowany, liczba odwołań dostępu `AddRef` i **wersji** są przechowywane w `m_dwRef`. Jeśli obiekt jest agregowana, wskaźnik do nieznanego zewnętrzne są przechowywane w [m_pOuterUnknown](#m_pouterunknown).  
  
##  <a name="m_pouterunknown"></a>  CComObjectRootEx::m_pOuterUnknown  
 Część Unii, który uzyskuje dostęp do czterech bajtów pamięci.  
  
```
IUnknown*
    m_pOuterUnknown;
```     
  
### <a name="remarks"></a>Uwagi  
 Z `m_dwRef`, część Unii:  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 Jeśli obiekt jest agregowana, wskaźnik do nieznanego zewnętrzne są przechowywane w `m_pOuterUnknown`. Jeśli obiekt nie jest agregowany, liczba odwołań dostępu `AddRef` i **wersji** są przechowywane w [m_dwRef](#m_dwref).  
  
##  <a name="objectmain"></a>  CComObjectRootEx::ObjectMain  
 Dla każdej klasy na liście [mapy obiektu](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f), ta funkcja jest wywoływana, gdy po zainicjowaniu modułu i ponownie, gdy zostanie zakończony.  
  
```
static void WINAPI ObjectMain(bool bStarting);
```  
  
### <a name="parameters"></a>Parametry  
 `bStarting`  
 [out] Wartość jest **true** Jeśli klasa jest zainicjowana; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Wartość `bStarting` parametr wskazuje, czy moduł jest zainicjowana lub zakończenia. Domyślna implementacja `ObjectMain` nie działa, ale można przesłonić tę funkcję w klasie, aby zainicjować lub wyczyścić zasoby, które mają zostać przydzielone na klasie. Należy pamiętać, że `ObjectMain` jest wywoływana przed wymagane są wszystkie wystąpienia klasy.  
  
 `ObjectMain` jest wywoływana z punktu wejścia biblioteki dll, więc typ operacji, która może przeprowadzać funkcję punktu wejścia jest ograniczony. Aby uzyskać więcej informacji o tych ograniczeń, zobacz [biblioteki dll i Visual C++ zachowanie biblioteki wykonawczej](../../build/run-time-library-behavior.md) i [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]  
  
##  <a name="outeraddref"></a>  CComObjectRootEx::OuterAddRef  
 Zwiększa liczbę odwołanie zewnętrzne nieznany agregacji.  
  
```
ULONG OuterAddRef();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która może być przydatne w przypadku diagnostyki i testowania.  
  
##  <a name="outerqueryinterface"></a>  CComObjectRootEx::OuterQueryInterface  
 Pobiera pośredni wskaźnik do żądanego interfejsu.  
  
```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator GUID żądanego interfejsu.  
  
 `ppvObject`  
 [out] Wskaźnik do wskaźnika interfejsu określonego w `iid`, lub **NULL** Jeśli agregacja nie obsługuje interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
##  <a name="outerrelease"></a>  CComObjectRootEx::OuterRelease  
 Zmniejsza liczba odwołanie zewnętrzne nieznany agregacji.  
  
```
ULONG OuterRelease();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W kompilacjach do debugowania nie zawsze zwraca wartość 0. W kompilacjach debugowania zwraca wartość, która może być przydatne w przypadku diagnostyki lub testowania.  
  
##  <a name="unlock"></a>  CComObjectRootEx::Unlock  
 W przypadku wielowątkowe modelu wątków, ta metoda wywołuje funkcji Win32 API [LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169), które wersje prawo własności obiektu sekcja krytyczna uzyskanymi za pośrednictwem elementu członkowskiego danych prywatnych.  
  
```
void Unlock();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby otrzymać prawo własności, należy wywołać wątku `Lock`. Każde wywołanie `Lock` wymaga odpowiedniego wywołania `Unlock` zwolnienia własność sekcja krytyczna.  
  
 W przypadku modelu wątku jednowątkowego, ta metoda nie działa.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)   
 [Element CComObject — klasa](../../atl/reference/ccomobject-class.md)   
 [Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
