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
ms.openlocfilehash: e8db86f6214f95cd9bb08d3b5f6c6c1a38ca475c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327607"
---
# <a name="ccomobjectrootex-class"></a>Klasa CComObjectRootEx

Ta klasa zawiera metody obsługi zarządzania liczbą odwołań do obiektów dla obiektów nieagregowanych i zagregowanych.

## <a name="syntax"></a>Składnia

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>Parametry

*GwintModel*<br/>
Klasa, której metody implementują żądany model wątkowania. Model wątków można jawnie wybrać, ustawiając *threadmodel* na [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)lub [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Domyślny model wątku serwera można zaakceptować, ustawiając *ThreadModel* na [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) lub [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Ccomobjectrootex](#ccomobjectrootex)|Konstruktor.|
|[InternalAddRef](#internaladdref)|Zwiększa liczbę odwołań dla obiektu nieagregowanego.|
|[Wewnętrznywydaj](#internalrelease)|Zmniejsza liczbę odwołań dla obiektu nieagregowanego.|
|[Blokady](#lock)|Jeśli model wątku jest wielowątkowy, uzyskuje własność obiektu sekcji krytycznej.|
|[Odblokować](#unlock)|Jeśli model wątku jest wielowątkowy, zwalnia własność obiektu sekcji krytycznej.|

### <a name="ccomobjectrootbase-methods"></a>Metody CComObjectRootBase

|||
|-|-|
|[Finalconstruct](#finalconstruct)|Zastąd w klasie, aby wykonać inicjalizację wymaganą przez obiekt.|
|[Finalrelease](#finalrelease)|Zastąpuj w klasie, aby wykonać wszelkie oczyszczanie wymagane przez obiekt.|
|[ZewnętrznyRefAddRef](#outeraddref)|Zwiększa liczbę odwołań dla obiektu zagregowanego.|
|[OuterQueryInterface (Kontrowersje)](#outerqueryinterface)|Delegaci `IUnknown` do zewnętrznej strony zagregowanego obiektu.|
|[Publikacja zewnętrzna](#outerrelease)|Zmniejsza liczbę odwołań dla obiektu zagregowanego.|

### <a name="static-functions"></a>Funkcje statyczne

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|Delegaci `IUnknown` do obiektu nieagregowanego.|
|[ObiektMain](#objectmain)|Wywoływana podczas inicjowania modułu i zakończenia dla klas pochodnych wymienionych na mapie obiektu.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_dwRef](#m_dwref)|Z `m_pOuterUnknown`, częścią związku. Używane, gdy obiekt nie jest agregowany `AddRef` `Release`do przechowywania liczby odwołań i .|
|[m_pOuterUnknown](#m_pouterunknown)|Z `m_dwRef`, częścią związku. Używane, gdy obiekt jest agregowany do przechowywania wskaźnika do zewnętrznej nieznanej.|

## <a name="remarks"></a>Uwagi

`CComObjectRootEx`obsługuje zarządzanie liczbą odwołań do obiektów dla obiektów nieagregowanych i zagregowanych. Przechowuje liczbę odwołań do obiektu, jeśli obiekt nie jest agregowany, i przechowuje wskaźnik do zewnętrznej nieznanej, jeśli obiekt jest agregowany. W przypadku obiektów `CComObjectRootEx` zagregowanych metody mogą być używane do obsługi awarii obiektu wewnętrznego do konstruowania i ochrony obiektu zewnętrznego przed usunięciem po zwolnieniu interfejsów wewnętrznych lub usunięciu obiektu wewnętrznego.

Klasa implementuje serwer COM musi `CComObjectRootEx` dziedziczyć z lub [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).

Jeśli definicja klasy określa [makro DECLARE_POLY_AGGREGATABLE,](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) ATL tworzy `CComPolyObject<CYourClass>` `IClassFactory::CreateInstance` wystąpienie, gdy jest wywoływana. Podczas tworzenia sprawdzana jest wartość zewnętrznej nieznanej. Jeśli jest null, `IUnknown` jest zaimplementowana dla obiektu nieagregowanego. Jeśli zewnętrzna niewiadoma nie jest null, `IUnknown` jest implementowana dla zagregowanego obiektu.

Jeśli klasa nie określa makra DECLARE_POLY_AGGREGATABLE, ATL tworzy `CAggComObject<CYourClass>` wystąpienie zagregowanych obiektów `CComObject<CYourClass>` lub wystąpienie obiektów nieagregowanych.

Zaletą korzystania `CComPolyObject` jest, że `CComAggObject` można `CComObject` uniknąć posiadania zarówno i w module do obsługi zagregowanych i nieagregowanych przypadkach. Pojedynczy `CComPolyObject` obiekt obsługuje obie sprawy. W związku z tym tylko jedna kopia vtable i jedna kopia funkcji istnieje w module. Jeśli twój vtable jest duży, może to znacznie zmniejszyć rozmiar modułu. Jeśli jednak tabela vtable `CComPolyObject` jest mała, użycie może spowodować nieco większy rozmiar modułu, ponieważ nie jest `CComAggObject` zoptymalizowany pod kątem zagregowanego lub nieagregowanego obiektu, tak jak są i `CComObject`.

Jeśli obiekt jest agregowany, [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) jest implementowany przez `CComAggObject` lub `CComPolyObject`. Te klasy `QueryInterface` `AddRef`delegata `Release` , `CComObjectRootEx`i `OuterQueryInterface` `OuterAddRef`wzywa `OuterRelease` do 's , i do przekazania do zewnętrznej nieznanej. Zazwyczaj można zastąpić `CComObjectRootEx::FinalConstruct` w klasie, aby utworzyć wszystkie zagregowane `CComObjectRootEx::FinalRelease` obiekty i zastąpić, aby zwolnić wszystkie obiekty zagregowane.

Jeśli obiekt nie jest `IUnknown` agregowany, `CComObject` `CComPolyObject`jest implementowany przez lub . W takim przypadku `QueryInterface`wywołania , `AddRef` `Release` , `CComObjectRootEx`i `InternalQueryInterface`są `InternalAddRef`delegowane do 's , i `InternalRelease` do wykonywania rzeczywistych operacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomobjectrootexccomobjectrootex"></a><a name="ccomobjectrootex"></a>CComObjectRootEx::CComObjectRootEx

Konstruktor inicjuje liczbę odwołań do 0.

```
CComObjectRootEx();
```

## <a name="ccomobjectrootexfinalconstruct"></a><a name="finalconstruct"></a>CComObjectRootEx::FinalConstruct

Tę metodę można zastąpić w klasie pochodnej, aby wykonać inicjację wymaganą dla obiektu.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po sukcesie lub jedną ze standardowych wartości HRESULT błędu.

### <a name="remarks"></a>Uwagi

Domyślnie `CComObjectRootEx::FinalConstruct` po prostu zwraca S_OK.

Istnieją zalety wykonywania inicjowania w, `FinalConstruct` a nie w konstruktorze klasy:

- Nie można zwrócić kodu stanu z konstruktora, ale można `FinalConstruct`zwrócić HRESULT za pomocą 's zwracana wartość. Gdy obiekty klasy są tworzone przy użyciu fabryki klasy standardowej dostarczonej przez ATL, ta wartość zwracana jest propagowana z powrotem do klienta COM, co pozwala na podanie szczegółowych informacji o błędzie.

- Nie można wywołać funkcji wirtualnych za pośrednictwem mechanizmu funkcji wirtualnych z konstruktora klasy. Wywołanie funkcji wirtualnej z konstruktora klasy powoduje statycznie rozpoznane wywołanie funkcji, jak jest zdefiniowana w tym momencie w hierarchii dziedziczenia. Wywołania czystych funkcji wirtualnych powodują błędy konsolidatora.

   Klasa nie jest najbardziej pochodną klasą w hierarchii dziedziczenia — opiera się na klasie pochodnej dostarczonej przez ATL, aby zapewnić niektóre z jej funkcji. Istnieje duża szansa, że inicjowanie będzie musiał użyć funkcji dostarczonych przez tę klasę (jest to z pewnością prawdziwe, gdy obiekty klasy trzeba agregować inne obiekty), ale konstruktor w klasie nie ma możliwości dostępu do tych funkcji. Kod konstrukcyjny dla klasy jest wykonywany przed najbardziej pochodną klasy jest w pełni skonstruowany.

   Jednak `FinalConstruct` jest wywoływana natychmiast po najbardziej pochodnych klasy jest w pełni skonstruowany, dzięki czemu można wywołać funkcje wirtualne i używać implementacji zliczania odwołań dostarczonych przez ATL.

### <a name="example"></a>Przykład

Zazwyczaj należy zastąpić tę metodę w klasie `CComObjectRootEx` pochodnej, aby utworzyć wszystkie obiekty zagregowane. Przykład:

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

Jeśli konstrukcja nie powiedzie się, można zwrócić błąd. Można również użyć [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) makra, aby chronić obiekt zewnętrzny przed usunięciem, jeśli podczas tworzenia wewnętrzny obiekt zagregowany zwiększa liczbę odwołań, a następnie zmniejsza liczbę do 0.

Oto typowy sposób tworzenia agregacji:

- Dodaj `IUnknown` wskaźnik do obiektu klasy i zai morsować go do wartości NULL w konstruktorze.

- Zastąd, `FinalConstruct` aby utworzyć agregację.

- Użyj `IUnknown` wskaźnika zdefiniowanego jako parametr do [makra COM_INTERFACE_ENTRY_AGGREGATE.](com-interface-entry-macros.md#com_interface_entry_aggregate)

- `FinalRelease` Zastąpuj, `IUnknown` aby zwolnić wskaźnik.

## <a name="ccomobjectrootexfinalrelease"></a><a name="finalrelease"></a>CComObjectRootEx::Ostateczna wersja

Tę metodę można zastąpić w klasie pochodnej, aby wykonać wszelkie oczyszczanie wymagane dla obiektu.

```
void FinalRelease();
```

### <a name="remarks"></a>Uwagi

Domyślnie `CComObjectRootEx::FinalRelease` nic nie robi.

Wykonywanie oczyszczania `FinalRelease` w jest lepsze niż dodawanie kodu do destruktora klasy, ponieważ obiekt `FinalRelease` jest nadal w pełni skonstruowany w punkcie, w którym jest wywoływana. Dzięki temu można bezpiecznie uzyskać dostęp do metod dostarczonych przez najbardziej pochodne klasy. Jest to szczególnie ważne w przypadku zwalniania wszystkich zagregowanych obiektów przed usunięciem.

## <a name="ccomobjectrootexinternaladdref"></a><a name="internaladdref"></a>CComObjectRootEx::InternalAddRef

Zwiększa liczbę odwołań nieagregowanego obiektu o 1.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna do diagnostyki i testowania.

### <a name="remarks"></a>Uwagi

Jeśli model wątku jest wielowątkowy, jest używany, `InterlockedIncrement` aby zapobiec więcej niż jeden wątek z zmieniania liczby odwołań w tym samym czasie.

## <a name="ccomobjectrootexinternalqueryinterface"></a><a name="internalqueryinterface"></a>CComObjectRootEx::InternalQueryInterface

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
[w] Wskaźnik do obiektu zawierającego mapę COM interfejsów narażonych na `QueryInterface`działanie .

*pEntries (PEntries)*<br/>
[w] Wskaźnik do `_ATL_INTMAP_ENTRY` struktury, która uzyskuje dostęp do mapy dostępnych interfejsów.

*Iid*<br/>
[w] Identyfikator GUID żądanego interfejsu.

*ppvObiekt*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu określonego w *iid*lub NULL, jeśli nie zostanie znaleziony interfejs.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

`InternalQueryInterface`obsługuje tylko interfejsy w tabeli mapy COM. Jeśli obiekt jest agregowany, `InternalQueryInterface` nie przekazuje do zewnętrznej nieznanej. Interfejsy można wprowadzić w tabeli mapy COM z [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) makra lub jednym z jego wariantów.

## <a name="ccomobjectrootexinternalrelease"></a><a name="internalrelease"></a>CComObjectRootEx::InternalRelease

Zmniejsza liczbę odwołań obiektu nieagregowanego o 1.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach bez debugowania i debugowania ta funkcja zwraca wartość, która może być przydatna do diagnostyki lub testowania. Dokładna zwracana wartość zależy od wielu czynników, takich jak używany system operacyjny i może lub nie może być liczbą odwołań.

### <a name="remarks"></a>Uwagi

Jeśli model wątku jest wielowątkowy, jest używany, `InterlockedDecrement` aby zapobiec więcej niż jeden wątek z zmieniania liczby odwołań w tym samym czasie.

## <a name="ccomobjectrootexlock"></a><a name="lock"></a>CComObjectRootEx::Blokada

Jeśli model wątku jest wielowątkowy, ta metoda wywołuje funkcję interfejsu API Win32 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), która czeka, aż wątek może przejąć na własność obiekt sekcji krytycznej uzyskany za pośrednictwem prywatnego elementu członkowskiego danych.

```
void Lock();
```

### <a name="remarks"></a>Uwagi

Po zakończeniu wykonywania chronionego kodu wątek `Unlock` musi wywołać, aby zwolnić własność sekcji krytycznej.

Jeśli model wątku jest jednowątkowy, ta metoda nic nie robi.

## <a name="ccomobjectrootexm_dwref"></a><a name="m_dwref"></a>CComObjectRootEx::m_dwRef

Część unii, która uzyskuje dostęp do czterech bajtów pamięci.

```
long m_dwRef;
```

### <a name="remarks"></a>Uwagi

Z `m_pOuterUnknown`, częścią związku:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Jeśli obiekt nie jest agregowany, liczba `AddRef` `Release` odwołań, `m_dwRef`do których dostęp ma i jest przechowywana w programie . Jeśli obiekt jest agregowany, wskaźnik do zewnętrznej nieznanej jest przechowywany w [m_pOuterUnknown](#m_pouterunknown).

## <a name="ccomobjectrootexm_pouterunknown"></a><a name="m_pouterunknown"></a>CComObjectRootEx::m_pOuterUnknown

Część unii, która uzyskuje dostęp do czterech bajtów pamięci.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Uwagi

Z `m_dwRef`, częścią związku:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Jeśli obiekt jest agregowany, wskaźnik do zewnętrznej `m_pOuterUnknown`nieznanej jest przechowywany w pliku . Jeśli obiekt nie jest agregowany, liczba `AddRef` `Release` odwołań, do których dostęp ma i jest przechowywana w [m_dwRef](#m_dwref).

## <a name="ccomobjectrootexobjectmain"></a><a name="objectmain"></a>CComObjectRootEx::ObjectMain

Dla każdej klasy wymienionej na mapie obiektu ta funkcja jest wywoływana raz, gdy moduł jest inicjowany i ponownie po jego zakończeniu.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>Parametry

*bRozpoczenie*<br/>
[na zewnątrz] Wartość jest PRAWDA, jeśli klasa jest inicjowana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wartość parametru *bStarting* wskazuje, czy moduł jest inicjowany, czy zakończony. Domyślna implementacja `ObjectMain` nie robi nic, ale można zastąpić tę funkcję w klasie, aby zainicjować lub oczyścić zasoby, które chcesz przydzielić dla klasy. Należy `ObjectMain` zauważyć, że jest wywoływana przed wszelkie wystąpienia klasy są wymagane.

`ObjectMain`jest wywoływana z punktu wejścia biblioteki DLL, więc typ operacji, który może wykonywać funkcję punktu wejścia jest ograniczona. Aby uzyskać więcej informacji na temat tych ograniczeń, zobacz [biblioteki DLL i zachowanie biblioteki wykonywania visual C++](../../build/run-time-library-behavior.md) i [DllMain](/windows/win32/Dlls/dllmain).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

## <a name="ccomobjectrootexouteraddref"></a><a name="outeraddref"></a>CComObjectRootEx::OuterAddRef

Zwiększa liczbę odwołań zewnętrznej nieznanej agregacji.

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna do diagnostyki i testowania.

## <a name="ccomobjectrootexouterqueryinterface"></a><a name="outerqueryinterface"></a>CComObjectRootEx::OuterQueryInterface

Pobiera wskaźnik pośredni do żądanego interfejsu.

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator GUID żądanego interfejsu.

*ppvObiekt*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu określonego w *iid*lub NULL, jeśli agregacja nie obsługuje interfejsu.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="ccomobjectrootexouterrelease"></a><a name="outerrelease"></a>CComObjectRootEx::Publikacja zewnętrzna

Zmniejsza liczbę odwołań zewnętrznej nieznanej agregacji.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>Wartość zwracana

W kompilacjach innych niż debugowanie zawsze zwraca wartość 0. W kompilacjach debugowania zwraca wartość, która może być przydatna do diagnostyki lub testowania.

## <a name="ccomobjectrootexunlock"></a><a name="unlock"></a>CComObjectRootEx::Odblokuj

Jeśli model wątku jest wielowątkowy, ta metoda wywołuje funkcję interfejsu API Win32 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), która zwalnia własność obiektu sekcji krytycznej uzyskanej za pośrednictwem prywatnego elementu członkowskiego danych.

```
void Unlock();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać własność, wątek musi wywołać `Lock`. Każde wywołanie `Lock` wymaga odpowiedniego `Unlock` wywołania, aby zwolnić własność sekcji krytycznej.

Jeśli model wątku jest jednowątkowy, ta metoda nic nie robi.

## <a name="see-also"></a>Zobacz też

[Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Klasa CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
