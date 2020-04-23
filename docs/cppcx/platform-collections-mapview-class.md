---
title: Platform::Collections::MapView, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
ms.openlocfilehash: a770b318d893b9e81bdf11a75c2b0b05c0a9979f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750612"
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections::MapView, klasa

Reprezentuje widok tylko do odczytu na *mapie,* który jest zbiorem par klucz-wartość.

## <a name="syntax"></a>Składnia

```
template <
   typename K,
   typename V,
   typename C = ::std::less<K>>
ref class MapView sealed;
```

#### <a name="parameters"></a>Parametry

*K*<br/>
Typ klucza w parze klucz-wartość.

*V*<br/>
Typ wartości w parze klucz-wartość.

*C*<br/>
Typ, który udostępnia obiekt funkcji, który może porównać dwie wartości elementu jako klucze sortowania, aby określić ich względną kolejność w MapView. Domyślnie [std::less\<K>](../standard-library/less-struct.md).

### <a name="remarks"></a>Uwagi

MapView jest konkretną implementacją języka C++ [systemu Windows::Foundation::Collections::IMapView \<K,V>interfejsie,](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) który jest przekazywany przez interfejs binarny aplikacji (ABI). Aby uzyskać więcej informacji, zobacz [Kolekcje (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Widok map::Widok map](#ctor)|Inicjuje nowe wystąpienie klasy MapView.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Widok map::Najpierw](#first)|Zwraca iterator, który jest inicjowany do pierwszego elementu w widoku mapy.|
|[MapView::HasKey](#haskey)|Określa, czy bieżący MapView zawiera określony klucz.|
|[Widok map::wyszukiwanie](#lookup)|Pobiera element przy określonym kluczu w bieżącym obiekcie MapView.|
|[Widok map::Rozmiar](#size)|Zwraca liczbę elementów w bieżącym obiekcie MapView.|
|[Widok map::Podziel](#split)|Dzieli oryginalny obiekt MapView na dwa obiekty MapView.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`MapView`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Obszar nazw:** Platforma::Kolekcje

## <a name="mapviewfirst-method"></a><a name="first"></a>MapView::Pierwsza metoda

Zwraca iterator, który określa pierwszy element w widoku mapy.

### <a name="syntax"></a>Składnia

```
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element w widoku mapy.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratora zwróconego przez First() jest przypisanie wartości zwracanej do zmiennej zadeklarowanej za pomocą słowa kluczowego **automatycznego** potrącenia typu. Na przykład `auto x = myMapView->First();`.

## <a name="mapviewhaskey-method"></a><a name="haskey"></a>MapView::Metoda HasKey

Określa, czy bieżący MapView zawiera określony klucz.

### <a name="syntax"></a>Składnia

```

bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz używany do lokalizowania elementu MapView. Typ *klucza* to nazwa typu *K*.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli zostanie znaleziony klucz; w przeciwnym razie **false**.

## <a name="mapviewlookup-method"></a><a name="lookup"></a>MapView::Metoda odnośnika

Pobiera wartość typu V, która jest skojarzona z określonym kluczem typu K.

### <a name="syntax"></a>Składnia

```
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz używany do lokalizowania elementu w MapView. Typ to `key` nazwa typu *K*.

### <a name="return-value"></a>Wartość zwracana

Wartość sparowana z . `key` Typem zwracanej wartości jest nazwa typu *V*.

## <a name="mapviewmapview-constructor"></a><a name="ctor"></a>MapView::Konstruktor mapview

Inicjuje nowe wystąpienie klasy MapView.

### <a name="syntax"></a>Składnia

```cpp
explicit MapView(const C& comp = C());

explicit MapView(const ::std::map<K, V, C>& m);

explicit MapView(std::map<K, V, C>&& m);

template <typename InIt> MapView(
    InIt first,
    InIt last,
    const C& comp = C());

MapView(
    ::std::initializer_list<std::pair<const K, V>> il,
    const C& comp = C());
```

### <a name="parameters"></a>Parametry

*Init*<br/>
Nazwa typu bieżącego widoku map.

*Komp*<br/>
Obiekt funkcji, który może porównać dwie wartości elementów jako klucze sortowania w celu określenia ich względnej kolejności w MapView.

*M*<br/>
Odwołanie lub [wartości Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) `map Class` do, który jest używany do inicjowania bieżącego MapView.

*Pierwszym*<br/>
Iterator wejściowy pierwszego elementu w zakresie elementów używanych do inicjowania bieżącego MapView.

*Ostatnio*<br/>
Iterator wejściowy pierwszego elementu po zakresie elementów używanych do inicjowania bieżącego MapView.

*Il*<br/>
[Std::initializer_list<\<std::pair K,V>>](../standard-library/initializer-list-class.md) których elementy zostaną wstawione do MapView.

## <a name="mapviewsize-method"></a><a name="size"></a>MapView::Metoda rozmiaru

Zwraca liczbę elementów w bieżącym obiekcie MapView.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w bieżącym MapView.

## <a name="mapviewsplit-method"></a><a name="split"></a>MapView::Metoda podziału

Dzieli bieżący obiekt MapView na dwa obiekty MapView. Ta metoda nie działa.

### <a name="syntax"></a>Składnia

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * secondPartition);
```

### <a name="parameters"></a>Parametry

*firstPartition (część pierwsza)*<br/>
Pierwsza część oryginalnego obiektu MapView.

*secondPartition (drugipartition)*<br/>
Druga część oryginalnego obiektu MapView.

### <a name="remarks"></a>Uwagi

Ta metoda nie działa; nic nie robi.

## <a name="see-also"></a>Zobacz też

[Obszar nazw platformy](platform-namespace-c-cx.md)
