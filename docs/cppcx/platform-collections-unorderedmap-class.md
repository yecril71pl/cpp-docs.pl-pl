---
title: Platform::Collections::UnorderedMap — Klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: c6f702850f5bf84b8b1bc857c9d0a744728d0cbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354421"
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap — Klasa

Reprezentuje nieuiszczona *mapa*, która jest kolekcją par klucz-wartość.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename K,
   typename V,
   typename C = std::equal_to<K>
>
ref class Map sealed;
```

#### <a name="parameters"></a>Parametry

*K*<br/>
Typ klucza w parze klucz-wartość.

*V*<br/>
Typ wartości w parze klucz-wartość.

*C*<br/>
Typ, który udostępnia obiekt funkcji, który może porównać dwie wartości elementu jako klucze sortowania w celu określenia ich względnej kolejności na mapie. Domyślnie [std::equal_to\<K>](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Uwagi

Dozwolone typy to:

- liczby całkowite

- klasa interfejsu^

- publiczna klasa ref^

- struktura wartości

- klasa wyliczenia publicznego

**UnorderedMap** jest w zasadzie otoką dla [std::unordered_map,](../standard-library/unordered-map-class.md) która obsługuje przechowywanie typów środowiska wykonawczego systemu Windows. Jest to konkretna implementacja [typów windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) i [IObservableMap,](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) które są przekazywane przez publiczne interfejsy środowiska wykonawczego systemu Windows. Jeśli spróbujesz `Platform::Collections::UnorderedMap` użyć typu w public return wartość lub parametr, błąd kompilatora C3986 jest wywoływana. Błąd można naprawić, zmieniając typ parametru lub zwracając wartość do [systemu Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Aby uzyskać więcej informacji, zobacz [Kolekcje](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Nieuchorowanamapa::Nieurządzonymap](#ctor)|Inicjuje nowe wystąpienie klasy Map.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Nieuiarszonamapa::Wyczyść](#clear)|Usuwa wszystkie pary klucz-wartość z bieżącego obiektu Mapa.|
|[Nieuiarszonamapa::Najpierw](#first)|Zwraca iterator, który określa pierwszy element na mapie.|
|[Nieuporządkowanamapa::GetView](#getview)|Zwraca widok tylko do odczytu bieżącej mapy; oznacza to, że platforma::Collections::UnorderedMapView Class.|
|[Nieuiarszonamapa::HasKey](#haskey)|Określa, czy bieżąca mapa zawiera określony klucz.|
|[Nieuiarszonamapa::Wstawianie](#insert)|Dodaje określoną parę klucz-wartość do bieżącego obiektu Map.|
|[Nieuiarszonamapa::Odnośnik](#lookup)|Pobiera element przy określonym kluczu w bieżącym obiekcie Map.|
|[Nieuiarszonamapa::Usuń](#remove)|Usuwa określoną parę klucz-wartość z bieżącego obiektu Map.|
|[Nieuiarszonamapa::Rozmiar](#size)|Zwraca liczbę elementów w bieżącym obiekcie Mapa.|

### <a name="events"></a>Zdarzenia

|||
|-|-|
|Nazwa|Opis|
|[Mapa::MapChanged](#mapchanged) zdarzenie|Występuje, gdy mapa się zmienia.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`UnorderedMap`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Obszar nazw:** Platforma::Kolekcje

## <a name="unorderedmapclear-method"></a><a name="clear"></a>Nieuiarszonamapa::Wyczyść metodę

Usuwa wszystkie pary klucz-wartość z bieżącego obiektu UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual void Clear();
```

## <a name="unorderedmapfirst-method"></a><a name="first"></a>Nieuiarszonamapa::Pierwsza metoda

Zwraca iterator, który określa pierwszy [windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) element na mapie nieurządzonej.

### <a name="syntax"></a>Składnia

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element na mapie.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratora zwróconego przez First() jest przypisanie wartości zwracanej do zmiennej zadeklarowanej za pomocą słowa kluczowego **automatycznego** potrącenia typu. Na przykład `auto x = myUnorderedMap->First();`.

## <a name="unorderedmapgetview-method"></a><a name="getview"></a>Nieuporządkowanamapa::Metoda GetView

Zwraca widok tylko do odczytu bieżącej mapy nieuporządkowanego; oznacza to, że [platforma::Kolekcje::UnorderedMapView Klasa,](../cppcx/platform-collections-unorderedmapview-class.md) która implementuje [Windows::Foundation::Collections::IMapView::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) interfejs.

### <a name="syntax"></a>Składnia

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `UnorderedMapView`.

## <a name="unorderedmaphaskey-method"></a><a name="haskey"></a>UnorderedMap::Metoda HasKey

Określa, czy bieżąca mapa nieurządzony zawiera określony klucz.

### <a name="syntax"></a>Składnia

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz używany do lokalizowania Elementu UnorderedMap. Typ *klucza* to nazwa typu *K*.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli zostanie znaleziony klucz; w przeciwnym razie **false**.

## <a name="unorderedmapinsert-method"></a><a name="insert"></a>Nieuiarszonamapa::Metoda wstawiania

Dodaje określoną parę klucz-wartość do bieżącego obiektu UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Kluczowa część pary klucz-wartość. Typ *klucza* to nazwa typu *K*.

*value*<br/>
Część wartości pary klucz-wartość. Typem *wartości* jest nazwa typu *V*.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli klucz istniejącego elementu w bieżącej mapie pasuje *do klucza,* a część wartości tego elementu jest *ustawiona*na wartość . **false,** jeśli żaden istniejący element w bieżącym Mapa pasuje *do klucza,* a parametry *klucza* i *wartości* są przekształcane w parę klucz-wartość, a następnie dodawane do bieżącego UnorderedMap.

## <a name="unorderedmaplookup-method"></a><a name="lookup"></a>Nieuchorowanamapa::Metoda odnośnika

Pobiera wartość typu V, która jest skojarzona z określonym kluczem typu K.

### <a name="syntax"></a>Składnia

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz używany do lokalizowania elementu w UnorderedMap. Typ *klucza* to nazwa typu *K*.

### <a name="return-value"></a>Wartość zwracana

Wartość sparowana z *kluczem*. Typem zwracanej wartości jest nazwa typu *V*.

## <a name="unorderedmapmapchanged"></a><a name="mapchanged"></a>Nieuchorowanamapa::MapChanged

Wywoływane, gdy element zostanie wstawiony lub usunięty z mapy.

### <a name="syntax"></a>Składnia

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

[MapChangedEventHandler\<K,V>,](/uwp/api/windows.foundation.collections.mapchangedeventhandler) który zawiera informacje o obiekcie, który wywołał zdarzenie i rodzaj zmiany, która wystąpiła. Zobacz też [IMapChangedEventArgs\<K>](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) i [CollectionChange Wyliczenie](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework

Aplikacje środowiska wykonawczego systemu Windows, które\<nas C# lub Visual Basic\<projektu IMap K, V> jako IDictionary K, V>.

## <a name="unorderedmapremove-method"></a><a name="remove"></a>Nieuiarszonamapa::Metoda usuwania

Usuwa określoną parę klucz-wartość z obiektu UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Kluczowa część pary klucz-wartość. Typ *klucza* to nazwa typu *K*.

## <a name="unorderedmapsize-method"></a><a name="size"></a>Nieuiarszonamapa::Metoda rozmiaru

Zwraca liczbę [elementów systemu Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) w nieuległym zamówićmapie.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na mapie nieurządzone.

## <a name="unorderedmapunorderedmap-constructor"></a><a name="ctor"></a>UnorderedMap::UnorderedMap Constructor

Inicjuje nowe wystąpienie klasy UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
UnorderedMap();

explicit UnorderedMap(
    size_t n
    );

UnorderedMap(
    size_t n,
    const H& h
    );

UnorderedMap(
    size_t n,
    const H& h,
    const P& p
    );

explicit UnorderedMap(
    const std::unordered_map<K, V, H, P>& m
    );

explicit UnorderedMap(
    std::unordered_map<K, V, H, P>&& m
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p
    );
```

### <a name="parameters"></a>Parametry

*Init*<br/>
Nazwa typu bieżącej mapy nieurządzonych.

*P*<br/>
Obiekt funkcji, który można porównać dwa klucze, aby ustalić, czy są one równe. Ten parametr jest domyślnie [std::equal_to\<K>](../standard-library/equal-to-struct.md).

*H*<br/>
Obiekt funkcji, który tworzy wartość mieszania dla kluczy. Ten parametr domyślnie [hash klasy 1](../standard-library/hash-class.md) dla typów kluczy, które obsługuje klasy.

*M*<br/>
Odwołanie lub [wartości Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std::unordered_map,](../standard-library/unordered-map-class.md) który jest używany do inicjowania bieżącego UnorderedMap.

*Il*<br/>
[Std::initializer_list](../standard-library/initializer-list-class.md) [obiektów std::pair,](../standard-library/pair-structure.md) który jest używany do inicjowania mapy.

*Pierwszym*<br/>
Iterator wejściowy pierwszego elementu w zakresie elementów używanych do inicjowania bieżącego UnorderedMap.

*Ostatnio*<br/>
Iterator wejściowy pierwszego elementu po zakresie elementów używanych do inicjowania bieżącego UnorderedMap.

## <a name="see-also"></a>Zobacz też

[Obszar nazw platformy](platform-namespace-c-cx.md)<br/>
[Platforma::Obszar nazw kolekcji](../cppcx/platform-collections-namespace.md)<br/>
[Platform::Collections::Map, klasa](../cppcx/platform-collections-map-class.md)<br/>
[Platform::Collections::UnorderedMapView, klasa](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[Kolekcje](../cppcx/collections-c-cx.md)<br/>
[Tworzenie składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
