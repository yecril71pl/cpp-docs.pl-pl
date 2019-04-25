---
title: 'Platform::Collections:: mapview, klasa'
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
ms.openlocfilehash: 1e38865f1d43edac4fc895052f1ea1b5a54a34ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161715"
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections:: mapview, klasa

Reprezentuje widok tylko do odczytu *mapy*, który stanowi kolekcję par klucz wartość.

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
Typ klucza w pary klucz wartość.

*V*<br/>
Typ wartości w pary klucz wartość.

*C*<br/>
Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w MapView. Domyślnie [std::less\<K >](../standard-library/less-struct.md).

### <a name="remarks"></a>Uwagi

MapView jest konkretną implementację C++ [Windows::Foundation::Collections::IMapView \<K, V >](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) interfejsu, który jest przekazywany między interfejsem binarnym aplikacji (ABI). Aby uzyskać więcej informacji, zobacz [kolekcji (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[MapView::MapView](#ctor)|Inicjuje nowe wystąpienie klasy MapView.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[MapView::First](#first)|Zwraca iterator, który jest inicjowany do pierwszego elementu w widoku mapy.|
|[MapView::HasKey](#haskey)|Określa, czy bieżący MapView zawiera określony klucz.|
|[MapView::Lookup](#lookup)|Pobiera element w określonym kluczu w bieżącym obiekcie MapView.|
|[MapView::Size](#size)|Zwraca liczbę elementów w bieżącym obiekcie MapView.|
|[MapView::Split](#split)|Dzieli oryginalnego obiektu MapView na dwa obiekty MapView.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`MapView`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Namespace:** Platform::Collections

## <a name="first"></a> Metoda MapView::First

Zwraca iterator, który określa pierwszy element w widoku mapy.

### <a name="syntax"></a>Składnia

```
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element w widoku mapy.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratorów zwróconych przez First() jest przypisanie zwracana wartość do zmiennej, która jest zadeklarowana za pomocą **automatycznie** słowem kluczowym dedukcji typu. Na przykład `auto x = myMapView->First();`.

## <a name="haskey"></a>  Metoda MapView::HasKey

Określa, czy bieżący MapView zawiera określony klucz.

### <a name="syntax"></a>Składnia

```

bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz, używana do lokalizowania elementu MapView. Typ *klucz* jest typename *K*.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli klucz został znaleziony; w przeciwnym razie **false**.

##  <a name="lookup"></a> Metoda MapView::Lookup

Pobiera wartość typu V, który jest skojarzony z określonym kluczem typu K.

### <a name="syntax"></a>Składnia

```
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz, używana do lokalizowania elementu w MapView. Typ `key` jest typename *K*.

### <a name="return-value"></a>Wartość zwracana

Wartość, która jest powiązany z `key`. Typ wartości zwracanej jest typename *V*.

##  <a name="ctor"></a> Konstruktor MapView::MapView

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
Element typename MapView bieżącego.

*comp*<br/>
Obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w MapView.

*m*<br/>
Odwołanie lub [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do `map Class` używany do zainicjowania MapView bieżącego.

*pierwszy*<br/>
Iterator danych wejściowych pierwszego elementu w zakresie elementów używane do zainicjowania MapView bieżącego.

*last*<br/>
Iterator danych wejściowych od szeregu elementów używane do zainicjowania bieżącego MapView pierwszego elementu.

*il*<br/>
A [std::initializer_list < std::pair\<K, V >>](../standard-library/initializer-list-class.md) której elementy zostaną wstawione do MapView.

##  <a name="size"></a> Metoda MapView::Size

Zwraca liczbę elementów w bieżącym obiekcie MapView.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w bieżącym MapView.

##  <a name="split"></a> Metoda MapView::Split

Bieżący obiekt MapView jest podzielony na dwa obiekty MapView. Ta metoda jest nie działa.

### <a name="syntax"></a>Składnia

```
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

## <a name="see-also"></a>Zobacz także

[Namespace platformy](platform-namespace-c-cx.md)
