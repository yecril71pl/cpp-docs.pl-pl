---
title: Platform::Collections::Map, klasa
ms.date: 10/01/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Map::Map
- COLLECTION/Platform::Collections::Map::Clear
- COLLECTION/Platform::Collections::Map::First
- COLLECTION/Platform::Collections::Map::GetView
- COLLECTION/Platform::Collections::Map::HasKey
- COLLECTION/Platform::Collections::Map::Insert
- COLLECTION/Platform::Collections::Map::Lookup
- COLLECTION/Platform::Collections::Map::Remove
- COLLECTION/Platform::Collections::Map::Size
helpviewer_keywords:
- Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
ms.openlocfilehash: ff27f6c543a2326dd4318f66aae51b89092b28e2
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032450"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map, klasa

Reprezentuje *mapę*, która jest kolekcją par klucz-wartość. Implementuje [system Windows::Foundation::Collections::IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) w celu pomocy w [wiązaniu danych](/windows/uwp/data-binding/data-binding-in-depth)XAML .

## <a name="syntax"></a>Składnia

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>Parametry

*K*<br/>
Typ klucza w parze klucz-wartość.

*V*<br/>
Typ wartości w parze klucz-wartość.

*C*<br/>
Typ, który udostępnia obiekt funkcji, który może porównać dwie wartości elementu jako klucze sortowania w celu określenia ich względnej kolejności na mapie. Domyślnie [std::less\<K>](../standard-library/less-struct.md).

*__is_valid_winrt_type()* Funkcja generowana przez kompilator, która sprawdza poprawność typu *K* i *V* i zapewnia przyjazny komunikat o błędzie, jeśli typ nie może być przechowywany na mapie.

### <a name="remarks"></a>Uwagi

Dozwolone typy to:

- liczby całkowite

- klasa interfejsu^

- publiczna klasa ref^

- struktura wartości

- klasa wyliczenia publicznego

Mapa jest w zasadzie otoką dla [std::map](../standard-library/map-class.md). Jest to konkretna implementacja [systemu Windows::Foundation::Collections::IMap<Windows::Foundation::Collections::IKeyValuePair\<K,V>>](/uwp/api/windows.foundation.collections.imap-2) i [IObservableMap,](/uwp/api/windows.foundation.collections.iobservablemap-2) które są przekazywane przez publiczne interfejsy środowiska wykonawczego systemu Windows. Jeśli spróbujesz `Platform::Collections::Map` użyć typu w public return wartość lub parametr, błąd kompilatora C3986 jest wywoływana. Błąd można naprawić, zmieniając typ parametru lub zwracając wartość do [systemu Windows::Foundation::Collections::IMap\<K,V>](/uwp/api/windows.foundation.collections.imap-2).

Aby uzyskać więcej informacji, zobacz [Kolekcje](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Mapa::Mapa](#ctor)|Inicjuje nowe wystąpienie klasy Map.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Mapa::Wyczyść](#clear)|Usuwa wszystkie pary klucz-wartość z bieżącego obiektu Mapa.|
|[Mapa::Najpierw](#first)|Zwraca iterator, który określa pierwszy element na mapie.|
|[Mapa::GetView](#getview)|Zwraca widok tylko do odczytu bieżącej mapy; oznacza to, [że platforma::Kolekcje::Klasa MapView](../cppcx/platform-collections-mapview-class.md).|
|[Mapa::HasKey](#haskey)|Określa, czy bieżąca mapa zawiera określony klucz.|
|[Mapa::Wstaw](#insert)|Dodaje określoną parę klucz-wartość do bieżącego obiektu Map.|
|[Mapa::Wyszukiwanie](#lookup)|Pobiera element przy określonym kluczu w bieżącym obiekcie Map.|
|[Mapa::Usuń](#remove)|Usuwa określoną parę klucz-wartość z bieżącego obiektu Map.|
|[Mapa::Rozmiar](#size)|Zwraca liczbę elementów w bieżącym obiekcie Mapa.|

### <a name="events"></a>Zdarzenia

|||
|-|-|
|Nazwa|Opis|
|[Mapa::MapChanged](#mapchanged) zdarzenie|Występuje, gdy mapa się zmienia.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Map`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Obszar nazw:** Platforma::Kolekcje

## <a name="mapclear-method"></a><a name="clear"></a>Mapa::Wyczyść metodę

Usuwa wszystkie pary klucz-wartość z bieżącego obiektu Mapa.

### <a name="syntax"></a>Składnia

```cpp
virtual void Clear();
```

## <a name="mapfirst-method"></a><a name="first"></a>Mapa::Pierwsza metoda

Zwraca iterator, który określa pierwszy element na `nullptr` mapie lub jeśli mapa jest pusta.

### <a name="syntax"></a>Składnia

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element na mapie.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratora zwróconego przez First() jest przypisanie wartości zwracanej do zmiennej zadeklarowanej za pomocą słowa kluczowego **automatycznego** potrącenia typu. Na przykład `auto x = myMap->First();`.

## <a name="mapgetview-method"></a><a name="getview"></a>Mapa::Metoda GetView

Zwraca widok tylko do odczytu bieżącej mapy; oznacza to [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md), który implementuje [interfejs systemu Windows::Foundation::Collections::IMapView\<K,V>.](/uwp/api/windows.foundation.collections.imapview-2)

### <a name="syntax"></a>Składnia

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `MapView`.

## <a name="maphaskey-method"></a><a name="haskey"></a>Mapa::Metoda HasKey

Określa, czy bieżąca mapa zawiera określony klucz.

### <a name="syntax"></a>Składnia

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz używany do lokalizowania elementu Mapa. Typ *klucza* to nazwa typu *K*.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli zostanie znaleziony klucz; w przeciwnym razie **false**.

## <a name="mapinsert-method"></a><a name="insert"></a>Mapa::Metoda wstawiania

Dodaje określoną parę klucz-wartość do bieżącego obiektu Map.

### <a name="syntax"></a>Składnia

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Kluczowa część pary klucz-wartość. Typ *klucza* to nazwa typu *K*.

*value*<br/>
Część wartości pary klucz-wartość. Typem *wartości* jest nazwa typu *V*.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli klucz istniejącego elementu w bieżącej mapie pasuje *do klucza,* a część wartości tego elementu jest *ustawiona*na wartość . **false,** jeśli żaden istniejący element w bieżącym Mapa pasuje *do klucza,* a parametry *klucza* i *wartości* są przekształcane w parę klucz-wartość, a następnie dodawane do bieżącej mapy.

## <a name="maplookup-method"></a><a name="lookup"></a>Mapa::Metoda odnośnika

Pobiera wartość typu V, która jest skojarzona z określonym kluczem typu K, jeśli klucz istnieje.

### <a name="syntax"></a>Składnia

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz używany do lokalizowania elementu na mapie. Typ *klucza* to nazwa typu *K*.

### <a name="return-value"></a>Wartość zwracana

Wartość sparowana z *kluczem*. Typem zwracanej wartości jest nazwa typu *V*.

### <a name="remarks"></a>Uwagi

Jeśli klucz nie istnieje, a następnie [Platform::OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md) jest generowany.

## <a name="mapmap-constructor"></a><a name="ctor"></a>Mapa::Konstruktor map

Inicjuje nowe wystąpienie klasy Map.

### <a name="syntax"></a>Składnia

```cpp
explicit Map(const C& comp = C());
explicit Map(const StdMap& m);
explicit Map(StdMap&& m ;
template <typename InIt>
Map(
   InItfirst,
   InItlast,
   const C& comp = C());
```

### <a name="parameters"></a>Parametry

*Init*<br/>
Nazwa typu bieżącej mapy.

*Komp*<br/>
Typ, który udostępnia obiekt funkcji, który może porównać dwie wartości elementu jako klucze sortowania w celu określenia ich względnej kolejności na mapie.

*M*<br/>
Odwołanie lub [wartość rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) do, `map Class` który jest używany do inicjowania bieżącej mapy.

*Pierwszym*<br/>
Iterator wejściowy pierwszego elementu w zakresie elementów używanych do inicjowania bieżącej mapy.

*Ostatnio*<br/>
Iterator wejściowy pierwszego elementu po zakresie elementów używanych do inicjowania bieżącej mapy.

## <a name="mapmapchanged-event"></a><a name="mapchanged"></a>Mapa::MapChanged Zdarzenie

Wywoływane, gdy element zostanie wstawiony lub usunięty z mapy.

### <a name="syntax"></a>Składnia

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

[MapChangedEventHandler\<K,V>,](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) który zawiera informacje o obiekcie, który wywołał zdarzenie i rodzaj zmiany, która wystąpiła. Zobacz też [IMapChangedEventArgs\<K>](/uwp/api/windows.foundation.collections.imapchangedeventargs-1) i [CollectionChange Wyliczenie](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework

Aplikacje środowiska wykonawczego systemu Windows, które\<używają języka C# lub Visual Basic\<projektu IMap K, V> jako IDictionary K, V>.

## <a name="mapremove-method"></a><a name="remove"></a>Mapa::Metoda usuwania

Usuwa określoną parę klucz-wartość z bieżącego obiektu Map.

### <a name="syntax"></a>Składnia

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Kluczowa część pary klucz-wartość. Typ *klucza* to nazwa typu *K*.

## <a name="mapsize-method"></a><a name="size"></a>Mapa::Metoda rozmiaru

Zwraca liczbę [elementów systemu Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) na mapie.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na mapie.

## <a name="see-also"></a>Zobacz też

[Kolekcje (C++/CX)](collections-c-cx.md)<br/>
[Obszar nazw platformy](platform-namespace-c-cx.md)<br/>
[Tworzenie składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
