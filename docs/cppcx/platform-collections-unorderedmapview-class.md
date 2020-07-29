---
title: Platform::Collections::UnorderedMapView — Klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: acfc168959deb83244c98c5d361cf9e73c1388f2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213063"
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView — Klasa

Reprezentuje widok tylko do odczytu w *mapie*, który jest kolekcją par klucz-wartość.

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
Typ klucza w parze klucz-wartość.

*V*<br/>
Typ wartości w parze klucz-wartość.

*S*<br/>
Typ, który dostarcza obiekt funkcji, który może porównać dwie wartości klucza dla równości. Domyślnie [std:: equal_to \<K> ](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>Uwagi

UnorderedMapView jest konkretną implementacją języka C++ [systemu Windows:: Foundation:: Collections: \<K,V> : IMapView](/uwp/api/windows.foundation.collections.imapview-2) , który jest przesyłany przez interfejs binarny aplikacji (ABI). Aby uzyskać więcej informacji, zobacz [kolekcje (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[UnorderedMapView:: UnorderedMapView](#ctor)|Inicjuje nowe wystąpienie klasy UnorderedMapView.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[UnorderedMapView:: First](#first)|Zwraca iterator, który jest zainicjowany do pierwszego elementu w widoku mapy.|
|[UnorderedMapView:: Haskey —](#haskey)|Określa, czy bieżący UnorderedMapView zawiera określony klucz.|
|[UnorderedMapView:: Lookup](#lookup)|Pobiera element z określonego klucza w bieżącym obiekcie UnorderedMapView.|
|[UnorderedMapView:: size](#size)|Zwraca liczbę elementów w bieżącym obiekcie UnorderedMapView.|
|[UnorderedMapView:: Split](#split)|Dzieli oryginalny obiekt UnorderedMapView na dwa obiekty UnorderedMapView.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`UnorderedMapView`

### <a name="requirements"></a>Wymagania

**Nagłówek:** Collection. h

**Przestrzeń nazw:** Platform:: Collections

## <a name="unorderedmapviewfirst-method"></a><a name="first"></a>UnorderedMapView:: First — Metoda

Zwraca iterator, który określa pierwszy element [Windows:: Foundation:: Collections:: \<K,V> IKeyValuePair](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) w nieuporządkowanej mapie.

### <a name="syntax"></a>Składnia

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element w widoku mapy.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratora zwracanego przez First () jest przypisanie wartości zwracanej do zmiennej, która jest zadeklarowana za pomocą **`auto`** słowa kluczowego odejmowania. Na przykład `auto x = myMapView->First();`.

## <a name="unorderedmapviewhaskey-method"></a><a name="haskey"></a>UnorderedMapView:: Haskey —, Metoda

Określa, czy bieżący UnorderedMap zawiera określony klucz.

### <a name="syntax"></a>Składnia

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Klucz służący do lokalizowania elementu. Typ `key` to TypeName *K*.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli klucz zostanie znaleziony; w przeciwnym razie **`false`** .

## <a name="unorderedmapviewlookup-method"></a><a name="lookup"></a>UnorderedMapView:: Lookup — Metoda

Pobiera wartość typu V, która jest skojarzona z określonym kluczem typu K.

### <a name="syntax"></a>Składnia

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Klucz służący do lokalizowania elementu w UnorderedMapView. Typ `key` to TypeName *K*.

### <a name="return-value"></a>Wartość zwracana

Wartość, która jest sparowana z `key` . Typ zwracanej wartości to TypeName *V*.

## <a name="unorderedmapviewsize-method"></a><a name="size"></a>UnorderedMapView:: size — Metoda

Zwraca liczbę [IKeyValuePair \<K,V> elementów Windows:: Foundation:: Collections](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) w UnorderedMapView.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w nieuporządkowanej MapView.

## <a name="unorderedmapviewsplit-method"></a><a name="split"></a>UnorderedMapView:: Split — metoda

Dzieli bieżący obiekt UnorderedMapView na dwa obiekty UnorderedMapView. Ta metoda nie działa.

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

## <a name="unorderedmapviewunorderedmapview-constructor"></a><a name="ctor"></a>UnorderedMapView:: UnorderedMapView — Konstruktor

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

*Azotan*<br/>
Liczba elementów, dla których należy wstępnie przydzielić miejsce.

*InIt*<br/>
Nazwa typu UnorderedMapView.

*C*<br/>
Obiekt funkcji, który może mieć wartość skrótu dla klucza. Wartość domyślna to [std:: \<K> hash](../standard-library/hash-class.md) dla typów, które `std::hash` obsługują.

*P*<br/>
Typ, który dostarcza obiekt funkcji, który może porównać dwa klucze w celu określenia ich równości. Wartość domyślna to [std:: \<K> equal_to](../standard-library/equal-to-struct.md).

*mol*<br/>
Odwołanie lub [lvalues i rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std:: unordered_map](../standard-library/unordered-map-class.md) , który jest używany do inicjowania UnorderedMapView.

*pierwszego*<br/>
Iterator wejściowy pierwszego elementu w zakresie elementów używanych do inicjowania UnorderedMapView.

*ostatniego*<br/>
Iterator wejściowy pierwszego elementu po zakresie elementów użytych do zainicjowania UnorderedMapView.

## <a name="see-also"></a>Zobacz także

[Platform:: Collections, przestrzeń nazw](../cppcx/platform-collections-namespace.md)<br/>
[Windows:: Foundation:: IMapView](/uwp/api/windows.foundation.collections.imapview-2)
