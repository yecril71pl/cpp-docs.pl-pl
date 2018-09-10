---
title: 'Platform::Collections:: unorderedmap — klasa | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2050be008f89ff2d125842d5919407dc292eed40
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105838"
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap — Klasa

Reprezentuje nieuporządkowaną *mapy*, który stanowi kolekcję par klucz wartość.

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
Typ klucza w pary klucz wartość.

*V*<br/>
Typ wartości w pary klucz wartość.

*C*<br/>
Typ, który dostarcza obiekt funkcji, która może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w mapie. Domyślnie [std::equal_to\<K >](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Uwagi

Dozwolone typy to:

- liczby całkowite

- Klasa interfejsu ^

- Klasa ref publicznych ^

- Struktura wartości

- Klasa wyliczeniowa publiczne

**UnorderedMap** jest zasadniczo otoką [std::unordered_map](../standard-library/unordered-map-class.md) , która obsługuje przechowywanie typów środowiska wykonawczego Windows. Jest konkretną implementację [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) i [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) interfejsów Windows Runtime typy, które są przekazywane przez publiczny. Jeśli spróbujesz użyć `Platform::Collections::UnorderedMap` wpisz publiczny wartość zwracana lub parametr, błąd kompilatora C3986 jest wywoływane. Można naprawić błąd, zmieniając typ parametru lub wartości zwracanej do [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Aby uzyskać więcej informacji, zobacz [kolekcje](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Unorderedmap::unorderedmap —](#ctor)|Inicjuje nowe wystąpienie klasy mapy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Unorderedmap::Clear —](#clear)|Usuwa wszystkie pary klucz wartość z bieżącego obiektu mapy.|
|[Unorderedmap::First —](#first)|Zwraca iterator, który określa pierwszy element w mapie.|
|[Unorderedmap::getview —](#getview)|Zwraca widok tylko do odczytu w bieżącym mapy; oznacza to, że klasa platform::Collections:: unorderedmapview.|
|[UnorderedMap::HasKey](#haskey)|Określa, czy bieżący mapa zawiera określony klucz.|
|[Unorderedmap::INSERT —](#insert)|Dodaje określoną parę klucz wartość do bieżącego obiektu mapy.|
|[Unorderedmap::LOOKUP —](#lookup)|Pobiera element w określonym kluczu w bieżącym obiekcie mapy.|
|[Unorderedmap::Remove —](#remove)|Usuwa określoną parę klucz wartość z bieżącego obiektu mapy.|
|[Unorderedmap::size —](#size)|Zwraca liczbę elementów w bieżącym obiekcie mapy.|

### <a name="events"></a>Zdarzenia

|||
|-|-|
|Nazwa|Opis|
|[Map::mapchanged —](#mapchanged) zdarzeń|Występuje po zmianie mapy.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`UnorderedMap`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Namespace:** Platform::Collections

## <a name="clear"></a>  Unorderedmap::Clear — metoda

Usuwa wszystkie pary klucz wartość z bieżącego obiektu UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual void Clear();
```

## <a name="first"></a>  Unorderedmap::First — metoda

Zwraca iterator, który określa pierwszy [Windows::Foundation::Collections::IKeyValuePair\<K, V >](https://msdn.microsoft.com/library/windows/apps/br226031.aspx) element mapy nieuporządkowanej.

### <a name="syntax"></a>Składnia

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element w mapie.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratorów zwróconych przez First() jest przypisanie zwracana wartość do zmiennej, która jest zadeklarowana za pomocą **automatycznie** słowem kluczowym dedukcji typu. Na przykład `auto x = myUnorderedMap->First();`.

## <a name="getview"></a>  Unorderedmap::getview — metoda

Zwraca bieżący UnorderedMap; widok tylko do odczytu oznacza to, że [platform::Collections:: unorderedmapview — klasa](../cppcx/platform-collections-unorderedmapview-class.md) implementującej [interfejs Windows::Foundation::Collections::IMapView::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_).

### <a name="syntax"></a>Składnia

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Wartość zwracana

`UnorderedMapView` Obiektu.

## <a name="haskey"></a>  Unorderedmap::haskey — metoda

Określa, czy bieżący UnorderedMap zawiera określony klucz.

### <a name="syntax"></a>Składnia

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz, używana do lokalizowania elementu UnorderedMap. Typ *klucz* jest typename *K*.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli klucz zostanie znaleziony; w przeciwnym razie `false`.

## <a name="insert"></a>  Unorderedmap::INSERT — metoda

Dodaje określoną parę klucz wartość, jak bieżący obiekt UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Część klucza pary klucz wartość. Typ *klucz* jest typename *K*.

*value*<br/>
Część wartości pary klucz wartość. Typ *wartość* jest typename *V*.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli klucz istniejącego elementu w bieżącym planie odpowiada *klucz* a część wartości tego elementu jest ustawiona na *wartość*. `false` Jeśli nie istniejącego elementu w mapie bieżący pasuje *klucz* i *klucz* i *wartość* parametry są wykonywane w pary klucz wartość i następnie dodawane do bieżącego UnorderedMap.

## <a name="lookup"></a>  Unorderedmap::LOOKUP — metoda

Pobiera wartość typu V, który jest skojarzony z określonym kluczem typu K.

### <a name="syntax"></a>Składnia

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz, używana do lokalizowania elementu w UnorderedMap. Typ *klucz* jest typename *K*.

### <a name="return-value"></a>Wartość zwracana

Wartość, która jest powiązany z *klucz*. Typ wartości zwracanej jest typename *V*.

## <a name="mapchanged"></a>  UnorderedMap::MapChanged

Wywoływane, gdy element jest wstawiony lub usuwany z mapy.

### <a name="syntax"></a>Składnia

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

A [MapChangedEventHandler\<K, V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler) zawierający informacje dotyczące obiektu, który podniósł zdarzenie i rodzaju zmiany, który wystąpił. Zobacz też [IMapChangedEventArgs\<K >](https://msdn.microsoft.com/library/windows/apps/br226034.aspx) i [wyliczenie CollectionChange](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx).

## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework

Aplikacje środowiska wykonawczego Windows, czy nam C# lub Visual Basic projektu IMap\<K, V > jako element IDictionary\<K, V >.

## <a name="remove"></a>  Unorderedmap::Remove — Metoda

Usuwa określoną parę klucz wartość z obiektu UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Część klucza pary klucz wartość. Typ *klucz* jest typename *K*.

## <a name="size"></a>  Unorderedmap::size — metoda

Zwraca liczbę [Windows::Foundation::Collections::IKeyValuePair\<K, V >](https://msdn.microsoft.com/library/windows/apps/br226031.aspx) elementów w UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w mapie nieuporządkowane.

## <a name="ctor"></a>  Unorderedmap::unorderedmap — Konstruktor

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

*InIt*<br/>
Element typename UnorderedMap bieżącego.

*P*<br/>
Obiekt funkcji, która może porównać dwa klucze, aby sprawdzić, czy są równe. Ten parametr [std::equal_to\<K >](../standard-library/equal-to-struct.md).

*H*<br/>
Obiekt funkcji, która generuje wartość skrótu dla kluczy. Ten parametr [wyznaczania wartości skrótu klasy 1](../standard-library/hash-class.md) dla typów klucza, który obsługuje klasy.

*m*<br/>
Odwołanie lub [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std::unordered_map](../standard-library/unordered-map-class.md) używany do zainicjowania UnorderedMap bieżącego.

*il*<br/>
A [std::initializer_list](../standard-library/initializer-list-class.md) z [std::pair](../standard-library/pair-structure.md) obiektów, które służy do inicjowania mapy.

*pierwszy*<br/>
Iterator danych wejściowych pierwszego elementu w zakresie elementów używane do zainicjowania UnorderedMap bieżącego.

*ostatni*<br/>
Iterator danych wejściowych od szeregu elementów używane do zainicjowania bieżącego UnorderedMap pierwszego elementu.

## <a name="see-also"></a>Zobacz także

[Namespace platformy](platform-namespace-c-cx.md)<br/>
[Platform::Collections, przestrzeń nazw](../cppcx/platform-collections-namespace.md)<br/>
[Platform::Collections::Map, klasa](../cppcx/platform-collections-map-class.md)<br/>
[Platform::Collections::UnorderedMapView, klasa](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[Kolekcje](../cppcx/collections-c-cx.md)<br/>
[Tworzenie składników środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
