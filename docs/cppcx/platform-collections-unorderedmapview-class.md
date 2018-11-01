---
title: Platform::Collections::UnorderedMapView — Klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: 9564904fa77ae6a7355119e83bdfa3ac65a4050c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560839"
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView — Klasa

Reprezentuje widok tylko do odczytu *mapy*, który stanowi kolekcję par klucz wartość.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename K,
   typename V,
   typename C = ::std::equal_to<K>>
ref class UnorderedMapView sealed;
```

#### <a name="parameters"></a>Parametry

*K*<br/>
Typ klucza w pary klucz wartość.

*V*<br/>
Typ wartości w pary klucz wartość.

*C*<br/>
Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości klucza dla równości. Domyślnie [std::equal_to\<K >](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>Uwagi

UnorderedMapView jest konkretną implementację C++ [Windows::Foundation::Collections::IMapView\<K, V >](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) interfejsu, który jest przekazywany między interfejsem binarnym aplikacji (ABI). Aby uzyskać więcej informacji, zobacz [kolekcje (C + +/ CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[UnorderedMapView::UnorderedMapView](#ctor)|Inicjuje nowe wystąpienie klasy UnorderedMapView.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[UnorderedMapView::First](#first)|Zwraca iterator, który jest inicjowany do pierwszego elementu w widoku mapy.|
|[UnorderedMapView::HasKey](#haskey)|Określa, czy bieżący UnorderedMapView zawiera określony klucz.|
|[Unorderedmapview::LOOKUP —](#lookup)|Pobiera element w określonym kluczu w bieżącym obiekcie UnorderedMapView.|
|[Unorderedmapview::size —](#size)|Zwraca liczbę elementów w bieżącym obiekcie UnorderedMapView.|
|[UnorderedMapView::Split](#split)|Dzieli oryginalnego obiektu UnorderedMapView na dwa obiekty UnorderedMapView.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`UnorderedMapView`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Namespace:** Platform::Collections

## <a name="first"></a>  Unorderedmapview::First — metoda

Zwraca iterator, który określa pierwszy [Windows::Foundation::Collections::IKeyValuePair\<K, V >](https://msdn.microsoft.com/library/windows/apps/br226031.aspx) element mapy nieuporządkowanej.

### <a name="syntax"></a>Składnia

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element w widoku mapy.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratorów zwróconych przez First() jest przypisanie zwracana wartość do zmiennej, która jest zadeklarowana za pomocą **automatycznie** słowem kluczowym dedukcji typu. Na przykład `auto x = myMapView->First();`.

## <a name="haskey"></a>  Unorderedmapview::haskey — metoda

Określa, czy bieżący UnorderedMap zawiera określony klucz.

### <a name="syntax"></a>Składnia

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz, używana do lokalizowania elementu. Typ `key` jest typename *K*.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli klucz został znaleziony; w przeciwnym razie **false**.

## <a name="lookup"></a>  Unorderedmapview::LOOKUP — metoda

Pobiera wartość typu V, który jest skojarzony z określonym kluczem typu K.

### <a name="syntax"></a>Składnia

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz, używana do lokalizowania elementu w UnorderedMapView. Typ `key` jest typename *K*.

### <a name="return-value"></a>Wartość zwracana

Wartość, która jest powiązany z `key`. Typ wartości zwracanej jest typename *V*.

## <a name="size"></a>  Unorderedmapview::size — metoda

Zwraca liczbę [Windows::Foundation::Collections::IKeyValuePair\<K, V >](https://msdn.microsoft.com/library/windows/apps/br226031.aspx) elementów w UnorderedMapView.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w MapView nieuporządkowane.

## <a name="split"></a>  Unorderedmapview::split — metoda

Bieżący obiekt UnorderedMapView jest podzielony na dwa obiekty UnorderedMapView. Ta metoda jest nie działa.

### <a name="syntax"></a>Składnia

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * secondPartition);
```

### <a name="parameters"></a>Parametry

*firstPartition*<br/>
Pierwsza część oryginalnego obiektu UnorderedMapView.

*secondPartition*<br/>
Druga część oryginalnego obiektu UnorderedMapView.

### <a name="remarks"></a>Uwagi

Ta metoda nie działa; nic nie robi.

## <a name="ctor"></a>  Unorderedmapview::unorderedmapview — Konstruktor

Inicjuje nowe wystąpienie klasy UnorderedMapView.

### <a name="syntax"></a>Składnia

```cpp
UnorderedMapView();
explicit UnorderedMapView(size_t n);
UnorderedMapView(size_t n, const H& h);
UnorderedMapView(size_t n, const H& h, const P& p);

explicit UnorderedMapView(
    const std::unordered_map<K, V, H, P>& m);
explicit UnorderedMapView(
    std::unordered_map<K, V, H, P>&& m);

template <typename InIt> UnorderedMapView(InIt first, InIt last );
template <typename InIt> UnorderedMapView(InIt first, InIt last, size_t n );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p );

UnorderedMapView(std::initializer_list<std::pair<const K, V>);

UnorderedMapView(std::initializer_list< std::pair<const K, V>> il, size_t n

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h);

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p );
```

### <a name="parameters"></a>Parametry

*N*<br/>
Liczba elementów do wstępnie przydziel miejsce dla.

*InIt*<br/>
Element typename UnorderedMapView.

*H*<br/>
Obiekt funkcji, która może być wartość skrótu dla klucza. Wartość domyślna to [std::hash\<K >](../standard-library/hash-class.md) dla typów, `std::hash` obsługuje.

*P*<br/>
Typ, który dostarcza obiekt funkcji, która może porównać dwa klucze, aby określić ich równości. Wartość domyślna to [std::equal_to\<K >](../standard-library/equal-to-struct.md).

*m*<br/>
Odwołanie lub [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std::unordered_map](../standard-library/unordered-map-class.md) używany do zainicjowania UnorderedMapView.

*pierwszy*<br/>
Iterator danych wejściowych pierwszego elementu w zakresie elementów używane do zainicjowania UnorderedMapView.

*ostatni*<br/>
Iterator danych wejściowych od szeregu elementów używane do zainicjowania UnorderedMapView pierwszego elementu.

## <a name="see-also"></a>Zobacz też

[Platform::Collections, przestrzeń nazw](../cppcx/platform-collections-namespace.md)<br/>
[Windows::Foundation::IMapView](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_)