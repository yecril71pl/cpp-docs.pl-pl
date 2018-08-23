---
title: 'Platform::Collections:: map, klasa | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 01/18/2018
ms.technology: cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6831369f6327b7cef38b1a4f15013f1e3ff4043
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608991"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections:: map, klasa

Reprezentuje *mapy*, który stanowi kolekcję par klucz wartość.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>Parametry

*K*  
 Typ klucza w pary klucz wartość.

*V*  
Typ wartości w pary klucz wartość.

*C*  
Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w mapie. Domyślnie [std::less\<K >](../standard-library/less-struct.md).

*__is_valid_winrt_type()*  
Funkcja wygenerowanego przez kompilator, która sprawdza typ *K* i *V* zawiera przyjazny komunikat o błędzie, jeśli typ nie może być przechowywany w mapie.

### <a name="remarks"></a>Uwagi

Dozwolone typy to:

- liczby całkowite

- Klasa interfejsu ^

- Klasa ref publicznych ^

- Struktura wartości

- Klasa wyliczeniowa publiczne

Mapa jest zasadniczo otoką [std::map](../standard-library/map-class.md). Jest C++ konkretną implementację [Windows::Foundation::Collections::IMap < Windows::Foundation::Collections::IKeyValuePair\<K, V >>](http://go.microsoft.com/fwlink/p/?LinkId=262408) i [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) typy, które są przekazywane przez publiczny interfejsów Windows Runtime. Jeśli spróbujesz użyć `Platform::Collections::Map` wpisz publiczny wartość zwracana lub parametr, błąd kompilatora C3986 jest wywoływane. Można naprawić błąd, zmieniając typ parametru lub wartości zwracanej do [Windows::Foundation::Collections::IMap\<K, V >](http://go.microsoft.com/fwlink/p/?LinkId=262408).

Aby uzyskać więcej informacji, zobacz [kolekcje](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Map::map](#ctor)|Inicjuje nowe wystąpienie klasy mapy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Map::Clear](#clear)|Usuwa wszystkie pary klucz wartość z bieżącego obiektu mapy.|
|[Map::First](#first)|Zwraca iterator, który określa pierwszy element w mapie.|
|[Map::GetView](#getview)|Zwraca widok tylko do odczytu w bieżącym mapy; oznacza to, że [platform::Collections:: mapview, klasa](../cppcx/platform-collections-mapview-class.md).|
|[Map::HasKey](#haskey)|Określa, czy bieżący mapa zawiera określony klucz.|
|[Map::INSERT](#insert)|Dodaje określoną parę klucz wartość do bieżącego obiektu mapy.|
|[Map::LOOKUP](#lookup)|Pobiera element w określonym kluczu w bieżącym obiekcie mapy.|
|[Map::Remove](#remove)|Usuwa określoną parę klucz wartość z bieżącego obiektu mapy.|
|[Map::size](#size)|Zwraca liczbę elementów w bieżącym obiekcie mapy.|

### <a name="events"></a>Zdarzenia

|||
|-|-|
|Nazwa|Opis|
|[Map::mapchanged —](#mapchanged-event.md) `event`|Występuje po zmianie mapy.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Map`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Namespace:** Platform::Collections

## <a name="clear"></a>  Map::Clear — metoda

Usuwa wszystkie pary klucz wartość z bieżącego obiektu mapy.

### <a name="syntax"></a>Składnia

```cpp
virtual void Clear();
```

## <a name="first"></a>  Metoda map::First

Zwraca iterator, który określa pierwszy element w mapie, lub `nullptr` Jeśli mapa jest pusta.

### <a name="syntax"></a>Składnia

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element w mapie.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratorów zwróconych przez First() jest przypisanie zwracana wartość do zmiennej, która jest zadeklarowana za pomocą **automatycznie** słowem kluczowym dedukcji typu. Na przykład `auto x = myMap->First();`.

## <a name="getview"></a>  Metoda map::GetView

Zwraca widok tylko do odczytu w bieżącym mapy; oznacza to, że [platform::Collections:: mapview, klasa](../cppcx/platform-collections-mapview-class.md), która implementuje [Windows::Foundation::Collections::IMapView\<K, V >] / uwp/api/Windows.Foundation.Collections.IMapView_K_V_) interfejsu.

### <a name="syntax"></a>Składnia

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Wartość zwracana

Element `MapView` obiektu.

## <a name="haskey"></a>  Metoda map::HasKey

Określa, czy bieżący mapa zawiera określony klucz.

### <a name="syntax"></a>Składnia

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*Klucz*  
Klucz, używana do lokalizowania elementu mapy. Typ *klucz* jest typename *K*.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli klucz zostanie znaleziony; w przeciwnym razie `false`.

## <a name="insert"></a>  Map::INSERT, metoda

Dodaje określoną parę klucz wartość do bieżącego obiektu mapy.

### <a name="syntax"></a>Składnia

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parametry

*Klucz*  
Część klucza pary klucz wartość. Typ *klucz* jest typename *K*.

*value*  
Część wartości pary klucz wartość. Typ *wartość* jest typename *V*.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli klucz istniejącego elementu w bieżącym planie odpowiada *klucz* a część wartości tego elementu jest ustawiona na *wartość*. `false` Jeśli nie istniejącego elementu w mapie bieżący pasuje *klucz* i *klucz* i *wartość* parametry są wykonywane w pary klucz wartość, a następnie dodane do bieżącej mapy.

## <a name="lookup"></a>  Metoda map::LOOKUP

Pobiera wartość typu V, który jest skojarzony z określonym kluczem typu K, jeśli klucz istnieje.

### <a name="syntax"></a>Składnia

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*Klucz*  
Klucz, używana do lokalizowania elementu w mapie. Typ *klucz* jest typename *K*.

### <a name="return-value"></a>Wartość zwracana

Wartość, która jest powiązany z *klucz*. Typ wartości zwracanej jest typename *V*.

### <a name="remarks"></a>Uwagi

Jeśli klucz nie istnieje, a następnie [Platform::OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md) zgłaszany.

## <a name="ctor"></a>  Map::map konstruktora

Inicjuje nowe wystąpienie klasy mapy.

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

*InIt*  
Element typename bieżącej mapy.

*Comp*  
Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w mapie.

*m*  
Odwołanie lub [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do `map Class` używany do zainicjowania bieżącej mapy.

*pierwszy*  
Iterator danych wejściowych pierwszego elementu w zakresie elementów używane do zainicjowania bieżącej mapy.

*ostatni*  
Iterator danych wejściowych w pierwszym elementem po szereg elementów używane do zainicjowania bieżącej mapy.

## <a name="mapchanged"></a>  Map::mapchanged — zdarzenie

Wywoływane, gdy element jest wstawiony lub usuwany z mapy.

### <a name="syntax"></a>Składnia

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

A [MapChangedEventHandler\<K, V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler) zawierający informacje dotyczące obiektu, który podniósł zdarzenie i rodzaju zmiany, który wystąpił. Zobacz też [IMapChangedEventArgs\<K >](http://msdn.microsoft.com/library/windows/apps/br226034.aspx) i [wyliczenie CollectionChange](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx).

## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework

Aplikacje środowiska wykonawczego Windows, które używają języka C# lub Visual Basic projektu IMap\<K, V > jako element IDictionary\<K, V >.

## <a name="remove"></a>  Metoda map::Remove

Usuwa określoną parę klucz wartość z bieżącego obiektu mapy.

### <a name="syntax"></a>Składnia

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parametry

*Klucz*  
Część klucza pary klucz wartość. Typ *klucz* jest typename *K*.

## <a name="size"></a>  Metoda map::size

Zwraca liczbę [Windows::Foundation::Collections::IKeyValuePair\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) elementów w mapie.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w mapie.

## <a name="see-also"></a>Zobacz też

[Namespace platformy](platform-namespace-c-cx.md)  
[Tworzenie składników środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)  
