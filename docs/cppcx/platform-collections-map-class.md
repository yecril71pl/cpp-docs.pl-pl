---
title: 'Platform:: Collections:: map, Klasa'
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
ms.openlocfilehash: 30dbc71a03c398c77124738b2477a3563191d50d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214987"
---
# <a name="platformcollectionsmap-class"></a>Platform:: Collections:: map, Klasa

Reprezentuje *mapę*, która jest kolekcją par klucz-wartość. Implementuje [system Windows:: Foundation:: Collections:: IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) , aby pomóc w [powiązaniu danych](/windows/uwp/data-binding/data-binding-in-depth)XAML.

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

*S*<br/>
Typ, który dostarcza obiekt funkcji, który może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w mapie. Domyślnie [std:: less \<K> ](../standard-library/less-struct.md).

*__is_valid_winrt_type ()* Funkcja wygenerowana przez kompilator, która sprawdza poprawność typu *K* i *V* i zapewnia przyjazny komunikat o błędzie, jeśli typ nie może być przechowywany w mapie.

### <a name="remarks"></a>Uwagi

Dozwolone typy to:

- integers

- Klasa interfejsu ^

- publiczna Klasa referencyjna ^

- Struktura wartości

- publiczna Klasa enum

Mapa jest zasadniczo otoką dla elementu [std:: map](../standard-library/map-class.md). Jest to konkretna implementacja języka C++ dla [systemu Windows:: Foundation:: Collections:: IMAP<Windows:: Foundation:: Collections \<K,V> > ](/uwp/api/windows.foundation.collections.imap-2) i [IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) , które są przesyłane przez interfejsy środowisko wykonawcze systemu Windows publicznego. Jeśli spróbujesz użyć `Platform::Collections::Map` typu w publicznej wartości zwracanej lub parametrze, zostanie zgłoszony błąd kompilatora C3986. Możesz naprawić ten błąd, zmieniając typ parametru lub wartość zwrotną na [Windows:: Foundation:: Collections:: IMAP \<K,V> ](/uwp/api/windows.foundation.collections.imap-2).

Aby uzyskać więcej informacji, zobacz [kolekcje](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Map:: map](#ctor)|Inicjuje nowe wystąpienie klasy map.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Map:: Clear](#clear)|Usuwa wszystkie pary klucz-wartość z bieżącego obiektu mapy.|
|[Map:: First](#first)|Zwraca iterator, który określa pierwszy element na mapie.|
|[Mapa:: GetView](#getview)|Zwraca widok tylko do odczytu bieżącej mapy; oznacza to, że [Klasa platform:: Collections:: MapView](../cppcx/platform-collections-mapview-class.md).|
|[Map:: Haskey —](#haskey)|Określa, czy bieżąca Mapa zawiera określony klucz.|
|[Map:: INSERT](#insert)|Dodaje określoną parę klucz-wartość do bieżącego obiektu mapy.|
|[Map:: Lookup](#lookup)|Pobiera element z określonego klucza w obiekcie mapy bieżącej.|
|[Map:: Remove](#remove)|Usuwa określoną parę klucz-wartość z bieżącego obiektu mapy.|
|[Map:: size](#size)|Zwraca liczbę elementów w bieżącym obiekcie mapy.|

### <a name="events"></a>Zdarzenia

|||
|-|-|
|Nazwa|Opis|
|[Map:: MapChanged](#mapchanged) , zdarzenie|Występuje, gdy mapa zostanie zmieniona.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Map`

### <a name="requirements"></a>Wymagania

**Nagłówek:** Collection. h

**Przestrzeń nazw:** Platform:: Collections

## <a name="mapclear-method"></a><a name="clear"></a>Map:: Clear — Metoda

Usuwa wszystkie pary klucz-wartość z bieżącego obiektu mapy.

### <a name="syntax"></a>Składnia

```cpp
virtual void Clear();
```

## <a name="mapfirst-method"></a><a name="first"></a>Map:: First — Metoda

Zwraca iterator, który określa pierwszy element na mapie, lub **`nullptr`** Jeśli mapa jest pusta.

### <a name="syntax"></a>Składnia

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element na mapie.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratora zwracanego przez First () jest przypisanie wartości zwracanej do zmiennej, która jest zadeklarowana za pomocą **`auto`** słowa kluczowego odejmowania. Na przykład `auto x = myMap->First();`.

## <a name="mapgetview-method"></a><a name="getview"></a>Map:: GetView — metoda

Zwraca widok tylko do odczytu bieżącej mapy; oznacza to, że [Klasa platform:: Collections:: MapView](../cppcx/platform-collections-mapview-class.md), która implementuje interfejs [systemu Windows:: Foundation:: Collections \<K,V> :: IMapView](/uwp/api/windows.foundation.collections.imapview-2) .

### <a name="syntax"></a>Składnia

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `MapView`.

## <a name="maphaskey-method"></a><a name="haskey"></a>Map:: Haskey —, Metoda

Określa, czy bieżąca Mapa zawiera określony klucz.

### <a name="syntax"></a>Składnia

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Klucz służący do lokalizowania elementu mapy. Typ *klucza* to TypeName *K*.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli klucz zostanie znaleziony; w przeciwnym razie **`false`** .

## <a name="mapinsert-method"></a><a name="insert"></a>Map:: Insert — Metoda

Dodaje określoną parę klucz-wartość do bieżącego obiektu mapy.

### <a name="syntax"></a>Składnia

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Część klucza pary klucz-wartość. Typ *klucza* to TypeName *K*.

*wartościami*<br/>
Część wartości pary klucz-wartość. Typ *wartości* to TypeName *V*.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli klucz istniejącego elementu w bieżącej mapie pasuje do *klucza* , a część wartości tego elementu jest ustawiona na *wartość Value*. **`false`** Jeśli żaden istniejący element w bieżącej mapie nie pasuje do *klucza* , a parametry *klucza* i *wartości* są wprowadzane do pary klucz-wartość, a następnie dodane do bieżącej mapy.

## <a name="maplookup-method"></a><a name="lookup"></a>Map:: Lookup — Metoda

Pobiera wartość typu V, która jest skojarzona z określonym kluczem typu K, jeśli istnieje klucz.

### <a name="syntax"></a>Składnia

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Klucz służący do lokalizowania elementu na mapie. Typ *klucza* to TypeName *K*.

### <a name="return-value"></a>Wartość zwracana

Wartość sparowana z *kluczem*. Typ zwracanej wartości to TypeName *V*.

### <a name="remarks"></a>Uwagi

Jeśli klucz nie istnieje, zostanie zgłoszony obiekt [platform:: OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md) .

## <a name="mapmap-constructor"></a><a name="ctor"></a>Map:: map — Konstruktor

Inicjuje nowe wystąpienie klasy map.

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

*InIt*<br/>
Wartość atrybutu TypeName bieżącej mapy.

*przepisów*<br/>
Typ, który dostarcza obiekt funkcji, który może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w mapie.

*mol*<br/>
Odwołanie lub [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) do elementu `map Class` , który jest używany do inicjowania bieżącej mapy.

*pierwszego*<br/>
Iterator wejściowy pierwszego elementu w zakresie elementów używanych do inicjowania bieżącej mapy.

*ostatniego*<br/>
Iterator wejściowy pierwszego elementu po zakresie elementów użytych do zainicjowania bieżącej mapy.

## <a name="mapmapchanged-event"></a><a name="mapchanged"></a>Map:: MapChanged, zdarzenie

Uruchamiany, gdy element zostanie wstawiony do mapy lub usunięty z niego.

### <a name="syntax"></a>Składnia

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Element [MapChangedEventHandler \<K,V> ](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) , który zawiera informacje o obiekcie, który spowodował zdarzenie, oraz o rodzaju zmiany, które wystąpiły. Zobacz również [Wyliczenie \<K> IMapChangedEventArgs](/uwp/api/windows.foundation.collections.imapchangedeventargs-1) i [CollectionChange](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework

Środowisko wykonawcze systemu Windows aplikacje używające języka C# lub Visual Basic projektu IMap \<K,V> jako IDictionary \<K,V> .

## <a name="mapremove-method"></a><a name="remove"></a>Map:: Remove — Metoda

Usuwa określoną parę klucz-wartość z bieżącego obiektu mapy.

### <a name="syntax"></a>Składnia

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Część klucza pary klucz-wartość. Typ *klucza* to TypeName *K*.

## <a name="mapsize-method"></a><a name="size"></a>Map:: size — Metoda

Zwraca liczbę elementów [Windows:: IKeyValuePair \<K,V> :: Collections](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) .

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w mapie.

## <a name="see-also"></a>Zobacz także

[Kolekcje (C++/CX)](collections-c-cx.md)<br/>
[Przestrzeń nazw platformy](platform-namespace-c-cx.md)<br/>
[Tworzenie składników środowisko wykonawcze systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
