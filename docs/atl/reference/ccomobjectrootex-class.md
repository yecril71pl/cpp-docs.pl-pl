---
title: Klasa CComObjectRootEx
ms.date: 11/04/2016
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
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
ms.openlocfilehash: 8fa4e7a035ded2e1a20dd278a5d54d40252e1958
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862613"
---
# <a name="ccomobjectrootex-class"></a>Klasa CComObjectRootEx

Ta klasa dostarcza metody do obsługi zarządzania licznikami odwołań do obiektów zarówno dla obiektów niezagregowanych, jak i agregowanych.

## <a name="syntax"></a>Składnia

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>Parametry

*ThreadModel*<br/>
Klasa, której metody implementują żądany model wątkowości. Można jawnie wybrać model wątkowości, ustawiając *ThreadModel* na [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)lub [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Domyślny model wątku serwera można zaakceptować, ustawiając *ThreadModel* na [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) lub [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|Konstruktor.|
|[InternalAddRef —](#internaladdref)|Zwiększa liczbę odwołań dla niezagregowanego obiektu.|
|[InternalRelease —](#internalrelease)|Zmniejsza liczbę odwołań dla niezagregowanego obiektu.|
|[Skręt](#lock)|Jeśli model wątku jest wielowątkowy, uzyskuje własność obiektu sekcji krytycznej.|
|[Odblokowania](#unlock)|Jeśli model wątku jest wielowątkowy, zwalnia własność obiektu sekcji krytycznej.|

### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase Methods

|||
|-|-|
|[FinalConstruct](#finalconstruct)|Przesłoń w klasie, aby wykonać wszelkie inicjalizacje wymagane przez obiekt.|
|[FinalRelease](#finalrelease)|Przesłoń w klasie, aby wykonać każde oczyszczanie wymagane przez obiekt.|
|[OuterAddRef](#outeraddref)|Zwiększa liczbę odwołań dla zagregowanego obiektu.|
|[OuterQueryInterface](#outerqueryinterface)|Deleguje do zewnętrznego `IUnknown` obiektu agregowanego.|
|[OuterRelease](#outerrelease)|Zmniejsza liczbę odwołań dla zagregowanego obiektu.|

### <a name="static-functions"></a>Funkcje statyczne

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|Deleguje do `IUnknown` niezagregowanego obiektu.|
|[ObjectMain](#objectmain)|Wywoływana podczas inicjowania modułu i kończenia dla klas pochodnych wymienionych na mapie obiektu.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_dwRef](#m_dwref)|Z `m_pOuterUnknown`częścią Unii. Używany, gdy obiekt nie jest zagregowany, aby pomieścić liczbę odwołań `AddRef` i `Release`.|
|[m_pOuterUnknown](#m_pouterunknown)|Z `m_dwRef`częścią Unii. Używany, gdy obiekt jest agregowany do przechowywania wskaźnika do nieznanego elementu zewnętrznego.|

## <a name="remarks"></a>Uwagi

`CComObjectRootEx` obsługuje zarządzanie liczbami odwołań do obiektów zarówno dla obiektów niezagregowanych, jak i agregowanych. Zawiera licznik odwołań do obiektów, jeśli obiekt nie jest agregowany i utrzymuje wskaźnik do nieznanego obiektu zewnętrznego, jeśli obiekt jest agregowany. W przypadku obiektów agregowanych metody `CComObjectRootEx` mogą służyć do obsługi awarii obiektu wewnętrznego do skonstruowania oraz do ochrony zewnętrznego obiektu przed usunięciem po wydaniu interfejsów wewnętrznych lub usunięciu obiektu wewnętrznego.

Klasa implementująca serwer COM musi dziedziczyć po `CComObjectRootEx` lub [klasy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).

Jeśli definicja klasy określa makro [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) , ATL tworzy wystąpienie `CComPolyObject<CYourClass>`, gdy zostanie wywołane `IClassFactory::CreateInstance`. Podczas tworzenia jest sprawdzana wartość nieznanego elementu zewnętrznego. Jeśli ma wartość NULL, `IUnknown` jest zaimplementowana dla niezagregowanego obiektu. Jeśli nieznana zewnętrzna nie ma wartości NULL, `IUnknown` jest zaimplementowana dla obiektu agregowanego.

Jeśli Klasa nie określi makra DECLARE_POLY_AGGREGATABLE, ATL tworzy wystąpienie `CAggComObject<CYourClass>` dla zagregowanych obiektów lub wystąpienia `CComObject<CYourClass>` dla obiektów niezagregowanych.

Zaletą korzystania z `CComPolyObject` jest unikanie `CComAggObject` i `CComObject` w module do obsługi zagregowanych i niezagregowanych przypadków. Pojedynczy obiekt `CComPolyObject` obsługuje oba przypadki. W związku z tym w module istnieje tylko jedna kopia tabeli metod wirtualnych i jedna kopia funkcji. W przypadku dużej liczby tablic wirtualnych może to znacznie zmniejszyć rozmiar modułu. Jeśli jednak tablica tablicowa jest mała, użycie `CComPolyObject` może spowodować nieco większy rozmiar modułu, ponieważ nie jest zoptymalizowany pod kątem zagregowanych lub niezagregowanych obiektów, ponieważ są one `CComAggObject` i `CComObject`.

Jeśli obiekt jest zagregowany, [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) jest implementowany przez `CComAggObject` lub `CComPolyObject`. Te klasy umożliwiają delegowanie wywołań `QueryInterface`, `AddRef`i `Release` `CComObjectRootEx``OuterQueryInterface`, `OuterAddRef`i `OuterRelease` do nieznanego elementu zewnętrznego. Zwykle zastępuje się `CComObjectRootEx::FinalConstruct` w klasie w celu utworzenia dowolnych zagregowanych obiektów i przesłonięcie `CComObjectRootEx::FinalRelease` w celu zwolnienia wszystkich zagregowanych obiektów.

Jeśli obiekt nie jest zagregowany, `IUnknown` jest implementowana przez `CComObject` lub `CComPolyObject`. W takim przypadku wywołania do `QueryInterface`, `AddRef`i `Release` są delegowane do `InternalQueryInterface``CComObjectRootEx`, `InternalAddRef`i `InternalRelease` w celu wykonania rzeczywistych operacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="ccomobjectrootex"></a>CComObjectRootEx::CComObjectRootEx

Konstruktor inicjuje liczbę odwołań do 0.

```
CComObjectRootEx();
```

##  <a name="finalconstruct"></a>CComObjectRootEx::FinalConstruct

Można zastąpić tę metodę w klasie pochodnej, aby wykonać wszelkie inicjalizacje wymagane dla obiektu.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Wartość zwrócona

Zwróć S_OK po powodzeniu lub jednej z wartości HRESULT błędu standardowego.

### <a name="remarks"></a>Uwagi

Domyślnie, `CComObjectRootEx::FinalConstruct` po prostu zwraca S_OK.

Istnieją zalety wykonywania inicjalizacji w `FinalConstruct`, a nie konstruktora klasy:

- Nie można zwrócić kodu stanu z konstruktora, ale można zwrócić wynik HRESULT przy użyciu wartości zwracanej przez `FinalConstruct`. Gdy obiekty klasy są tworzone przy użyciu fabryki klasy standardowej dostarczonej przez ATL, ta wartość zwracana jest propagowana z powrotem do klienta COM, co umożliwia podanie szczegółowych informacji o błędzie.

- Nie można wywoływać funkcji wirtualnych za pośrednictwem mechanizmu funkcji wirtualnej z konstruktora klasy. Wywołanie funkcji wirtualnej z konstruktora klasy skutkuje statycznie rozwiązanym wywołaniem funkcji, która jest zdefiniowana w tym punkcie w hierarchii dziedziczenia. Wywołania czystych funkcji wirtualnych powodują błędy konsolidatora.

   Klasa nie jest najbardziej klasą pochodną w hierarchii dziedziczenia — opiera się na klasie pochodnej dostarczonej przez ATL, aby udostępnić niektóre jej funkcje. Istnieje dobry szansa, że inicjalizacja będzie wymagała korzystania z funkcji dostarczonych przez tę klasę (jest to bardzo prawdziwe, gdy obiekty klasy muszą agregować inne obiekty), ale Konstruktor w klasie nie ma sposobu na dostęp do tych funkcji. Kod budowlany dla klasy jest wykonywany przed pełnym skonstruowaniem klasy z największą pochodną.

   Jednak `FinalConstruct` jest wywoływana natychmiast po pełnej konstrukcji klasy pochodnej, co umożliwia wywoływanie funkcji wirtualnych i użycie implementacji zliczania odwołań dostarczonej przez ATL.

### <a name="example"></a>Przykład

Zwykle Przesłoń tę metodę w klasie pochodnej `CComObjectRootEx`, aby utworzyć wszystkie zagregowane obiekty. Na przykład:

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

Jeśli konstrukcja nie powiedzie się, można zwrócić błąd. Można również użyć makra [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) , aby chronić obiekt zewnętrzny przed usunięciem, jeśli podczas tworzenia, wewnętrzny obiekt zagregowany zwiększy liczbę odwołań, a następnie zmniejszy liczbę do 0.

Oto typowy sposób tworzenia agregacji:

- Dodaj `IUnknown` wskaźnik do obiektu klasy i zainicjuj go do wartości NULL w konstruktorze.

- Zastąp `FinalConstruct`, aby utworzyć agregację.

- Użyj wskaźnika `IUnknown` zdefiniowanego jako parametr w makrze [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) .

- Przesłoń `FinalRelease`, aby zwolnić wskaźnik `IUnknown`.

##  <a name="finalrelease"></a>CComObjectRootEx::FinalRelease

Można zastąpić tę metodę w klasie pochodnej, aby wykonać każde oczyszczanie wymagane dla obiektu.

```
void FinalRelease();
```

### <a name="remarks"></a>Uwagi

Domyślnie `CComObjectRootEx::FinalRelease` nic nie robi.

Wykonanie czyszczenia w `FinalRelease` jest lepszym rozwiązaniem w przypadku dodawania kodu do destruktora klasy, ponieważ obiekt jest nadal w pełni skonstruowany w punkcie, w którym wywoływany jest `FinalRelease`. Dzięki temu można bezpiecznie uzyskać dostęp do metod dostarczonych przez najbardziej pochodną klasę. Jest to szczególnie ważne w przypadku zwalniania wszystkich zagregowanych obiektów przed usunięciem.

##  <a name="internaladdref"></a>CComObjectRootEx:: InternalAddRef —

Zwiększa liczbę odwołań obiektu niezagregowanego o 1.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>Wartość zwrócona

Wartość, która może być przydatna w przypadku diagnostyki i testowania.

### <a name="remarks"></a>Uwagi

Jeśli model wątku jest wielowątkowy, `InterlockedIncrement` jest używany do uniemożliwienia więcej niż jednego wątku zmiany liczby odwołań w tym samym czasie.

##  <a name="internalqueryinterface"></a>CComObjectRootEx::InternalQueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*pThis*<br/>
podczas Wskaźnik do obiektu, który zawiera mapę COM interfejsów dostępnych do `QueryInterface`.

*pEntries*<br/>
podczas Wskaźnik do struktury `_ATL_INTMAP_ENTRY`, która uzyskuje dostęp do mapy dostępnych interfejsów.

*IID*<br/>
podczas Identyfikator GUID żądanego interfejsu.

*ppvObject*<br/>
określoną Wskaźnik do wskaźnika interfejsu określonego w *identyfikatorze IID*lub wartość null, jeśli nie można odnaleźć interfejsu.

### <a name="return-value"></a>Wartość zwrócona

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

`InternalQueryInterface` obsługuje tylko interfejsy w tabeli mapy COM. Jeśli obiekt jest zagregowany, `InternalQueryInterface` nie jest delegowany do nieznanego obiektu zewnętrznego. Możesz wprowadzić interfejsy w tabeli mapy modelu COM z makrem [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) lub jednym z jego wariantów.

##  <a name="internalrelease"></a>CComObjectRootEx:: InternalRelease —

Zmniejsza liczbę odwołań obiektu niezagregowanego o 1.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>Wartość zwrócona

W przypadku kompilacji niedebugowania i debugowania ta funkcja zwraca wartość, która może być przydatna w przypadku diagnostyki lub testowania. Dokładna wartość zwrócona zależy od wielu czynników, takich jak używany system operacyjny, i może nie być liczbą odwołań.

### <a name="remarks"></a>Uwagi

Jeśli model wątku jest wielowątkowy, `InterlockedDecrement` jest używany do uniemożliwienia więcej niż jednego wątku zmiany liczby odwołań w tym samym czasie.

##  <a name="lock"></a>CComObjectRootEx:: Lock

Jeśli model wątku jest wielowątkowy, Metoda ta wywołuje Win32 API funkcji [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), która czeka, aż wątek będzie mógł przejąć własność obiektu sekcji krytycznej uzyskanego za pomocą prywatnego elementu członkowskiego danych.

```
void Lock();
```

### <a name="remarks"></a>Uwagi

Gdy kod chroniony kończy wykonywanie, wątek musi wywołać `Unlock`, aby zwolnić własność sekcji krytycznej.

Jeśli model wątku jest jednowątkowy, ta metoda nie wykonuje żadnych operacji.

##  <a name="m_dwref"></a>CComObjectRootEx:: m_dwRef

Część Unii, która uzyskuje dostęp do czterech bajtów pamięci.

```
long m_dwRef;
```

### <a name="remarks"></a>Uwagi

Z `m_pOuterUnknown`częścią Unii:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Jeśli obiekt nie jest zagregowany, liczbę odwołań dostępną przez `AddRef` i `Release` są przechowywane w `m_dwRef`. Jeśli obiekt jest zagregowany, wskaźnik do nieznanego obiektu zewnętrznego jest przechowywany w [m_pOuterUnknown](#m_pouterunknown).

##  <a name="m_pouterunknown"></a>CComObjectRootEx:: m_pOuterUnknown

Część Unii, która uzyskuje dostęp do czterech bajtów pamięci.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Uwagi

Z `m_dwRef`częścią Unii:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Jeśli obiekt jest zagregowany, wskaźnik do nieznanego obiektu zewnętrznego jest przechowywany w `m_pOuterUnknown`. Jeśli obiekt nie jest zagregowany, liczbę odwołań dostępną przez `AddRef` i `Release` są przechowywane w [m_dwRef](#m_dwref).

##  <a name="objectmain"></a>CComObjectRootEx::ObjectMain

Dla każdej klasy wymienionej w mapie obiektów ta funkcja jest wywoływana raz, gdy moduł zostanie zainicjowany i ponownie po jej zakończeniu.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>Parametry

*bStarting*<br/>
określoną Wartość jest RÓWNa TRUE, jeśli klasa jest inicjowana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wartość parametru *bStarting* wskazuje, czy moduł jest inicjowany, czy zakończony. Domyślna implementacja `ObjectMain` nic nie robi, ale można zastąpić tę funkcję w klasie, aby inicjować lub czyścić zasoby, które mają zostać przydzielone dla klasy. Należy pamiętać, że `ObjectMain` jest wywoływana przed zażądaniem wystąpienia klasy.

`ObjectMain` jest wywoływana z punktu wejścia biblioteki DLL, więc typ operacji, którą może wykonać funkcja punktu wejścia, jest ograniczony. Aby uzyskać więcej informacji o tych ograniczeniach, zobacz [biblioteki C++ dll i zachowanie biblioteki uruchomieniowej](../../build/run-time-library-behavior.md) i [DllMain](/windows/win32/Dlls/dllmain).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

##  <a name="outeraddref"></a>CComObjectRootEx::OuterAddRef

Zwiększa liczbę odwołań zewnętrznego nieznanego elementu agregacji.

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>Wartość zwrócona

Wartość, która może być przydatna w przypadku diagnostyki i testowania.

##  <a name="outerqueryinterface"></a>CComObjectRootEx::OuterQueryInterface

Pobiera pośredni wskaźnik do żądanego interfejsu.

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Identyfikator GUID żądanego interfejsu.

*ppvObject*<br/>
określoną Wskaźnik do wskaźnika interfejsu określonego w *identyfikatorze IID*lub wartość null, jeśli agregacja nie obsługuje interfejsu.

### <a name="return-value"></a>Wartość zwrócona

Jedna ze standardowych wartości HRESULT.

##  <a name="outerrelease"></a>CComObjectRootEx::OuterRelease

Zmniejsza liczbę odwołań zewnętrznego nieznanego elementu agregacji.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>Wartość zwrócona

W kompilacjach niedebugowanych zawsze zwraca wartość 0. W kompilacjach debugowania zwraca wartość, która może być przydatna w przypadku diagnostyki lub testowania.

##  <a name="unlock"></a>CComObjectRootEx:: Unlock

Jeśli model wątku jest wielowątkowy, Metoda ta wywołuje Win32 API funkcji [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), która zwalnia własność obiektu sekcji krytycznej uzyskanego za pomocą prywatnego elementu członkowskiego danych.

```
void Unlock();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać własność, wątek musi wywołać `Lock`. Każde wywołanie `Lock` wymaga odpowiedniego wywołania do `Unlock`, aby zwolnić własność sekcji krytycznej.

Jeśli model wątku jest jednowątkowy, ta metoda nie wykonuje żadnych operacji.

## <a name="see-also"></a>Zobacz też

[Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Klasa CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
