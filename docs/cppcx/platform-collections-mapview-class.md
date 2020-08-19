---
title: 'Platform:: Collections:: MapView, Klasa'
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
ms.openlocfilehash: 693854499dafd23752337652ef298907fdecbcc2
ms.sourcegitcommit: 65fead53d56d531d71be42216056aca5f44def11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2020
ms.locfileid: "88610897"
---
# <a name="platformcollectionsmapview-class"></a>Platform:: Collections:: MapView, Klasa

Reprezentuje widok tylko do odczytu w *mapie*, który jest kolekcją par klucz-wartość.

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
Typ, który dostarcza obiekt funkcji, który może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w MapView. Domyślnie [std:: less \<K> ](../standard-library/less-struct.md).

### <a name="remarks"></a>Uwagi

MapView jest konkretną implementacją języka C++ [systemu Windows:: Foundation:: Collections: \<K,V> : IMapView](/uwp/api/windows.foundation.collections.imapview-2) , który jest przesyłany przez interfejs binarny aplikacji (ABI). Aby uzyskać więcej informacji, zobacz [kolekcje (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[MapView::MapView](#ctor)|Inicjuje nowe wystąpienie klasy MapView.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[MapView:: First](#first)|Zwraca iterator, który jest zainicjowany do pierwszego elementu w widoku mapy.|
|[MapView:: Haskey —](#haskey)|Określa, czy bieżący MapView zawiera określony klucz.|
|[MapView:: Lookup](#lookup)|Pobiera element z określonego klucza w bieżącym obiekcie MapView.|
|[MapView:: size](#size)|Zwraca liczbę elementów w bieżącym obiekcie MapView.|
|[MapView:: Split](#split)|Dzieli oryginalny obiekt MapView na dwa obiekty MapView.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`MapView`

### <a name="requirements"></a>Wymagania

**Nagłówek:** Collection. h

**Przestrzeń nazw:** Platform:: Collections

## <a name="mapviewfirst-method"></a><a name="first"></a> MapView:: First — Metoda

Zwraca iterator, który określa pierwszy element w widoku mapy.

### <a name="syntax"></a>Składnia

```
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element w widoku mapy.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratora zwracanego przez First () jest przypisanie wartości zwracanej do zmiennej, która jest zadeklarowana za pomocą **`auto`** słowa kluczowego odejmowania. Na przykład `auto x = myMapView->First();`.

## <a name="mapviewhaskey-method"></a><a name="haskey"></a> MapView:: Haskey —, Metoda

Określa, czy bieżący MapView zawiera określony klucz.

### <a name="syntax"></a>Składnia

```

bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Klucz używany do lokalizowania elementu MapView. Typ *klucza* to TypeName *K*.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli klucz zostanie znaleziony; w przeciwnym razie **`false`** .

## <a name="mapviewlookup-method"></a><a name="lookup"></a> MapView:: Lookup — Metoda

Pobiera wartość typu V, która jest skojarzona z określonym kluczem typu K.

### <a name="syntax"></a>Składnia

```
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Klucz służący do lokalizowania elementu w MapView. Typ `key` to TypeName *K*.

### <a name="return-value"></a>Wartość zwracana

Wartość, która jest sparowana z `key` . Typ zwracanej wartości to TypeName *V*.

## <a name="mapviewmapview-constructor"></a><a name="ctor"></a> MapView:: MapView — Konstruktor

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

*InIt*<br/>
Wartość atrybutu TypeName bieżącego MapView.

*przepisów*<br/>
Obiekt funkcji, który może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w MapView.

*mol*<br/>
Odwołanie lub [lvalues i rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do elementu `map Class` , który jest używany do inicjowania bieżącego MapView.

*pierwszego*<br/>
Iterator wejściowy pierwszego elementu w zakresie elementów używanych do inicjowania bieżącego MapView.

*ostatniego*<br/>
Iterator wejściowy pierwszego elementu po zakresie elementów użytych do zainicjowania bieżącego MapView.

*II*<br/>
[Std:: initializer_list \<std::pair\<K,V> > ](../standard-library/initializer-list-class.md) , którego elementy zostaną wstawione do MapView.

## <a name="mapviewsize-method"></a><a name="size"></a> MapView:: size — Metoda

Zwraca liczbę elementów w bieżącym obiekcie MapView.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w bieżącym MapView.

## <a name="mapviewsplit-method"></a><a name="split"></a> MapView:: Split — metoda

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

*firstPartition*<br/>
Pierwsza część oryginalnego obiektu MapView.

*secondPartition*<br/>
Druga część oryginalnego obiektu MapView.

### <a name="remarks"></a>Uwagi

Ta metoda nie działa; nic nie robi.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](platform-namespace-c-cx.md)
