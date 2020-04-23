---
title: Platform::Collections::UnorderedMapView — Klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: f0096982ad5d11b9ea394c9f02ba748a52e4216b
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031488"
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView — Klasa

Reprezentuje widok tylko do odczytu na *mapie,* który jest zbiorem par klucz-wartość.

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

*C*<br/>
Typ, który udostępnia obiekt funkcji, który można porównać dwie wartości klucza dla równości. Domyślnie [std::equal_to\<K>](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>Uwagi

UnorderedMapView jest konkretną implementacją języka C++ [systemu Windows::Foundation::Collections:::IMapView\<K,V>](/uwp/api/windows.foundation.collections.imapview-2) interfejsie przekazywanym przez interfejs binarny aplikacji (ABI). Aby uzyskać więcej informacji, zobacz [Kolekcje (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[UnorderedMapView::UnorderedMapView](#ctor)|Inicjuje nowe wystąpienie klasy UnorderedMapView.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[NieuporządkowanamapaView::Najpierw](#first)|Zwraca iterator, który jest inicjowany do pierwszego elementu w widoku mapy.|
|[Nieuporządkowana mapa:](#haskey)|Określa, czy bieżący UnorderedMapView zawiera określony klucz.|
|[Nieuporządkowana mapa: odnośnik](#lookup)|Pobiera element przy określonym kluczu w bieżącym UnorderedMapView obiektu.|
|[NieuporządkowanamapaView::Rozmiar](#size)|Zwraca liczbę elementów w bieżącym obiekcie UnorderedMapView.|
|[NieuporządkowanamapaView::Split](#split)|Dzieli oryginalny obiekt UnorderedMapView na dwa obiekty UnorderedMapView.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`UnorderedMapView`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Obszar nazw:** Platforma::Kolekcje

## <a name="unorderedmapviewfirst-method"></a><a name="first"></a>NieuporządkowanamapaView::Pierwsza metoda

Zwraca iterator, który określa pierwszy [windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) element na mapie nieurządzonej.

### <a name="syntax"></a>Składnia

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element w widoku mapy.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratora zwróconego przez First() jest przypisanie wartości zwracanej do zmiennej zadeklarowanej za pomocą słowa kluczowego **automatycznego** potrącenia typu. Na przykład `auto x = myMapView->First();`.

## <a name="unorderedmapviewhaskey-method"></a><a name="haskey"></a>UnorderedMapView::Metoda HasKey

Określa, czy bieżąca mapa nieurządzony zawiera określony klucz.

### <a name="syntax"></a>Składnia

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz używany do lokalizowania elementu. Typ to `key` nazwa typu *K*.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli zostanie znaleziony klucz; w przeciwnym razie **false**.

## <a name="unorderedmapviewlookup-method"></a><a name="lookup"></a>UnorderedMapView::Metoda odnośnika

Pobiera wartość typu V, która jest skojarzona z określonym kluczem typu K.

### <a name="syntax"></a>Składnia

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz używany do lokalizowania elementu w UnorderedMapView. Typ to `key` nazwa typu *K*.

### <a name="return-value"></a>Wartość zwracana

Wartość sparowana z . `key` Typem zwracanej wartości jest nazwa typu *V*.

## <a name="unorderedmapviewsize-method"></a><a name="size"></a>UnorderedMapView::Metoda rozmiaru

Zwraca liczbę [elementów systemu Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) w widoku UnorderedMapView.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w nieuporządkowanym widoku map.

## <a name="unorderedmapviewsplit-method"></a><a name="split"></a>UnorderedMapView::Metoda podziału

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

*firstPartition (część pierwsza)*<br/>
Pierwsza część oryginalnego obiektu UnorderedMapView.

*secondPartition (drugipartition)*<br/>
Druga część oryginalnego obiektu UnorderedMapView.

### <a name="remarks"></a>Uwagi

Ta metoda nie działa; nic nie robi.

## <a name="unorderedmapviewunorderedmapview-constructor"></a><a name="ctor"></a>UnorderedMapView::UnorderedMapView Constructor

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
Liczba elementów, dla które mają być wstępnie przydzielone.

*Init*<br/>
Nazwa typu UnorderedMapView.

*H*<br/>
Obiekt funkcji, który może wartość mieszania dla klucza. Domyślnie [wartość\<std::hash K>](../standard-library/hash-class.md) dla typów, które `std::hash` obsługuje.

*P*<br/>
Typ, który udostępnia obiekt funkcji, który można porównać dwa klucze, aby określić ich równość. Domyślnie [wartość std::equal_to\<K>](../standard-library/equal-to-struct.md).

*M*<br/>
Odwołanie lub [wartości Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std::unordered_map,](../standard-library/unordered-map-class.md) który jest używany do inicjowania UnorderedMapView.

*Pierwszym*<br/>
Iterator wejściowy pierwszego elementu w zakresie elementów używanych do inicjowania UnorderedMapView.

*Ostatnio*<br/>
Iterator wejściowy pierwszego elementu po zakresie elementów używanych do inicjowania UnorderedMapView.

## <a name="see-also"></a>Zobacz też

[Platforma::Obszar nazw kolekcji](../cppcx/platform-collections-namespace.md)<br/>
[Windows::Fundacja::IMapView](/uwp/api/windows.foundation.collections.imapview-2)
