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
ms.openlocfilehash: f24cf6cce5cdf268367f547e8a536dcdae7cc859
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098956"
---
# <a name="ccomobjectrootex-class"></a>Klasa CComObjectRootEx

Ta klasa dostarcza metody do obsługi zarządzania liczba odwołanie do obiektu nieagregowane i zagregowane obiekty.

## <a name="syntax"></a>Składnia

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>Parametry

*ThreadModel*<br/>
Klasa, której metody wdrożenia żądany model wątku. Można jawnie wybrać modelu wątkowości, ustawiając *ThreadModel* do [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), lub [ CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Możesz zaakceptować serwera domyślnego wątku modelu, ustawiając *ThreadModel* do [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) lub [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).  

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|Konstruktor.|
|[Internaladdref —](#internaladdref)|Zwiększa liczbę odwołań dla obiektu nieagregowane.|
|[Internalrelease —](#internalrelease)|Dekrementuje liczbę odwołań dla obiektu nieagregowane.|
|[Blokady](#lock)|Jeśli model wątku jest wielowątkowych, uzyskuje własność obiektu sekcję krytyczną.|
|[Odblokowywanie](#unlock)|Jeśli model wątku jest wielowątkowych, zwalnia własność obiektu sekcję krytyczną.|

### <a name="ccomobjectrootbase-methods"></a>Metody CComObjectRootBase

|||
|-|-|
|[FinalConstruct](#finalconstruct)|Musi zostać zastąpiona w klasie przeprowadzić inicjowanie wymagane przez obiekt.|
|[FinalRelease](#finalrelease)|Musi zostać zastąpiona w klasie do wykonywania oczyszczania wymaganego przez obiekt.|
|[OuterAddRef](#outeraddref)|Zwiększa liczbę odwołań dla obiektu zagregowanego.|
|[OuterQueryInterface](#outerqueryinterface)|Obiektów delegowanych z zewnętrzny `IUnknown` zagregowane obiektu.|
|[OuterRelease](#outerrelease)|Dekrementuje liczbę odwołań dla obiektu zagregowanego.|

### <a name="static-functions"></a>Funkcje statyczne

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|Deleguje do `IUnknown` nieagregowane obiektu.|
|[ObjectMain](#objectmain)|Wywoływana podczas inicjowania modułu i zakończenia dla klasy pochodne, na liście na mapie obiektu.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_dwRef](#m_dwref)|Za pomocą `m_pOuterUnknown`, część Unii. Używany, gdy obiekt nie jest agregowany na potrzeby przechowywania licznik odwołań `AddRef` i `Release`.|
|[m_pOuterUnknown](#m_pouterunknown)|Za pomocą `m_dwRef`, część Unii. Używane, gdy obiekt jest zagregowany, aby pomieścić wskaźnik zewnętrzne nieznany.|

## <a name="remarks"></a>Uwagi

`CComObjectRootEx` obsługuje zarządzanie liczba odwołanie do obiektu nieagregowane i zagregowane obiekty. Jeśli obiekt nie są agregowane i przechowuje wskaźnik nieznany zewnętrznego, jeśli obiekt są agregowane, przechowuje licznik odwołań obiektu. Zagregowane obiekty `CComObjectRootEx` metody może służyć do obsługi błędu wewnętrznego obiektu do utworzenia i ma być chroniony obiektu zewnętrznego przed usunięciem zwolnionych interfejsów wewnętrznych lub wewnętrzny obiekt zostanie usunięty.

Klasa, która implementuje serwer COM musi dziedziczyć `CComObjectRootEx` lub [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).

Jeśli Twoja definicja klasy Określa [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) makra ATL tworzy wystąpienie `CComPolyObject<CYourClass>` podczas `IClassFactory::CreateInstance` jest wywoływana. Podczas tworzenia jest sprawdzany wartość zewnętrzne nieznany. Jeśli ma wartość NULL, `IUnknown` został zaimplementowany dla obiektu nieagregowane. Jeśli nieznany zewnętrzny nie ma wartość NULL, `IUnknown` został zaimplementowany dla obiektu zagregowanego.

Jeśli klasa nie określa makro DECLARE_POLY_AGGREGATABLE, ATL, tworzy wystąpienie `CAggComObject<CYourClass>` zagregowane obiektów lub wystąpienia `CComObject<CYourClass>` nieagregowane obiektów.

Zaletą korzystania z `CComPolyObject` to uniknąć konieczności zarówno `CComAggObject` i `CComObject` w module sposób obsługiwać przypadki zagregowane i nieagregowane. Pojedynczy `CComPolyObject` obiektu obsługuje w obu przypadkach. W związku z tym tylko jedna kopia vtable i jedną kopię funkcji istnieje w module. Jeśli Twoje vtable jest duży, to znacznie zmniejszyć rozmiar modułu. Jednak jeśli Twoja vtable jest mały, za pomocą `CComPolyObject` może spowodować nieco większy rozmiar modułu, ponieważ nie jest zoptymalizowana do zagregowanych lub nieagregowane obiektu, ponieważ są `CComAggObject` i `CComObject`.

Jeśli obiekt jest zagregowany, [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) jest implementowany przez `CComAggObject` lub `CComPolyObject`. Delegowanie tych klas `QueryInterface`, `AddRef`, i `Release` wywołania `CComObjectRootEx`firmy `OuterQueryInterface`, `OuterAddRef`, i `OuterRelease` do przekazywania do zewnętrznego nieznany. Zazwyczaj można zastąpić `CComObjectRootEx::FinalConstruct` w klasie tworzyć wszystkie zagregowane obiekty i zastąpić `CComObjectRootEx::FinalRelease` zwolnienie dowolne zagregowane obiekty.

Jeśli obiekt nie jest zagregowany, `IUnknown` jest implementowany przez `CComObject` lub `CComPolyObject`. W takim przypadku wywołania `QueryInterface`, `AddRef`, i `Release` są delegowane `CComObjectRootEx`firmy `InternalQueryInterface`, `InternalAddRef`, i `InternalRelease` przeprowadzić operacje.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="ccomobjectrootex"></a>  CComObjectRootEx::CComObjectRootEx

Konstruktor inicjuje licznik odwołań na 0.

```
CComObjectRootEx();
```

##  <a name="finalconstruct"></a>  CComObjectRootEx::FinalConstruct

Mogą przesłaniać tę metodę w pochodnej klasie przeprowadzić inicjowanie wymagane dla obiektu.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Wartość zwracana

Zwróć S_OK sukces lub jednego z błędu standardowego wartości HRESULT.

### <a name="remarks"></a>Uwagi

Domyślnie `CComObjectRootEx::FinalConstruct` po prostu zwraca wartość S_OK.

Istnieją zalety łączenia Trwa inicjalizacja w `FinalConstruct` zamiast konstruktora klasy:

- Nie można zwrócić kod stanu z konstruktorem, ale może zwrócić wartość HRESULT poprzez `FinalConstruct`firmy zwracają wartość. Gdy obiekty klasy są tworzone przy użyciu fabryki klas standardowych, dostarczone przez ATL, zwrócona wartość jest propagowany z powrotem do klient modelu COM, co pozwala dostarczać szczegółowe informacje o błędzie.

- Nie można wywołać funkcji wirtualnych za pośrednictwem mechanizmu funkcji wirtualnej z konstruktora klasy. Wywoływanie funkcji wirtualnej z konstruktora klasy powoduje statycznie rozwiązany wywołanie do funkcji, jak jest zdefiniowany w tym momencie w hierarchii dziedziczenia. Wywołania do czystych funkcji wirtualnych powoduje błędy konsolidatora.

     Klasa nie jest najbardziej pochodnej klasy w hierarchii dziedziczenia — opiera się na klasę pochodną dostarczonych przez ATL, aby zapewnić niektóre swoje funkcje. Istnieje szansa, że inicjalizacji będą musieli używać funkcji oferowanych przez tę klasę (jest to wartość true, bez obaw podczas obiektów klasy należy zagregować innych obiektów), ale Konstruktor w klasie nie ma możliwości uzyskania dostępu do tych funkcji. Kod konstruowania dla klasy jest wykonywany przed najbardziej pochodnej klasy jest w pełni skonstruowany.

     Jednak `FinalConstruct` nazywa się natychmiast po najbardziej pochodnej klasy jest w pełni skonstruowany umożliwiając wywołują funkcje wirtualne i użyć implementacji zliczanie odwołań, dostarczone przez ATL.

### <a name="example"></a>Przykład

Zazwyczaj należy przesłonić tę metodę w klasie pochodnej od `CComObjectRootEx` na tworzenie każdego zagregowane obiekty. Na przykład:

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

W przypadku niepowodzenia konstrukcji może zwrócić błąd. Można również użyć makra [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) Aby chronić zewnętrznego obiektu jest usunięte, jeśli podczas tworzenia wewnętrznego obiektu zagregowanego zwiększa liczbę odwołań, a następnie zmniejsza liczbę na wartość 0.

Oto typowy sposób tworzenie agregacji:

- Dodaj `IUnknown` wskaźnik do klasy obiektu i zainicjować go na wartość NULL w konstruktorze.

- Zastąp `FinalConstruct` do utworzenia agregacji.

- Użyj `IUnknown` zdefiniowany jako parametr do wskaźnika [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) makra.

- Zastąp `FinalRelease` zwolnić `IUnknown` wskaźnika.

##  <a name="finalrelease"></a>  CComObjectRootEx::FinalRelease

Mogą przesłaniać tę metodę w pochodnej klasie do wykonywania oczyszczania wymaganego obiektu.

```
void FinalRelease();
```

### <a name="remarks"></a>Uwagi

Domyślnie `CComObjectRootEx::FinalRelease` nic nie robi.

Trwa oczyszczanie w `FinalRelease` jest dodanie kodu do destruktor klasy, ponieważ obiekt jest nadal w pełni tworzony w momencie w którym `FinalRelease` jest wywoływana. Dzięki temu można bezpiecznie otrzymać dostęp metod dostarczonych przez klasę najbardziej pochodnej. Jest to szczególnie ważne w przypadku zwalnianie wszystkie zagregowane obiekty przed usunięciem.

##  <a name="internaladdref"></a>  CComObjectRootEx::InternalAddRef

Zwiększa licznik odwołań obiektu nieagregowane o 1.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatne w przypadku diagnostyki i testowania.

### <a name="remarks"></a>Uwagi

Jeśli model wątku jest wielowątkowych, `InterlockedIncrement` używany w celu zapobiegania więcej niż jeden wątek na zmienianie licznik odwołań w tym samym czasie.

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

*pThis*<br/>
[in] Wskaźnik do obiektu, która zawiera mapę COM, interfejsów narażonych na `QueryInterface`.

*pEntries*<br/>
[in] Wskaźnik do `_ATL_INTMAP_ENTRY` strukturę, która uzyskuje dostęp do mapy z dostępnych interfejsów.

*IID*<br/>
[in] Identyfikator GUID interfejsu żądanej.

*ppvObject*<br/>
[out] Wskaźnik do wskaźnika interfejsu określonego w *iid*, lub wartość NULL, jeśli nie można odnaleźć interfejsu.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

`InternalQueryInterface` obsługuje tylko interfejsów COM tabeli mapy. Jeśli obiekt jest zagregowany, `InternalQueryInterface` nie delegować do zewnętrznego nieznany. Możesz wprowadzić interfejsy do tabeli mapy COM za pomocą makra [com_interface_entry —](com-interface-entry-macros.md#com_interface_entry) lub jedna z jej wariantów.

##  <a name="internalrelease"></a>  CComObjectRootEx::InternalRelease

Dekrementuje liczbę odwołań obiektu nieagregowane o 1.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>Wartość zwracana

W obu bez debugowania i zwiększono wydajność debugowania kompilacji, ta funkcja zwraca wartość, która może być użyteczna, diagnostykę lub testowania. Dokładna wartość zwracana jest zależna od wielu czynników, takich jak system operacyjny używany i może lub nie mogą, być licznika odwołań.

### <a name="remarks"></a>Uwagi

Jeśli model wątku jest wielowątkowych, `InterlockedDecrement` używany w celu zapobiegania więcej niż jeden wątek na zmienianie licznik odwołań w tym samym czasie.

##  <a name="lock"></a>  CComObjectRootEx::Lock

Jeśli model wątku jest wielowątkowych, ta metoda wywołuje funkcję Win32 API [EnterCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-entercriticalsection), która czeka, aż wątek może zająć własności obiektu sekcję krytyczną uzyskane za pośrednictwem element członkowski danych prywatnych.

```
void Lock();
```

### <a name="remarks"></a>Uwagi

Po zakończeniu wykonywania kodu chronionych wątku, należy wywołać `Unlock` zwolnić własności sekcję krytyczną.

W przypadku modelu wątku jednowątkowe, ta metoda nie działa.

##  <a name="m_dwref"></a>  CComObjectRootEx::m_dwRef

Część Unii, który uzyskuje dostęp do czterech bajtów pamięci.

```
long m_dwRef;
```

### <a name="remarks"></a>Uwagi

Za pomocą `m_pOuterUnknown`, część Unii:  

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Jeśli obiekt nie jest zagregowany, licznik odwołań dostępu `AddRef` i `Release` są przechowywane w `m_dwRef`. Jeśli obiekt jest zagregowany, wskaźnik do nieznanych zewnętrzne są przechowywane w [m_pOuterUnknown](#m_pouterunknown).

##  <a name="m_pouterunknown"></a>  CComObjectRootEx::m_pOuterUnknown

Część Unii, który uzyskuje dostęp do czterech bajtów pamięci.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Uwagi

Za pomocą `m_dwRef`, część Unii:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Jeśli obiekt jest zagregowany, wskaźnik do nieznanych zewnętrzne są przechowywane w `m_pOuterUnknown`. Jeśli obiekt nie jest zagregowany, licznik odwołań dostępu `AddRef` i `Release` są przechowywane w [m_dwRef](#m_dwref).

##  <a name="objectmain"></a>  CComObjectRootEx::ObjectMain

Dla każdej klasy na mapie obiektu na liście, ta funkcja jest wywoływana, gdy kiedy moduł został zainicjowany, i ponownie, gdy zostanie zakończony.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>Parametry

*bStarting*<br/>
[out] Ma wartość TRUE, jeśli klasa jest inicjowany; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wartość *bStarting* parametr wskazuje, czy moduł jest inicjowana lub zakończone. Domyślna implementacja klasy `ObjectMain` nie robi nic, ale możesz zastąpić tę funkcję w klasie do inicjowania lub wyczyścić zasoby, które mają zostać przydzielone dla klasy. Należy pamiętać, że `ObjectMain` jest wywoływana przed wymagane są wszystkie wystąpienia klasy.

`ObjectMain` jest wywoływana z punktu wejścia biblioteki dll, więc typ operacji, które może wykonywać funkcję punktu wejścia jest ograniczona. Aby uzyskać więcej informacji na temat tych ograniczeń, zobacz [bibliotek DLL i Visual C++ zachowanie biblioteki wykonawczej](../../build/run-time-library-behavior.md) i [DllMain](/windows/desktop/Dlls/dllmain).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

##  <a name="outeraddref"></a>  CComObjectRootEx::OuterAddRef

Zwiększa liczbę odwołań zewnętrznych nieznany agregacji.

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

*IID*<br/>
[in] Identyfikator GUID interfejsu żądanej.

*ppvObject*<br/>
[out] Wskaźnik do wskaźnika interfejsu określonego w *iid*, lub wartość NULL, jeśli agregacji nie obsługuje interfejsu.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="outerrelease"></a>  CComObjectRootEx::OuterRelease

Dekrementuje liczbę odwołań zewnętrzne nieznany agregacji.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach nieprzeznaczonych do debugowania zawsze zwraca wartość 0. W przypadku kompilacji do debugowania zwraca wartość, która może być użyteczna, diagnostykę lub testowania.

##  <a name="unlock"></a>  CComObjectRootEx::Unlock

Jeśli model wątku jest wielowątkowych, ta metoda wywołuje funkcję Win32 API [LeaveCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-leavecriticalsection), które wersje własności obiektu sekcję krytyczną uzyskane za pośrednictwem element członkowski danych prywatnych.

```
void Unlock();
```

### <a name="remarks"></a>Uwagi

Aby otrzymać prawo własności, wątek musi wywołać `Lock`. Każde wywołanie `Lock` wymaga odpowiedniego wywołania `Unlock` zwolnić własności sekcję krytyczną.

W przypadku modelu wątku jednowątkowe, ta metoda nie działa.

## <a name="see-also"></a>Zobacz też

[Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Klasa CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
